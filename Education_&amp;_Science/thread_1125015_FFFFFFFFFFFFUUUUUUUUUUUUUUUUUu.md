---
title: "FFFFFFFFFFFFUUUUUUUUUUUUUUUUUu"
date: 2009-04-13
forum: Education &amp; Science
---

### Post by u-slayer on 2009-04-13
I wrote a short script to search for different versions of FFFFFFFFFUUUUUU on google:

```
 F="FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF"; U="UUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUU"; for f in `seq 1 25`; do for u in `seq 1 25`; do echo -n "$f $u "; lynx -dump "http://www.google.com/search?hl=en&safe=off&q=`echo $F | head -c $f``echo $U | head -c $u`&btnG=Search" | grep "Results 1 - 10" | sed 's/.*of about //;s/ for.*//;s/,//g'; done; don
```

How do I convert this:
```
3 16 232
3 17 126
3 18 152
3 19 367
3 20 231
3 21 2100
3 22 198
3 23 129
3 24 91
3 25 103
4 1 2540
4 2 341
4 3 1250
4 4 4100
4 5 1520
4 6 2420
4 7 1170
4 8 854
```

Into a 3D graph in open office?

---

