---
title: "nvidia-glx getting corrupted?"
date: 2005-12-30
forum: Desktop Environments
---

### Post by chenel on 2005-12-30
So I installed breezy on my Inspiron 8100 a few weeks ago.  Everything worked great, except for a weird pattern of short horizontal lines on the left side of the display in X.  I discovered shortly afterward that I could get them to go away by using the binary Nvidia driver.  Cool.

Unfortunately, I found out not too long after that that there's something weird going on -- about every other time I boot, the Nvidia splash screen appears on the screen for about a half second, flickers, and a weird half-black, half-white display shows up.  gdm re-tries it--with the same results--a total of 3 times, after which it gives up on loading X with an error message saying something like "failed to start the X server -- it's probably misconfigured."  I've found since then that reinstalling the nvidia-glx module fixes the problem and lets gdm & X load fine.  Since that seems to fix it, I'm wondering if somehow the nvidia-glx module is getting corrupted.

When things are broken, the /var/log/Xorg.0.log file ends with the line
[FONT="Courier New"](II) Initializing extension GLX[/FONT],
where when things work fine, there's a bunch of stuff after that that talks about loading the keyboard, mouse, and other modules.

I've also noticed that when X is working all right, I get some weird behavior that seems to be related.  I sometimes get strange segmentation faults if I try to run XMMS or OpenOffice; after that happens, the next time I restart the X server the nvidia driver is messed up.

I have a NVidia GeForce2 Go card with 32MB of onboard RAM.
I've been installing the driver from the repositories.

Anyone have any ideas?

---

### Post by MButterman on 2005-12-30
Just a shot in the dark, Are you using the nvidia-glx-legacy or nvidia-glx? I was having issues with a GeForce2 MX 440 and so being under the impression that this card wasn't supported by nvidia-glx, I loaded the legacy version. While I didn't have the issue you have now, the card didn't work very well with that driver. Finally I found this thread to install the latest driver.

[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

While this recommends a earlier version, I loaded the recent one from Nvidia because it loads not only the driver but the nvidia settings menu.

Merrill

---

### Post by chenel on 2005-12-30
Well, I tried using the newest Nvidia driver.  Didn't seem to fix anything.  :???:

[Sidenote: I originally tried using the Nvidia legacy driver back when I used Gentoo, but it didn't work at all, so I've been using the nvidia-glx one since then.]

Any other ideas?

Thanks!

---

### Post by chenel on 2005-12-30
Hmm.  I wonder if this has anything to do with another error I've been getting that I thought was unrelated...

So the last thing I see on my screen before the computer shuts off is a kernel message that says "Error evaluating _GTM".  I poked around on Google for a while, and found out that _GTM is an ACPI method that's used to get the device timings for an IDE device so that they can be saved.  I wonder if (since my hard drive is IDE) that maybe means that something isn't getting saved correctly, and so the NVIDIA driver gets corrupted?...

I'm not sure if that even makes any sense...  Thoughts?

---

### Post by chenel on 2005-12-31
So after doing the reinstall thing with the NVIDIA-provided installer, I found out what's happening.  The NVIDIA installer tries to uninstall the old version... and when I ran it for the second time, it gave me an error that said that the old installation had been messed up.

On checking out the /var/log/nvidia-installer.log file, I found out that apparently every time I have this problem, the /usr/lib/tls directory--which is where the NVIDIA .so file is--gets wiped somehow.  Normally there's a file there, and it ends up empty.

what on earth is going on??

---

### Post by chenel on 2005-12-31
I think I got it!!

So it turns out that my memory was wrong.  Apparently I tried the nvidia-glx-legacy package at the beginning of my Ubuntu experience.  And apparently there was an old initscript in the /etc/init.d directory that (for some reason) was removing the /usr/lib/tls files on boot.  I have no idea (a) what that script was for, or (b) why it wasn't deleted when I removed nvidia-glx-legacy, but disabling it seemed to fix all my problems.

Word.

---

### Post by MButterman on 2006-01-15
That was the same issue I was having. The legacy driver left old entries that would mess up the install of the newer driver. So I had to go in and manually delete the older entries. the link I provided in my last post should provide instructions to delete those entries. Glad to hear you got it working.

MButterman

---

### Post by mo_x on 2006-01-15
The nvidia related packages should be removed with the --purge option to also remove config files.

---

