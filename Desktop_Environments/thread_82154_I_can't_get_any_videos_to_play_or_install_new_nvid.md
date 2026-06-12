---
title: "I can't get any videos to play or install new nvidia drivers."
date: 2005-10-26
forum: Desktop Environments
---

### Post by hootpie on 2005-10-26
I'm new to Ubuntu and Linux.  I installed it on an old AMD 950mhz, 512mb, 30gb HD, 64mb Geforce 2 GTS Pro system that couldn't handle WinXP that well (plus, I wanted to get familiar with Linux).

Thanks in advance for any and all help!

**Problem #1 - Inability to play video files**
I tried to play a .wmv and a .avi file with the pre-installed Totem Movie Player, but it said it could not find the appropriate codecs.  A quick google search revealed that I needed W32 Codecs.  More google searches later, I had completely installed the codecs.  I tried again, but this time as soon as it would show the first frame it would close.

I tried installing mplayer, xine, and VLC only to get the same random crash.  I did some searching on this forum and found a few people that had the same problem, but there were no posted results.  I ran it from the CLI to see the error output, which is exactly the same from all the programs, which is:

[QUOTE=mplayer]MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
X11 error: BadAlloc (insufficient resources for operation)


MPlayer interrupted by signal 6 in module: uninit_vo
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  97
  Current serial number in output stream:  128
[/QUOTE]

(I also get the "open up and shut down immediately" response when I try to play .ogg files in Totem)

This lead me to believe that my video card drivers needed updating, which leads me to...


**Problem #2 - Unable to install new Nvidia drivers**

I searched the forum and found the beautiful HOWTO written by TSEliot (IIRC).  I followed it very closely, but when I tried to restart Gnome with "sudo /etc/init.d/gdm start" I got the blue screen of X server death.  The only way to fix it was to edit the xorg.conf to read "nv" instead of "nvidia" (which is what his tutorial says to change it to).

I used the 7174 install because my video card (Geforce 2 GTS Pro) is not supported by anything newer than that.  When I do "rmmod nvidia" I get this error:

ERROR: Module nvidia does not exist in /proc/modules

I get that error even after using Nvidia's installer.  I read that Hoary has the 7174 drivers in it's repository as nvidia-glx.  Is it possible for me to use the Synaptic Package Manager to somehow install the drivers?



PLEASE help.  I really want to get this working well, so I can make the most out of this system.

---

### Post by RAOF on 2005-10-26
The easy way to install the nvidia drivers is to install nvidia-glx-legacy from synaptic, and then run nvidia-glx-config enable.  Is that what you did?  Fixing that might even solve you're video problems.

Plus, I thought that geforce 2 cards were supported by the newer drivers.  But I'm not sure, so the legacy drivers should be safe.

---

### Post by hootpie on 2005-10-26
[QUOTE=RAOF]The easy way to install the nvidia drivers is to install nvidia-glx-legacy from synaptic, and then run nvidia-glx-config enable.  Is that what you did?  Fixing that might even solve you're video problems.

Plus, I thought that geforce 2 cards were supported by the newer drivers.  But I'm not sure, so the legacy drivers should be safe.[/QUOTE]

My card is listed as unsupported.  I just installed the legacy drivers from synaptic, then ran nvidia-glx-config enable.  Now what do I do (or is that it)?

---

### Post by RAOF on 2005-10-26
Now, save everything and press Ctrl-Alt-Backspace to restart X (warning: that will log you off, and kill anything you've got running.  Save first :) ).  It should load with an nvidia splash screen.  And you're done :)

---

### Post by hootpie on 2005-10-26
[QUOTE=RAOF]Now, save everything and press Ctrl-Alt-Backspace to restart X (warning: that will log you off, and kill anything you've got running.  Save first :) ).  It should load with an nvidia splash screen.  And you're done :)[/QUOTE]

If this works:

