---
title: "compiz not working. upgraded to 10.04. nvidia card"
date: 2010-05-01
forum: Desktop Environments
---

### Post by metro2003 on 2010-05-01
Hi,

I have recently upgraded to Lucid 10.04 and my compiz is no longer working. everything was working fine before. I even tried a clean install and after I installed compiz on the clean pc I have the same issue.  everyting works fine with KWin, but I want compiz working. 

When I enable compiz, I see my desktop but without any borders and the following error message comes up:

```

Application: KDE Window Decorator (kde4-window-decorator), signal: Segmentation fault
[KCrash Handler]
#6  0x001e7941 in KDecorationUnstable::compositingActive() const () from /usr/lib/libkdecorations.so.4
#7  0x001ed705 in KCommonDecorationUnstable::compositingActive() const () from /usr/lib/libkdecorations.so.4
#8  0x02390180 in ?? () from /usr/lib/kde4/kwin3_oxygen.so
#9  0x001ef8a7 in KCommonDecoration::borders(int&, int&, int&, int&) const () from /usr/lib/libkdecorations.so.4
#10 0x001f1ed0 in ?? () from /usr/lib/libkdecorations.so.4
#11 0x08059b40 in ?? ()
#12 0x0805a3ab in ?? ()
#13 0x0805deae in ?? ()
#14 0x08057146 in ?? ()
#15 0x0805066d in ?? ()
#16 0x00327bd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#17 0x0804fe81 in ?? ()

```

I have an **Nvidia GeForce 8600M GT** card on an Asus G2S laptop. Also, I correctly installed the recommended restricted NVidia driver through the "Hardware Drivers" section.  I checked and it installed "nvidia-glx-185"

Any help is greatly appreciated. Thank you !!

---

### Post by dino99 on 2010-05-01
> **metro2003 said:**
> Hi,

I have recently upgraded to Lucid 10.04 and my compiz is no longer working. everything was working fine before. I even tried a clean install and after I installed compiz on the clean pc I have the same issue.  everyting works fine with KWin, but I want compiz working. 

When I enable compiz, I see my desktop but without any borders and the following error message comes up:

```

Application: KDE Window Decorator (kde4-window-decorator), signal: Segmentation fault
[KCrash Handler]
#6  0x001e7941 in KDecorationUnstable::compositingActive() const () from /usr/lib/libkdecorations.so.4
#7  0x001ed705 in KCommonDecorationUnstable::compositingActive() const () from /usr/lib/libkdecorations.so.4
#8  0x02390180 in ?? () from /usr/lib/kde4/kwin3_oxygen.so
#9  0x001ef8a7 in KCommonDecoration::borders(int&, int&, int&, int&) const () from /usr/lib/libkdecorations.so.4
#10 0x001f1ed0 in ?? () from /usr/lib/libkdecorations.so.4
#11 0x08059b40 in ?? ()
#12 0x0805a3ab in ?? ()
#13 0x0805deae in ?? ()
#14 0x08057146 in ?? ()
#15 0x0805066d in ?? ()
#16 0x00327bd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#17 0x0804fe81 in ?? ()

```

I have an **Nvidia GeForce 8600M GT** card on an Asus G2S laptop. Also, I correctly installed the recommended restricted NVidia driver through the "Hardware Drivers" section.  I checked and it installed "nvidia-glx-185"

Any help is greatly appreciated. Thank you !!

***  /usr/lib/libkdecorations.so.4  *** libkdecorations4 might be corrupted, better to reinstall it from archive 
sudo apt-get install libkdecorations4
or
 sudo dpkg-reconfigure libkdecorations4  
or
 sudo dpkg --configure -a

---

### Post by metro2003 on 2010-05-01
Thank for the quick reply dino99.

I tried what you suggested, however, it didn't do anything. same problem and error message. It's a clean install so I'm not sure why it'll be corrupt.

---

### Post by metro2003 on 2010-05-02
any ideas??? anyone?? 

Thank you !

---

### Post by metro2003 on 2010-05-03
I got it. for those that are interested, here's how to do it:

credit goes to these guys here:
[http://kubuntuforums.net/forums/index.php?topic=3111381.0](http://kubuntuforums.net/forums/index.php?topic=3111381.0)

```


this is not a nvidia issue.  It is a kde issue.  It's easily fixed.

sudo apt-get install emerald

then create a file and name it compiz.sh, right click on it and go to properties and give it execute permission.

add this info into it.

#!/bin/bash
emerald --replace | compiz

and then go to system settings, advanced, autostart, click on add script and remove "create as symlink".  look for your file and add it as a startup.

make sure you leave under default applications and windows manager, leave it as kwin and in Desktop effects, uncheck "enable desktop effects"

reboot and your good to go


```

---

