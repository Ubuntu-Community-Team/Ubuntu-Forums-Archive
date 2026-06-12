---
title: "Yet another NO SOUND!!!, can't find device!!"
date: 2005-12-02
forum: Desktop Environments
---

### Post by muted on 2005-12-02
I have a SB Live PCI card and a nvidia onboard thing which im not planning on using (unless SB live wont work)

everything in alsamixer is maxed out, all the stuff in "multimedia systems selector" is set on ALSA stuff. and my device from system -> preferences -> sound is on "SB live! Platinum"

Some sounds will play, but it seems that something has set a wrong default of soundcard for some programs...

Most programs says something like device not found and so on...

I do not have a /dev/dsp file


```
jacob@ubuntu:~$ lspci

0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:06.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 25)
0000:01:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
0000:01:07.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 05)
0000:01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:01:0a.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0140 (rev a2)
```

Thaks for your help!

---

### Post by muted on 2005-12-02
i also tried ```
jacob@ubuntu:~$ lsmod | grep snd
snd_emu10k1            96772  0
snd_rawmidi            22816  1 snd_emu10k1
snd_seq_device          8204  2 snd_emu10k1,snd_rawmidi
snd_util_mem            4480  1 snd_emu10k1
snd_hwdep               8608  1 snd_emu10k1
snd_intel8x0           30144  0
snd_ac97_codec         72188  2 snd_emu10k1,snd_intel8x0
snd_pcm                78344  3 snd_emu10k1,snd_intel8x0,snd_ac97_codec
snd_timer              21764  2 snd_emu10k1,snd_pcm
snd                    48644  8 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  3 snd_emu10k1,snd_intel8x0,snd_pcm

```

---

### Post by muted on 2005-12-03
Bump?

---

### Post by Cyhatch on 2005-12-03
Could you tell which sounds play and which don't? Gnome theme sounds/XMMS (what-have-you)/Totem (never worked for me)/etc.?

---

### Post by muted on 2005-12-03
For some reason Kaffeine works for me... GAIM plays sounds too...

The "test"button in multimedia systems selector works too on ALSA and ESD

But then nothing else... Totem/VLC/beep/XMMS/games likee quake3/ doom3/other stuff doesnt work... alot of it comes with an error message that says (BEEP):

> Couldn't open audio.

Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.


or 

gtick (a metronnome program to practice playing music):

> Couldn't start metronome.
Please check if specified sound device
and sample file are accessible.

The sound device set in gtick is /dev/dsp and i don't think that even exists, so that makes sence...

How do i find out what my device is called, then maybe i can set it manually in every program!???

Yet it all happened at an instant, so my guess is it could be changed right back?

i hope...

---

### Post by Cyhatch on 2005-12-03
Hmm. Do you mean you have ALSA and [FONT="Courier New"]esd[/FONT] working at the same time?

I've heard that [FONT="Courier New"]esd[/FONT] "doesn't help" ;) much with gaming. Also you probably don't need it if ALSA works anyway. So go:

```
sudo killall esd
```

That'll kill esd for the current session.

also, you might want to do

```
esd
``` to see what [FONT="Courier New"]esd[/FONT] itself says.

---

### Post by muted on 2005-12-03
Well, i typed "sudo killall esd" but my sound still is dead in theese programs. The esd command itself makes a funny beep sound and then freezes.

:confused:

---

### Post by Cyhatch on 2005-12-04
[FONT="Courier New"]sudo killall esd[/FONT] doing nothing means it's not running. [FONT="Courier New"]esd[/FONT] beeping means it has launched. Otherwise you would have gotten something like:

```
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd/socket
This socket already exists indicating esd is already running.
Exiting...
```

So, normally [FONT="Courier New"]esd[/FONT] is not running.

I suppose you should try setting it all to ALSA manually. That's what I did.

---

### Post by Cyhatch on 2005-12-04
[QUOTE=muted]For some reason Kaffeine works for me... GAIM plays sounds too...[/QUOTE]

What sound driver do these use?

By the way, just remembered: there was a topic here on the Ubuntu forums about some freaky SB card. You might want to search.

---

### Post by muted on 2005-12-04
[QUOTE=Cyhatch][FONT="Courier New"]sudo killall esd[/FONT] doing nothing means it's not running. [FONT="Courier New"]esd[/FONT] beeping means it has launched. Otherwise you would have gotten something like:

```
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd/socket
This socket already exists indicating esd is already running.
Exiting...
```

So, normally [FONT="Courier New"]esd[/FONT] is not running.

I suppose you should try setting it all to ALSA manually. That's what I did.[/QUOTE]
no im sorry, esd was running by default, and killall did turn it off, but no sound for that reason!

How do i set it all to alsa? :(

---

### Post by muted on 2005-12-04
[QUOTE=Cyhatch]What sound driver do these use?

By the way, just remembered: there was a topic here on the Ubuntu forums about some freaky SB card. You might want to search.[/QUOTE]
Dunno... none i know of! It worked when i installed ubuntu and then i had done nothing...

This might be a problem though...

---

### Post by veehell on 2005-12-04
Hi dudes,

check if /dev/dsp and other proper devices exist, if they not create them manualy or via scripts.

Some SB pci/isa card are not correctly PnP to system (in Breezy, not in Hoary). 
check /etc/modules.conf and /etc/modules which modules you are loading.
if your "favorite card's" one is missing load or compile to the kernel.

isa> use isapnptools package and dump isa information to file, provide(particual info specialy for your card) to ALSA via the scripts from (isapnptools package) or manually via ALSA tools...... edit /etc/modules and add the exact information such as in DOS starting files, (io adress, irq, dma, dma16) 

pci > it is similar, but i think you can follow the scenario, but i dont know the exact pci tools

What help me, were DEbian howto pages, wikipages for ubuntulinux and 
google groups have also some interest threads which might to navigate faster.
good luck. And here in forum i browse it as guest and it help me to, but i have not the URLs at the moment, search your self ;)

I am now running gnome with esd daemon and use ALSA output in XMMS, quake3arena running directly via alsa ( magic startup +set_initsound 1 which force quake to sound!, skype running via /dev/dsp, alsa mixer or gnome mixer operates well....so maybe i did it right.

But what is weird, i see arts proccess sleeping and esd too ... so maybe i need to correct it to run just only one.

heh the thread is here>
[http://ubuntuforums.org/showthread.php?t=1805]("http://ubuntuforums.org/showthread.php?t=1805")
ad_alsa_and_Audigy>
[http://alsa.opensrc.org/ca0106]("http://alsa.opensrc.org/ca0106")

---

### Post by muted on 2005-12-04
yes well i dont have any /dev/dsp .... 


how do i create that again??

and how do i set the default device in alsamixer (which is currently the onboard soundcard) to my SB live! ??

---

### Post by veehell on 2005-12-05
in /dev/ there si @MAKEDEV link...chek it and there is link >> [no /dev/dsp/ ]("http://lists.debian.org/debian-user/2000/06/msg00953.html") .... 

and here [Gentoo thread about ALSA and soundcards ]("http://forums.gentoo.org/viewtopic-t-279086.html") read it, there are some similar issues and some hints ho to proceed to solution ;) and some /dev/dsp vs /dev/sound diffs.

ad_alsamixer: there is command line mixer you just specify which card you are interest.... 
Usage: alsamixer [-h] **[-c <card: 0...7>] [-D <mixer device>]** [-g] [-s] [-V <view>]

if you have ALSA card correctly installed you can check the existing file(s)
/proc/asound/cards
/proc/asound/devices
/proc/asound/version

PS: i am lost same as you....with sound...so i am browsing and reading in parallel ;)

---