A) I'll feel dumb for not figuring it out on my own
B) I'll kiss you right on the mouth :)

---

### Post by hootpie on 2005-10-26
I restarted X...no Nvidia splash screen and the video playback still doesn't work.

Did I mention I can't even run the 3D screensavers that come with Breezy?

:confused: :(

---

### Post by RAOF on 2005-10-26
But X started?  That's good.  Maybe the legacy drivers don't use the splash screen.

But to check, look at xorg.conf, and see if it's using the "nvidia" driver.  It should, 'cause you ran nvidia-glx-config enable.  If it is, then you've got the proper nvidia drivers installed, and they work.  Yay!  

But it looks like the video problem is a different matter, and I don't know how to fix that :(

---

### Post by hootpie on 2005-10-26
[QUOTE=RAOF]But X started?  That's good.  Maybe the legacy drivers don't use the splash screen.

But to check, look at xorg.conf, and see if it's using the "nvidia" driver.  It should, 'cause you ran nvidia-glx-config enable.  If it is, then you've got the proper nvidia drivers installed, and they work.  Yay!  

But it looks like the video problem is a different matter, and I don't know how to fix that :([/QUOTE]

It's still using the "nv" driver :(

> Section "Device"
	Identifier	"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Driver		"nv"
	BusID		"PCI:1:0:0"

---

### Post by RAOF on 2005-10-26
Oh well.  Try changing "nv" to "nvidia".  I'm not sure why glx-config enable didn't do that...

---

### Post by hootpie on 2005-10-26
[QUOTE=RAOF]Oh well.  Try changing "nv" to "nvidia".  I'm not sure why glx-config enable didn't do that...[/QUOTE]

I'll give that a try, brb.

---

### Post by hootpie on 2005-10-26
Still no go, but I think the problem is becoming clearer.  These are the errors X gave me during the blue screen:

Error inserting "nvidia"
Failed to load the nvidia kernel module
Screens found, but none have usable configurations
Fatal server error, no screens found


So apparently I don't have the nvidia module installed, but how is that possible and more importantly, how do I fix it?

---

### Post by RAOF on 2005-10-26
Check that you've got the right linux-restricted-modules installed.  Run "uname -r".  You should get something like "2.6.12-9-amd64-k8".  You need to have the package "linux-restricted-modules-(output of uname -r)-nvidia-legacy" installed.

It's possible because nvidia ship annoying proprietry drivers, with a two-part structure - an xorg driver and a kernel module.  If one of these is the wrong version, or doesn't exist, it won't work.

---

### Post by hootpie on 2005-10-26
Ok, I downloaded linux-restricted-modules-2.6.12-9-k7-nvidia-legacy and installed it.  Now should I rerun nvidia-glx-config enable and restart X?

---

### Post by RAOF on 2005-10-26
If you've got the driver set to "nvidia" in the xorg.conf, you just need to restart X.  Otherwise, set the driver, then restart X.

---

### Post by hootpie on 2005-10-26
[QUOTE=RAOF]If you've got the driver set to "nvidia" in the xorg.conf, you just need to restart X.  Otherwise, set the driver, then restart X.[/QUOTE]

I set the driver to nvidia, restarted X and I'm getting the same error about the missing nvidia module.

---

### Post by RAOF on 2005-10-26
Bah!  I'm out of answers, sorry. Oh, maybe not...

Can you just run "modprobe nvidia" before trying to run X?  That's the final thing I can think of - you should have the kernel module, you should have the xorg driver.  Maybe the kernel module's just not loaded.

Maybe a restart is in order, too, although that tends to fix things less often than in windows :)

---

### Post by hootpie on 2005-10-26
[QUOTE=RAOF]Bah!  I'm out of answers, sorry. Oh, maybe not...

Can you just run "modprobe nvidia" before trying to run X?  That's the final thing I can think of - you should have a kernel module, you should have the xorg driver.  Maybe the kernel module's just not loaded.

