---
title: "Monitor/Shadow LTSP sessions"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Johnathon on 2006-09-19
Hi,

We're in the process of moving a m$ office over to an Ubuntu/LTSP/Thin Client system. Now, the users are OK(ish) with the switch-over, but there are (as you would expect) quite a lot of user-support questions coming our way atm. 

One thing that would really REALLY help us in supporting them, would be to be able to see what they see - so we can watch what they are doing, and talk them through some difficult issues. (We are connected to their network via a VPN.)

Does anyone know of a way to do this? Is there a program from Edubuntu you can use to do it?

Thanks,
Jon

---

### Post by Johnathon on 2006-09-20
*bump*

---

### Post by Johnathon on 2006-09-20
Final *bump*

No one has any idea?

---

### Post by lns on 2006-09-21
Sorry..I just wandered in.

Although I haven't tried it in the field myself, there *is* a "share my desktop" (vnc integration) feature in Gnome. I would assume this would work in an LTSP setting, but I can't say for sure. In Edubuntu Dapper, it is under System -> Administration I believe.

---

### Post by Lem on 2007-11-15
Install thin client manager. (thin-client-manager I believe is the name of the package - currently at work in windows-ville)

You will also need to install x11vnc on your chroot build.

I'm going to be doing a load of work on the wiki this this weekend, including this kind of stuff :)

---

