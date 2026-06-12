---
title: "Change screen resolution"
date: 2007-05-23
forum: Desktop Environments
---

### Post by milu04 on 2007-05-23
Hi all,

I am new to Ubuntu. I just installed Ubuntu Desktop 7.04. My LCD monitor is 19'' MultiSync LCD2010 XtraView. However, Ubuntun can only detect that the maximal resolution  is 1024x768 and Refresh Rate is 61Hz. At the moment, in the Screen Resolution Preference box, I only have 3 resolutions: 640x480, 800x600, 1024x760, and only one Refresh rate 61Hz. 

Can anyone please tell me how to increase the resolution and adjust the Refresh rate?

I guess there may be some way to re-configure the monitor but I can not find it from Desktop interface.

Thank you very much for your help.

-Long

---

### Post by benanzo on 2007-05-23
This is an issue that deals with your actual graphics chip rather than the monitor.  What graphics chip do you have?  Is it an integrated Intel chip or ATI or nVidia?  We can help when we know what hardware you're using.

---

### Post by milu04 on 2007-05-23
Thank you very much for your instant reply. I have check it and the chipset is  ATI

Please help!

-Long

---

### Post by siteguru on 2007-05-23
Boot in recovery mode and at the prompt (after several loading screens) when it asks for a password or CTRL-D put in your root password.

Then type in **dpkg-reconfigure xserver-xorg** (enter) and follow the instructions. Most of the screens you can accept the default settings. When you get to questions about the graphics, make sure to select your graphics card make (ATI) and at a later screen make sure you define the horizontal and vertical refresh rates high enough, (e.g. on mine I set 28-100 horizontal and 60-120 vertical). At another screen be sure to select the resolutions your monitor can handle.

Once done you should end up at the login screen. After login you can then select the resolution and refresh rate you want.

---

### Post by milu04 on 2007-05-23
Thank you very much for your help.

I have tried dpkg-reconfigure xserver-xorg in recovery mode with root access. My Video Card is 256MB ATI Radeon X1300 Pro. Therefore, I enter:
- "ATI" for X server driver
- "ATI RADEON X1300" for video card identifier
- I take the default value "PCI:1:0:0" for Video card's bus identifier

However, when I restart the machine, it can not start X server. The out put is:

"(WW) RADEON: No matching Device section for instance (Bus ID PCI:1:0:1) found"
"(EE) No devices detected"

"Fatal server error: no screen found"


I also use "lspci" to check and I got:
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7183
01:00.1 Display controller: ATI Technologies Inc Unknown device 71a3
02:00.0 Multimedia controller: ATI Technologies Inc Unknown device 4d53

I guess Ubuntu can not detect ATI Video Card. If so, where could I get the driver to install it or what should I do next?

Please help!

---

### Post by benanzo on 2007-05-23
I think you changed the identifier for your Screen in your /etc/X11/xorg.conf so now it doesn't match the ServerLayout.

While in terminal do:
```
sudo nano /etc/X11/xorg.conf
```

and find:
```
Section "Screen"
```
Be sure that the Identifier matches the Screen line in
```
Section "ServerLayout"
```

It doesn't matter what it is, just as long as they are the same.
press CTRL-o (the letter) then enter to save
CTRL-x exits nano

Then type:
```
startx
```

to start the X server

---