Maybe a restart is in order, too, although that tends to fix things less often than in windows :)[/QUOTE]

Here's what I get with "modprobe nvidia":

> FATAL: Error inserting nvidia (/lib/modules/2.6.12-9-k7/volatile/nvidia.ko): Operation not permitted


---

### Post by RAOF on 2005-10-26
Sorry, that should be "sudo modprobe nvidia"

---

### Post by hootpie on 2005-10-26
[QUOTE=RAOF]Sorry, that should be "sudo modprobe nvidia"[/QUOTE]

Same thing:

FATAL: Error inserting nvidia (/lib/modules/2.6.12-9-k7/volatile/nvidia.ko): No such device


By the way, thanks for helping me out with this, I really appreciate it :)

---

### Post by RAOF on 2005-10-26
No problem.  Sorry that I couldn't help you.

---

### Post by hootpie on 2005-10-26
[QUOTE=RAOF]No problem.  Sorry that I couldn't help you.[/QUOTE]

Any other thoughts about my lack of an nvidia module and how I can get one?

---

### Post by lerrup on 2005-10-26
why not uninstall your present driver and try loading the non-legacy driver.  

Follow the steps in the FAQ; that should work.

---

### Post by hootpie on 2005-10-26
[QUOTE=lerrup]why not uninstall your present driver and try loading the non-legacy driver.  

Follow the steps in the FAQ; that should work.[/QUOTE]

I actually ended up finding a solution.  I booted with a previous kernel, edited the xorg.conf and now I get the nvidia splash screen and I can run the 3d screensavers.

Edit: Videos work too!@!@!@!@!

---

### Post by RAOF on 2005-10-26
[QUOTE=hootpie]...
Edit: Videos work too!@!@!@!@![/QUOTE]

Well, at least I was right in that :)

---

### Post by hootpie on 2005-10-26
[QUOTE=RAOF]Well, at least I was right in that :)[/QUOTE]

Thanks again :)

---

### Post by Efwis on 2005-10-26
[QUOTE=hootpie]I actually ended up finding a solution.  I booted with a previous kernel, edited the xorg.conf and now I get the nvidia splash screen and I can run the 3d screensavers.

Edit: Videos work too!@!@!@!@![/QUOTE]
What kernel did you use? and could you please write down the steps you did.

I have the same problem you did, except that my card *IS* supported by the new drivers according to the Nvidia website. I don't use a legacy card. but still its a no joy for installing it. While I wait for you answer I will try and do the other steps listed in this thread.

EDIT:
No joy the other steps didn't work for me either

---

### Post by hootpie on 2005-10-26
[QUOTE=Efwis]What kernel did you use? and could you please write down the steps you did.

I have the same problem you did, except that my card *IS* supported by the new drivers according to the Nvidia website. I don't use a legacy card. but still its a no joy for installing it. While I wait for you answer I will try and do the other steps listed in this thread.

EDIT:
No joy the other steps didn't work for me either[/QUOTE]

I installed the Ubuntu boot loader thing that lets me choose between installations of Linux and Windows.  I was booting under 2.6.12-9-386-k7, but switched back to 2.6.12-9-386 and modified the /etc/X11/xorg.conf to read the driver as "nvidia" instead of "nv"

I'll post more detailed instructions later tonight if you need.

---

### Post by Efwis on 2005-10-28
[QUOTE=hootpie]I installed the Ubuntu boot loader thing that lets me choose between installations of Linux and Windows.  I was booting under 2.6.12-9-386-k7, but switched back to 2.6.12-9-386 and modified the /etc/X11/xorg.conf to read the driver as "nvidia" instead of "nv"

I'll post more detailed instructions later tonight if you need.[/QUOTE]
for some odd reason my notification of this went to my junkmail. anyway, I tried that, still no joy. I'll check at the NVforums to see what I can find out.

I'm actually quite irritated that this is such an issue

---

