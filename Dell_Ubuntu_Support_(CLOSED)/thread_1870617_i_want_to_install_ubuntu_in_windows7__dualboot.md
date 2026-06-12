---
title: "i want to install ubuntu in windows7  dualboot"
date: 2011-10-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nrmurali on 2011-10-27
i want to install ubuntu in windows7, when i start the laptop i want the windows bootloader to select windows or ubuntu.....can any one suggest me how to do that...clearly...i made a partetion of 20gb for ubuntu...

---

### Post by BillyBoa on 2011-10-27
Try this link. In any case it's not so difficult.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by JRV on 2011-10-27
> **nrmurali said:**
> when i start the laptop i want the windows bootloader to select windows or ubuntu.

Then you want to do a WUBI install.

Start here: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Then search the forum for WUBI.

---

### Post by nrmurali on 2011-11-04
what is the difference between "ubuntu-11.10-desktop-i386.iso" & "ubuntu-11.10-alternate-i386.iso".....please suggest me which os i have to install in above 2 of them & also tell me 32 bit or 64 bit...iam using windows7 64bit for my dell laptop

---

### Post by BillyBoa on 2011-11-04
Actually there is no big difference. It's better to install the 32bits version unless you like to exploit all Ubuntu possibilities, which is rather difficult.

---

### Post by ronnystickshift on 2011-11-04
hi Billy, could you be more specific?  if the OP has more than 4GB of RAM i would think they'd definitely want to go for the 64 bit, and the ubuntu community documentation recommends the 64 bit as well:

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by BillyBoa on 2011-11-04
And if you go to the page to download Ubuntu, the option 32 is recommended.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
It's your choice. In any case with a 32 bit installation you have less problems with some programs, such is Flash. The Flash 64bit for Linux is terrible.

---

### Post by bcbc on 2011-11-04
The flash runs fine on my 64bit.

PS you don't *have* to use Wubi just because you want to keep the windows boot manager in charge. You can use easybcd instead: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

caveat: I haven't used easybcd personally

My recommendation is - if you have a dedicated partition - install direct to it. Best to have two logical partitions (one for swap). Unless of course you are totally new to Ubuntu and just want to try it out. In that case, Wubi will probably be the easiest option.

---

### Post by nrmurali on 2011-11-05
what is the difference between "ubuntu-11.10-desktop-i386.iso" & "ubuntu-11.10-alternate-i386.iso"....


i tried installing using wubi...but at last iy shown me 5minutes remaining & it stopped there...it had installed "ubuntu-11.10-alternate-i386"...

---

### Post by BillyBoa on 2011-11-05
"alternate" is for special installations. Just use the "desktop-i386.iso". If you use wubi and have a failed installation, you have to uninstall ubuntu from windows programs and then to start again the installation.

---

### Post by linuxaddix on 2011-11-06
use easybcd to

---

### Post by linuxaddix on 2011-11-06
doesnt wubi knock off the windows installation?ive tried ubuntu10.10 wubi on a laptop with winxp and it erased the winxp and booted only from ubuntu.with dualboot i found it easier to just do fresh installs of both,(back up your data if you want).installing windows first and partitioning the space you want for it then installing ubuntu with the remainder of space.grub will give you the option of ubuntu or windows.partioning the drive later in the game always creates boot errors for windows if using gparted to partition so thats why i do fresh installs.

---

### Post by nrmurali on 2011-11-08
is it possible to install through iso file in wubi... (i had already downloaded 'desktop.iso' file).

---

### Post by bcbc on 2011-11-08
> **nrmurali said:**
> is it possible to install through iso file in wubi... (i had already downloaded 'desktop.iso' file).

yes. Place wubi.exe and the ISO in the same folder. Make sure the wubi.exe and the ISO are for the same release.

More info: [https://wiki.ubuntu.com/WubiGuide#How_do_I_install_Wubi_on_a_machine_with_no_Internet_connection.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_install_Wubi_on_a_machine_with_no_Internet_connection.3F)

---

### Post by nrmurali on 2011-11-10
thank you guys... i had installed ubuntu sucessfully

---

