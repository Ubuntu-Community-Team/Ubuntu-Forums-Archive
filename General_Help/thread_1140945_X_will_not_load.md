---
title: "X will not load"
date: 2009-04-28
forum: General Help
---

### Post by kportertx on 2009-04-28
Every time I try to startx my laptop locks up.  This did not start happening till right after I upgraded to ubuntu 9.04 today.

So far I have tried
sudo gdm
sudo startx
sudo startxfce
sudo X -configure
sudo X -config ~/xorg.conf.new //created by previous command

all of the above lock up in the same manner.  When it locks up and cannot switch to a virtual console or restart x.  To restart I either have to hard power or raise a skinny elephant.

Any suggestions?

---

### Post by huntzire on 2009-04-28
> **kportertx said:**
> Every time I try to startx my laptop locks up.  This did not start happening till right after I upgraded to ubuntu 9.04 today.

So far I have tried
sudo gdm
sudo startx
sudo startxfce
sudo X -configure
sudo X -config ~/xorg.conf.new //created by previous command

all of the above lock up in the same manner.  When it locks up and cannot switch to a virtual console or restart x.  To restart I either have to hard power or raise a skinny elephant.

Any suggestions?

instresting you might want to post the xorg logs in /var/logs

to show us abit more,
in the mean time i'm not sure why your starting Xserver directly or with those other methods, have you tried /etc/init.d/gdm start

---

### Post by Peter09 on 2009-04-28
Can you post the output of
```
lshw -C video
```
so that we can see the configuration of your graphics card

---

### Post by kportertx on 2009-04-28
for lshw -C video,
*-display UNCLAIMED
description: VGA compatible controller
product: Radeon XPRESS 200M 5955 (PCIE)
vendor: ATI Technologies Inc
physical id: 5
bus info: pci@0000:01:05.0
verson: 00
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list
configuration: latency=66 mingnt=8

---

### Post by kportertx on 2009-04-28
Is there a way to load a failsafe x so that I can just cut an paste this information

---

### Post by kportertx on 2009-04-28
xorg.conf

Section "ServerLayout"
[INDENT]Identifies "X.org Configured"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyBoard"[/INDENT]
EndSection

Section "Files"
[INDENT]ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
{More fonts}[/INDENT]
EndSection

Section "Module"
[INDENT]Load "glx"
Load "extmod"
Load "dbe"
Load "dri2"
Load "dri"
Load "record"[/INDENT]
EndSection

{Input device sections skipped}

Section "Monitor"
[INDENT]Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
[/INDENT]EndSection

Section "Device"
[INDENT]Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
[INDENT]Viewport 0 0
Depth 1[/INDENT]
EndSubSection
SubSection "Display"
[INDENT]Viewport 0 0
Depth 4[/INDENT]
EndSubSection
SubSection "Display"
[INDENT]Viewport 0 0
Depth 8[/INDENT]
EndSubSection
SubSection "Display"
[INDENT]Viewport 0 0
Depth 15[/INDENT]
EndSubSection
SubSection "Display"
[INDENT]Viewport 0 0
Depth 16[/INDENT]
EndSubSection
SubSection "Display"
[INDENT]Viewport 0 0
Depth 24[/INDENT]
EndSubSection
[/INDENT]EndSection

---

### Post by kportertx on 2009-04-28
Notable entries in log

looks like it disabled my mouse and keyboard
(WW) Disabling Mouse0
(WW) Disabling Keyboard0

Not sure bout these
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 320, HOverPlus: 24, HSyncWidth: 136
VBlank: 38, VOverPlus: 3, VSyncWidth: 6

(WW) RADEON(0): LCD DDC Info Table found!
(WW) RADEON(0): Unknown vendor-specific block f
(WW) RADEON(0): Unknown vendor-specific block f
(WW) RADEON(0): Direct rendering disabled


that is all the warnings

---

### Post by kportertx on 2009-04-28
> **huntzire said:**
> instresting you might want to post the xorg logs in /var/logs

to show us abit more,
in the mean time i'm not sure why your starting Xserver directly or with those other methods, have you tried /etc/init.d/gdm start

/etc/init.d/gdm start has the same result

---

### Post by Peter09 on 2009-04-28
Could you try removing /etc/X11/xorg.conf (just save it by renaming it to something else)

Then restart you X server.

As a general principle xorg is not used by default these days, its is used to force settings on the video card. With a blank xorg you may get a working screen and you can then add to xorg bit by bit from there.

(note that your lshw tends to suggest that you have no driver attached)

---

### Post by kportertx on 2009-04-28
> **Peter09 said:**
> Could you try removing /etc/X11/xorg.conf (just save it by renaming it to something else)

Then restart you X server.

As a general principle xorg is not used by default these days, its is used to force settings on the video card. With a blank xorg you may get a working screen and you can then add to xorg bit by bit from there.

