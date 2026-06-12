---
title: "Shutdown and reboot on Xfce"
date: 2005-05-27
forum: Desktop Environments
---

### Post by cutOff on 2005-05-27
Hi all,

On Xfce 4.2 when I'm going to shutdown or reboot the machine, it asks me for root password. For me, it's a rather annoying behaviour.

Does anyone know how to avoid this??

I've looked for about this in google and I found a possible [solution](http://www.os-cillation.de/cgi-bin/yabb/YaBB.cgi?board=deb-help;action=display;num=1109528966)  but it didn't works for me.

Any suggestion are welcome.

Thanx

---

### Post by cutOff on 2005-05-27
bump

---

### Post by cutOff on 2005-05-30
bump?  ](*,)

---

### Post by bluex on 2005-10-16
Hi

i've had same problem and i fixed it by removing my user from the admin group.
I don't know why but right afer i disabled the xfce users possibility to act as root via sudo i was able to shutdown my computer without entering a password.

But important: create another user first which still has root rights!

---

### Post by john_c on 2005-10-22
Adding the following line at the end of /etc/sudoers will allow all users to shutdown or reboot the computer without a password:

 ALL ALL=NOPASSWD: /usr/sbin/xfsm-shutdown-helper

Use "sudo visudo" to change the file.

This was covered at the bottom of the link that you found - I have used it on several systems and it works for me.

Hope this is of some help,

John_c

---

### Post by doobit on 2006-05-30
Also, if you just wait a minute, it will shutdown without a password anyway.

---

### Post by Nopposan on 2007-01-04
Suppose that I don't want my user to be able to execute other commands with sudo?  I'm trying to enforce internet filtering and if any user can just $sudo mousepad /.config/whatever then all my efforts at installing DansGuardian etc. are probably wasted.

I know, I should $man sudo.  O.K., I'll do that when I get home but I'm on a Windows computer at the moment.

Thanks.

---

