---
title: "Jitsi not finding audio devices"
date: 2014-10-13
forum: Desktop Environments
---

### Post by Lars Noodén on 2014-10-13
I have jitsi installed from the nightly repository for Ubuntu 14.04 LTS for amd64 and it is not finding any useful audio systems, only Audio System : audiosilence.  Other applications on the same account are able to play audio and get input from the microphone.  What needs to be changed to restore audio functionality to Jitsi?

$ apt-cache policy jitsi
jitsi:
  Installed: 2.5.5319-1

$ uname -pso
Linux x86_64 GNU/Linux

$ lsb_release -rd
Description:    Ubuntu 14.04.1 LTS
Release:        14.04

---

### Post by Lars Noodén on 2014-10-15
The same for Jitsi 2.5.5320-1

Deleting the profile *appeared* to help a few times but does not now.

---

### Post by Lars Noodén on 2014-10-26
I've tried from a fresh installation of the OS (14.04.1 TLS) and jitsi worked once, but only once.  Thereafter it went back to only seeing audiosilence.  Deleting the profile does nothing these days.  

The problem is present even in 2.5.5327-1 from the nightly snapshots.

---

### Post by Lars Noodén on 2014-11-12
Can this be another pulseaudio problem? What do I need to diagnose it?

---

### Post by Lars Noodén on 2014-12-22
Something appears to be going south with pulseaudio.  If I start pulseaudio, then jitsi does sound again.  But there are these warnings in syslog:

```

Dec 22 22:27:16 gazell9 pulseaudio[3859]: [pulseaudio] main.c: Running in system
 mode, forcibly disabling SHM mode!
Dec 22 22:27:16 gazell9 pulseaudio[3859]: [pulseaudio] main.c: Running in system
 mode, forcibly disabling exit idle time!
Dec 22 22:27:16 gazell9 pulseaudio[3861]: [pulseaudio] main.c: OK, so you are ru
nning PA in system mode. Please note that you most likely shouldn't be doing tha
t.
Dec 22 22:27:16 gazell9 pulseaudio[3861]: [pulseaudio] main.c: If you do it none
theless then it's your own fault if things don't work as expected.
Dec 22 22:27:16 gazell9 pulseaudio[3861]: [pulseaudio] main.c: Please read http:
//pulseaudio.org/wiki/WhatIsWrongWithSystemMode for an explanation why system mo
de is usually a bad idea.

```

---

