---
title: "Simply trying to start Ubuntu without graphics"
date: 2011-02-27
forum: Desktop Environments
---

### Post by iamgeniusrnti on 2011-02-27
OK--All I want to do is run Nessus automatically without graphics.  And I'm completely frustrated because usually it's the other way around.  Perhaps I need to just start deleting files until it crashes.  I don't want to uninstall--I might need it one day.

I searched and came up with 4 methods, none of which worked.

The first method is System - Admin - Services ... doesn't exist.  And anyone who says it's there is lying.  I can give you a screen shot if you like.

The next method is /etc/inittab ... that doesn't exist either.

The third method is to edit the Grub file and stick the word text in there ... worked but the great Ubuntu got mad, froze up and complained about the "aperture".

The fourth method said to edit the /etc/init/gdm.conf and change [016] to [0136] ... BAHAHAHAHAHA!  The great Ubuntu said screw you, I'm still starting graphics--in fact that fixed the previous screw up!

The next method said to go into an rc file and add env runtime=3 ... I can't remember off the op of my head but that poster lied too.

Finally the most promising was posted here: [http://ubuntuforums.org/showthread.php?t=388344](http://ubuntuforums.org/showthread.php?t=388344)

I unchecked all 5 blocks, rebooted and the great Ubuntu gods took that file, spit on it and then started the graphics anyway:(  In fact I can give you another screen shot of the sysv-rc-conf running, all boxes unchecked under gdm and the graphics running in the background.

You can accuse me of not knowing something simple but hey--I searched!!!!!

Someone, seriously, there has to be a way to temporarily disable graphics and boot to console.  Anyone?

---

### Post by ankspo71 on 2011-02-27
Hi,
I don't know how well these work, but try these links:

How to disable GDM:
[http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/](http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/)
[http://linux.koolsolutions.com/2009/07/24/tip-disable-gdm-kdm-or-xdm-from-starting-up-automatically/](http://linux.koolsolutions.com/2009/07/24/tip-disable-gdm-kdm-or-xdm-from-starting-up-automatically/)

Hope this helps.

---

### Post by Krytarik on 2011-02-27
The most of these old solutions won't work nowadays, because the way GDM is run changed, and GDM itself changed.

I picked up a guide in the forums recently, but I don't have a link handy:
```
gksudo gedit /etc/init/gdm.conf
```The part:
```

start on (filesystem
          and started dbus
          and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
```Can be replaced by:
```
start on (start-gdm)
```To start the graphic login and gnome you can give the following command:
```
sudo service gdm start
```To stop it:
```
sudo service gdm stop
```I hope this works, please give feedback!

Greetings.

---

### Post by iamgeniusrnti on 2011-02-28
No dice on either.  When I tried the last method posted, it froze at the 10.10 splash screeen and just kept showing me the dots.  All the other methods mentioned in the links simply had no effect... I never knew it would be so hard to turn OFF the graphics.

I suppose I could do an ALT F2 and do a GDM stop but there's another problem.  I can't get a command prompt.  This server only has 512 MB.  That is most likely my problem.  I was hoping if I could knock it down to headless it would work.

---

### Post by Krytarik on 2011-02-28
One recent post states to replace```

start on (filesystem
          and started dbus
          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
```
with this
```
start on runlevel []
```
instead of what I posted earlier.

[http://ubuntuforums.org/showthread.php?p=9303525](http://ubuntuforums.org/showthread.php?p=9303525)

---

