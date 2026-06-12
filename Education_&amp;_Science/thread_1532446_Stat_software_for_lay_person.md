---
title: "Stat software for lay person"
date: 2010-07-16
forum: Education &amp; Science
---

### Post by KegHead on 2010-07-16
Hi!

I'm trying to find a stat program to determine roulette probability.

Is there an easy pkg for a lay person (non-scientist).

Thanks!

KegHead

---

### Post by lkjoel on 2010-07-18
It would be easily possible to program a shell script to do that.
Like:
```
export total
while read line
do
export total=$line
done < total.txt
while read line
do
echo "$line/$total"
done < roulette.txt
```and on total.txt:
```
10
```and on roulette.txt:
```
Red: 3
Blue: 5
Yellow: 2
```And when it runs, it will display:
```
Red: 3/10
Blue: 5/10
Yellow: 2/10
```I hope that can help you!

---

### Post by KegHead on 2010-07-19
Hi!

Thanks!

I'll try.

KegHead

---

