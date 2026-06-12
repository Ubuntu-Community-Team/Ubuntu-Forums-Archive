---
title: "Desktop effects could not be enabled"
date: 2007-12-19
forum: Desktop Effects &amp; Customization
---

### Post by twistymcgee on 2007-12-19
I have recently installed Gutsy on a Thinkpad T30 laptop.  Everything is going great but I don't seem to be able to get desktop effects to work.  I keep getting "Desktop effects could not be enabled".  My video card is:

ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

I was wondering what I might have to do to get desktop effects working?  Or is this card not capable of desktop effects?  I have read most of the forum threads about this topic and couldn't really find anything useful.  Any help would be appreciated.

Thanks

---

### Post by Leo the Lion on 2007-12-19
Sorry I can't answer this question because I have the same problem. I have a Rage Mobility M3 AGP 2X card on a Dell Inspiron 4000. Is this card just no good to run the cube or any other Compiz effects?

---

### Post by thenailedone on 2007-12-20
Quick question...

Are you guys connected to the net when you try this, the restricted drivers required to get desktop effects enabled must still be downloaded and installed before it will work (which is one of my major problems at present as I don't have[ net access working yet]("http://ubuntuforums.org/showthread.php?t=639330") :( )

*edit: I just saw you guys are using ATI cards... I am using nvidia so I might be of the mark with the above...*

---

### Post by Matej_C. on 2007-12-20
i have ati radeo x1950 gt

you can easily install drivers with restricted manager, or you can download the newest from ati website, but this new driver used with compiz makes firefox lacking while scroling (it was a bit frustrating), but faster with games (so its said, i am not a gamer), i think its the same, you choose:

**for older driver**
restricted manager>driver
synaptic>xserver-xgl
reboot and enable desktop effects, if it wont start, edit xorg.conf like its written in instructions for the new driver

**if you want new ones, this is how to:**
1. download the driver

2. change atributes (simply with right-click and properties-  make sure you have granted permision to run as a program/ using chmod if you want and know)

3. run with a console
```
 sudo /path/to/the/driver/ati-driver-installer-7-11-x86.x86_64.run
```

4. reboot

5. ```
sudo aticonfig --initial
```

6.now you have to enable composite, this can be done with installing xgl, but in my case, it was working worse than vesa driver (its used when you install ubuntu), so i just rewrote x-server configuration file (!!!make a copy first!!!)
```
sudo nano /etc/X11/xorg.conf
```
find a section "extension" and change an option "Composite", if you have there "0" write "1" or if there is  "false" write "true" and so on.
reboot

NOW PAY ATTENTION!!!!
if something fails....

a)after installing drivers:
 run save mode and do this:
```
dpkg-reconfigure xserver-xorg
```
and there you just choose your settings, dont forget to choose 

b)after changing xorg.conf:
if it starts in low resolution, undo the changes you have made (you can use that copy, which you have done before)
or when no graphic desktop appears, make the same as in a)

and just dont blame me, if it will make something wrong, it works well on my computer, i was trying to get the drivers and compiz working for 4 days without a breake (i went only to sleep and eat)

---

### Post by zolero on 2007-12-20
Hi everyone.

I'm on an Asus A3H laptop with Intel 915 GMLE video card trying to run Compiz Fusion. I've had played out with drivers, enabling and disabling stuffs in xorg.conf (and naturally got crashed Xserver few times) installing-uninstalling xserver-xgl, screwed in gconf and so on. But finally I've ended with this shitty message "Desktop effects could not be enabled"
What a heck can be? And where to find a good howto for Intel cards? I have found  only NVidia and ATI guides. Intel users are prohibited from Compiz use?
Plz help I'm despearte to have those fancy effects on my laptop.

---

### Post by Leo the Lion on 2007-12-21
> **Matej_C. said:**
> i have ati radeo x1950 gt

you can easily install drivers with restricted manager, or you can download the newest from ati website, but this new driver used with compiz makes firefox lacking while scroling (it was a bit frustrating), but faster with games (so its said, i am not a gamer), i think its the same, you choose:

**for older driver**
restricted manager>driver
synaptic>xserver-xgl
reboot and enable desktop effects, if it wont start, edit xorg.conf like its written in instructions for the new driver

