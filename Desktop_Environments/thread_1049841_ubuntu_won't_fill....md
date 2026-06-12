---
title: "ubuntu won't fill..."
date: 2009-01-25
forum: Desktop Environments
---

### Post by Exurion on 2009-01-25
ok, so i've enjoyed Kubuntu on my desktop, along with a short lived experience of openSUSE(i like ubuntu stuffs better), so i decided it was time to finally put the goodness of ubuntu on my laptop.  It's a Toshiba Satellite A25 S207 with a 40 gig hard drive and 512 mb RAM(not that i expect anyone to care, i know it's not the most impressive machine around, i'm just hoping maybe specs will help solve my problem ;)  ), and i also decided maybe it's time to graduate from the Kubuntu training wheels transition from windows to a full fledged regular ubuntu-ness...  so, it worked(minus the occassional initramfs thing, but no big deal, it's a simple fix...), but i want to figure out how i can have Ubuntu use my whole screen.  as it sits, it only uses about 3/5 of the screen, and i have this whole thick(and i mean THICK) black border that i know could be filled with more Ubuntu goodness...  as it sits, i need a dual OSinstall because my schooling requires me to use Internet Explorer, and i don't have that on Ubuntu.  But i am researching alternatives to using IE on Ubuntu, but that's a whole different problem not meant for this help thread...

anyways, long story short, i want help getting ubuntu to take up my whole screen...  i'm just trying to explain everything that's going on in hopes it can help better explain and/or identify the problem.  HALP!!!!!!

---

### Post by ugm6hr on 2009-01-25
What resolution is the screen, and what resolution is Ubuntu displaying?

It is possible that your laptop cannot resize smaller resolution screens, so just leaves the border pixels blank.

The xrandr command is recommended to change resolution.

This may be your problem too: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/185440](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/185440)

Check with lspci
```
secret@celery:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade XPAi1 [1023:8820] (rev 82)
```

---

### Post by NorthWesterUK on 2009-01-25
I had the same problem with the screen resolution with a toshiba laptop and had to edit the xorg.conf file....


 sudo gedit /etc/X11/xorg.conf


replace the monitor and screen sections with

Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection 


then save the file exit reboot

---

