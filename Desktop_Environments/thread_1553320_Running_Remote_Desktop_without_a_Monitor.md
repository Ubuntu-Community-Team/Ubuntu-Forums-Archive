---
title: "Running Remote Desktop without a Monitor"
date: 2010-08-14
forum: Desktop Environments
---

### Post by obogobo on 2010-08-14
How do I do this in 10.4? I need to be able to Remote Desktop into my server over SSH but can't because I don't have a spare monitor on hand... and Ubuntu won't start a desktop if it doesn't detect a monitor. Help anyone? Thanks!

---

### Post by JustinR on 2010-08-15
> **obogobo said:**
> How do I do this in 10.4? I need to be able to Remote Desktop into my server over SSH but can't because I don't have a spare monitor on hand... and Ubuntu won't start a desktop if it doesn't detect a monitor. Help anyone? Thanks!

Hi, you can use 'ssh -X USERNAME@IPADDRESS'. The -X (capital X) tells SSH to forward the X display to your screen.

This won't forward the whole display but just a specific application back to your screen.

Example:
```

jack@jjack-laptop:~$ *ssh -X justin@192.168.1.2*
justin@192.168.1.2 password: XXXXXXXXX
Welcome to Ubuntu 10.04.1 ...
...
justin@192.168.1.2: ***cheese***

```

Typing cheese will then run cheese from the remote computer but it will show up on your screen like any other normal application! Its pretty useful.

---

### Post by obogobo on 2010-08-15
That's a pretty clever function actually haha neat but I actually got an X session running without a monitor by creating the file /etc/X11/xorg.conf with these contents:

Created the xorg.conf in /etc/X11 with the following:

Section "Device"
Identifier "VNC Device"
Driver "vesa"
EndSection
 
Section "Screen"
Identifier "VNC Screen"
Device "VNC Device"
Monitor "VNC Monitor"
SubSection "Display"
Modes "1024x768"
EndSubSection
EndSection
 
Section "Monitor"
Identifier "VNC Monitor"
HorizSync 30-70
VertRefresh 50-75
EndSection

and these contents to /etc/modprobe.d/i915-kms.conf

options i915 modeset=0

Reboot and all good :)

---

### Post by bprins on 2010-08-15
did you try this:
[http://stevencamina.blogspot.com/2009/09/setting-up-remote-desktop-without.html](http://stevencamina.blogspot.com/2009/09/setting-up-remote-desktop-without.html)

---

### Post by obogobo on 2010-08-15
I'm using the built in remote desktop server in Ubuntu 10.4. With the changes I made above it works okay now... I just can't seem to get it working through SSH. I get a connection closed unexpectedly error when I forward 5900 to 5901 on my remote PC and connect with localhost:1

---

### Post by bprins on 2010-08-15
you are not running into lame firewall issues are you?

had the same thing here, was looking for the most sophisticated bugs while i just had to add 2 ports in my allow list :)

---

### Post by obogobo on 2010-08-15
I don't think so haha not unless Ubuntu has a firewall enabled by default... I have the correct port open on my router for SSH and can remote desktop locally, I just can't seem to get remote desktop forwarded through my tunnel and it is driving me INSANE haha

---

