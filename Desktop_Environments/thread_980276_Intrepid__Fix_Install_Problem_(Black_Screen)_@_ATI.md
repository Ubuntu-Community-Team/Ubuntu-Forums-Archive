---
title: "Intrepid : Fix Install Problem (Black Screen) @ ATI CARDS"
date: 2008-11-12
forum: Desktop Environments
---

### Post by binbash on 2008-11-12
Tested @ fresh install of Ubuntu Intrepid 

Notebook used : Asus F3sr (Ati Hd2400)




Download Ubuntu Alternate CD from here : 

[http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate](http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate)


If you don't have internet connected please download packages mentioned below (and its deps), you can mount and install via cdrom etc

build-essential xorg-driver-fglrx

PS : Make sure they are the latest ones! 


-Install Ubuntu.
-After installation , REBOOT
-You will see a black screen, wait around 15 seconds and hit CTRL+Alt + F1
-login with your username
-sudo apt-get update && sudo apt-get upgrade
-REBOOT after this is done
-Again you will see black screen, you will hit ctrl+alt+f1 again and login
-sudo apt-get install build-essential xorg-driver-fglrx
-If you are upgrading i suggest removing xorg.conf
-sudo aticonfig --initial
-REBOOT and you will be fine : )

---

### Post by Deeta on 2008-11-14
It is also worth noting that only the newer ATI graphic cards are supported by the fglrx driver bundled in Intrepid.

Here is a List of Supported Cards: [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

The ones that do not work seem to be GPUs using a rv200 or earlier series of chipsets.
Specifically these would be cards earlier than the Radeon 9500.
Budget cards like the 9000, 9100, 9200 and 9250 which were still based on the rv200 ceased to be supported as well it seems.

---

