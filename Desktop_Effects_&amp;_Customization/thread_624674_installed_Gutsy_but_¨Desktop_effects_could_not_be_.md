---
title: "installed Gutsy but ¨Desktop effects could not be enabled¨, xgl ?"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by Enginirical on 2007-11-27
Hey 

I recently installed Gutsy Gibbon after an eager return to ubuntu from having to use xp for the past 4months. Any way this was installed after a failed upgrade from feisty, I must say so far Gutsy has bowled me over having fixed all the major issues I had with feisty.

I am unfortunately unable to enable desktop effects getting the error message ¨desktop effects could not be enabled¨. (I have installed compiz settings manager aswell). My understanding is that ubuntu 7.10 is installed by default with xgl session running.

BUT after installing compiz settings manager I got this from the terminal...

[COLOR="Navy"]dim@gutsy-asus:~$ compiz --replace &
[1] 6590
Checking for Xgl: not present. 
dim@gutsy-asus:~$ No whitelisted driver found aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "aurora",
dim@gutsy-asus:~$ ccsm --replace
/usr/lib/python2.5/site-packages/ccm/Constants.py:60: GtkWarning: Unable to locate theme engine in module_path: "aurora",
  Tooltips = gtk.Tooltips()[/COLOR]

Can someone please explain to me what is going on and why? do I just need to install xserver-xgl? shouldn't it already be there by default? Could this be to do with using my old home folder from feisty? 

Cheers

---

### Post by cyberdork33 on 2007-11-27
It is not installed already. It will start automatically if installed, but you still have to install it first.

---

### Post by Nano Geek on 2007-11-27
> **cyberdork33 said:**
> It is not installed already. It will start automatically if installed, but you still have to install it first.It looks like it's installed, but it's giving an error.

What graphics card do you have?

---

### Post by Ub1476 on 2007-11-27
> No whitelisted driver found

I guess you are [blacklisted]("http://ubuntuforums.org/showthread.php?t=582112").

---

### Post by Enginirical on 2007-11-27
I have Mobility Radeon X1450. (hence the ball ache with feisty)

I havnt actively installed xgl, and if what I read is true that I still have to install..I think maybe any mention to xgl is from my old feisty home folder which I had backed up my settings on. I'm guessing I have to just install xgl then...?

---

### Post by Lagos on 2007-11-27
you have to download XGL from the package manager.  then reboot and everything will work.

---

### Post by Nano Geek on 2007-11-27
> **Lagos said:**
> you have to download XGL from the package manager.  then reboot and everything will work.Yes, I would try that.```
sudo apt-get install xserver-xgl
```

---

### Post by FuturePilot on 2007-11-27
It looks like there might be something wrong with your theme. Try changing it.

---

### Post by Enginirical on 2007-11-27
awesome! thanks guys, works a treat!

(yeah my last theme was part emerald part metacity, so the window theme aurora disappeared after gutsy install since emarald is no more.)

---

