---
editable: false
---

# MAVG

_Window functions_

#### Syntax {#syntax}


```
MAVG( value, rows_1 [ , rows_2 ] [ TOTAL | WITHIN [ dim1, ... ] | AMONG [ dim1, ... ] ] [ ORDER BY ... ] )
```

#### Description {#description}
Returns the moving average of values in a fixed-size window defined by the sort order and arguments:

| `rows_1`   | `rows_2`   | Window                                                                |
|:-----------|:-----------|:----------------------------------------------------------------------|
| positive   | -          | The current row and `rows_1` preceding rows.                          |
| negative   | -          | The current row and -`rows_1` following rows.                         |
| any sign   | any sign   | `rows_1` preceding rows, the current row and `rows_2` following rows. |


Window functions with a similar behavior: [MSUM](MSUM.md), [MCOUNT](MCOUNT.md), [MMIN](MMIN.md), [MMAX](MMAX.md).

See also [AVG](AVG.md), [RAVG](RAVG.md).

**Argument types:**
- `value` — `Number`
- `rows_1` — `Number (whole)`
- `rows_2` — `Number (whole)`


**Return type**: Same type as (`value`)

{% note info %}

Only constant values are accepted for arguments (`rows_1`, `rows_2`).

{% endnote %}

{% note warning %}

The sorting order is based on the fields listed in the chart's sorting section and in the function's `ORDER BY` clause. First, `ORDER BY` fields are used, and then they are complemented by the fields from the chart.


{% endnote %}


#### Examples {#examples}

```
MAVG([Profit], -2)
```

```
MAVG([Profit], 3)
```

```
MAVG([Profit] 5, 5 TOTAL)
```

```
MAVG([Profit], -5 WITHIN [Date])
```

```
MAVG([Profit], -5 AMONG [Date])
```


#### Data source support {#data-source-support}

`Materialized Dataset`, `ClickHouse 1.1`, `Microsoft SQL Server 2017 (14.0)`, `MySQL 5.6`, `Oracle Database 12c (12.1)`, `PostgreSQL 9.3`.
