---
title: "Looking For Data Reporting Tool With Graphing"
date: 2009-04-14
forum: General Help
---

### Post by PointyWombat on 2009-04-14
Hi all,

I'm looking for advice on how to digest a lot of data into simple graphs. In the past I've used gnuplot and manual scripts to parse out data to generate graphs which was very tedius and cumbersome and now I'm looking for something better. I'd rather not re-invent the wheel if something is already out there.

This would be to graph out performance data for a disk subsystem and data would be in this kind of format:

```
Date	Time	Volume	IOPS	%READ	KBr/s	KBw/s

040109	1255	ABCD	356	85	2353	227
040109	1255	EFGH	26	100	66	229
040109	1255	IJKL	561	85	3	242
040109	1255	MNOP	3856	65	223	227
040109	1255	QRST	1356	25	53	262
040109	1255	UVWX	2356	85	523	422
040109	1255	YZAB	36	100	355	122
040109	1255	CDEF	3	88	776	322
040109	1300	ABCD	356	85	2353	227
040109	1300	EFGH	26	100	66	229
040109	1300	IJKL	561	85	3	242
040109	1300	MNOP	3856	65	223	227
040109	1300	QRST	1356	25	53	262
040109	1300	UVWX	2356	85	523	422
040109	1300	YZAB	36	100	355	122
040109	1300	CDEF	3	88	776	322
```


(This example represents just two samples of data 5 minutes apart.)

What tool could be used to take this data that I have collecting into a flat file and generate graphs to report stats on something like the Volume name for a period of days, weeks, or even months, for example.

Thanks,

---

