---
title: "Pretty annoying Ubuntu bug"
date: 2008-12-11
forum: General Help
---

### Post by rubendodge on 2008-12-11
Ok I am currently having a problem installing the Nvidia driver so I can have 3d support for linux games. I tried installing it right from their website without updating anything and got a black screen and only console mode. So I reformated the partition and reinstalled ubuntu on it and this time tried doing it after updating all the packages and rebooting in hopes the new upgrades would have fixed the problem It didnt I still get a blackscreen and only a console mode when I bootup. So I uninstalled nvidia and envyng and reinstalled envyng. Now I am here waiting to figure out how to fix this bug so please someone help me I have been at this all day to no avail........... Tnx in advance!!!!

---

### Post by Titan8990 on 2008-12-11
What nvidia card do you have? Which version of Ubuntu?

---

### Post by cb951303 on 2008-12-11
why not install it from repo?

---

### Post by rubendodge on 2008-12-11
CPU:AMD 5200+ 2x dual core
VIDEO CARD 1:Nvidia Geforce 7900 GS
Video Card 2:Nvidia Geforce 7900 GS
and Ram 2gb Kingston ram

---

### Post by albinootje on 2008-12-11
Please show us the last 50 lines of /var/log/Xorg.0.log

---

### Post by rubendodge on 2008-12-11
K her it is

```
**) Option "xkb_rules" "evdev"
(**) Chicony USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Chicony USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Chicony USB Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Chicony USB Keyboard
(**) Chicony USB Keyboard: always reports core events
(**) Chicony USB Keyboard: Device: "/dev/input/event2"
(II) Chicony USB Keyboard: Found keys
(II) Chicony USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Chicony USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Chicony USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Chicony USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Chicony USB Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event1"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Thu Dec 11 16:15:42 2008: 9023 X: client 4 rejected from local host ( uid=0 gid=0 pid=9040 )
AUDIT: Thu Dec 11 16:15:45 2008: 9023 X: client 4 rejected from local host ( uid=0 gid=0 pid=9044 )
AUDIT: Thu Dec 11 16:15:50 2008: 9023 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=9046 )
AUDIT: Thu Dec 11 16:15:50 2008: 9023 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=9047 )
AUDIT: Thu Dec 11 16:15:50 2008: 9023 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=9048 )
```

---

### Post by ajgreeny on 2008-12-11
Are you sure that's the last 50 lines of that particular log?  It ought to say something about your nvidia card and the possible output from it.

---

### Post by Chunky Dunk on 2008-12-11
> **cb951303 said:**
> why not install it from repo? I second that one. It does all the configuring for you.

---

### Post by Therion on 2008-12-11
> **Chunky Dunk said:**
> I second that one. It does all the configuring for you.
Thirded.  I don't see any "bug" here.

Do a fresh install or upgrade
Download updates, reboot, repeat as needed
Install video driver via the Hardware Manager
Reboot one last time, and...
Get on with life.

I don't see the problem here...

---

### Post by nzadLithium on 2008-12-11
since noone is actually telling you where it is, I figured i will :D
system>>Administrtation>>Hardware drivers
That should set up your drivers nice and pretty for you :)

That program will find your drivers for you and set them up in a way that works properly with ubuntu. If you want any further configuration after that (dual screens etc), then type "gksudo nvidia-settings" into a terminal :D

---

### Post by 73ckn797 on 2008-12-11
> **rubendodge said:**
> CPU:AMD 5200+ 2x dual core
VIDEO CARD 1:Nvidia Geforce 7900 GS
Video Card 2:Nvidia Geforce 7900 GS
and Ram 2gb Kingston ram


I have the same 7900 GS and use the recommended repo driver 177 and have no problems at all. Running 8.10.

---

### Post by rubendodge on 2008-12-11
Ok look guys I did exactly that the first time and had a black screen currently the reason the nvidia info isnt inside of the log wa sbecause it was the ONLY way I could get back to the gui version of ubuntu was to uninstall nvidia and reboot and I could get back to here BUT no 3d support. I had installed the 177 driver via the hardware controller. I tried envyng and it didnt do it right. And I tried it after upgrading ALL upgrades and I still had this bug. Now I don't know how this doesn't count as a bug but trust me I couldn't make the driver and the gui work at the same time i only could get the gui back from removing nvidia.

