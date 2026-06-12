---
title: "Resolution goes to 640x480 after shutdown"
date: 2005-10-17
forum: Desktop Environments
---

### Post by rickmans on 2005-10-17
After a fresh install of breezy I have got sometimes the issue that my resolution jumps back 640x480 after a shutdown. To fix this I install (or remove, both works) kubuntu-desktop and then my resolution is fine again. However I got slightly the idea that is not quite normal that my resolution jumps back 640x480 without leaving me any other options to choose from.

Does anyone know a solution for this issue?

---

### Post by Ampersand on 2005-10-17
Try going to 'System - Preferences - Screen Resolution', and making sure that something higher than 640x480 is set as the default.

---

### Post by wjp.reg on 2005-10-17
I've experienced similar behaviour on my installation and found there were no other screen resolution preferences until a rebooted. :???: 

For a time I was attributing it to sharing my swap partition with a dual-boot version of SuSE 10 :confused:

---

### Post by rickmans on 2005-10-18
[QUOTE=Ampersand]Try going to 'System - Preferences - Screen Resolution', and making sure that something higher than 640x480 is set as the default.[/QUOTE]
I did that but it did not work...

---

### Post by jaegen on 2005-10-18
I think your monitor has to be on before you boot (or at least before the important time where it tries to check if a monitor is plugged in).  I've found this to be repeatable - and I think I even found the same behaviour on a Windows box.

Jaegen

---

### Post by gw90se on 2005-10-18
I have 2 boxes connected through a KVM. If I try to boot one while working on the other, it can't see the monitor and I getthe low res screen with no options. I have to have the KVM switched to the booting computer  so that it sees the monitor directly.

---

### Post by wjp.reg on 2005-10-18
[QUOTE=gw90se]I have 2 boxes connected through a KVM. If I try to boot one while working on the other, it can't see the monitor and I getthe low res screen with no options. I have to have the KVM switched to the booting computer  so that it sees the monitor directly.[/QUOTE]

Bingo!

That describes my situation (KVM setup); something I just hadn't considered :eek: 

I think I'll try to replicate right now..

---

### Post by wjp.reg on 2005-10-18
[QUOTE=wjp.reg]Bingo!

That describes my situation (KVM setup); something I just hadn't considered :eek: 

I think I'll try to replicate right now..[/QUOTE]

Confirmed.  ubuntu needs to have the monitor under KVM in order to set the screen resolutions properly.  Amazing :p

---

### Post by rickmans on 2005-10-18
[QUOTE=jaegen]I think your monitor has to be on before you boot (or at least before the important time where it tries to check if a monitor is plugged in).  I've found this to be repeatable - and I think I even found the same behaviour on a Windows box.

Jaegen[/QUOTE]
 sounds pretty plausible.

---

### Post by rickmans on 2005-10-18
[QUOTE=jaegen]I think your monitor has to be on before you boot (or at least before the important time where it tries to check if a monitor is plugged in).  I've found this to be repeatable - and I think I even found the same behaviour on a Windows box.

Jaegen[/QUOTE]
you were right, it worked :).

---

### Post by thekurst on 2005-10-22
Ok, I understand why this is happening, but is there any way for me to manually set breezy to stay at 1024x768 because I am accessing it via VNC with no monitor connected.

Help

---

### Post by evil-boweevil on 2005-10-22
I just figured this out :)

[http://www.ubuntuforums.org/showthread.php?t=80311]("http://www.ubuntuforums.org/showthread.php?t=80311")

Follow the links at the bottom...

---

