---
title: "ATI Driver"
date: 2009-02-25
forum: General Help
---

### Post by chevmaro on 2009-02-25
My ATI Driver is crap.  I just installed Ubuntu.  I got everything working really good except for this driver.  I installed the one Ubuntu automatically wanted to install.  I also tried updating the driver from ATI's website but it appears they are the same version anyways.  

I am having issues with the control center.  It never seems to save my settings after reboot.  They always default back.  I am trying to run dual screens.  Another problem I am having is whenever the system goes to sleep or turns off the display it doesnt wake up nice.  It will resize my desktop so I have to scroll.  The only way to fix this that I know of is a reboot.  Any videos I play appear to flicker.  I was thinking this was a codec but I noticed the screen saver doing this also.  

Any suggestions other then to buy nvidia?

Video card is Diamond HD4870 512MB

---

### Post by khelben1979 on 2009-02-25
Can you specify more what you mean by "my ati driver is crap" ?

Slow driver?

---

### Post by chevmaro on 2009-02-25
Screen flickers when anything graphical is loaded like screen saver or media.  ATI Control Center does not save settings for Res or Dual monitors that I specify.  After waking up from sleep or monitors turning off it resizes my desktop so I have to scroll around.  Only fix I find for that is a reboot.

---

### Post by zika on 2009-02-25
> **chevmaro said:**
> Screen flickers when anything graphical is loaded like screen saver or media.  ATI Control Center does not save settings for Res or Dual monitors that I specify.  After waking up from sleep or monitors turning off it resizes my desktop so I have to scroll around.  Only fix I find for that is a reboot.
first of all, You do not have to reboot, just logout and login to get X restarted. it faster and healthier for machine ... ;)

did You try to get ATI newest driver 9.2? [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) also, try using ATI Catalyst center in administrative mode.

also take a look at my thread [http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593)

---

### Post by stim on 2009-02-25
Try using Envy. Available in the package manager as envyng-core, this program will download, install and configure ATI/nVidia graphics drivers. I have an 8800GTX, and have used this program from day one.  It is THE MOST painless way to get your stuff up and running.

---

### Post by chevmaro on 2009-02-25
> **zika said:**
> first of all, You do not have to reboot, just logout and login to get X restarted. it faster and healthier for machine ... ;)

did You try to get ATI newest driver 9.2? [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) also, try using ATI Catalyst center in administrative mode.

also take a look at my thread [http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593)


I did install 9.2 driver.  However when I check the driver version in the Catalyst Control center it shows 8.5xx.  Can anyone with the 9.2 driver confirm this?  Possibly didnt install correctly?  Even when opening the installer it shows 8.5.

I'll read your thread.  Thanks.

---

### Post by chevmaro on 2009-02-25
> **stim said:**
> Try using Envy. Available in the package manager as envyng-core, this program will download, install and configure ATI/nVidia graphics drivers. I have an 8800GTX, and have used this program from day one.  It is THE MOST painless way to get your stuff up and running.

I will try this.  Thanks.


My intentions are to get everything running smooth.  I will then install WOW and if I can get that to work I will move away from windows.

---

### Post by zika on 2009-02-25
> **chevmaro said:**
> I did install 9.2 driver.  However when I check the driver version in the Catalyst Control center it shows 8.5xx.  Can anyone with the 9.2 driver confirm this?  Possibly didnt install correctly?  Even when opening the installer it shows 8.5.
I'll read your thread.  Thanks.
yes, 9.2 gives You 8.582 driver. just ask if I could be of any help.

---

### Post by Vince4Amy on 2009-02-25
> **chevmaro said:**
> I did install 9.2 driver.  However when I check the driver version in the Catalyst Control center it shows 8.5xx.  Can anyone with the 9.2 driver confirm this?  Possibly didnt install correctly?  Even when opening the installer it shows 8.5.

I'll read your thread.  Thanks.

That's right, it's the version of the driver it's fine.

> Screen flickers when anything graphical is loaded like screen saver or media. ATI Control Center does not save settings for Res or Dual monitors that I specify. After waking up from sleep or monitors turning off it resizes my desktop so I have to scroll around. Only fix I find for that is a reboot.

Simple, you need to disable compositing. Turn off Compiz or any desktop effects and give it a go. Having Compositing and other OpenGL will most of the time cause conflicts as Compiz can't currently turn it's self off when an OpenGL App is open like DWM (Aero) on Vista Does.

---

### Post by chevmaro on 2009-02-25
I do have compiz installed.  Im going to uninstall it and turn it off.  I dont think the special effects are that cool anyways.  I would rather have a good running system.  Thanks for the tip.

---

### Post by oldHat on 2009-02-25
#1)  More info on Catalyst is available here:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Finishing_the_Install:_Configuration](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Finishing_the_Install:_Configuration)

Refer to "Installing the restricted drivers manually" 

=======================================================

#2) Check your xorg.conf.  There's a good example at [http://ubuntuforums.org/showthread.php?t=849422](http://ubuntuforums.org/showthread.php?t=849422)

Remember to use aticonfig (edited...should be "sudo aticonfig --input=/etc/X11/xorg.conf --tls=1 ") after each xorg.conf update.

---

### Post by zika on 2009-02-25
> **chevmaro said:**
> I do have compiz installed.  Im going to uninstall it and turn it off.  I dont think the special effects are that cool anyways.  I would rather have a good running system.  Thanks for the tip.
do not uninstall. just turn it off. some of its options can come handy sometimes, negative, etc ...

---

### Post by chevmaro on 2009-02-25
I assume turn it off by unchecking all the boxes?  Like cube and stuff?

---

### Post by zika on 2009-02-25
> **chevmaro said:**
> I assume turn it off by unchecking all the boxes?  Like cube and stuff?
no. System->Preferences->Appearance->Visual Effects->None

---

