---
title: "Performance with VNC"
date: 2005-03-31
forum: Desktop Environments
---

### Post by Swad on 2005-03-31
I noticed with Kubuntu and remotely connecting with VNC that it pinned the processor usage of Xorg to the wall.  Whether using VNC Viewer 4.0 or Win2VNC from my Windows desktop, it didn't matter--the CPU would just hammer to 75-80%+ and stay there.  I know it was VNC because the process for Xorg would be fine until I connected with one of the two above mentioned apps.  Of course with the process eating that much of the CPU, it caused the fan on the laptop to run itself silly and drive me nuts.

This has been about a week or more since I last ran it.  I had a spare laptop hard drive that I swapped in to try Kubuntu.  Because of this issue, I wound up switching back to the hard drive I had with Ubuntu 5.04.  I do not have this issue at all with Ubuntu 5.04.  Daily I connect to my laptop from my windows desktop with Win2VNC.  The processor usage goes up a bit with the remote connection, but by no means nowhere to the magnitude I saw with Kubuntu.  So what is the deal with Kubuntu's implementation of VNC / "remote desktop"?  Why is it totally eating the processor when used?

---

### Post by chaumurky on 2005-07-04
[QUOTE=Swad]I noticed with Kubuntu and remotely connecting with VNC that it pinned the processor usage of Xorg to the wall.  Whether using VNC Viewer 4.0 or Win2VNC from my Windows desktop, it didn't matter--the CPU would just hammer to 75-80%+ and stay there.  I know it was VNC because the process for Xorg would be fine until I connected with one of the two above mentioned apps.  Of course with the process eating that much of the CPU, it caused the fan on the laptop to run itself silly and drive me nuts.

This has been about a week or more since I last ran it.  I had a spare laptop hard drive that I swapped in to try Kubuntu.  Because of this issue, I wound up switching back to the hard drive I had with Ubuntu 5.04.  I do not have this issue at all with Ubuntu 5.04.  Daily I connect to my laptop from my windows desktop with Win2VNC.  The processor usage goes up a bit with the remote connection, but by no means nowhere to the magnitude I saw with Kubuntu.  So what is the deal with Kubuntu's implementation of VNC / "remote desktop"?  Why is it totally eating the processor when used?[/QUOTE]
 Same for me. I use x2vnc and my P4 2.4 goes crazy, even when my blank screensaver kicks in.

---

### Post by Divan Santana on 2005-09-09
I hope some one replies with what to do about this problem! Because its a major problem! 

I believe it has to do with krfb program! Thats seems to cause the X11 process to sky rocket! Perhaps we should use an alternative?

Wish there was something to do! I think this is really quite major and should be addressed!

---

### Post by ewangr on 2005-09-14
[QUOTE=Swad]I noticed with Kubuntu and remotely connecting with VNC that it pinned the processor usage of Xorg to the wall.  [/QUOTE]

Same here. Anyone heard of anything that can be done for this?

[QUOTE=Swad]Because of this issue, I wound up switching back to the hard drive I had with Ubuntu 5.04.  I do not have this issue at all with Ubuntu 5.04. [/QUOTE]

Since Kubuntu has the same packages as Ubuntu, do you have any idea what package Ubuntu might be using in place of krfb? Perhaps krfb could be disabled and the Ubuntu alternative enabled?

---

### Post by grim1234 on 2005-11-07
ubuntu uses vino, which is a wrapper for Xvnc i think. 

Perhaps attempting to set up vncserver or tightvncserver directly might help?

---

