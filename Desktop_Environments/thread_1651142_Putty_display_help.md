---
title: "Putty display help?"
date: 2010-12-22
forum: Desktop Environments
---

### Post by drummeralec on 2010-12-22
Hi all,

   What I'm trying to is have the ability to type something like "firefox" into the Putty terminal and have firefox open on the HOST screen (on the computer running ubuntu).

   I can get Xming to work on the windows computer so i can open the linux apps on the windows machine, but I still can't figure out how to point the DISPLAY location to the host machine. Any help? 

-Alec

---

### Post by drummeralec on 2010-12-22
Just figured it out -
$ export DISPLAY=":0.0"

---

