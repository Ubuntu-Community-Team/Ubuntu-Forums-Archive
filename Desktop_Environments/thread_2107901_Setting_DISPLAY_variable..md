---
title: "Setting DISPLAY variable."
date: 2013-01-23
forum: Desktop Environments
---

### Post by yasirkh on 2013-01-23
Dear All,

I am very new to ubuntu but not to the UNIX world.

Here is my problem: I use to connect to my HP-UX server's CDE via Reflection X. Now I want to do the same via ubuntu. Can I do this using native xterm? or I should use another software in ubuntu to do the same?

Here is what I have tried so far:
Xterm in UBUNTU:

yroot@Y-HP-Compaq:~$ echo $DISPLAY
:0

rlogin root@myserver
password: xxxxx
..
..
..
# echo $DISPLAY
sh: DISPLAY: Parameter not set.
# export DISPLAY=172.20.30.195:0
# xclock
export DISPLAY=172.20.30.195Error: Can't open display: 172.20.30.195:0
Error: Couldn't find per display information
# export DISPLAY=172.20.30.195:0.0
# xclock
Error: Can't open display: 172.20.30.195:0.0
Error: Couldn't find per display information

Please help me in setting the DISPLAY variable correctly. or there is something else that I am missing here?

PS: let me know if this is not the right forum for this question.

TIA,

Yasir.

---

### Post by yasirkh on 2013-01-23
BTW, I am using 12.1

---

### Post by The Cog on 2013-01-23
You probably have to tell your Ubuntu PC to allow incoming X connections before you make the connection to the HP box. Try using this command before doing the remote login:
```
xhost +
```

If you used SSH rather than rlogin, then you could get all the X setup done automatically for you with just the one command, but this of course requires the HP box to be running an SSH server:
```
ssh -X root@myserver
```

---

### Post by yasirkh on 2013-01-23
Thanks a lot. my issue is resolved.

---

