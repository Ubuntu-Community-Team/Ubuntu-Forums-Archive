---
title: "Need help booting up with vesa."
date: 2009-02-15
forum: General Help
---

### Post by dodle on 2009-02-15
I just installed 8.10 on my laptop which has Unichrome graphics.  I had to use the Alternate Installation disk because it wouldn't boot into the live CD normally, or in safe graphics mode.  I have the same issue after finishing the installation and trying to boot up.  I think booting up with vesa might solve this problem.  From the GRUB menu, how can I make an option to boot up with vesa mode?

Alternatively, I could edit the xorg.conf file from the shell, but I don't know what command to use to do this.  What tool do I use to edit text files in the shell?

---

### Post by ridetheteapot on 2009-02-15
sudo nano /etc/X11/xorg.conf

nano is simple editor ctrl+o to save ctrl+x exit
Section Device
Driver "vesa"

---

### Post by dodle on 2009-02-15
Didn't work for me.  I also tried the following under "Screen":
```
SubSection
    Depth 16
    Modes "1024x768@75"
```

I got a message, after rebooting, that Ubuntu was running in Safe Graphics mode.  I hit "okay" but just got a black screen after that.

BTW: This laptop uses Unichrome S3 graphics.

---

### Post by dodle on 2009-02-15
Here is what my xorg.conf looks like:
```
Section "Device"
    Identifier "vesa"
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor    "Configured Monitor"
    Device     "vesa"
    SubSection "Display"
        Depth 16
        Modes "1024x768@75"
    EndSubSection
EndSection
```

---

### Post by ridetheteapot on 2009-02-15
K i think that your card doesn't play with vesa too nicely.
There are other driver which you can try is savage [http://linux.die.net/man/4/savage](http://linux.die.net/man/4/savage)

EDIT --- fyi its in synaptic and already installed

---

### Post by dodle on 2009-02-15
Okay, here is what my xorg.conf looks like now:
```
Section "Device"
    Identifier "Configured Video Device"
    Driver     "savage"
EndSection


Section "Monitor"
    Identifier "Configured Monitor"
EndSection


Section "Screen"
    Identifier "Default Screen"
    Monitor    "Configured Monitor"
    Device     "Configured Video Device"
    SubSection "Display"
        Depth 16
        Modes "1024x768@75"
    EndSubSection
EndSection
```Now I get the following error when I type "startx":> (EE) No devices detected.

Fatal server error:
no screens found

---

### Post by dodle on 2009-02-15
I think I'm getting closer.  I'm using the via driver and get the following error when I input "startx":```
(EE) Failed to load /usr/lib/xorg/modules/driver//via_drv.so: Undefined Symbol: xf86errno
```
Notice the "//" before via_drv.so?  I think this is what is causing my problem.  Anyone know how to fix this?

**Edit:** I copied the xorg.conf from a 6.06 live cd to /etc/X11 because 6.06 boots up fine on my laptop.

---

### Post by ridetheteapot on 2009-02-15
I pretty sure that extra / wont do anthing...

I looked a little into the via thing. Maybe check for new drivers at thier own site? might need a new release.

The other thing you can try is the openchrome driver, see if that works... oh also might want to check man openchrome for some xorg options/compatibility

---

### Post by dodle on 2009-02-15
I've pretty much given up and installed dapper since it's the only one that will run on this machine.  I'm doing a:```
sudo apt-get dist-upgrade
```to Hardy.  I know this isn't the recommended way to get the newer distro, but we'll see what happens.

---

### Post by ridetheteapot on 2009-02-15
did you try the openchrome driver?
If not it out and see if it works, if the upgrade goes well.

---

### Post by dodle on 2009-02-16
Okay, I have successfully upgraded to Hardy and everything is working fine with the via driver.  Next I'm going attempt an Intrepid upgrade.

---

### Post by zy_guy on 2009-02-17
I had the same issue when I boot a live 8.10 cd. I have to go into xorg.conf and change the driver to openchrome and it works for me everytime.

---

### Post by dodle on 2009-02-17
I wish that I would have just tried the openchrome driver before going through all these upgrades.  After the upgrades, the via driver is working fine, but I am still having issues.  I thought that it was related to the video driver but does not appear so anymore.  I am going to start a new thread about it, but system freezes just before GDM starts up.

---

