---
title: "Vostro 1720 Audio from both Speakers and Headphone"
date: 2009-10-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by johnathanamber on 2009-10-27
Hey everyone,

I've been having an issue where the audio comes from both the internal speakers and the headphone jack at the same time.

I'vea lready checked the Ubuntu Forums about the ALSA mixer and turning on the headphone sensor switch... but I am not using ALSA. I am using OSS.

The Headphone jack sensor switch isn't there... or at least it is easily recognizable.

I am running Ubuntu 9.04 64bit.

Everything else is running great, except that.

Any ideas?

Thank you,
Johnathan

---

### Post by pierre.bellec on 2010-11-08
Same problem here. I bought two laptop DELL vostro with Ubuntu 10.04 and both have the same problem. The sound control interface is much simpler than what I was used to on earlier versions of ubuntu, and there is no separate PCM / master volume control, or a switch for detecting the earphones. I tried alsamixer, but somehow I was unable to control the PCM/master separately, moving one changed the other. No sign of a switch for earphones there either. In any case, I have looked in a number of forums and have found a couple of related solutions, but none of them worked for me. If anyone has a tip, I would really appreciate it.

---

### Post by pierre.bellec on 2010-11-08
quick update : I have found numerous posts suggesting to intall the linux-backports-modules-alsa-lucid-generic package. It seems to fix the issue for a lot of people. In my case, it crashed my computer. Black screen at start up. I had no choice but to launch a recovery mode and uninstall the package. All the tweeks based on /etc/modprobe.d/alsa-base.conf had no effect. I'll keep trying, but I am afraid I am going to have to wait for an upgrade of some sort ...

---

