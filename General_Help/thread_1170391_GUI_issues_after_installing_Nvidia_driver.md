---
title: "GUI issues after installing Nvidia driver"
date: 2009-05-26
forum: General Help
---

### Post by punxnotdead on 2009-05-26
I am absloutely new to Ubuntu, and I'm having graphic card driver issues. I installed 9.04 and installed the recommended driver for my card an EVGA gtx285 and restarted. When i restart I'm in text hell. No Gui and I have no idea how to get back to the GUI to disable or remove the driver. I tried startx and CTRL ALT F1, CTRL ALT F4, yadda. None of these seem to help, any advice would be appreciated, as I am VERY new, thanks in advance.:D

---

### Post by pro003 on 2009-05-26
how exactly did you installed this driver and where from?

anyway when you get in this non-gui mode, try to login and type

```
 startx
```

---

### Post by punxnotdead on 2009-05-26
i installed in in Ubuntu under the driver installation feature Ubnutu said it was the recommended driver and told me to restart for it to become active. I tried startx after login and it doesn't work.

---

### Post by punxnotdead on 2009-05-26
says primary device is not PCI 
(EE) No devices detected.
 
Fatal server error:
no screens found

---

### Post by spcwingo on 2009-05-26
Try this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That reconfigures the xserver back to the default settings.  After that, enter this command:

```
sudo /etc/init.d/gdm restart
```

This restarts the Gnome Display Manager.  You should now have your GUI back.  At this point you should now go back to system>admin>hardware drivers and disable/uninstall the driver that didn't work.  If you want, you can try installing envyng to install the graphics drivers...I had to do this to get my graphics card rolling.  To install envyng just enter this command in a terminal:

```
sudo apt-get install envyng-core
```

Now press CTRL+ALT+F1 to drop out of X.  Enter this command to run envyng:

```
envyng -t
```

After that follow the on-screen instructions to install the driver for your card.  Just reboot when prompted.  Let us know if this get her going.

---

### Post by punxnotdead on 2009-05-26
Nope, after i enter: 
 
sudo dpkg-reconfigure -phigh xserver-xorg
 
it says:
 
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20090526080036
 
then i enter:
 
sudo /etc/init.d/gdm restart
 
and it says: 
 
* Stopping GNOME Display Manager...
* Starting GNOME Display Manager...
 
then i'm back at the prompt...lol
 
I tried it twice and double checked to make sure it was all entered correctly also.

---

### Post by Kareeser on 2009-05-26
That seems good... if it starts GDM, and there are no errors, then press Ctrl-Alt-F7, and see if you're back in.

Alternatively, reboot.

---

### Post by punxnotdead on 2009-05-26
CTRL ALT F7 gives me a flashing cursor with a blank screen, and a reboot gets me back to the screen where it says:
 
* starting ...
* enabling additional executable binary formats binfmt-support
* checking battery state...       
 all of which return a value of ok
 
but there is just a flashing cursor afterward, zero activity.
 
I have installed this sucessfully on my laptop without any issue(32bit).
the last time i did this on my desktop (64 bit version) i reinstalled (32 bit) and it worked, the reason i tried it again was because i tried the 32 bit version which is the one i have on my laptop. the 64 bit version wouldnt even let me update for some reason.

---

### Post by punxnotdead on 2009-05-26
I think ima just reinstall and try the envyng installer for my drivers.

---

