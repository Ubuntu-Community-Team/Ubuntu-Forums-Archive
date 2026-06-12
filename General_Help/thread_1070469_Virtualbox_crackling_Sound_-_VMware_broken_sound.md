---
title: "Virtualbox: crackling Sound - VMware: broken sound"
date: 2009-02-15
forum: General Help
---

### Post by DjNDB on 2009-02-15
Hi there,

i'm trying to get a virtualized Windows running on Ubuntu 8.10 AMD64.

VMWare Player 2.5.1 build-126130:
I first tried to get my VMWare Windows XP running wit Vmware Player. I had no sound at all. Trying to connect the Soundcard produced the Message Popup:
"Cannot connect virtual device sound. No corresponding device is available on the host."

When i kill pulseaudio first with "pulseaudio -k" then sound kinda works, but misses a few seconds of the beginning and crackles.

VirtualBox 2.1.2:
Annoyed by VMWare i decided to try Virtualbox. There the sound "works" via Pulseaudio, but it crackles all the time.
I tried this with a fresh Windows Vista, and Ubuntu Jaunty Alpha 4.
The VirtualBox Audio device is set to ICH AC97



Bottomline: 
Both are entirely useless for me that way. 

Can someone please help me?

---

### Post by nicoverbking on 2009-02-15
> **DjNDB said:**
> 
Virtualbox:
Annoyed by VMWare i decided to try Virtualbox. There the sound "works" via Pulseaudio, but it crackles all the time.


Are you using the version of VirtualBox provided in the official repositories? 

If so, you might have more luck with the latest version on [the official site]("http://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by DjNDB on 2009-02-15
> **nicoverbking said:**
> Are you using the version of VirtualBox provided in the official repositories? 

If so, you might have more luck with the latest version on [the official site]("http://www.virtualbox.org/wiki/Linux_Downloads").

Sorry, I forgot that i'm using that already

---

### Post by nicoverbking on 2009-02-15
Try the ALSA Audio Driver, (if it's installed) it's under Settings > Audio in VirtualBox.
That might fix the problem.

---

### Post by DjNDB on 2009-02-15
> **nicoverbking said:**
> Try the ALSA Audio Driver, (if it's installed) it's under Settings > Audio in VirtualBox.
That might fix the problem.

I tried that already :(
Alsa with Pulseaudio or Alsa with Pulseaudio and "padsp VirtualBox":
Same Crackling sound

Without Pulseaudio or Pulseaudio with OSS and "aoss VirtualBox":
"No audio devices could be opened. Selecting the NULL audio backend with the consequence that no sound is audible.


Error ID: 
HostAudioNotResponding
Severity: 
Warning"

---

### Post by nicoverbking on 2009-02-15
Sounds like a broken driver for your sound card - are there any problems playing back music/sounds in Ubuntu itself?

Else, take a look at Launchpad to see if there are any similar sound problems. When you find nothing, you might want to file a bug.

Good luck!

---

### Post by DjNDB on 2009-02-15
I just found [Someone with the same problem]("http://ubuntuforums.org/showthread.php?t=972023") and no solution. :confused: :(

---

### Post by DjNDB on 2009-02-15
> **nicoverbking said:**
> Sounds like a broken driver for your sound card - are there any problems playing back music/sounds in Ubuntu itself?


Not at all. Otherwise Audio Playback works perfectly.

---

### Post by nicoverbking on 2009-02-15
All right, here are some steps for you to try. If the first step doesn't work, try the next to see if it doesn't fix the problem.

1. Reboot the machine. (VM and the Host)
2. Reinstall VirtualBox Additions on XP;
3. Reinstall VirtualBox on Ubuntu;
4. Reinstall PulseAudio ("pulseaudio-module-x11" in synaptic) and the Linux sound base ("linux-sound-base" in synaptic)

Hopefully, that fixes the problem. 
If the problem persists, then what sound card are you using? And what version of Ubuntu?

5. If you really can't find a solution, I suggest you remove PulseAudio completely. PulseAudio and ALSA might be conflicting.

---

### Post by DjNDB on 2009-02-15
> **nicoverbking said:**
> All right, here are some steps for you to try. If the first step doesn't work, try the next to see if it doesn't fix the problem.

1. Reboot the machine. (VM and the Host)
2. Reinstall VirtualBox Additions on XP;
3. Reinstall VirtualBox on Ubuntu;
4. Reinstall PulseAudio ("pulseaudio-module-x11" in synaptic) and the Linux sound base ("linux-sound-base" in synaptic)

Hopefully, that fixes the problem. 
If the problem persists, then what sound card are you using? And what version of Ubuntu?

I'll try a fresh Ubuntu installation instead of 4. as soon as i have time for that. I don't indent to break my current system. I'll post the other results as soon as i get around to doing that.

It is Ubuntu 8.10 AMD64.

---

### Post by nicoverbking on 2009-02-15
All right. Good luck, I hope your problem gets fixed. Personally, I've used Ubuntu 8.10 AMD64 since its Release and I haven't had any problems with VirtualBox though, so a fresh install can help. (I did a fresh install)

---

### Post by DjNDB on 2009-02-15
> **nicoverbking said:**
> All right, here are some steps for you to try. If the first step doesn't work, try the next to see if it doesn't fix the problem.

1. Reboot the machine. (VM and the Host)
2. Reinstall VirtualBox Additions on XP;
3. Reinstall VirtualBox on Ubuntu;


So far I tried 1, 2 on Vista and 3+2 With VMware OSE 2.0.4 from the Ubuntu Repository. Same old same old :-(

I'll dig out a Hard disk one day and Try it on a fresh Ubuntu Jaunty.

btw. My Sound is Onboard of the [GA-MA78GM-S2H (rev.1.1)]("http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=2814"). I might try one of the SB Live! Cards i have lying around first.

Thank you for your help so far. Maybe the last steps will do something good.

---

### Post by Martin Rabson on 2009-09-02
bump!

Ubuntu 9.04 Host (SoundBlaster Audigy)
XP 64 Guest
VirtualBox 3 Guest Addition installed

PulseAudio / ALSA / OSS

Sound scratchy broken, tried all settings combinations.

Wondering why threads RE: VirtualBox and audio issues keep dying?

---

### Post by dcstar on 2009-09-03
> **Martin Rabson said:**
> 
..........
Wondering why threads RE: VirtualBox and audio issues keep dying?

Are you referring to threads that clearly should be in the Virtualization forum and **NOT** the General forum?

---

### Post by Martin Rabson on 2009-09-03
Thankyou good sir

That would most likely explain it. Didn't even notice that section.
Think I need to spend some time getting to know the Forum contents :oops:

Ta muchly!

---

