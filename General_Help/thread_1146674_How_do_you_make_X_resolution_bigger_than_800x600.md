---
title: "How do you make X resolution bigger than 800x600?"
date: 2009-05-02
forum: General Help
---

### Post by scott8035 on 2009-05-02
I just installed Ubuntu on my son's computer which has an old-fashioned glass CRT monitor. When he was running Windows XP, it was running fine at 1024x768@75Hz. Ubuntu is maxing out at 800x600@60Hz. What's the "ubuntu way" for configuring this so he can have the higher resolution?

---

### Post by BslBryan on 2009-05-02
First, try System --> Preferences --> Screen Resolution.

If no higher resolution is available, please post what graphics card he has in his machine.

---

### Post by _Purple_ on 2009-05-02
Try to change it from System > Administration > Screen Resolution

Edit: BslBryan beat me :)

---

### Post by scott8035 on 2009-05-02
I already tried the System > Preferences > Display thing, that's where I got the previous specs from.

When I look at /var/log/Xorg.0.log, it says he has a "nVidia Corporation C51 [GeForce 6150 LE]".

---

### Post by _Purple_ on 2009-05-02
Go to System > Administration > Hardware drivers. Is there any recommended driver available? Is it activated?

---

### Post by BslBryan on 2009-05-02
nVIDIA drivers and Ubuntu don't mix very well, as they are a little tricky to configure sometimes.  

I have a couple of suggestions.  
Try 
```
mkdir /etc/X11/backup
cp /etc/X11/xorg.conf /etc/X11/backup
rm /etc/X11/xorg.conf
dpkg-reconfigure -phigh xserver-xorg
nvidia-xconfig
```

Then reboot. If that doesn't work then restore what you have done above by doing

```
rm /etc/X11/xorg.conf
cp /etc/X11/backup/xorg.conf /etc/X11/
```

Also, you can simply edit /etc/X11/xorg.conf 
```
gksudo gedit /etc/X11/xorg.conf
```
and make anything you see there with a list of screen resolutions also say ```
1024x768@75
```

Or, you can run 
```
cat /etc/X11/xorg.conf | grep Driver
```
and make sure that the line ```
driver
```
reads
```
driver "nvidia"
```

and if it doesn't, run 
```
gksudo gedit /etc/X11/xorg.conf
```
and change it.

Finally, you can install envyng, which is an application specifically made for installing nVIDIA drivers.  I've got a few more ideas if none of these work, but I think envy may be your best shot, but the other ideas are easier and so you might try those first.  Anyway, to install envy:

```
sudo apt-get install envyng-qt
```

Then, the GUI will be available in Applications --> System Tools
But if you want, you can get it by typing in the terminal

```
sudo envyng -t
```

Then follow the instructions on the GUI.

The first time I did that, it worked flawlessly.

Then I tried to configure a second screen for my tv, and I completely messed up everything, and had to reinstall envy. For some reason, it did not work correctly the first time running it, but worked after that.

Just use your knowledge and common sense, and you should be fine.

If it still doesn't work, though, let us know?

Good luck. :)

---

### Post by scott8035 on 2009-05-02
I don't think the problem is the video driver, I think it's because it's detecting a generic CRT monitor and can't tell what its capabilities are. How can I tell X what settings to use for the monitor?

---

### Post by ad_267 on 2009-05-02
> **BslBryan said:**
> nVIDIA drivers and Ubuntu don't mix very well, as they are a little tricky to configure sometimes.

I've never had any problems with the default nvidia drivers.

Just enable them from System - Administration - Hardware Drivers and restart. Then press alt-f2 and run "gksu nvidia-settings" and set the resolution there.

---

### Post by michy99 on 2009-05-02
You need the Horizontal Sync and Vertical Refresh values for your monitor. If you don't have the manual, you may be able to find on the internet.

 Then open a terminal and enter

```
gksudo gedit /etc/X11/xorg.conf
```

Change the monitor section like this, but use the values for your monitor.

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync       30-85
        VertRefresh     50-160
```

Save and re-boot.

---

### Post by BslBryan on 2009-05-02
> **ad_267 said:**
> I've never had any problems with the default nvidia drivers.

Note that I did say *sometimes.*

For me it was tricky, and for at least 3 other people on the front page of "general help" at this very second it was too.  I'm just offering advice that I have, because I had the same problem he did.  Not forcing it on anybody. :)

---

### Post by scott8035 on 2009-05-03
Thanks, everyone. Doing a simple System > Administration > Hardware drivers and updating to the proprietary nVidia driver did the trick. Thansk for all your help.
---scott

---

### Post by faris_zero on 2010-01-04
i have the same problem..  then i use envyng and VOILA.. it's work \:D/
thanks all...

---

