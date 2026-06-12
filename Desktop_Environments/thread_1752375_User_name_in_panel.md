---
title: "User name in panel"
date: 2011-05-07
forum: Desktop Environments
---

### Post by daniel.cotter on 2011-05-07
Howdy,

I see in many help pages instructions that start with "Click on user name in the top right of the screen...", or similar.  My username is not there.  (Here's a screenshot of the panel area).


I updated from 10.10 to Natty, and no longer have the fingerprint-gui package, but I can turn on software by changing the properties for my user account.  If there is another way, I'd love to hear it, but if you just want to tell me how to add my user name to the panel, that will work, as well.

Thanks

---

### Post by Frogs Hair on 2011-05-07
In classic Gnome , right click the panel > add to panel add Indicator applet session. 
In unity ```
sudo apt-get install indicator-me
```

---

### Post by daniel.cotter on 2011-05-07
Thanks,

That adds my name to the panel (classic gnome method), but it looks like it only addresses chat accounts:

To activate the fingerprint reader, there is supposed to be a "My Account" button, from which i can turn the fingerprint reader on.

By the way, 11.04 documentation says it comes packaged with Unity, but it appears i still have the classic gnome desktop.  Is that an option at login?

---

### Post by daniel.cotter on 2011-05-10
I still can't enable fingerprint reading...any suggestions?

---

### Post by ManualSparrow on 2011-05-11
I think you need fprint, which is in the Synaptic Package Manager.

---

### Post by Frogs Hair on 2011-05-11
Unity is an option at login if your hardware supports it . There is Unity 2D , Unity 3D and Classic Gnome . ManualSparrow is correct about the fprint application.

---

### Post by daniel.cotter on 2011-05-18
Thanks, both of you, for the reference to fprint.  I have installed it, but can't figure out where it is to use it ;~

Frog's hair:  Thanks for breaking it down.  I hadn't translated the nicknames.

---

### Post by Frogs Hair on 2011-05-18
Fprint is listed as an accessory in the software center open applications search and on the top right there is a drop-down menu with application categories . It may also appear in dash if you type the name , but this is not always the case the first time an application is used and don't forget Alt + F2.

---

### Post by Blasphemist on 2011-05-18
> **daniel.cotter said:**
> Thanks,

That adds my name to the panel (classic gnome method), but it looks like it only addresses chat accounts:

To activate the fingerprint reader, there is supposed to be a "My Account" button, from which i can turn the fingerprint reader on.

By the way, 11.04 documentation says it comes packaged with Unity, but it appears i still have the classic gnome desktop.  Is that an option at login?

> How do I know my GPU can run Unity?
There is a test program in Natty for that. Run this command: 

```
/usr/lib/nux/unity_support_test -p
``` 

It will tell you if your system has the required capabilities for Unity. This is the same program we run at boot time to decide if Unity will be started or if a fall-back should run instead.

What drivers do you recommend?
AMD GPUs:

Fglrx driver: We have had some issues with the fglrx driver but we have been able to resolve them. With the fglrx driver, you will be missing features such as Kernel Mode Setting (KMS).
Open Source Radeon driver: can exhibit rendering artifacts on some systems. In the "System 3" configuration, Unity is not usable due to serious rendering issues.
NVidia GPUs: Nvidia propietary drivers; Experimental 3D nouveau driver
Intel GPUs: Intel open source drivers.

You either have insufficient hardware to run unity, or very possibly need to change the video driver and/or kernel mode-settings. There are many threads on making the changes. You'll need to know the specifics of your gpu.

---

