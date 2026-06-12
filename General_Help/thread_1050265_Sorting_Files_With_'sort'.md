---
title: "Sorting Files With 'sort'"
date: 2009-01-25
forum: General Help
---

### Post by xluryan on 2009-01-25
sort is an awesome utility, but either it's not working correctly, or I'm confused about how it should be working here.

Take this sample input file:
```

a .100  abcd
b .99   aabc
c .92   bdca
d .108  baba
e .7    dacb
f .56   aaab

```

The second field is ***not*** a decimal place. The period is only to signify a certain type of field in my application, and is not to be concerned with the numeric value superseding it. Therefore, we have the current values for field 2: 100, 99, 92, 108, 7, and 56. In descending order those would be: 108, 100, 99, 92, 56, and 7. However, using the following sort command does not produce those results:

```

$ sort -k 2nr test
b .99   aabc
c .92   bdca
e .7    dacb
f .56   aaab
d .108  baba
a .100  abcd

```

So what I would like to do is specify that it start with character 2 of field 2. However, that also does not appear to be functioning as I would expect:

```

$ sort -k 2.2nr test
b .99   aabc
c .92   bdca
e .7    dacb
f .56   aaab
d .108  baba
a .100  abcd

```

I have also experimented by trying to choose the second character position in field 3, but that has also yielded less than positive results:

```

$ sort -k 3.2 test
f .56   aaab
b .99   aabc
a .100  abcd
d .108  baba
c .92   bdca
e .7    dacb

```

Can someone tell me what I'm doing wrong? I'd hate to blame it on the sort command, but I can't see where my logic is incorrect... Thanks in advance :)

---

### Post by heindsight on 2009-01-25
Try
```
sort -k 2 -t . -nr test
```
the -t . option tells sort to use . as a field separator, so using that in conjunction with -k 2 will cause sort to ignore the first part of each line (up to and including the first .) when comparing lines.

---

### Post by xluryan on 2009-01-25
> **heindsight said:**
> Try
```
sort -k 2 -t . -nr test
```
the -t . option tells sort to use . as a field separator, so using that in conjunction with -k 2 will cause sort to ignore the first part of each line (up to and including the first .) when comparing lines.

What would you propose for the third field and second character then?

---

### Post by heindsight on 2009-01-25
To sort on field 2, ignoring the . you could also use:
```
sort -k 2.3,2 -nr test
```
OR
```
sort -b -k 2.2,2 -nr test
```

The reason for using the -k 2.3 is that the space between fields 1 and 2 is considered part of field 2. The -b option changes that behaviour by causing sort to ignore leading blanks in fields.

The reason that ```
sort -k 3.2 test
``` didn't work for you, is once again, because of the leading blanks. In this case, because you have a different number of leading blanks in field 3 in each line, you have to use the -b option:
```
sort -bk 3.2 test
```

---

### Post by xluryan on 2009-01-25
Very nice. This *does* work for the 3rd field. But when I tried on the 2nd field, I still didn't get correct results:

3rd Field:
```

$ sort -bk 3.3 test
f .56   aaab
d .108  baba
b .99   aabc
c .92   bdca
e .7    dacb
a .100  abcd

```

2nd Field:
```

$ sort -bk 2.2,2nr test
b .99   aabc
c .92   bdca
e .7    dacb
f .56   aaab
d .108  baba
a .100  abcd

```

---

### Post by heindsight on 2009-01-25
> **xluryan said:**
> But when I tried on the 2nd field, I still didn't get correct results:

2nd Field:
```

$ sort -bk 2.2,2nr test
b .99   aabc
c .92   bdca
e .7    dacb
f .56   aaab
d .108  baba
a .100  abcd

```

Strange, I looked over the info page for sort and according to that
```
sort -bk 2.2,2n test
```
OR
```
sort -bk 2.2n,2 test
```
OR
```
sort -bnk 2.2,2 test
```
should all produce the same results, but they don't - only the last one (ie supplying -n as a global option instead of just attached to the field) works.

Not sure why - a bug maybe?

---

### Post by xluryan on 2009-01-26
Either it's a bug, or the developers just intended to use global sort options versus per field options.

In any case, thanks for your help :)

---

### Post by heindsight on 2009-01-26
> **xluryan said:**
> Either it's a bug, or the developers just intended to use global sort options versus per field options.

In any case, thanks for your help :)

I would consider it a bug either way. Being able to use per field options is a very useful feature. I've had a look on launchpad and I don't see any bug reports related to this. I'm going to do a bit more experimenting to see exactly what works and what doesn't and then I'll file a report (and post a link to the bugreport here).

---

### Post by xluryan on 2009-01-26
Awesome! Keep me updated.

---

### Post by heindsight on 2009-01-26
Looks like it's not a bug after all but rather a case of me misunderstanding the documentation. It appears that if you supply key-specific options, then no global options are applied to that key.

For example, if test.in looks like:
```
a  a100
b  b20
g  g30
a  a40
n  n10
b  b25
m  m10
```

Then ```
sort -bk 2.2,2n test.in
``` produces:
```
a  a100
a  a40
b  b20
b  b25
g  g30
m  m10
n  n10

``` because the -b option is not applied to the specified key. However if we do ```
sort -bnk 2.2,2 test.in
``` OR ```
sort -k 2.2b,2bn test.in
``` OR ```
sort -k 2.2b,2n test.in
``` we get the expected output:
```
m  m10
n  n10
b  b20
b  b25
g  g30
a  a40
a  a100
```

Interestingly, while it doesn't matter where we put the 'n' (ie. -k 2.2n,2  -k 2.2,2n and -k 2.2n,2n are all equivalent) it does matter where we put the 'b': -k 2.2b,2bn and -k 2.2b,2n both work as expected but if we use -k 2.2,2bn then the 'b' seems to have no effect.

---

### Post by xluryan on 2009-01-26
That's very counter-intuitive, although I'm sure they had their reasons when they created it that way. Unless that was not their intent.

It perplexes me as to why sort options are allowed after the 2nd field position indicator, yet the -b flag is not. I suppose I should say *ineffective* rather than *not allowed*. Very interesting...

***edit***
Looking again at the man file, it does say:
```

POS is F[.C][OPTS]

```

I suppose it told us right there that the options go directly after the field and/or character position, and **not** after the 2nd field position. I completely missed that :-s

---

### Post by heindsight on 2009-01-26
It is a bit counter intuitive, but in a way it makes sense.

You can put the options after the first or second POS and for all options except 'b' it makes no difference whether you put it after the first, second or both. 

It's not clear from the documentation what differences are between putting 'b' after the first, after the second or after both position indicators. It seems clear from my experiments that putting 'b' after the first POS causes leading blanks to be ignored for the field. Perhaps putting it after the second POS ignores trailing blanks (eg if the -t option is used).

---

### Post by xluryan on 2009-01-26
I was thinking the same thing. This definitely clears things up about *sort* for me. Thanks again for all your help :)

---

