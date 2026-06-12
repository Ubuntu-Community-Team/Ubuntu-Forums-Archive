---
title: "Idle users in X"
date: 2005-05-25
forum: Desktop Environments
---

### Post by gmc on 2005-05-25
Hello All,

I'm trying to set a time limit for idle users in an X session. I played with autolog, but it would not log the user out (well it would close down terminal sessions running in X). I've found that the variable TMOUT=<seconds> can be used to automatically log idle users out. The problem is I'm not sure where to set it so that X users get logged out. Anyone have any ideas?

G

P.S. I also tried idled but there's no package for it and it refuses to compile :-(

---

### Post by Alexander Kirillov on 2005-05-26
Try /etc/profile

---

### Post by gmc on 2005-05-27
Hi,

I did try but without success. The other thing about /etc/profile is that it can (and has been) upgraded on occasion. I found that /etc/enviroment is a better place to put/set global enviroment variables.

However TMOUT=<sec> does not work in Xwindows (cli shells not included). So I'm back to the drawing board. Perhaps someone out there has figured out what to put in /etc/autolog.conf to handle X sessions. I tried /dev/pts* but that didn't work. 

I can't believe there aren't any internet cafe's that are using linux or that someone hasn't had the need to do this. Even google and yahoo searches have turned up no solutions.

G

---

