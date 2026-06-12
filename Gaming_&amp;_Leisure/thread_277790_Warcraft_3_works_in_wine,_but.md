---
title: "Warcraft 3 works in wine, but"
date: 2006-10-15
forum: Gaming &amp; Leisure
---

### Post by Zaggy on 2006-10-15
Hi, I'm running wine 0.9.23 and can start warcraft3:tft just fine, but ingame it stutters a lot, I disabled sound everywhere I could in wine and wc3, but it -still- stutters.

Anyone has idea's?

---

### Post by pay on 2006-10-15
Do you have an Ati card? I think that it is a problem with the Ati drivers (fglrx).

---

### Post by Zaggy on 2006-10-15
Thanks for the reply.

Nope I have a Nvidia Geforce 6600GT.

---

### Post by pay on 2006-10-16
Sometimes for things like these there are patches on the wine site. Or you could compile the cvs. Or wait for the next new release. 0.9.23 is out but they might not have made a debian file of it yet.

---

### Post by smithveg on 2006-10-22
I faced the same problems, i can run the warcraft3, but it's very lag.
As my past os, windows xp, it can run the games smoothy.

I do not know what is happening, i guess it might be the graphic card problems. But i do not know how to check it in the device manager. Since all the driver is package in the ubuntu installation disc. I think it might not have my graphic card driver.

What should i do now, do i need to download from synaptic or my graphic card's driver (cd).

Hopes you received my reply.

---

### Post by phoqueyoo on 2006-10-22
try running it with -opengl

---

### Post by smithveg on 2006-10-23
Sorry,

Wat do you means running in -opengl?

Can i have a complete example in that.

is that $ -opengl /media/storage/warcraftIII/war2.exe

Thank your reply.

---

### Post by phoqueyoo on 2006-10-23
wine "Warcraft III.exe" -opengl

---

### Post by DraeLee on 2006-10-23
does anyone have the flickering screen problem?

---

### Post by smithveg on 2006-10-23
ya, also have the flickring problems when i try to play a games. I think this is a graphic card problems.

As i know, at the first screen (first page of warcraft / menu select screen)
I noticed that the graphic is not in the 3D mode. I just guess that the linux - ubuntu can not find the correct driver for my 3D card. Then i try to get back the 3D card driver (in cd). It does not have the linux installation. So, where can i install my 3D card driver.

---

### Post by DraeLee on 2006-10-23
well the odd thing is everything is looking good except that i have no sound but i can try and fix that later.  The video looks smooth and even with it flickering i ran around to see how smooth it was.  So If I can just get rid of the flickering I think I would be good to go and troubleshoo the audio later.  If anyone can point me in right direction that would be great:)

---

### Post by smithveg on 2006-10-23
Ok, sound is your problems, video is mo problems.

Do you know how to fix your sound device problems?
In device manager, i can see my sound card name. But i can not see my graphic card name. Where can i update my graphic driver?

Someone helps us.

---

### Post by DraeLee on 2006-10-23
what kind of card do you have I have a nvidia card i used a howto in the forums here to download and install the latest driver.  I dont know much for anyother card

I tried doing what was said in a HOWTO for WoW in the Wtf config file.  I did that (adding the SET lines and all) but it didnt work do you know another method.

---

### Post by smithveg on 2006-10-23
The graphic card that i'm using is 'HIS Excalibur 9250 - powered by ATI Radeon 9250VPU - 240MGZ' Where can i get this unix driver. Because the CD Driver a vendor give me when i bought, is for windows platform.

---

### Post by DraeLee on 2006-10-23
dont know if you tried this but look at this guide

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by smithveg on 2006-10-23
I had do the graphic device installation from,
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

From this article, After the installation, i try to type 'fglrxinfo', but the information displayed is not related to my graphic card. I'm using Radeon 9250. And the information displayed to me as below,
##################################
smith@smith-host:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
##################################

Am i need to do the thing at here, [http://xfree86.org/](http://xfree86.org/) to install my graphic card?

Thank your helps

---

### Post by smithveg on 2006-10-23
Am i need xfree86 to install Radeon 9250 driver?

After i see this page, [http://xfree86.org/4.6.0/radeon.4.html](http://xfree86.org/4.6.0/radeon.4.html)
I noticed that there is no Redeon 9250 support, So, What should i do now?

In addition, i check back the graphic card's box, in the System Requirements,
Operating Systems: Windows XP/2000.

What should i do now? Is that possible for me to install Radeon 9250 for running in Ubuntu.
I hope that i no need to change a graphic card.

Any reply would be thank.

---

