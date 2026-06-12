---
title: "Switchers and expo won't work"
date: 2011-02-06
forum: Desktop Environments
---

### Post by HTMLCrazy on 2011-02-06
I am not sure if this is the right place to post this or not. I had the expo, ring switcher, and the shift switcher configured to run when I put my cursor in each corner that I had set up to start the switcher. ONe day, I was doing schoolwork when the windows that I had spread out over the different workspaces all consolidated to Workspace 1 and none of my switchers worked. I tried rebooting the computer, reverting all changes I had made in Compiz, everything I knew how to do. Is there any way to fix this?

---

### Post by HTMLCrazy on 2011-02-06
when the switchers stopped working, the desktop effects were switched to none. I tried to reenable the desktop effects, but to no avail. Now when i click in one of those corners, it always reverts to none no matter what setting I have it on.

---

### Post by HTMLCrazy on 2011-02-06
I use Ubuntu 10.10

---

### Post by Krytarik on 2011-02-06
If you cannot enable desktop effects, Compiz isn't running, thus none of its plugins will work. It's most probably a video driver related issue. What card/chip do you have? What driver do you run? How did you install those?

---

### Post by HTMLCrazy on 2011-02-06
I am using an ATI Radeon card in my laptop. I didn't download or install any drivers as I didn't think I needed to since it seemed everything was working all right. I had looked into drivers, but there were no linux drivers available.

---

### Post by Krytarik on 2011-02-06
> **HTMLCrazy said:**
> I am using an ATI Radeon card in my laptop.
It would be nice, if you are more specific.;-)

However, try installing the best available driver, to not at least increase the video performance of your system as best as you can.

First go to "System -> Administration -> Additional Drivers". With that tool you can search for compatible drivers and install/activate them.

If you have an older ATI card/chip, which isn't supported by the proprietary drivers anymore, the Open Source Edge Drivers are currently the best solution:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)
(look below that section to get to a list of now unsupported video cards/chips)

---

### Post by HTMLCrazy on 2011-02-06
I am new to Ubuntu. I have only had it for about 4 months.

I have no idea what to look for on that web page you linked to. What should i be looking for? 

How do I find my video card type?

---

### Post by Krytarik on 2011-02-06
Did you try the "Additional Drivers" thing before? What card do you finally have, specifically!? If you have an older card, the Open Source Edge driver is relevant for you, as I wrote.

---

### Post by HTMLCrazy on 2011-02-06
I did what that webpage said and everything worked....for about 30 sec. Then it changes back to no graphical effects. Do you have any other suggestions?

If I knew how to find my exact card type, I would. Like I said, I am new to Ubuntu and need help with finding my exact card type. Any guidance would be greatly appreciated.

---

### Post by Krytarik on 2011-02-06
> **HTMLCrazy said:**
> 
If I knew how to find my exact card type, I would. Like I said, I am new to Ubuntu and need help with finding my exact card type. Any guidance would be greatly appreciated.
What is the output of the following command?:
```
lspci |grep VGA
```

---

### Post by HTMLCrazy on 2011-02-06
Radeon IGP 330M/340M/350M

I rebooted my comp. and now it CAN'T enable desktop effects at all.

---

### Post by Krytarik on 2011-02-06
> **HTMLCrazy said:**
> Radeon IGP 330M/340M/350M

I rebooted my comp. and now it CAN'T enable desktop effects at all.
So, the Open Source Edge drivers will not work with your onboard video chip:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

If you did upgrade to those, downgrade again with the following commands:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```
After that, reboot and then check if direct rendering (hw-accelerated video) is enabled:
```
sudo apt-get install mesa-utils
glxinfo |grep rendering
```

---

### Post by HTMLCrazy on 2011-02-06
I did remove the open edge drivers. 

I also did what you said for the direct rendering. I input the command but nothing perceptible happens. Is that what is supposed to happen?

I then tried to reenable desktop effects, and it still says that it can't enable them.

---

### Post by Krytarik on 2011-02-06
> **HTMLCrazy said:**
> 
I also did what you said for the direct rendering. I input the command but nothing perceptible happens. Is that what is supposed to happen?
At my system, it says:
```
krytarik@krytarik-desktop:~$ glxinfo |grep rendering
direct rendering: Yes
krytarik@krytarik-desktop:~$ 

```

---

### Post by HTMLCrazy on 2011-02-06
nothing like that came up on mine
> jon@Jonslaptop$ glxinfo |grep rendering
jon@Jonslaptop$

---

### Post by Krytarik on 2011-02-06
Did you install it before? What if you only enter "glxinfo"?

---

### Post by HTMLCrazy on 2011-02-06
```
name of display: :0.0
Segmentation fault
```

---

### Post by HTMLCrazy on 2011-02-15
I ran the code and this is what I got:
```
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon IGP 330M/340M/350M
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y
```

---

### Post by realzippy on 2011-02-16
*Driver in use:         vesa*

Why using vesa?Do you have a xorg.conf file where you explicitly load the vesa driver?
Open terminal,run:
```
cat < /etc/X11/xorg.conf | grep Driver
```

---

### Post by HTMLCrazy on 2011-02-16
Here is the output code of the command:
```
bash: /etc/X11/xorg.conf: No such file or directory

```

---

### Post by realzippy on 2011-02-17
You could create a xorg.conf which calls explicitly the intel driver,
but strange thing is that compiz runs for 30 seconds and then stops..

Boot an Ubuntu LiveCD to check if compiz runs on a vanilla system...

---

### Post by HTMLCrazy on 2011-03-01
Slight problem.....my computer does not support usb boot and my internal drive is shot. Any ideas for maybe booting off of a cd from inside an os?

---

