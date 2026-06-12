---
title: "interrupting boot and escaping to text mode ?"
date: 2012-10-28
forum: Desktop Environments
---

### Post by raalst on 2012-10-28
HI all, 

I was busy allowing my raspi to use the X11 on my desktop ubuntu (12.04), using some instructions on the web. 
<from memory> I edited /etc/gdm/lightdm.conf, and /etc/x11/<someconffile>
but not the /etc/gdm/gdm.schema, which is probably what is causing the trouble. 

after a reboot, I now find that logging on acts normally, I boot, I get bios screen, no grub(as always), I get the graphic login screen, type my  password. then the screen briefly gets black and the logon screen returns. 

the guest session cannot sudo (why ?), ssh from the network is refused (probably still default). using a boot-cd I cannot change the data on the disk

So, I'm locked out. this post is from the guest account

I'm sure there is a way to interrupt the boot sequence and prevent getting into graphic mode but I do not know it.  
Can anybody point me to some documentation or hand me the right words to google on ? I have found nothing helpful using the words I could imagine. 

Thanks a lot !

Regards, 
Ronald van Aalst

---

### Post by steeldriver on 2012-10-28
> **raalst said:**
> 
after a reboot, I now find that logging on acts normally, I boot, I get bios screen, no grub(as always), I get the graphic login screen, type my  password. then the screen briefly gets black and the logon screen returns. 


Sounds like your X session is failing to start - you can check your ~/.xsession-errors file, also often worth checking the ownership / permissions on your ~/.Xauthority and ~/.ICEauthority files (should be user:user and mode 600)

> **raalst said:**
> 
the guest session cannot sudo (why ?), ssh from the network is refused (probably still default). using a boot-cd I cannot change the data on the disk


The guest account cannot sudo because 'guest' is not a member of the sudo group (for obvious reasons). An SSH server is not installed by default in the desktop editions. To fix things via the recovery console you will likely need to remount the filesystem with read-write permissions:

```
# mount -o remount,rw /
```You should also be able to login to a virtual terminal (Ctrl-Alt-F1 etc.) and fix things from there.

---

### Post by raalst on 2012-10-28
I was looking and hoping for that last sentence !

CTRL-ALT-F1, let's see...

---

### Post by raalst on 2012-10-28
Yep, CTRL ALT F1 gave me a working (text) logon again, with root/sudo privileges.
 
The problem proper seems to be linked to my NVIDIA graphics card. but 
I can now at least do something about it again.
 
THANKS !
 
Regards, 
Ronald

---

