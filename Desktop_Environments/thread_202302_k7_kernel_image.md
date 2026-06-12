---
title: "k7 kernel image"
date: 2006-06-23
forum: Desktop Environments
---

### Post by geforceter on 2006-06-23
Hello...
I installed ubuntu and all was working fine.
i followed the last tip here [link]("http://tips.linux.com/tips/06/06/08/1651225.shtml?tid=50&tid=92&tid=96")

It said that the kernel that come with Ubuntu is not really configured for an AMD cpu and its configured so that any pc can run ubuntu...

So i got to Synaptic and searched for "linux-image" and then ticked the k7 one.

Now when i boot Ubuntu with K7 kernal, X server is not working. But there is still a backup of the old kernel so i assume the old kernel will work.

So should i continue with the default kernal or will i get a very good performance boost with the k7 image?

I have a AMD Athlon Xp 2800+ and nvidia geforce 6600gt and dell LCD . I also installed Automatix and its nvidia drivers.

I think i was abit greedy to ask for a performance boost...


Pls help

---

### Post by mips on 2006-06-23
reconfigure the xserver or if you have nvidia drivers you will have to reinstall them.

---

### Post by tseliot on 2006-06-23
Turn on your computer and boot in Recovery Mode (select it in the GRUB menu)

then (after it boots) type:
```
apt-get install linux-k7
```

and reboot by typing:
```
reboot
```

Boot as usual and this time the xserver will not fail.

---

### Post by geforceter on 2006-06-23
lol...
Thats a faster reply than an irc support
Will try tseliot's solution... 

thanks alot for your reply...awesome

---

### Post by Jucato on 2006-06-23
Did you install the nvidia driver (nvidia-glx) before (in the older kernel)?
If yes, you have to also install the matching linux-restricted-modules and install the nvidia driver again. 

Which k7 kernel version did you install, btw (2.6.15-*XX*-k7)??

---

### Post by geforceter on 2006-06-23
[QUOTE=Fenyx]Did you install the nvidia driver (nvidia-glx) before (in the older kernel)?
If yes, you have to also install the matching linux-restricted-modules and install the nvidia driver again. 

Which k7 kernel version did you install, btw (2.6.15-*XX*-k7)??[/QUOTE]


ya i installed it thru Automatix...i forgot which k7 kernal i installed there were two options i remeber

how do i install the matching linux-restricted-modules and install the nvidia driver again?

i am abut of a linux noob...

---

### Post by Jucato on 2006-06-23
follow what tseliot said. that will install the appropriate linux-restricted-modules

---

### Post by geforceter on 2006-06-23
[QUOTE=Fenyx]follow what tseliot said. that will install the appropriate linux-restricted-modules[/QUOTE]

followed wat tseliot said. it working now...
do i still need to reinstall the nvidia drivers again(if yes how?)? it flashed the nvidia logo before the login screen.

can i follow the instructions here to install XGL ? [link]("http://www.ubuntuforums.org/showthread.php?t=127090")
or should i just go to synaptic search for xgl and install from there considering i am new to ubuntu...?

---

### Post by Jucato on 2006-06-23
no need to reinstall the nvidia driver. I guess just installing the proper linux-restricted-modules did the trick

I'm not so sure about XGL. Had no experience with it. Sorry.

---

### Post by tseliot on 2006-06-23
[QUOTE=geforceter]followed wat tseliot said. it working now...
do i still need to reinstall the nvidia drivers again(if yes how?)? it flashed the nvidia logo before the login screen.[/QUOTE]
No

[QUOTE=geforceter]can i follow the instructions here to install XGL ? [link]("http://www.ubuntuforums.org/showthread.php?t=127090")
or should i just go to synaptic search for xgl and install from there considering i am new to ubuntu...?[/QUOTE]
XGL can break you system.

---

