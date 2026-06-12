---
title: "PulseAudio RTP Receiver Module Not Loading"
date: 2009-04-25
forum: General Help
---

### Post by ionman on 2009-04-25
Hi all! I have a clean install of 9.04 on a couple of different machines now. On all of them, I can enable Multicast/RTP receiver in my PulseAudio Preferences, but no module is ever loaded in the PulseAudio Manager. I can see when I enable the sender, a new module pops up, but nothing ever happens for the receiver.

I have even tried enabling it manually through pacmd and then load-module module-rtp-recv. This would be really cool to have working, and I think I am almost there, I just can't seem to figure out any way to get this module to load. Has anyone else had this issue? If so, please help!

Thanks!

- ionman

---

### Post by hufman on 2009-05-16
I have the same symptom. Ubuntu Intrepid had it working, but it stopped when I dist-upgraded to Ubuntu Jaunty.

The pactl command returns the following error message: ```
Failure: Module initalization failed
```.

When running a debugging instance of pulseaudio, the following message appears when I try to load the module:
```
I: client.c: Created 1 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 14, local 14
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
E: module.c: Failed to open module "module-rtp-recv": file not found
I: client.c: Freed 1 "pactl"
I: protocol-native.c: Connection died.
```

However, in /usr/lib/pulse-0.9/modules, the file is clearly there:
```
ls -l *rtp*
-rw-r--r-- 1 root root 22672 2009-04-08 19:10 librtp.so
-rw-r--r-- 1 root root 27200 2009-04-08 19:10 module-rtp-recv.so
-rw-r--r-- 1 root root 22928 2009-04-08 19:10 module-rtp-send.so
```

Does anyone else know about this regression? Should I open a bug report for it?

---

### Post by TheMagican on 2009-05-18
I've the same problem with the module so it may be a bug ...(?)

Greets

---

### Post by ionman on 2009-05-22
Cool! I found a bug! Now how do we fix it? :D

---

### Post by Forlornity on 2009-05-25
I'm experiencing this too.
Nowhere else has any discussion of this, so I'm pretty sure it's new with Jaunty.

---

### Post by nave.notnilc on 2009-06-18
Bump, for what it's worth, here's a bug report that seems pertinent:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/384028]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/384028")

---

