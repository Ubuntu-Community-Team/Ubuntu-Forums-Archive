---
title: "Lack of /usr free space - solution?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Neutron Bomber on 2006-09-27
Hi folks - first time poster here and newbie 'administrator'. I installed the 64-bit version a few weeks ago and clearly screwed up the partition sizes during installation: I read somewhere that the more partitions created during installation the better, so I did just that and created a bunch of (mostly) 2Gb-partitions for Ubuntu. Now I apparently have only 2% of space on the /usr partition left :( . I'd like to resize but GParted doesn't seem to allow this (all Ubuntu partitions exist in a 'full' extended partition). I'm dual booting with XP64. I do have a 4Gb swap partition and 1Gb of RAM so maybe I can remove swap partition 'temporarily' and rearrange things that way? (I also have a 4Gb "/" partition.) Any advice welcomed...

---

### Post by turbojugend_gr on 2006-09-27
Well I would keep my home partition and go for a clean install this way you will keep your configurations. This way you will only have to re-download any apps you have downloaded through apt-get or synaptic plus follow again the updates.

If you can't afford the time needed (about 2 hours tops) or you don't wish to do so, I know that gParted have created a LiveCD so you can change your linux partitions (I believe that you can't resize your partitions because of them being mounted). Google it up and read it's documentation it seems pretty handy.

---

### Post by Neutron Bomber on 2006-09-27
Cheers turbojugend - the LiveCD sounds like a go but it only seems to be for i386 architecture - would this be ok on an AMD64 machine?

---

