---
title: "Beryl crashed my x system"
date: 2007-03-11
forum: Desktop Environments
---

### Post by dmg025 on 2007-03-11
after installing beryl with directins directly from the beryl site.  I rebooted my computer as instructed and upon the restart Nvidia gave me a message that the x system could not be logged into.  I think that the problem may be that the Nvidia drivers installed with beryl conflicted with the Nvidia driver I installed on my own (Geforce 6800 and I installed the newest 9755 drivers).  Anyone have any advice?  Thanks in advance

---

### Post by raul_ on 2007-03-11
To get started, if you did a backup of xorg.conf do a 

```

sudo cp /etc/X11/xorg.conf.backup (or whatever it's called) /etc/X11/xorg.conf

```

if not

```

sudo dpkg-reconfigure xserver-xorg

```

and follow the instructions

---

### Post by steveneddy on 2007-03-11
If you installed the nVidia's driver from the website, you will have to uninstall the nvidia-glx and associated nvidia graphics drivers that come with ubuntu.

after this you can run the new drivers.

[Look here]("http://ubuntuforums.org/showthread.php?t=221313&highlight=nvidia"):

Hope it helps

-SE

It's only a starting place but to run the nvidia drivers from nVidia you will need to do some advanced tweaking. It's not hard, but read a lot of forums until you understand and then attempt the process. 

If I can do it, anyone can. 

[Also look here]("http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia").

cheers - SE

---

### Post by dmg025 on 2007-03-11
Thanks for your help already, I haven't had a chance to try any of your advice yet because I have been out all day but I will try some as soon as I can.  To be more specific here are my exact error messages (these occur after the ubuntu splash screen but before log in)

"Failed to start x system (your graphical interface).  It is likely that you didn't set it up correctly.  Would you like to view the X server output to diagnose problem"

I click yes.

"using config file '/etc/X11/xorg.conf' "
FATAL could not open ' /lib/modules/2.6.17-11-generic/volatile/nvidia.ko ' no such file or directory

EE NVidia: fauiled to load the nvidia kernwl module
***aborting***
EE scrceens found bu tnone have a useable configuration

fatal error:
no screens found

I click <ok>

Again, thankyou.

---

### Post by dmg025 on 2007-03-11
ok, well I used the guide I used initially and just reinstalled my new 9755 drivers and now beryl still works and everything seems to be fixed.

---

### Post by K.Mandla on 2007-03-12
(Moved to Desktop Environments. ;) )

---

