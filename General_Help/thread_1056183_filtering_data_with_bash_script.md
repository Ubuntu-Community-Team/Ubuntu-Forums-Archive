---
title: "filtering data with bash script"
date: 2009-01-31
forum: General Help
---

### Post by nguyenthanhvuh on 2009-01-31
Hi All - I need to filter out a large amount of data in a file and thought using bash script would be appropriate for this purpose. Greatly appreciate your help

The file has this format

something this is a line a
r3 request 1: 1
something this is a line b
r4 request 1: 0.3
something this is a line c
r5 request 1: 0.6
something this is a line d
r6 request 1: 0.02
something this is a line e
r7 request 1: 0.7

So I want to filter out lines that have score say <= 0.6 , thus the result would look something like

something this is a line b
r4 request 1: 0.3
something this is a line c
r5 request 1: 0.6
something this is a line d
r6 request 1: 0.02

---

### Post by fragos on 2009-01-31
The command you're looking for may be grep. "grep --help" will give you the options. The command to extract all lines with "0.6" would be:

grep 0.6 old.txt > new.txt

---

### Post by heindsight on 2009-01-31
I don't think a bash script would work for this. The problem is that bash only does quite basic integer arithmetic so you while you could extract the floating point numbers from your input lines, I can't think of an easy way to test whether they're larger than 0.6. Maybe you'd be better off writing something in Python.

---

### Post by geirha on 2009-01-31
awk is nice for these kinds of problems.
```
awk '{ if ($4 <= 0.6) print $0 }' <input.txt >output.txt
```
If the fourth field ($4) is less than or equal to 0.6, print the line ($0); otherwise, don't print anything.

---

