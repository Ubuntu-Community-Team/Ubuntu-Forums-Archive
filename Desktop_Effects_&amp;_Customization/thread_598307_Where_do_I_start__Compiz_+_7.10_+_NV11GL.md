---
title: "Where do I start?  Compiz + 7.10 + NV11GL"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by joesmith1234 on 2007-10-31
I've been following some threads but none of the steps really seem to be working, and now I fear that I'm hacking up my environment without doing anything positive.

Here's my problem...
System->Preferences->Appearance->Visual Effects->Custom
then wait 5 seconds... 
The screen "flickers" in some kind of context switch
then wait 5 seconds...
The screen "flickers" back and I see the popup: "Desktop effects could not be enabled".

If I try to run from the command line....

:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

And the shell waits....  am I running compiz?  How do I know?  What should I do to fix these wacky errors?

---

### Post by gcrussell1 on 2007-10-31
Have you gotten xserver-xgl from the package manager? I'm not exactly sure what it does (still a noob myself), but several threads I've read about getting compiz working here or there involve installing that package. Additionally, are the proper video drivers installed for your video card/integrated graphics?

I don't know much, but maybe one of these things will work, and if not, consider this a bump...

---

### Post by Zorael on 2007-10-31
NV11GL; is that an Nvidia card? Do you have the proper drivers installed?

If you install them through Envy, for instance, I believe the process installs xgl as well.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


If it's not an Nvidia card, don't mind me.

---

### Post by FuturePilot on 2007-10-31
Envy does not install XGL. You don't need XGL with Nvidia anyway. Try System>Administration>Restricted Driver Manager and enable the Nvidia driver. That is if you do have a Nvidia card.

---

### Post by Zorael on 2007-10-31
Er, yes, that's how it is. My bad.

---

### Post by joesmith1234 on 2007-11-01
> **FuturePilot said:**
> Envy does not install XGL. You don't need XGL with Nvidia anyway. Try System>Administration>Restricted Driver Manager and enable the Nvidia driver. That is if you do have a Nvidia card.

Hmm, Restricted Driver Manager shows that it is in use.

What should I do now?  Are there any report sheets I can show you guys to try to troubleshoot this?

---

### Post by KingWilliam on 2007-11-01
I have the same problem. Same error message. Same output in console. Also an NVidia card (but an older one :p NVidia GeForce 256). Drivers are set to NVidia and xserver-xgl is installed. I feel stuck like a moth in a bath. :p

---

