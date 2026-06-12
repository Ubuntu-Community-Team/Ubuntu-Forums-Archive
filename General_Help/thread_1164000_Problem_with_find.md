---
title: "Problem with find"
date: 2009-05-19
forum: General Help
---

### Post by tom56 on 2009-05-19
Hi

Pretty simple question really: why doesn't this command work?
```

find . -name "*.jpg" -o -name "*.nfo" -o -name "*.oldversion" -o -name "*.tbn" -print0 | xargs -0 rm
```

Thanks
Tom

---

### Post by kpkeerthi on 2009-05-19
```

find . -name "*.jpg" -o -name "*.nfo" -o -name "*.oldversion" -o -name "*.tbn" -print0 | xargs -0

```
Does this print anything?

---

### Post by tom56 on 2009-05-19
It seems to only be working on the last expression, i.e. it deletes every file ending in "tbn" but doesn't do the others even though there's plenty of files that match.

---

### Post by sisco311 on 2009-05-19
```
find . \( -name "*.jpg" -o -name "*.nfo" -o -name "*.oldversion" -o -name "*.tbn" \) -print0 | xargs -0
```
or
```
find . \( -name "*.jpg" -o -name "*.nfo" -o -name "*.oldversion" -o -name "*.tbn" \) -exec rm -i {} \;
```

---

### Post by tom56 on 2009-05-19
> **sisco311 said:**
> ```
find . \( -name "*.jpg" -o -name "*.nfo" -o -name "*.oldversion" -o -name "*.tbn" \) -print0 | xargs -0
```
or
```
find . \( -name "*.jpg" -o -name "*.nfo" -o -name "*.oldversion" -o -name "*.tbn" \) -exec rm -i {} \;
```

What was wrong with the way I did it though? I'm just curious :)

---

### Post by kpkeerthi on 2009-05-19
I tried with and without the surrounding \( and \). I got identical results. I wonder why it didn't work for you. :confused:

---

### Post by sisco311 on 2009-05-19
> **tom56 said:**
> What was wrong with the way I did it though? I'm just curious :)

-print0 is an expression and it's always true.
-and is assumed where the operator is omitted.

exp1 -or exp2 = exp2 is not evaluated if exp1 is true:

```
find . -name "*.ex1" -o -name "*.ex2" -a -print0
```
-name "*.ex1" = exp1
( -name "*.ex2" -a -print0 ) = exp2

if the file is a *.ex1 file exp2 is not evaluated so -print0 is not executed. 

```
find . \( -name "*.ex1" -o -name "*.ex2" \) -a -print0
```

( -name "*.ex1" -o -name "*.ex2" ) = exp1
-print0 = exp2 (always true)

either -name "*.ex1" or -name "*.ex2" is true -print0 is executed.

---

### Post by tom56 on 2009-05-19
> **sisco311 said:**
> -print0 is an expression and it's always true.
-and is assumed where the operator is omitted.

exp1 -or exp2 = exp2 is not evaluated if exp1 is true:

```
find . -name "*.ex1" -o -name "*.ex2" -a -print0
```
-name "*.ex1" = exp1
( -name "*.ex2" -a -print0 ) = exp2

if the file is a *.ex1 file exp2 is not evaluated so -print0 is not executed. 

```
find . \( -name "*.ex1" -o -name "*.ex2" \) -a -print0
```

( -name "*.ex1" -o -name "*.ex2" ) = exp1
-print0 = exp2 (always true)

either -name "*.ex1" or -name "*.ex2" is true -print0 is executed.

Thanks, I think I get it now. So the computer was reading it in the following chunks as it were?

find . [-name "*.jpg"] [-o -name "*.nfo"] [-o -name "*.oldversion"] [-o -name "*.tbn" -print0]

So technically, the following works but is butt ugly:
find . -name "*.jpg" -print0 -o -name "*.nfo" -print0 -o -name "*.oldversion" -print0 -o -name "*.tbn" -print0

And the right command all along was
find . \( -name "*.jpg" -o -name "*.nfo" -o -name "*.oldversion" -o -name "*.tbn" \) -print0 |  xargs -0 rm

Thanks for all the help guys!

---

