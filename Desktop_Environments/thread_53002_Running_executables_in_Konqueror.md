---
title: "Running executables in Konqueror"
date: 2005-07-29
forum: Desktop Environments
---

### Post by kreso on 2005-07-29
How can I do it?

the only way to run executables is by opening Konsole and typing ./executable-name

What I'd like is to run the program when I double click the program's icon in Konqueror.

---

### Post by godzero on 2005-07-29
Works for me. Look to see if the file has it's executable bit set. Some programs are cli based to the point where they got nothing to do if you click on them. For those, make a shortcut, check "run in terminal".

---

### Post by cwaldbieser on 2005-07-30
[QUOTE=kreso]How can I do it?

the only way to run executables is by opening Konsole and typing ./executable-name

What I'd like is to run the program when I double click the program's icon in Konqueror.[/QUOTE]

Lots of times, you just need to include the full path to the executable.  If that doesn't work, sometimes I just create a shell script like:

```
#! /bin/bash
/full/path/to/executable
```
and give it executable permissions.  Then I can click on that in Konqueror.

---

