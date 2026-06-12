---
title: "Ubuntu 12.04 &amp; Dell E6410: screen not powering down"
date: 2012-06-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by artofsnow on 2012-06-26
I'm running Ubuntu 12.04 with the latest updates on my Dell Latitude E6410 with the latest BIOS and the screen doesn't power down (it does blank but backlight stays on) after the defined timeout set like it used to be in the previous versions.

This is the exact same issue as described here: [http://ubuntuforums.org/showthread.php?t=1954960](http://ubuntuforums.org/showthread.php?t=1954960) but there's no solution & the thread is locked.

---

### Post by mwclark4453 on 2012-06-27
having the same problem.

---

### Post by darthwouter on 2012-08-29
I am also having this problem. Has anyone had any luck? all the threads regarding this issue are fairly old.
The closest I've gotten is by using the command  > xset dpms force offwhich does turn off the backlight but only for a short period of time when you move the mouse or use the keyboard after the command has been run

---

### Post by eorz on 2012-10-17
I had the same problem.
I solved the issue by installing the new Nvidia drivers (version 304.51).
I used the x-swat PPA:[INDENT]
[LIST]
[*][COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/COLOR]
[*][COLOR=red]sudo apt-get update[/COLOR]
[*][COLOR=red]sudo apt-get install nvidia-current[/COLOR]
[/LIST]
[/INDENT]I hope I helped someone...

---

### Post by zhocchao on 2012-10-21
Changing the driver to the "post-release updates" driver in "Additional drivers" fixed it.

---

### Post by mk4umha on 2012-10-25
That worked, thanks!

---

### Post by gerrman97 on 2012-11-08
it seems that many people are having this problem. i just reinstalled ubuntu and that worked. i doubt it will work for anyone else though. mine was because the wubi.exe installer got messed up.

---

