---
title: "No sound  - Help! - Intel 82440MX (AC 97 type integrated chip)"
date: 2006-01-14
forum: General Help
---

### Post by Q4U on 2006-01-14
Hi:

I have no sound in Breezy, neither system sounds nor music. I have tried quite a few things, but none seem to work. :( 

Please contribute any hunch you have on my situation, I might help me solve my problem and finally get rid of the hated mainstream os I am forced to continue to use.

**My Hardware** 

I have a Toshiba Portege 3490CT laptop. The sound card is an Intel 82440MX. It is recognized correctly, it seems.

dante@inferno:~$ lspci
...
0000:00:00.1 Multimedia audio controller: Intel Corp. 82440MX AC'97 Audio Controller
....

**What I Have Tried**

1. Opened all the channels imaginable with alsamixer.

2. Checked that I am part of the audio group with id. It would seem that I am.

3. Checked the driver needed: it is the snd_intel8x0, according to the alsa homepage. It appears to be correctly loaded.

dante@inferno:~$ lsmod
....
snd_pcm_oss    0
snd_pcm          3   snd_intel8x0,snd_ac97_codec, snd_pcm_oss
snd_timer         1   snd_pcm
snd                 8   snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
sndcore           1   snd
snd_page_alloc 2   snd_intel8x0,snd_pcm
.....

4. Fiddled with System -> Preferences -> Multimedia System Selector, swithcing to and from alsa, oss, and esd. 

5. I speculated it was an irq conflict, so I tried passing (several attempts) acpi=off, pci=routeirq,  acpi_irq_force=5 then 7 then 9 (all should be free according to my bios) in the grub menu.lst.

6. Blacklisted the oss drivers in /etc/hotplug/blacklist, speculating they might conflict with the alsa drivers. Also tried to take snd_intel8x0m out of the blacklist (it is blacklisted by default).

7. Tried the [UbuntuGuide fix]("http://www.ubuntuguide.org/#configuresoundproperly")

8. Temporarely replaced the hdd with one with Windows on it. The hardware works.

9. Googled madly, to no avail.

**Clues that something is wrong**

Although the system apparently seems to recognize the sound chip and to load the driver module correctly, there are several subtle malfunctionings which might give you a clue on what's wrong with the setup.

When I fiddle with System -> Preferences -> Multimedia System Selector, the Pipeline Test in Default Source hangs my laptop.

At bootup, the various modules are loaded and respond with "ok" before passing to the next stage. Hotplug though does not respond with "ok", the system just skips through to the next stage.

Also, blacklisting a module does not always work.

As you might notice, the output of lsmod says that there are 8 snd modules, but it lists only 6.

Thanks for any help.

---

### Post by neo_reloaded on 2006-01-14
Do not want to alter the initial post's context. 
But I am also faced with a very similar problem
I have a thinkpad with
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

I had sound playing initially.
but recently I did a bunch of updates including kernel. - not sure if it had a direct impact, but now, I am unable to hear any multimedia output.:confused: 
The system bell is the only sound I can hear( when I hit a backspace on a gnome-terminal prompt)

Please help

---

### Post by Q4U on 2006-01-14
If you have the console sounds and you used to have it fully working before, then arguably your situation is less severe than mine.

Have you gone through my checklist? I would think that the kernel updates have muted your sound channels (try 1. - open the terminal and type "alsamixer", you should be presented with a curses menu. Then navigate through the various channels, which are graphically represented by bars. See if Master and the other relevant ones are off, type "m" to turn then on). 

Alternatively, it might be possible that the esd drivers are overriding your alsa drivers (try 7. The UbuntuGuide Fix, it was originally written for 5.04 but some people say it is still relevant - I don't know though).

Hope that this works. ;) 

Q

---

### Post by -pod- on 2006-04-27
Hi,

Did somebody manage tosolve this problem?

i have exactly the same problems stated on the first post,
and i almost tryed everything Q4U already tried, none worked, plus i also tried to recompile the kernel a couple of times 2.6.10 and 2.6.16 (removing some modules) but nothing really changed.

I have a different soundcard working (actually **not** really working :p) as well with *snd_intel8x0*.

here i put some details about my sistem (i'm on Asus laptop Amd64, A6km model, breezy64bit)

```
cat /proc/interrupts
           CPU0
  0:    1882787    IO-APIC-edge  timer
  1:       2259    IO-APIC-edge  i8042
  7:          0    IO-APIC-edge  parport0
  8:          0    IO-APIC-edge  rtc
  9:    1629077   IO-APIC-level  acpi
 12:        678    IO-APIC-edge  i8042
 14:      21121    IO-APIC-edge  ide0
 15:      16472    IO-APIC-edge  ide1
 16:     117348   IO-APIC-level  nvidia
 17:          0   IO-APIC-level  yenta
 18:       8786   IO-APIC-level  ndiswrapper, SiS SI7012, ohci1394
 19:       6723   IO-APIC-level  eth0
 20:          0   IO-APIC-level  ohci_hcd:usb1
 21:      48177   IO-APIC-level  ohci_hcd:usb2
 22:          0   IO-APIC-level  ohci_hcd:usb3
 23:        135   IO-APIC-level  ehci_hcd:usb4
NMI:       1777
LOC:    1881403
ERR:          0
MIS:          0

```

*lspci -v*
```
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev  a0) (prog-if 00 [Generic])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1816
        Flags: medium devsel, IRQ 18
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: [48] Power Management version 2

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97  Sound Controller (rev a0)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1103
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at e400 [size=256]
        I/O ports at e000 [size=128]
        Capabilities: [48] Power Management version 2


0000:00:0a.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev  08) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1107
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at febf9800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

```

```
cat /proc/asound/cards
0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with ALC650F at 0xe400, irq 18
1 [default        ]: USB-Audio - USB2.0 Video
                     Syntek Semicon.     USB2.0 Video        at usb-0000:00:03.3-4, high speed

```

Thanks for any help

---

### Post by roderikk on 2006-04-29
Hi,

I've also been stuck with this problem since I installed breezy nearly 2 months ago. I couldn't get any sound to work. I recently upgraded to dapper flight 6 and did all the updates since then in the vain hope my sound would 'just start working' but to no avail. This is really starting to freak me out...

lspci -v:

```
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: Giga-byte Technology: Unknown device ae01
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at bc00 [size=256]
        I/O ports at c000 [size=256]
        Memory at f0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>
```

```
cat /proc/asound/cards
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC850 at 0xf0000000, irq 225
```

I've tried almost every step on Q4U's list and am slowly turning crazy...

Hope anyone can help!!

PS Sometimes when I type sudo gedit something I get the following message:

```
roderik@dapper:~$ sudo gedit /etc/modules
- using device default
- using device default
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.

```

Which I think is very weird because it shouldn't do that...? :-k

---

