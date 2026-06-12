---
title: "Streamtuner Help"
date: 2006-06-23
forum: Desktop Environments
---

### Post by lonelypauly on 2006-06-23
Was following some instructions I found online about configuring streamripper within streamtuner.  everything seems to work fine, except...my streams aren't saving where i can find them...below are my settings for ripping streams. i want to save them in /home/paul/music/ what am i doing wrong? i am very happy with ubuntu but i totally suck at the command line.

x-terminal-emulator -e streamripper %q  /home/paul/music/ -r -q

---

### Post by lazyd2 on 2006-06-23
It should be *x-terminal-emulator -e streamripper %q **-d** /your/directory/here -r -q*

---

### Post by lonelypauly on 2006-06-24
thanks for the info, BUT...now it gives me Error 33...(http: 404 Not Found)

any ideas?  i had it working wonderfully under breezy.

---

