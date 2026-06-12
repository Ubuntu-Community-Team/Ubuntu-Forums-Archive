---
title: "[Solved] Pysol and No Sound in Jaunty Jackalope"
date: 2009-04-22
forum: Gaming &amp; Leisure
---

### Post by Sef on 2009-04-22
I installed Jaunty and then pysol via Add/Remove.   It said to 'Install pysol-sound-server and pysol-sounds to get support for sound effects and background music.'   However, after doing that, the sound button is still grayed out, so no sound.   Any ideas of what to do?

---

### Post by sisco311 on 2009-04-22
```
sudo ln -s /usr/lib/python2.5/site-packages/pysolsoundserver.so /usr/share/games/pysol/
```
should solve the problem.


I've found the fix here: [thread]379617[/thread]

It works for me.

---

### Post by Sef on 2009-04-22
That does not work for me.   How do I find what version of python do I have?

---

### Post by sisco311 on 2009-04-22
Do a search for pysolsoundserver.so in /usr/lib :
```
find /usr/lib -name "pysolsoundserver.so"
```

EDIT: the file is installed from pysol-sound-server

```
dpkg-query -S pysolsoundserver.so
```
should also list the location.

---

### Post by Sef on 2009-04-22
[s]I copy the command for the link, but still nothing.   Any other ideas?[/s]

Update: I got sound now.  Thank you for your help.

---

### Post by Ms_Angel_D on 2009-05-27
Can you post how exactly you fixed this issue, I'm having the same problem.

thanks,
Angel

Nevermind I figured out that it was this command

```
sudo ln -s /usr/lib/python2.5/site-packages/pysolsoundserver.so /usr/share/games/pysol/
```

---

