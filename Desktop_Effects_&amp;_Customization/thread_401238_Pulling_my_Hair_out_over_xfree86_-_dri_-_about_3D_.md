---
title: "Pulling my Hair out over xfree86 - dri - about 3D Desktop"
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by Damo1976 on 2007-04-04
Hi,

I loaded the 3D desktop programme successfully and was very pleased with it.  It looks very nice. I wanted to decrease the depth a bit but other than that no probs.

I then made a huge mistake and tried to load Beryl.  
It slowed my laptop down to an unusable speed (its a dual core 2Ghz, 1GB, 256 X1800 ATI Radeon - so no hardware reason)

I got rid of Beryl, but its stopped my 3d desktop working too.

I now get :

Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

From reading this its quite common, but no one seems to have answered the problem.
I've tried everything I can think of.
I'm new to Linux, but have managed to set everything else up perfectly, screen res, wireless, audio, even migrated Outlook to Evolution and I really don't want to have to go back and start it all again as its taken about a week.

Thanks in advance...

Damo 1976

---

### Post by cypher523 on 2007-04-13
Try the following steps as root:

modprobe fglrx

backup your xorg.conf incase something goes wrong:
cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup

then edit your /etc/X11/xorg.conf file and change the module it uses to fglrx from either radeon or ati to fglrx.  below is from my xorg.conf  the commented line is the orginal line

Section "Device"
        Identifier  "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
#       Driver      "radeon"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "TwinView"
        Option      "MetaModes" "1280x1024,1280X1024"
        Option      "UseEdidFreqs"
        BusID       "PCI:1:0:0"
EndSection

then restart X with control+alt+backspace and log back in and give it a shot.  if you have any problems, just revert to the working config with:

cp /etc/X11/xorg.conf.backup  /etc/X11/xorg.conf 

and restart X

---