Lastly I am going to try again but I KNOW it wont work...........

EDIT: I did as you guys said and now I have the black screen again and no ability to get to gui mode. How do I remove the driver so I can get back into gui mode..... 

P.S. Could the problem have anything to do with dual video cards?

---

### Post by rubendodge on 2008-12-11
Please help people I really want to get ubuntu working so I can have a stable 32bit linux distro :(.

NOTE: sorry for double post but i dont have much time to work on it tonight and need to see if anyone knows how to make it work

---

### Post by nzadLithium on 2008-12-11
Its unlikely. Try this 
sudo nvidia-xconfig --sli=Auto

u'll need to start it up using ubuntu's second boot option.

---

### Post by rubendodge on 2008-12-11
Ok dude I tried what you said but it still isnt working please help me solve this delima :(. If you can tell me how to remove the driver then I could get back into the gui version and get the logs and stuff from this and upload them. Tnx in advance guys.....

---

### Post by nzadLithium on 2008-12-12
sudo apt-get remove nvidia-common nvidia-glx-177 nvidia-177-modaliases nvidia-177-kernel-source

should remove it.

---

### Post by cb951303 on 2008-12-12
when you get black screen, to change to a console try crtl+alt+f1/2/3/4
login and type "sudo apt-get remove nvidia-glx-177"

---

### Post by rubendodge on 2008-12-12
Ok guys I will dow hat you said tomorrow but how will I get the nvidia driver working/installed correctly when all my other attempts have failed....

NOTE:What logs do you need when I uninstall the drivers?

---

### Post by cb951303 on 2008-12-12
it may be a SLI problem. I would update my motherboard bios just to be sure and retry with 177 drivers.

---

### Post by 3rdalbum on 2008-12-12
Devil's Advocate here: Why do you need 3D acceleration? With that card, even with two of them in SLI, you're probably not planning to do any serious gaming. If such a thing currently exists on Linux.

In Envy, have you tried installing an older version of the drivers?

---

### Post by rubendodge on 2008-12-12
Well actually I do like to do serious gaming I even play COD4 with these dual cars bud I like to play LInux games aswell because they get a really high fps compared to windows versions. I will try the 96 driver but if the 177 driver doesnt work I dont see how the 96 driver will.....

---

### Post by sedawk on 2008-12-12
Hello!

The problem has been reported a few times now, so you might also
try to search older threads (via google).

1) Have a look at /var/log/Xorg.0.log and the end of the file,
   there might be a "no (proper) device/screen found" message

2) Removing the nvidia stuff without a full reinstall is possible.
   (Cleanup /etc/x11/xorg.conf (remove "nv" driver")) and then
   remove packages still related to nvidia (dpkg -l).
   But first try this:

3) What solved the problem here is to list all devices with "lspci"
   and then to check the ID of the nvidia cards.
   Then I added a BusID entry to xorg.conf.
   (e.g configuring the 2nd card might work because the monitor is
    connected to it, not the first one.)
   E.g. if lspci lists 00:02.1 and 00:03.1 you can try to add
   the line BusID "PCI:00:03:01" to the device section of the
   nv driver in xorg.conf.

---

### Post by nzadLithium on 2008-12-12
[http://ubuntuforums.org/showthread.php?t=966315](http://ubuntuforums.org/showthread.php?t=966315)

From there it seems you need to install those drivers again, but you also need to specify in your xorg.conf what your primary video card is. You'll need to install the nvidia gfx driver again (if u removed), then hit crtl+alt+f2 login. 
type lspci
find your primary graphics card 
at the start of the line, is a number that follows the format aa:bb:c write down that number :D (you probably won't know which is your primary, so write down the number infront of both :D)
type sudo nano /etc/X11/xorg.conf
find Section "Device"
in that section should be an Identifier line and a Driver line, AFTER those, but BEFORE EndSection, you need to add a new line that says, 

BusID "aa:bb:c"

If the number for your first card doesn't work, then try the second one :)

Tell us how that goes :D

---

