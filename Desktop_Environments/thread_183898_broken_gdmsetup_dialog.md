---
title: "broken gdmsetup dialog"
date: 2006-05-28
forum: Desktop Environments
---

### Post by Iandefor on 2006-05-28
As the title says. Using the menu entry, gdmsetup will appear for just an instant, then it'll disappear. Anybody have any clues? I'm stumped.

---

### Post by bluevoodoo1 on 2006-05-28
Try opening it in the terminal to see what might be going on.

gksudo gdmsetup

---

### Post by Iandefor on 2006-05-28
[quote=bluevoodoo1]Try opening it in the terminal to see what might be going on.

gksudo gdmsetup[/quote] Did that. Doesn't return anything.

---

### Post by charnov on 2006-05-29
I tried that and it spit out a segmentation fault.

May 29 00:41:08 localhost kernel: [  335.821785] gdmsetup[5481]: segfault at 0000000000000000 rip 00002aaaacd18ae0 rsp 00007fffffaf81f8 error 4

---

### Post by Pausanias on 2006-05-29
Here is the solution:

[http://www.ubuntuforums.org/showthread.php?t=172368](http://www.ubuntuforums.org/showthread.php?t=172368)

---

### Post by Iandefor on 2006-05-29
[quote=Pausanias]Here is the solution:

[http://www.ubuntuforums.org/showthread.php?t=172368]("http://www.ubuntuforums.org/showthread.php?t=172368")[/quote] Oh, excellent! I just applied the fix, will see how it works on reboot. Thanks!

---

### Post by dpm on 2006-05-31
Seeing that this is still happening, might it be worth reopening the bug?

[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/42712](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/42712)

---

