---
title: "ATI 7.11 Released Nov 21"
date: 2007-11-21
forum: Desktop Effects &amp; Customization
---

### Post by dannns on 2007-11-21
Has anybody installed the new drivers? I'm specifically interested in any Compiz-Fusion performance improvements on the HD2600XT.

---

### Post by dannns on 2007-11-21
Well, I couldn't resist. So I just downloaded it and installed it without doing any packaging or removing the previous version, and seems to be working. During installation it said version 8.43.3, however in the ATI CCC it says version 8.43.2 which is definately newer than the 8.42.3.

Well, Firefox scrolling seems to be somewhat better, not perfect, but at least usable. Open and Close windows effects now work with the real window, not with a black square. However when you turn on mipmaps for any of Compiz effects, they still produce a white window.

---

### Post by eldragon on 2007-11-21
ive tried them too, there is no improvement here aiglx-wise

glxgears pops 3700fps which is new to this x600 card...always a plus

---

### Post by jonray74 on 2007-11-21
can you guys please post a link on how to install this driver? Also, is this driver stable?

I would really appreciate if you guys could post a link or a guide on how to install it.

thanks

:)

---

### Post by eldragon on 2007-11-21
> **jonray74 said:**
> can you guys please post a link on how to install this driver? Also, is this driver stable?

I would really appreciate if you guys could post a link or a guide on how to install it.

thanks

:)

ive installed the 8.42.3 drivers following the original thread here:
[http://ubuntuforums.org/showthread.php?t=588383](http://ubuntuforums.org/showthread.php?t=588383)

i guess it would apply for these drivers too

if you already have the 8.42 drivers, then just run the installer and follow the gui's instructions, it will step over the 8.42 drivers... thats what i did.

i find them quite stable, except for compiz, or some quake4 lightning glitch which i cant really blame on ati.....

---

### Post by therealknewman on 2007-11-21
Curse the Mesa driver! Its back again after all that work to make it go away with the 8.42.3 driver :(
Anyone else getting the Mesa driver in their fglrxinfo output as well? I tried doing what I did last time but no avail...
EDIT: working, it was my fault I missed one of the deb packages

---

### Post by jimerickso on 2007-11-21
had to install mine both ways (buildpkg and regular install) to get it to work. not sure why.

---

### Post by tiachopvutru on 2007-11-21
Sadly, I still have the same problem on this one.. with AIGLX if I'm not mistaken...

---

### Post by Melcar on 2007-11-22
Screen flickering with Compiz is still an issue, in fact, it didn't seem to fix anything for me.  3D performance is still good thought.

---

### Post by macmus on 2007-11-22
> **eldragon said:**
> if you already have the 8.42 drivers, then just run the installer and follow the gui's instructions, it will step over the 8.42 drivers... thats what i did.


u mean adding execution righ to the **.run script and executing ?

---

### Post by fettuohi on 2007-11-22
Has anyone else problems with the new driver (since they introduced AIGLX) on gutsy with video playback? My screen goes black for 2-3 secs every freaking time I start a video of some sort (even in firefox via the mplayerplug-in) the video plays after that fine but with some flickering. It is irritating as hell and I can't figure out what is causing it. The problem wasn't there when I used the 8.40 driver. Has anyone else that problem with the new driver (8.42.3 &/or 8.43.3)? My card is a HD2400XT ATI PCI-e 16x card from Sapphire.

Regards

André

---

### Post by eldragon on 2007-11-22
> **macmus said:**
> u mean adding execution righ to the **.run script and executing ?

either that and running with "sudo ./ati-blah-blah.run"

or just running "sudo sh ati-blah-blah.run"

i first built the deb packages for gutsy, and installed them, i was back to the mesa driver.

then i just ran the installer and let it do its thing :D
worked great

---

### Post by tiachopvutru on 2007-11-22
> **eldragon said:**
> either that and running with "sudo ./ati-blah-blah.run"

or just running "sudo sh ati-blah-blah.run"

i first built the deb packages for gutsy, and installed them, i was back to the mesa driver.

then i just ran the installer and let it do its thing :D
worked great

... Those commands actually work...

Meh, and I went through the whole installation process following the old 8.42.3 tutorial <.<

---

### Post by gillis on 2007-11-22
The following steps i did to get it working

**step 1**
download and instal the driver [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-11-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-11-x86.x86_64.run")
sudo ./ati-driver-installer-7-11-x86.x86_64.run


**step 2**
reboot the computer
i my case i got a white screen as soon as ubuntu and compiz started.
the only thing i could do was entering the console by pressing ctrl + alt + f1
i disabled compiz in xorg.conf

sudo nano /etc/X11/xorg.conf

and put the following lines at the bottom.

Section "Extensions"
       Option          "Composite"     "0"
EndSection


**step3**
Restart the computer
 ubuntu will start up without problems and without compiz of course.

**step4**
Enable the propiated ati driver in system ->administration ->propiated drivers.

**step5**
i installed the 7.11 ati driver again by entering the following line in a console:
sudo ./ati-driver-installer-7-11-x86.x86_64.run


**step6 **
sudo nano /etc/default/linux-restricted-modules-common 
(if it not works do firstr: sudo apt-get install linux-restricted-modules-generic restricted-manager)

Delete everything and enter the following lines. press alt+o to save and alt+x to quit

# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="fglrx"


**step7**
sudo nano /etc/xdg/compiz/compiz-manager

it should look like:

# Ubuntu specifc compiz-manager configuration file
# goes into /etc/xdg/compiz/compiz-manager
# works with git://anongit.compiz-fusion.org/fusion/misc/compiz-manager
COMPIZ_BIN_PATH="/usr/bin/"
PLUGIN_PATH="/usr/lib/compiz/"
COMPIZ_NAME="compiz.real"
WHITELIST="nvidia intel ati radeon i810 fglrx"


**step8**
sudo nano /etc/X11/xorg.conf
add the following lines in the bottom of the screen. make sure to delete the old ones

#Section "Extensions"
#       Option          "Composite"     "0"
#EndSection
Section "Module"
        Load            "glx"
EndSection


**step9 **
reboot computer. compiz should work now.
3d apps will work also. 
i recommend to disable compiz, cause its slowing down the system very much.
cube effects and transparancy is working ok, but some 2d things like scrolling and watching flash movies is a pain in the ***.
without compiz everything (2d and 3d) works perfectly. 
So when your friends are checking your ubuntu out, enable compiz. When you are alone disable it and wait till Compiz or Ati will fix our frustration



my config btw

Laptop
Compaq hp nc8000
centrino 1.4ghz
ATI 9600 64mb

---

### Post by jonray74 on 2007-11-27
is this driver gonna be included in the updates of Ubuntu eventually? or do we have to keep manually installing this driver?

---

