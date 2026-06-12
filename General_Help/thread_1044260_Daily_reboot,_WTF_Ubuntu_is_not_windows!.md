---
title: "Daily reboot, WTF? Ubuntu is not windows!"
date: 2009-01-19
forum: General Help
---

### Post by Milambar on 2009-01-19
After upgrading to Intrepid Ibex, every single update is now followed by a prompt to reboot! Like the update I just downloaded... There were no kernels or headers in the update, yet I'm still being prompted to reboot.

[center][color=red]**Ubuntu is not Windows**[/color][/center]

Stop with the reboot requests ffs. Or at least explain WHY a reboot is being requested. I want this machine for doing work, not rebooting.

Rant over.

---

### Post by OrangeCrate on 2009-01-19
> **Milambar said:**
> After upgrading to Intrepid Ibex, **every single update is now followed by a prompt to reboot!** Like the update I just downloaded... There were no kernels or headers in the update, yet I'm still being prompted to reboot.

[center][color=red]**Ubuntu is not Windows**[/color][/center]

Stop with the reboot requests ffs. Or at least explain WHY a reboot is being requested. I want this machine for doing work, not rebooting.

Rant over.

Honestly?

I haven't seen that here. If true, could you give us a list of the updates that caused the reboots? (Synaptic > File > History)

---

### Post by Sprut1 on 2009-01-19
I've never rebooted after an update. I thought the only time a reboot was necessary was when the kernel was updated.

---

### Post by Milambar on 2009-01-19
I wasn't aware I could get the history of updates in that manner. Many thanks for that tit-bit of information.

Looking at the list, I can see there was a kernel update hidden away in the list, so now my query becomes, why are they issuing kernel updates so frequently? Its seriously annoying me having to reboot so often. 

I remember the days when I ran Mandriva, and I considered myself unfortunate if I had to reboot once a month (I changed because I got tired of Mandriva's dependency hell and broken RPM's).

```

Upgraded the following packages:
acpi-support (0.114-0intrepid1) to 0.114-0intrepid2
dolphin (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
evolution-exchange (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
kdebase-bin (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
kdebase-data (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
kfind (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
konqueror (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
konqueror-nsplugins (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
konsole (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
libkonq5 (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
libkonq5-templates (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
libxine1 (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-bin (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-console (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-ffmpeg (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-gnome (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-misc-plugins (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-x (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
linux-headers-2.6.27-11 (2.6.27-11.23) to 2.6.27-11.24
linux-headers-2.6.27-11-generic (2.6.27-11.23) to 2.6.27-11.24
linux-image-2.6.27-11-generic (2.6.27-11.23) to 2.6.27-11.24
linux-libc-dev (2.6.27-11.23) to 2.6.27-11.24
python-kde4 (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid1
transcode (2:1.0.2-0.8ubuntu10) to 2:1.0.2-0.8ubuntu10.1

```

---

### Post by OrangeCrate on 2009-01-19
> **Milambar said:**
> I wasn't aware I could get the history of updates in that manner. Many thanks for that tit-bit of information.

Looking at the list, I can see there was a kernel update hidden away in the list, so now my query becomes, why are they issuing kernel updates so frequently? Its seriously annoying me having to reboot so often. 

I remember the days when I ran Mandriva, and I considered myself unfortunate if I had to reboot once a month (I changed because I got tired of Mandriva's dependency hell and broken RPM's).

```

Upgraded the following packages:
acpi-support (0.114-0intrepid1) to 0.114-0intrepid2
dolphin (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
evolution-exchange (2.24.2-0ubuntu1) to 2.24.3-0ubuntu1
kdebase-bin (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
kdebase-data (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
kfind (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
konqueror (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
konqueror-nsplugins (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
konsole (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
libkonq5 (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
libkonq5-templates (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid2
libxine1 (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-bin (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-console (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-ffmpeg (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-gnome (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-misc-plugins (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
libxine1-x (1.1.15-0ubuntu3) to 1.1.15-0ubuntu3intrepid1
linux-headers-2.6.27-11 (2.6.27-11.23) to 2.6.27-11.24
linux-headers-2.6.27-11-generic (2.6.27-11.23) to 2.6.27-11.24
linux-image-2.6.27-11-generic (2.6.27-11.23) to 2.6.27-11.24
linux-libc-dev (2.6.27-11.23) to 2.6.27-11.24
python-kde4 (4:4.1.3-0ubuntu1~intrepid1) to 4:4.1.4-0ubuntu1~intrepid1
transcode (2:1.0.2-0.8ubuntu10) to 2:1.0.2-0.8ubuntu10.1

```

All of those updates asked for you to reboot? If so, it's beyond me as to why.

The kernel updates are security updates.

(The open source community at it's finest - find 'em and fix 'em. :))

For future reference, you can track security updates here on the forums:

[http://ubuntuforums.org/forumdisplay.php?f=13](http://ubuntuforums.org/forumdisplay.php?f=13)

---

### Post by Yellow Pasque on 2009-01-19
> so now my query becomes, why are they issuing kernel updates so frequently?
If you want the technical details, read the changelog for the kernel image package (You can use the Package -> Download Changelog in Synaptic). 

Ubuntu customizes the "vanilla" kernel with special patches, so these need to be maintained. I guess you could petition the Ubuntu devs to stop fixing the bugs in their kernel package, but for some reason, I don't see too many other people supporting that :P

Another solution would be to grab the vanilla 2.6.27.12 kernel source and roll your own kernel, though I don't recommend that on a production system unless you have experience and/or a good reason. (note: being "annoyed" by kernel updates is not a good reason).

---

### Post by scouser73 on 2009-01-19
I've had to reboot twice after updates, but that was a long time between the two updates. Not that I'm complaining, because I'm not.

---