(note that your lshw tends to suggest that you have no driver attached)

I renamed xorg.conf to xorg.conf.123 and executed sudo gdm with the same result.  Black screen for the most part and what looks like multi-colored static on white backgrond n the bottom 9th of the screen.

---

### Post by kportertx on 2009-04-28
I'm currently downloading ubuntu 9.04 iso, any suggestion if it is able to boot?

---

### Post by Monsieur Gonzalez on 2009-04-28
Have you tried to reconfigure the Xorg server (sudo dpkg-reconfigure xserver-xorg) ? 

You might try with radeon or radeonhd to see if it helps.

---

### Post by Peter09 on 2009-04-28
Note - having renamed your xorg you will need to restart your x server. Logging out/in will do it.

---

### Post by kportertx on 2009-04-28
Now that I'm using a blank xorg file, it loading up with VESA.
sudo dpkg-reconfigure xserver-xorg did not resolve the problem

---

### Post by Peter09 on 2009-04-28
OK, check that you do not have a third party driver waiting to be enabled in System->Admin->Hardware Drivers

---

### Post by kportertx on 2009-04-28
> **Peter09 said:**
> OK, check that you do not have a third party driver waiting to be enabled in System->Admin->Hardware Drivers

X will not load, so those menus are not available.

---

### Post by kportertx on 2009-04-28
> **kportertx said:**
> Now that I'm using a blank xorg file, it loading up with VESA.
sudo dpkg-reconfigure xserver-xorg did not resolve the problem

But fails to load with VESA as well...

---

### Post by Peter09 on 2009-04-28
have a look in Xorg.0.log

```
more /var/log/Xorg.0.log
```

---

### Post by kportertx on 2009-04-29
i now have wireless connected, and can browse internet with links...

---

### Post by kportertx on 2009-04-29
I have ubuntu on a thumb drive, but my bios does not have a boot from usb option.  I have mounted the usb drive and the iso image
is there a way to boot it from the image?

---

### Post by loganp82 on 2009-04-29
when i first updated to 9.04 and tried installing the nvidia drivers it messed up x so i did a sudo apt-get dist-upgrade and then installed the nvidia drivers and everythings worked fine since. maybe this will help. maybe not.

---

### Post by kportertx on 2009-04-29
I removed fglrx and followed the steps detailed here:[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Now I can startx as root but not as a user using sudo...  Also I would like to try to install the proprietary driver again but it does not show up in restricted drivers manager

---

### Post by kportertx on 2009-05-12
Think I found the issue for me...  When I install the ATI drivers on 9.04 my laptop will no longer load X.  I am currently running fine without them installed.  Any suggestions?

---

### Post by kportertx on 2009-05-15
bump ):P

---

### Post by remmyshroomo on 2009-05-16
I have just experienced the same issue. I updated my ATI drivers to the new ones and did a reboot. All of a sudden I started getting the same black screen with a few weird block lines at the top. IT IS THE DRIVERS!

Since I was already in the middle of a reload of the system I can sacrifice a total system reload, but that still begs the question... WTF did the ATI driver do to kill it and how would someone in the future roll back their ATI drivers from the recovery console?

Please help us!

---

### Post by ledzepjes on 2009-05-16
Yeah, anytime I have experienced issues with ubuntu not loading xorg, or having a funky display with green or yellow or black lines or when after logging in it goes to a black screen, it's usually always my video card drivers. I have to uninstall my video card drivers before any upgrade to ubuntu, and even after installing some ubuntu updates, I get a black screen. Luckily I know how to boot to ubuntu cmd line by 
 
1) selecting the second option in the grub menu labeled "recovery mode" and go to "Drop to root shell prompt" (as of 9.04)
2) uninstall my current video card drivers. If I was using envy or envyng or radeon drivers, "sudo apt-get remove envy", or "sudo apt-get remove envyng" (or just use "sudo apt-get remove env*" the * will find and uninstall all versions of programs in synaptic starting with env, it's a catch all that's good for other things when using the cmd line, it'll work when typing in just some of the word) and you can then
3) type "y" for yes when it asks "Do you want to uninstall?" then
4) I type: "reboot" or "sudo init 6" which reboot's the computer. 
5) Another option if you don't want to reboot from the cmd line, you can also type "sudo /etc/init.d/gdm stop" to stop the gnome display manager then "sudo init 2" which loads the gui.
 
After this sequence your video card drivers should be uninstalled and you should be able to use the gui. From here, you can try to reinstall the drivers.

---

### Post by kportertx on 2009-06-12
Sorry never updated this post.  ATI dropped support for my video card (ATI Radeon x200).  My work-around is to use the open source driver.

---

### Post by remmyshroomo on 2009-07-03
So what's the solution? I'm in the same boat as you. :(

---