**if you want new ones, this is how to:**
1. download the driver

2. change atributes (simply with right-click and properties-  make sure you have granted permision to run as a program/ using chmod if you want and know)

3. run with a console
```
 sudo /path/to/the/driver/ati-driver-installer-7-11-x86.x86_64.run
```

4. reboot

5. ```
sudo aticonfig --initial
```

6.now you have to enable composite, this can be done with installing xgl, but in my case, it was working worse than vesa driver (its used when you install ubuntu), so i just rewrote x-server configuration file (!!!make a copy first!!!)
```
sudo nano /etc/X11/xorg.conf
```
find a section "extension" and change an option "Composite", if you have there "0" write "1" or if there is  "false" write "true" and so on.
reboot

NOW PAY ATTENTION!!!!
if something fails....

a)after installing drivers:
 run save mode and do this:
```
dpkg-reconfigure xserver-xorg
```
and there you just choose your settings, dont forget to choose 

b)after changing xorg.conf:
if it starts in low resolution, undo the changes you have made (you can use that copy, which you have done before)
or when no graphic desktop appears, make the same as in a)

and just dont blame me, if it will make something wrong, it works well on my computer, i was trying to get the drivers and compiz working for 4 days without a breake (i went only to sleep and eat)

Hehehe. I tried installing xserver.xgl. Everything was fine until I rebooted. After rebooting, I go through the login screen, enter my password and BOOM, the system restarts and goes back to the login window. I can't get into the desktop.

Any ideas on how I can fix this? I'm almost to the point of installing Ubuntu all over again.

---

### Post by Ub1476 on 2007-12-21
Everyone post the output of those commands:

```
compiz --replace
```
```
lspci | grep VGA
```

Leo the Lion: Change sessions to "failsafe terminal" and uninstall XGL:

```
sudo apt-get remove xserver-xgl
```

---

### Post by punkybouy on 2007-12-21
The first two posters appear to have older laptops, like I do.  These are 32 bit only so the driver mentioned to fix the problem looks to be for 64 bit machines.  ATI says to find the correct driver at your laptop manufacturers website.  Dell had nothing.  I am stuck with 1024x768 resolution...yuck!  I too cannot enable desktop effects.  I don't think the older laptop ATI cards have the capability.

ati-driver-installer-7-11-x86.x86_64.run

---

### Post by JoshuaRL on 2007-12-23
There seem to be a few radeon cards that aren't supported in the non-free ATI driver.  Unfortunately they all seem to be the Mobility Radeon ones found in the Inspiron 5100 and the IBM T40-42 (I believe).  I've found a thread that seems like it would work for the Inspiron, but it should work in theory for the IBM's too.  Not sure because I haven't had time to run this through my Dell, but I think it sounds right.  I'll update with what I find.

What have you to lose except hosing Xorg?  And if you have one of these Mobility Radeons, you've probably already done that a couple times.

As for anyone that has a supported card, please don't suggest the ATI drivers if you're not sure about the support for someone else's.  It will just lead them astray.  Thanks.

[http://ubuntuforums.org/showthread.php?t=580134](http://ubuntuforums.org/showthread.php?t=580134)

Edit

Alright, I think that works pretty good for the Mobility M7.  Not sure on anything else, but for me pretty good.  From 200-300fps to 1140fps.  Sweet.

/Edit

Another Edit
Sorry, Intel should work out of the box with the drivers included.  There are two, one normal one and one development included in Ubuntu.  You can also try this:

```

sudo dpkg-reconfigure xserver-xorg

```

/Another Edit

---

### Post by diafygi on 2008-01-01
I am having the same problem as you, and it seems to be narrowed to the installation of xserver-xgl. You shouldn't need XGL for 2D stuff. If you want Compiz-fusion, look on Free Software Magazine's [chart]("http://www.freesoftwaremagazine.com/blogs/bored_with_3d_desktops") for what you need to enable 3d effects for your video card. It says my video card (Nvidia GeForce2 Ultra) should work with XGL, but I can't seem to get XGL to work. So if you have found a solution for this problem that doesn't involve uninstalling XGL, please post it.

[This]("http://ubuntuforums.org/showthread.php?p=4053221#post4053221") is where I'll be posting any solutions I find.

---

