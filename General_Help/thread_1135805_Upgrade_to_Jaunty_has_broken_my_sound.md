---
title: "Upgrade to Jaunty has broken my sound"
date: 2009-04-24
forum: General Help
---

### Post by AFarris01 on 2009-04-24
This is very odd, and I'm not sure how to proceed to fix this...

after upgrading to jaunty, my sound has started acting all wonky... the first thing i noticed was that my surround sound was no longer working (5.1 before, now just piping through the 2 front channels).  No big deal... I've fixed this before, so i didn't imagine it would be a problem.  BIG mistake. 

I went first into my daemon.conf file to see if the update had overridden the file, so i'd have to reset my speakers up but... much to my suprise, the config file is exactly as it was before.  so, i checked the system-wide daemon file, which formerly had the same settings... also unchanged.  so...pulseaudio is being told to use 6 speakers, and it's only using 2... ok...

next i checked alsamixer to see if some of the channels had somehow become muted... nope, they're all unmuted, and the volume responded normally when adjusted... now im getting confused

Finally i went to the system >*preferences > sound menu to see if anything in there had changed.  it hadn't... so  i started testing various things while playing a song in the background so i would notice any changes... then the weirdness began... all my sounds started playing really fast... singing sounded like chipmunks, system sounds and the sound panel's 'test' noise all played abnormally fast, amarok plays them really fast, sound previews are abnormally fast, and totem wont play any noises at all.  In addition, when the sound does play, it's terribly choppy, and eventually cuts out completely.

I've never made any custom changes to the pulseaudio configuration other than changing the sample channels to 6 in the daemon.conf file, so theres no issues of a 'custom config that broke' thing here

what the CRAP is going on?? I mean... i've had some pretty big issues with pulseaudio before, but nothing ever like this!  is anybody else having these issues, or know a way to fix it?

thanks in advance!

---

### Post by paradigm2 on 2009-04-24
What audio hardware have you?

```

lspci

```

in the terminal.

Also you might try deleting the ~/.pulse directory (in your home folder) and rebooting.

---

### Post by AFarris01 on 2009-04-24
Sorry... forgot to post that initially... 
$ lspci <return>
```

00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
**01:0a.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600XT]
04:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]

```

I bolded my sound card since theres a also an audio device reported by my graphics card, though i have no idea how to use or disable it... i just never used it and it was never a problem.

never thought of deleting the ~/.pulse/ directory... i'll try it right now, and post back with results


[EDIT]: Nope... deleted the .pulse directory in my home, and it's still behaving the same way.
[EDIT-EDIT]: Correction, deleting the ~/.pulse directory did do something: sounds that play are no longer choppy, nor do i get the 'chipmunk effect.' Sound also appears to be playing from all my satellite speakers, but the sub still wont play any sound.  any ideas?

---

### Post by AFarris01 on 2009-04-24
I've been doing a little reading around to see if anybody else has posted about my problem...nothing yet, but i did get some more info in the mean time:

when I run
```

$ speaker-test -c 6

```
I get sound feedback from all channels, with the following output:
```


speaker-test 1.0.18

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 32 to 349525
Period size range from 10 to 116509
Using max buffer size 349524
Periods = 4
was set period_size = 87381
was set buffer_size = 349524
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 10.951611


```
from this test i can see that the channels appear to be mapped correctly, and the 'pink noise' the speaker test played came out of the expected channels.  this is still made all the more odd considering that when using applications, or (more importantly) listening to music, i get no sound at all from my sub.

how can i proceed from here? thanks!

---

### Post by AFarris01 on 2009-04-25
I hate to bump, but... bumpity bump

---

### Post by AFarris01 on 2009-04-26
figured it out... just wanted to let everybody know, in case someone else runs into this same issue.

first of all, i discovered the answer here:
[http://manpages.ubuntu.com/manpages/jaunty/man5/pulse-daemon.conf.5.html](http://manpages.ubuntu.com/manpages/jaunty/man5/pulse-daemon.conf.5.html)

the key was this: pulseaudio has a new feature, to allow/disallow LFE remixing (low frequency effects remixing... i.e. bass remixing) and by default it's now turned on (meaning LFE remixing is disabled...hence no bass in audio streams that dont request it).  

to turn this on, and restore previous behavior, the entry "disable-lfe-remixing" in pulses' daemon.conf file must be added/edited, and given the value of 'no'.  this restores pulses' traditional behavior of LFE remixing, and makes me a happy camper.

case closed!*:)
suggested listening:*"Sleepwalker (Heavy Version)" - Nightwish

:)

---

### Post by steak on 2009-05-05
Hi AFarris01

Did you work out what was causing the:

> **AFarris01 said:**
> all my sounds started playing really fast... singing sounded like chipmunks, system sounds and the sound panel's 'test' noise all played abnormally fast, amarok plays them really fast, sound previews are abnormally fast, and totem wont play any noises at all.  In addition, when the sound does play, it's terribly choppy, and eventually cuts out completely.


I also had this problem until about 10min ago when I took your advice and removed my ~/.pulse directory. There seems to be some thing about upgrading with 6 channel audio to jaunty which breaks.

Glad to hear you have got things sorted in the end.

---

### Post by AFarris01 on 2009-05-23
actually no... deleting the .pulse directory and restarting was as far as i went with that.
i looked into it a little bit, but i couldn't really figure it out.  The only thing i could think of was that maybe something changed in one of the .pa files, and they had to be 'refreshed'... but thats just grasping at straws to be honest

what's weird is that my brother upgraded his install, he also has 5.1 surround, and his sound worked just fine afterwards...

---

### Post by dtgolder on 2009-06-16
> **AFarris01 said:**
> figured it out... just wanted to let everybody know, in case someone else runs into this same issue.

first of all, i discovered the answer here:
[http://manpages.ubuntu.com/manpages/jaunty/man5/pulse-daemon.conf.5.html](http://manpages.ubuntu.com/manpages/jaunty/man5/pulse-daemon.conf.5.html)

the key was this: pulseaudio has a new feature, to allow/disallow LFE remixing (low frequency effects remixing... i.e. bass remixing) and by default it's now turned on (meaning LFE remixing is disabled...hence no bass in audio streams that dont request it).  

to turn this on, and restore previous behavior, the entry "disable-lfe-remixing" in pulses' daemon.conf file must be added/edited, and given the value of 'no'.  this restores pulses' traditional behavior of LFE remixing, and makes me a happy camper.

case closed!*:)
suggested listening:*"Sleepwalker (Heavy Version)" - Nightwish

:)

Hmmm...this solution DID NOT work for me...still have the chipmunks....

---

### Post by Logan 1229 on 2009-06-23
Had simialar problem on 2 separate computers; 1 integrated sound & other an Audigy 4 card.

Integrated sound solved immediately using:
  [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Audigy 4 required driver re-installation & worked after re-boot.

---

