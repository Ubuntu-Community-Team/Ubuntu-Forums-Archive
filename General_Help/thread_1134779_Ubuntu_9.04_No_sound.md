---
title: "Ubuntu 9.04 No sound"
date: 2009-04-23
forum: General Help
---

### Post by and1bskbl72 on 2009-04-23
I have no sound using gateway p6860fx, it was working in 8.10. 

Do I have to download the sound drivers from package manager?
I think I was using hda alsa before.

---

### Post by paradigm2 on 2009-04-23
In a terminal:

```

lspci

```

To show us what kind of hardware you have.

How did you upgrade to Jaunty?  Clean install or regular upgrade?

---

### Post by Synthros on 2009-04-23
Back when I upgraded from v8.04 to v8.10, the upgrade reset all my main mixer settings to a very low level.  Type the following in a terminal to ensure your main volume settings (Master, PCM) are at an acceptable level:

gnome-volume-control

---

### Post by paradigm2 on 2009-04-24
> **Synthros said:**
> Back when I upgraded from v8.04 to v8.10, the upgrade reset all my main mixer settings to a very low level.  Type the following in a terminal to ensure your main volume settings (Master, PCM) are at an acceptable level:

gnome-volume-control

Could very well be it too.  Especially check the front speakers.

---

### Post by and1bskbl72 on 2009-04-24
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


Taken from lspci - No sound everything turned up?

---

### Post by mdawgmike on 2009-04-24
I have this same issue.

Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

Worked fine in 8.10 x86_64 without having to take any extra steps
Works in Windows XP
Volume un-muted in control panel and at acceptable levels

The sound control panel seems to detect the correct device.  I do indeed have a SB Audigy Value.  I hear the faint popping (or whatever you'd call it) when the sound driver initiates at startup, but I cannot get any sound to come out of my speakers in Ubuntu.  I did a clean install of 9.04 x86_64.

Any tips?

---

### Post by paradigm2 on 2009-04-24
> **and1bskbl72 said:**
> Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


Taken from lspci - No sound everything turned up?

I hate to tell you this but it appears that this one will likely be tough to solve. :(

[http://ubuntuforums.org/showthread.php?t=1128699](http://ubuntuforums.org/showthread.php?t=1128699)

You can try everything else that everyone suggests but if it doesn't work, I recommend:

1. Upgrade to a newer Alsa.
2. Upgrade to a newer PulseAudio (tons of fixes).
3. Upgrade to the mainline 2.6.30rc3 kernel (there were intel audio fixes).

To install the new kernel:

1. Read this: [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds) and understand that this is unofficial and might break other things....possibly.

2. Install her from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/) using the instructions from the link above.

To install a much newer alsa and pulse audio (again this is unofficial) :

1. Add these unofficial PPA's to your sources list or else the "Third Party Repositories" in Synaptic Package Manager.

deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main

2. Upgrade all the upgrades suggested from the repository..


--- Something else to try.  Delete the directory ~/.pulse.


.. I had to install the new kernel and pulseaudio and alsa in order to get sound working well on my laptop (otherwise it crashed 30% of the time on startup and I often lost sound otherwise).  Although it has different hardware than you (though was still an intel HDA).  Good luck.  Again, only do this if all the other solutions people give you fail.

---

### Post by pickboy87 on 2009-04-24
If none of that works, you could always give OSS a shot as well. I've always used it, since it just tends to work much better than ALSA or Pulse for me.

Here's the link for the site: [http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

Select the .deb one for you're version (not sure if you're using x64 or the regular x86).

And this is how I installed it. I renamed the file to something simple to remember, try oss.deb or something to your liking. Keep it in your /home/username (change accordingly) folder. Log out, and select a fail-safe terminal from the sessions. Log back into that. From there, type in the command line:

```
sudo dpkg -i oss.deb
```

Let it install, then try this after to verify that it worked.

```
osstest
```

Hopefully that will work for you. It will basically shut off ALSA and have OSS take over.

---

### Post by trahald10 on 2009-04-25
I'm actually having the same exact problem with the p-6860fx laptop too. It's weird because it was working fine for 8.10.

Does anyone else have any ideas for us to try?

---

### Post by and1bskbl72 on 2009-04-25
bump, tried using oss, still not working, apparently another user with the same laptop has the same problem... any ideas?

---

### Post by bailunrui on 2009-04-27
I, too, am having this problem with 9.04. Pulseaudio and ALSA never really played nice on my laptop before, but now my usual fixes aren't working.

```
lscpi
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

---

### Post by nutz on 2009-05-02
I have a Sony Vaio VGN-AR630E with the following audio device...

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

I have audio with 9.04 64bit but no control over output device. The only output that works is the built in speakers and the volume is not very loud even when it is turned all the way up. The headphone jack, microphone jack and S/PDIF do not work. My notebook has HDMI and the video works excellent but the sound does not work. The HDMI and headphone jack I can live without but it would be really nice to have the S/PDIF working at least.

If anyone gets the S/PDIF to work on this audio device please post your alsa-base.conf. I have tried multiple combinations but none of them have worked so far.

---

### Post by som24 on 2009-05-06
@paradigm you are boss.you solveed my problem.finally my ubuntu is making sound
yahooo

---

### Post by DeusExM1 on 2009-05-08
would you mind telling us how you got sound to work? 

My friend has the same P-6860FX laptop and sound would only work through headphones. We were unable to get it to work in ubuntu and had to revert back to vista.

---

### Post by wconstantine on 2009-05-12
I had this problem but I found the solution. KILL THE PULSEAUDIO PROCESS.

---

### Post by nutz on 2009-06-05
Would you mind explaining in a little more detail? I have been struggling with this for a little over 6 months now and I have almost reached the conclusion it is not possible with current software. I don't care so much about the headphone or HDMI audio but the SPDIF would be really nice to have back. I have done a lot of searching and tried a lot of things but none of them have made it work yet even though others report success with the same chipset. It is a shame really because other than this audio issue Ubuntu runs really sweet on this laptop.

---

### Post by karvec on 2009-09-30
I have also had the same problem, same laptop, Gateway p6860-fx since 9.04.  Sound works on headphones, nothing through speakers.

Would love to get a solution for this.

---

