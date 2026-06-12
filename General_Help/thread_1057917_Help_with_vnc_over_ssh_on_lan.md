---
title: "Help with vnc over ssh on lan"
date: 2009-02-02
forum: General Help
---

### Post by composites on 2009-02-02
Hello,

I recently installed ubuntu 8.04 on a desktop I intended to use as a file server. It will be headless, so I wanted to connect using VNC over SSH on a LAN. I followed the [HOWTO: Setup vncserver + gdm on Ubuntu 8.04 Desktop](http://ubuntuforums.org/showthread.php?t=795036&highlight=vnc+gdm) guide.

My laptop currently dual boots xp/ubuntu. I have been able to tunnel through SSH and load VNC using xp, but not using ubuntu. I have read [VNC over SHH](https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH) but still having problems.

```
ssh -L 5901:localhost:5901 michael@192.168.1.7:54322
```
yields the error: name of service not known

Any ideas? Cheers

//edit this probably should have been in networking

---

### Post by The Cog on 2009-02-02
The ssh port number must be specified with a -p option, not a colon after the hostname. Try:
ssh -L 5901:localhost:5901 -p 54322 michael@192.168.1.7

---

### Post by composites on 2009-02-04
Doh, I actually knew about the -p switch, been staring at the screen too long :p

Thanks for pointing out my mistake.

---

