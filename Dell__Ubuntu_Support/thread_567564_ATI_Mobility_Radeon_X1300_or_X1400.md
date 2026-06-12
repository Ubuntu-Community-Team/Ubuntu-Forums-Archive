---
title: "ATI Mobility Radeon X1300 or X1400"
date: 2007-10-04
forum: Dell  Ubuntu Support
---

### Post by dem05k41 on 2007-10-04
How to configure this video card in Ubuntu???
I've Dell Inspiron 6400 laptop:

Intel Core 2 Duo (2x1,83GHz)
1GB of RAM
ATI Mobility Radeon X1400
and BROADCOM network card


Troubles:
1. I can't use my graphics card
2. I can't use my card reader
3. I can't use WIFI
4. My BROADCOM network card don't works on Ubuntu 7.04

Please help!
Thak you

---

### Post by Ub1476 on 2007-10-05
Just install the ATI drivers through Restricted Drivers Manager (System>administration). Don't know about your wifi though, but you'll likely fix it if you google it or something.

Btw, this forum is for computers which ships with Ubuntu preinstalled,  which I doubt your computer did;)

---

### Post by Najmudin on 2007-10-06
> **dem05k41 said:**
> How to configure this video card in Ubuntu???
I've Dell Inspiron 6400 laptop:

Intel Core 2 Duo (2x1,83GHz)
1GB of RAM
ATI Mobility Radeon X1400
and BROADCOM network card


Troubles:
1. I can't use my graphics card
2. I can't use my card reader
3. I can't use WIFI
4. My BROADCOM network card don't works on Ubuntu 7.04

Please help!
Thak you

I have the same laptop , and i was having the same problem i searched the forum and found the solution for the wifi problem here:
[http://ubuntuforums.org/showthread.php?t=405990&highlight=HOWTO%3A+Broadcom+43xx+based+wireless+cards+the+EASY+way]("http://ubuntuforums.org/showthread.php?t=405990&highlight=HOWTO%3A+Broadcom+43xx+based+wireless+cards+the+EASY+way")

just download the attached file and run the file with name "installer.py"
it will choose the right driver for you automatically .
Notice : there is no need to do that if are going to use Ubuntu Gutsy Gibbon 7.10 because all you will have to do is going to the system>administrator>restricted driver manager, just choose the driver from there and everything will be OK.
about No.1 issue you have to install fglrx driver to make your X1400 working
you can find it in system>administrator>synaptic package manager , search for "xorg.driver.fglrx" and install , may be you have to reboot after that , i don't remember .
Or you can follow this link:
[http://ubuntuforums.org/showthread.php?t=427852&highlight=ATI+X1400+resolution]("http://ubuntuforums.org/showthread.php?t=427852&highlight=ATI+X1400+resolution")
about issue No.2 i have no idea .
I hope that will help you , this is my first time trying to help some one in Ubuntu forums.

---

