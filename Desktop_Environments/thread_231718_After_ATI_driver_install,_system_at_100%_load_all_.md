---
title: "After ATI driver install, system at 100% load all the time"
date: 2006-08-07
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-08-07
Hey i installed an ati vid driver for my x1600 and after installing my computer seemed a lot faster on ubuntu. But now im at load all the time. So, i used to get a downtime of 6mb/s and now its cutt down in half (or less) due to my system load. Also i can barely launch more than 1 or 2 apps without the 3rd hanging or slowing down really, really bad. I know this all has to do with the load, but why am i always in load? what can i do to fix this?

---

### Post by Anduu on 2006-08-07
Open system monitor and see excactly what is eating up your cycles...

---

### Post by WalmartSniperLX on 2006-08-07
> **Anduu said:**
> Open system monitor and see excactly what is eating up your cycles...

lol the ati driver

edit: but thats odd cuz i googled it and i cant find any complaints about it loading up the cpu

---

### Post by Anduu on 2006-08-07
Ummmmm ...I don't see anywhere in the system monitor that says "ATI Driver".I use an ATI card.

If you dont want help just say so...:rolleyes:

---

### Post by WalmartSniperLX on 2006-08-07
> **Anduu said:**
> Ummmmm ...I don't see anywhere in the system monitor that says "ATI Driver".I use an ATI card.

If you dont want help just say so...:rolleyes:

lol its the process named 

atieventsd

---

### Post by Anduu on 2006-08-07
And guess what my ATI works flawlessly and there is no such entry for me...why do you think I would ask such a question?

Now open a terminal and type fglrxinfo and post your output.

---

### Post by WalmartSniperLX on 2006-08-07
patrick@patrick-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by Anduu on 2006-08-07
Your output is supposed to look like this:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

Of course substitute your ati card name for mine...

Your drivers are not installed properly.

---

### Post by Anduu on 2006-08-07
A couple of threads to check out...

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)
[http://www.ubuntuforums.org/showthread.php?t=143283&highlight=fix+mesa](http://www.ubuntuforums.org/showthread.php?t=143283&highlight=fix+mesa)

---

### Post by drarmi on 2006-08-07
I noticed the same problem today and also found atieventsd to be the process to steal all CPU Time ..... I tried alot of different things to solve the problem but the only thing that finally solved it was to install the ubuntu-fglrx-686 driver from the Seveas Repository.
I followed these instructions:
--------
Seveas Repository

You do not need to take all these steps if you run an up-to-date Dapper installation on a 32 bit system. Dennis Kaarsemaker provides these packages in a repository. Add the following line to /etc/apt/sources.list:

deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) dapper-seveas drivers

(There also is breezy-seveas for the Breezy users)

Then you can simply install the ubuntu-fglrx-$arch (see above for the meaning of $arch) package.

/!\ The fglrx driver on Dapper (8.26.18-1) can cause rss-glx screensavers to run very slowly.
Modifiying xorg.conf

When you install from ati.com drivers or the dapper-seveas repository, you still need to change xorg.conf and add the fglrx module to /etc/modules as described under "Ubuntu provided drivers". There are scripts from ATI that may or may not work for you. They will backup xorg.conf before modifying it.

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

/!\ Whether you install manually or from dapper-seveas, you MUST disable the Ubuntu-provided fglrx by performing these actions:

    *

      Disable fglrx in /etc/default/linux-restricted-modules-common
    *

      Run sudo /sbin/lrm-manager
    *

      Run sudo depmod -a
    *

      Reboot
-----------

They can be found at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by WalmartSniperLX on 2006-08-07
Ok problem solved everything runs smooth now. Thanks

---

### Post by Anduu on 2006-08-08
> **WalmartSniperLX said:**
> Ok problem solved everything runs smooth now. Thanks

Well fill us in man...what you do?

---

