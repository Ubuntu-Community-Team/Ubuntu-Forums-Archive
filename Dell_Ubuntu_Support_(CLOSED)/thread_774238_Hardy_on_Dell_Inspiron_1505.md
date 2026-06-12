---
title: "Hardy on Dell Inspiron 1505"
date: 2008-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fjgaude on 2008-04-29
I'm about to install Hardy 64-bit on my 1505. Has anyone done that yet?

---

### Post by mike.123850 on 2008-04-29
I have been wondering that myself. I have a Dell E1505n that came pre-loaded with Ubuntu and is running very well under 7.10. I won't "upgrade" to 8.04 for a few weeks, I figure there will be several fixes by then.


Mike

---

### Post by barq on 2008-04-29
I have to say I'm waiting for someone else to go first. ;)

I might try the upgrade in about ten days - I need my laptop to work at the moment. But after the 10th May I can mess around with it a bit more.

---

### Post by esteckis on 2008-05-03
I have the Dell 6400 which is supposed to be the equivalent to the 1505 on Dells site.  With the Heron version, you have to enable the restricted driver (being connected via Ethernet not wireless) and the 1390 (which is a broadcom driver will download) Then check updates to have it automatically download the FWCutter (I think this is for the wireless)

My video is the  ATI 1400 and if I use the compiz (system preferences appearence  visual effctes normal or advanced) the screen flickers with any Opengl screensaver running or using Google Earth ( I guess GE uses the Opengl version for linux and it was crashing) Now using the ATI video driver, I have to stick with (none) on the visual effects) The ATI Wiki driver site mentioned this. But using no visual effects the screensavers run fine and Google Earth runs fine.  Also note that there is a program called "ENVY" that will download the ATI driver for you and installs it no problem for me.  Also ENVY if you run it later on should check to see if ATI has a new driver for you.  It appears, that ATI is making a new driver version every other month, lol.  Besides the video driver problem (slight) everything else works fine.   Thanks UBUNTU Team :)

---

### Post by lyceum on 2008-05-05
A friend has an Inspiron 1505. When I upgraded it for her (she bought it from Dell w/ Ubuntu), everything worked great. But then I decided to install from the live CD to give her a fresh start and now the sound does not work, which is odd, as it does work with the live CD.:confused: 

But the upgrade went fine.

---

### Post by don.clark on 2008-05-05
I installed Hardy on my 1505, not the N, and after it installed the Broadcom drivers it worked pretty well. The only problem I have seen is that the wireless connection is really slow.  So slow it times out downloading Ubuntu updates.  Anyone seen this or have a fix?

---

### Post by amir.khosroshahi on 2008-05-06
I have installed Hardy from live CD on my Inspiron 6400.

After getting and installing the driver for modem (Conexant HSF) from Dell website, the sound stopped working. May be that is the same reason for sound not working for other people.

The default graphics driver works fine. But desktop effects won't work. I haven't tested ATI's propriety driver yet. Has any body? Will desktop effects work under ATI driver?

---

### Post by keeler1 on 2008-05-06
The desktop effects do work under the binary ATI driver now.  XGL is no longer required.  Pretty much everything worked on my E1505 after installatin of hardy.  But I have the intel 3945abg wireless and not the broadcom.  

However, when using some of the cool graphical screensavers, my laptop runs at like 60% cpu usage.  I would reccomend having a very simple screensaver not a cool one.

---

### Post by sdm_cacto on 2008-05-06
Tou will find a lot of info here [http://www.ubuntu1501.com/](http://www.ubuntu1501.com/)

good luck

---

### Post by alejobar on 2008-05-06
I have an inspiron 6400 E1505, and I installed from live cd connected to the internet with ethernet cable, everything work fine, you have to go to restricted drivers to enable the wireless driver and the ati driver, the reboot. 

There's a problem with compiz and the driver my screen flickers if I play any 3d game, so i have to turn off the visual effects before I play, after that everything runs great!

---

### Post by caro on 2008-05-06
I purchased an Inspiron E1505n from Dell preloaded with Feisty.  I've upgraded to Gutsy and Hardy with no problems.

---

### Post by xandraius on 2008-05-06
Done it. Cake. Wireless played much better. System is a dual-boot of Vista and Ubuntu. Upgrade from 7.10 to 8.04 was all happy except for one small glitch: Had to change the computer name to match the host name else all sudo and gksudo attempst failed with 'no route to host' which is a security feature. Other than that, happy-happy, joy-joy

By the by, have Avant running on the bottom, able to use all of the Cube and slide effects. A step up from the wireless hell of 7.10

---

