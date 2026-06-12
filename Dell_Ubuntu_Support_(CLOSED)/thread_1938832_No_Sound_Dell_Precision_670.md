---
title: "No Sound Dell Precision 670"
date: 2012-03-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by c4c on 2012-03-10
Set up 4 (out of 10) [Dell Precision 670]("http://computers4christians.org/Document/Computer/Dell/Precision/Precision-670WS.html") WorkStations, wiping them with [DBAN]("http://www.dban.org/about") and then using our [C4C]("http://computers4christians.org/index.html") Live CD of Ubuntu 10.04, but the *last two* have ***no sound***. The only difference I know between the first 4 and the last two installs was not being able to easily make it into the BIOS before wiping the hard drive.

All these Precision 670s came with WinXP on the drives and the last two, I wasn't able to F2 into Setup, so I just rebooted with a DBAN CD inside. It worked to wipe the drives. I shut down with our live CD in the drive, booted up and easily installed with the Live CD. I ran the updates, installed some extra apps, successfully got back into the BIOS Setup and changed the boot order. It wasn't until I tested out an Internet Radio Station in Rhythmbox I realized I had no sound. Tried VLC, Totem, etc. No sound on anything - not even the GNOME login sound. Setup shows the "onboard sound card" as on.

Playing with one of them now...
System Testing detects the sound card as
0 [ICH5        ]: ICH4 - Intel ICH5
                 Intel ICH5 with AD19181B at irq 17

Heard no sound ***except*** when doing the headphones test - heard a tone out of one side. Ooh-Totem didn't work to play a DVD either (in the System Testing). Am I missing something really obvious here, or is more info needed to trouble-shoot? Thanks in advance to anyone who can help.

---

### Post by c4c on 2012-03-10
From running
```
sudo aplay -l
```
I get
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
And
```
find /lib/modules/`uname -r` | grep snd
```
finds a bunch of sounds; over 100
Running ```
lspci -v | grep -A7 -i "audio"
```
Shows me
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Dell Device 0168
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ec00 [size=256]
    I/O ports at e8c0 [size=64]
    Memory at dffffa00 (32-bit, non-prefetchable) [size=512]
    Memory at dffff900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
```
Hope this helps someone help me?

---

### Post by c4c on 2012-03-11
Tried the Sound Troubleshooting Procedure, but got stuck after the very first command(s) for Ubuntu 10.04.

```
E: Couldn't find package linux-alsa-driver-modules-2.6.32-39-generic
```

---

### Post by c4c on 2012-03-19
Went through the whole [SoundTrobleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") using the Ubuntu 10.04 (Lucid) command and following Steps 1, 2 and 3, even though the proper ALSA modules package couldn't be found.

The ALSA driver version, library version and utilities version were ***not*** exactly the same version number.

Driver version:     1.0.**21**
Library version:    1.0.**24**.1
Utilities version:  1.0.**24**.2

So, I then used the excellent [ALSA Upgrade Script Redux]("http://ubuntuforums.org/showthread.php?t=1681577"); download only the AlsaUpgrade-1.0.24-2.tar.gz, and replaced the version number 1.0.25-3 in steps 3-7 with 1.0.24.2

I then picked the SoundTrobleshootingProcedure back up in Step 4 and by Step 7 it was all good and sound was working. :)

---

### Post by c4c on 2012-03-24
Update - I have confirmed all the Dell Precision 670s I set up this month (in March - wish I had an exact date) had the exact same sound problem for the exact same reason; the ALSA Driver version was stuck at 1.0.21. I used the same method above to fix every one of them.

Addendum - The final two actions taken to produce sound (out of a pair of external speakers) was hitting F6 to select the Intel ICH5 sound card in Alsamixer (and unmuting and turning up the volumes on everything) and then unchecking most everything that had then been automatically checked in GNOME ALSA Mixer. ):P

---

