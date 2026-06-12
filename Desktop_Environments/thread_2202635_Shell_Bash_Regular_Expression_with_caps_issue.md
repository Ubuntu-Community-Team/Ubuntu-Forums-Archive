---
title: "Shell Bash Regular Expression with caps issue"
date: 2014-01-30
forum: Desktop Environments
---

### Post by diego7 on 2014-01-30
Hi!
I have a little problem with Bash on Ubuntu 13.10

when I use regular expressions with caps it doesnt works as espected.

I have 4 directories: a, A, b, and B.

When i ask for ls

```
ls [A-Z]
```
it shows A: b: and B: directories.

With
```
ls [a-z]
```
it shows a: A: b: and B:

why? :(
(I must use Bash, i cant change for another shell)

---

### Post by steeldriver on 2014-01-30
It's a matter of how the shell glob is interpreted within the current locale I think (these are really globs not regular expressions btw). You can try exporting an appropriate locale - you don't mention what behaviour you want but

```

$ export LC_ALL=C

$ ls [A-Z]
A:

B:

$ ls [a-z]
a:

b:

$ ls [A-z]
A:

B:

a:

b:

```

---

### Post by diego7 on 2014-01-30
Thank you so much. It works :D
(And sorry for the glob mismatch:oops:)

---

