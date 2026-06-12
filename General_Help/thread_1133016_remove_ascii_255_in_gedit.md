---
title: "remove ascii 255 in gedit"
date: 2009-04-22
forum: General Help
---

### Post by lavinog on 2009-04-22
I was making a test script for octave using gedit.
The script was working fine, and I made a change and saved it.
Now octave is complaining:
```
error: invalid character `&#65533;' (ASCII 255) near line 7, column 1
parse error near line 7 of file /home/greg/octave_test.m

  syntax error

```
line 6 is the last line in the file. I tried adding a newline, using delete...etc. Gedit can't remove it, I also dont know where it came from.

Any ideas short of copy and pasting the script to a new file?
Is this a bug?
I am using gedit version 2.24.2 with intrepid.

---

### Post by lavinog on 2009-04-22
It looks like the problem is with octave and not gedit

---

### Post by lavinog on 2009-04-22
Ha...I forgot a closing bracket.
apparently that error means that it reached eof without finding the closing bracket.
I remember now that matlab has some weird language for certain errors.

---

