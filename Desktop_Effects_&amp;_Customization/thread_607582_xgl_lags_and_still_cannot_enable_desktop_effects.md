---
title: "xgl lags and still cannot enable desktop effects"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by charles_316 on 2007-11-09
I have updated ubuntu 7.10 with compiz fusion, etc.

However, I cannot enable desktop effects - it sometimes says "composite extension is not available too" after trying out some of the different methods ppl have listed here..

I have tried installing xserver-xgl but it causes everything to lag! Am i doing something wrong because there is no way I can run xgl if it is like that? When I remove xserver-xgl from the Synaptics Package Manager and restart, the system is back to normal and no lag.... 

And despite all this, I still have not been able to get desktop effects to work... any advice?

My system is a new Thinkpad T60 with ATI Radeon X1400. 

Thanks in advance

---

### Post by Forlong on 2007-11-09
Did you install the proprietary driver via *System &#8594; Administration &#8594; Restricted Drivers Manager*

After doing that (and a reboot) post the output of ```
compiz
``` in a terminal.

---

### Post by charles_316 on 2007-11-10
yes the restricted drivers for my ATI card are enabled and in use... 

i have since deleted the xserver-xgl because of the extreme lag it caused...
here was the output of typing compiz into terminal:

charles@charles-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by charles_316 on 2007-11-10
and when i have xserver-xgl installed in synaptics package manager and put compiz into terminal, i get:

charles@charles-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

This is probably why things lag so much in XGL ? Can anyone please explain how to get it working so that XGL runs smoothly and I can get desktop effects enabled correctly?

Thanks

---

### Post by Forlong on 2007-11-10
What's the output of ```
fglrxinfo
```

---

### Post by charles_316 on 2007-11-10
the output of fglrxinfo WITHOUT xserver-xgl is:

charles@charles-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

Do you need the output when USING xserver-xgl?

---

### Post by charles_316 on 2007-11-12
bump

---

### Post by charles_316 on 2007-11-15
bump

---

### Post by Jouke74 on 2007-11-15
No you should adjust Xorg.conf to enable DRI and GLX. And run the XGL server as well. I have more optimalizations for XGL and ATI cards, but I need to find the document at my home computer.

---

### Post by Jouke74 on 2007-11-17
If you don't feel comfortable by doing these instruction please consult someone who has a bit more experience with Linux. Or hit the forums again.

**1. First step get ATI fglrx running. Change the following Xorg.conf sections under the 8.37 driver, not the new ATI 8.42 AIGLX driver(!):**

[INDENT]Section "Device"
Indentifier "Generic Video Card"
Driver "fglrx"
Busid "PCI:1:0:0"    *(note on your PC this may be different).*
Option "Backingstore" "true"
Option "DRI"  "true"
Option "ColorTiling" "true"
Option "EnablePageFlip" "true"
Option "Accelmethod" "EXA"
Option "XAANoOffscreenPixmaps" 
Option "RendelAccel" "true"
EndSection
[/INDENT]

[INDENT]Section "DRI"
Mode 0666
EndSection
[/INDENT]

[INDENT]Section "Extensions"
Option "Composite"  "0"
EndSection

[/INDENT]Leave the rest as is. 

**2. Install X-server**

Open a terminal and paste:

[INDENT]
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install xserver-xgl
[/INDENT]

**3. Change the GDM.conf to make XGL the standard server.**

[INDENT]cd /etc/gdm
sudo cp gdm.conf gdm.back *(this is your backup copy!).*
sudo gedit gdm.conf[/INDENT]

Check if the standard server is 0, should be somewhere close to the bottom in the text.
Careful go through this large file as there are many other options.

Change the standard server section into:

[I][server-standard]
name=Standard Server
command=/usr/bin/Xgl -fullscreen -br +bs -ac -accel glx:pbuffer -accel xv:pbuffer -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11dpi/:unscaled, usr/share/fonts/X11/75dpi/:unscaled,usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType

flexible=true.[/I]

NB the fonts paths can be found in your Xorg.conf as well, however XGL tends to read them wrong, thats why they need to be specified here again. The huge XGL command is one(!) line.

[INDENT]Then remove the "#" sign from priority and make it : priority=-5.

Change the GDMXservertimeout to 40 instead of 10.[/INDENT]

Save this file, and also make a copy of it because with updates the original might be restored by Ubuntu:

[INDENT]sudo cp gdm.conf gdm.adjustedbyme[/INDENT]

If you did not make typo's, reboot your PC and you are now running with a standard XGL server instead of X server. 

Done.

**In case of emergency**
If this fails and some error occurs the X-server which is the fail-save should start. However, if no server starts and it gives only an error, you can restore the original gdm.conf by running the system restore boot option. Then enter your normal login credentials. Then in the "terminal" = screen do:

[INDENT]cd /etc/gdm
sudo mv gdm.conf gdm.nogo
sudo mv gdm.back gdm.conf[/INDENT]

Reboot...

That restores whatever you had in the beginning.

Notes:
- If you are running XGL server. It will state with fglrxinfo that you don't have any direct rendering! This is correct, and that is because all direct rendering is taken over by the XGL server itself. It is silly to have direct rendering on top of direct rendering (can't be done actually). 
- If you are running the XGL server the fglrxinfo will also state that it is using the mesa drivers. This is correct, and it is the way it should be, unlike many forums members sometimes suggest. Below your fullscreen window in which you are running the XGL server the drivers are doing their work on the X-server layer which is also running in the background.  If you want to know more about this, read the XGL wiki and manual!
- Composite can now be enabled using XGL (even though Xorg.conf says 0).
- You might need to whitelist your videocard in the compiz config still.

---

### Post by cfrivas on 2007-11-17
I am having the same issues when I type "compiz" in Terminal. The effects start then really lag and stick. I had no problem before I updated from 7.04 Fiesty 64. What can I do now? I installed nvidia-glx-new 100.14.19+2.6.224-14.10 and was able to get compiz to run but slow.

---

### Post by charles_316 on 2007-11-18
thanks for the guide... what does whitelist your video card in compiz mean? 

im going to test out ur method

---

### Post by Jouke74 on 2007-11-18
- To be honest this is to set-up your XGL server and ATI(!!!) card (NOT Nvidia). I have never used the last Compiz only up to the pre alpha version of the current. 

- Please be warned that this is not the most easy manual to get it running. Take it one step at a time and start with the FGLRX driver (most important step). Also in case you see errors stop until they are solved. 

- Read some other posts about ATI and Compiz it in the forum (background knowledge). The compiz configuration needs to know that your videocard is ok. "Whitelist" "Compiz" should be enough as search terms. I don't know whether it is required at all by the way, since you are using the XGL server now. Try first without this step. 

- Make sure also that your laptop is not using power saving on your video card as it needs the power for 3D effects. Otherwise it will stay slow.

---

### Post by charles_316 on 2007-11-18
hmm wierd... i tried all the steps and i cant even get into ubuntu because it says it is in like a low-graphics mode configuration or somethin b/c it cant find my video card drivers even tho it was fine b4

anyways i am restoring back now

---

### Post by Jouke74 on 2007-11-19
Hmm, not good. 

Can't help you further this way. Need to check a lot of files from your config. How is your restored xorg.conf looking?

---

