---
title: "Problem in Elementary os when I start up"
date: 2014-05-18
forum: Debian
---

### Post by debdut2 on 2014-05-18
(my comp specs 3 gb ram, 140 amd sempron processor, nvidia geforce graphics card) I deleted win 7 recently and my computer runs elementary os. But when I power on the pc, it opens elementary os but in command interface, after several restart I can get to the desktop through advanced options while boot.

Things that may have caused the problem:(I do know surely)

I tried to update from kernel 3.2 to 3.5 and stopped it in the middile cause I was hearing bad things about it.

By command interface, I mean non- graphical interface like only a black screen with white coloured things written on it. Things written tell me to login , but when I login it shows:
debdut@debdut-System-Product-Name:~$

I can not do anything.

Thanks,
Debdut Karmakar

---

### Post by QIII on 2014-05-18
*Moved to Other **OS/Distro Support***

---

### Post by Stinger on 2014-05-20
Hi Debdut
Welcome to the Ubuntu forums.
If you are familiar with the command line, try this first:
```
sudo dpkg-reconfigure xserver-xorg
```
Type in your password when asked for ( it won't show ) and hit enter.
This should reconfigure the graphical server.
To reboot your computer type:
```
sudo reboot
```
And see if it works

I need to know if you have installed  the driver from nvidia ?
And the specs on the nvidia card too please

You might have broken the nvidia driver when you aborted the 3.5 kernel.

---

