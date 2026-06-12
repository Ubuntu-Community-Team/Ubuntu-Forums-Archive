---
title: "Cant get Ubuntu to not crash"
date: 2005-12-10
forum: Desktop Environments
---

### Post by WaTTz on 2005-12-10
I just installed Ubuntu and I am having a major display problem. Everytime I login and get ready to go to the desktop the screen freezes and turns funny colors with many lines flashing everywhere. I assume its a driver problem with my video card. I tried failsafe mode and I get the same error. What can I do ?



I have a Nvidia 7800GT video card.

---

### Post by taurus on 2005-12-10
Are you sure you have both horizontal and vertical refreshing rates right for your monitor?  Also, what video driver do you use anyway?  You can make all your changes in /etc/X11/xorg.conf

sudo gedit /etc/X11/xorg.conf

---

### Post by mo_x on 2005-12-10
I am not sure the nvidia driver in Ubuntu supports your card. You can try downloading and installing the latest driver from the nvidia website.

---

### Post by WaTTz on 2005-12-10
Well...right now I am not using any video driver I dont think. I have had Ubuntu installed for about ten mintues. I am on WinXP right now. How I am suppose to install the driver at all if I cant even get into the desktop ?

---

### Post by taurus on 2005-12-10
[QUOTE=WaTTz]Well...right now I am not using any video driver I dont think. I have had Ubuntu installed for about ten mintues. I am on WinXP right now. How I am suppose to install the driver at all if I cant even get into the desktop ?[/QUOTE]
After Ubuntu finishes booting, hold down <Ctrl><Alt>F2 and that would put you to a terminal.  Log in and use a text editor to edit your /etc/X11/xorg.conf

sudo pico /etc/X11/xorg.conf

Then, make sure both horizontal & vertical are correct (those are the values for my Dell 17" monitor so better use the correct ones from the manual for your monitor),

HorizSync       28-51
VertRefresh     43-60

Then, make sure your video card driver looks like this,

Driver          "nv"

Save it and reboot and hopefully, everything is fine now...

---

### Post by ubunick on 2005-12-10
[QUOTE=WaTTz]I just installed Ubuntu and I am having a major display problem. Everytime I login and get ready to go to the desktop the screen freezes and turns funny colors with many lines flashing everywhere. I assume its a driver problem with my video card. I tried failsafe mode and I get the same error. What can I do ?

I have a Nvidia 7800GT video card.[/QUOTE]

I'm actually having a similar problem, but I don't have an Nvidia card.  I think it's on-board video, and I have pretty much the same glitches you do.

---

### Post by WaTTz on 2005-12-10
I tried editing my /etc/x11/xorg.conf and I am using the "nv" driver but I didnt see anything at all about HorizontalSync...and VertRefresh. I am still having the same problem . Help !!

---

### Post by taurus on 2005-12-10
Don't have a section for your "Monitor"???

Okay, add these lines to your /etc/X11/xorg.conf (after the Section "Device")

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

And again, please use the values for horizontal and vertical for your monitor, not the ones above since they are for my Dell 17" monitor...

But if you are not sure about it, then just post your /etc/X11/xorg.conf and will see if we can figure out what's wrong with it.

---

### Post by willoc on 2005-12-10
you could also try ctrl-alt F2 at the login and then run "apt-get install nvidia-glx"  I also have an nvidia card and ran into similar login problems.  I can't be positive that this is what is wrong, but you may want to give it a try.  

Make sure you comment out GLcore and dri too.  and add glx if it is not there.  also, change nv to nvidia in the device section:

Section "Module"
#       Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection


If this does not fix it, you can just undo the changes in xorg.conf.

---

### Post by WaTTz on 2005-12-10
I tried adding the sync horizontal and vertrefresh lines and that didnt work. I tried sudo apt-get install nvidia glx and I got this message " could not open lock file /var/lib/apt/lists/lock"


I would post my xorg.conf but I dont want to write all that down and I dont know how I could copy paste it so I guess thats not an option.

---

### Post by mo_x on 2005-12-11
If you want to install the nvidia drive you need to get it from their website. Your card is not supported by the driver that comes with Ubuntu. You can search this forum on how to install the driver.
It should be possible to make it work with another driver first. Can you post /etc/X11/xorg.conf and /var/log/Xorg.0.log as attachments, you may have to change the extension of the files do so.
Try editing your xorg.conf and use the vesa driver.

---

