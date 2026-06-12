---
title: "Ubuntu Music playback skips"
date: 2009-05-04
forum: General Help
---

### Post by Brainy142 on 2009-05-04
Ya I know I'm having LOTS of issues right now but my audio makes a jump about every 30seconds even when the processor is not capped?

Any ideas?
Just so you know I tried multiple program's

---

### Post by paradigm2 on 2009-05-04
> **Brainy142 said:**
> Ya I know I'm having LOTS of issues right now but my audio makes a jump about every 30seconds even when the processor is not capped?

Any ideas?
Just so you know I tried multiple program's

Its probably pulseaudio.

What sound card do you have?

From terminal:

```

lspci

```

And is this a stock (From standard repositories) 9.04 Jaunty?

---

### Post by Brainy142 on 2009-05-05
It is a standard Jaunty.

Here we go:
VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
(Ya I know I hate VIA too I'm working on getting a new computer..... dont get me started on having no 3d acceleration..._)

And It worked before in my older linux W/O issues. It happens in any audio program emulators video audio playback etc

---

### Post by Brainy142 on 2009-05-05
I would like to point out that AUDIO SOUNDS AMAZING...

Fixed: had to change audio output to alsa (getting rid of Via sound acell.)

Did the new kernal make audio output more awesome?

---

### Post by Lantesh on 2009-06-30
I had the same issue in Mint 7 (based on Jaunty).  Here is my reply/fix from another similar thread:

I found a solution that works, but it's not for the squeamish. Therefore I'm going to keep this guide brief, and if you understand what I'm talking about then you will have no issues. If you don't then well...don't try this. If you do this wrong your system will be hosed.

Ok so what you need to do is edit your sources.list file and add the Karmic Koala repos. Sudo apt-get update and then install the 2.6.30-10 kernel via Synaptic. Don't forget the headers too. While you are in there upgrade ALSA, the Gstreamer codecs, and Pulse Audio. Be very careful what packages you mark for upgrade. Pay particular attention to what packages will be removed, and don't upgrade a package if you think it's going to mess something up. There were one or two things I had marked, but then unmarked. Just be careful and use common sense.

If you've got an Nvidia graphics card: Reboot, and start up in to low graphics mode. Next go back into synaptic and upgrade from the 180 to the 185 drivers. You need the 185 drivers for this kernel. You have to do this. Now go into the Hardware drivers tool in the administrative menu, and enable the drivers. It's only going to show 173 and 180. Just pick 180 and it will enable the 185 drivers.

Reboot and choose the new kernel. Everything should load fine. As long as you didn't mess with your xorg.conf file video should work correctly now that the 185 drivers are enabled.

Finally remove the Karmic repos from your sources.list file and sudo apt-get update again.

If you've got an ATI graphics card I can't help you. I've never used one with Linux.

I can tell you with 99.9% certainty that this fixed all my audio issues. I leave the .1% to chance, because hey you never know.

Good luck. 8)

---

