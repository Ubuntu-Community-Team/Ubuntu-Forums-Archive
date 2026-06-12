---
title: "Getting ALSA to work."
date: 2009-01-21
forum: General Help
---

### Post by dragos240 on 2009-01-21
I don't know why, but after i removed the startup programs so xorg would start, it doesn't work. I'm pretty sure when i removed the startup programs, the sound didn't already start, how do you start ALSA?

---

### Post by gettinoriginal on 2009-01-21
What happens when you type ```
alsamixer
``` into terminal ??

---

### Post by dragos240 on 2009-01-22
> **gettinoriginal said:**
> What happens when you type ```
alsamixer
``` into terminal ??

No mixer elements found.

---

### Post by gettinoriginal on 2009-01-22
May I suggest you try this:  :p
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by dragos240 on 2009-01-22
> **gettinoriginal said:**
> May I suggest you try this:  :p
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


Sadly it looks like it doesn't recognise my soundcard, it did before i went non-gui, and sound works on my brother's account.

---

### Post by gettinoriginal on 2009-01-22
In terminal type:    ```
lspci
```  and post the results

---

### Post by dragos240 on 2009-01-23
```

~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

```

---

### Post by gettinoriginal on 2009-01-23
Try installing "linux-sound-base" and "gnome-alsa-mixer"

---

### Post by dragos240 on 2009-01-24
> **gettinoriginal said:**
> Try installing "linux-sound-base" and "gnome-alsa-mixer"


my linux sound base is at it's newest, and gnome-alsa-mixer doesn't exist.

edit: It's gnome-alsamixer, good thing i have google on my side.
edit2: I installed both packages, but sadly get the same annoying thing

---

### Post by dragos240 on 2009-01-26
Bump [IMG]http://img132.imageshack.us/img132/5470/bumpgy3.png[/IMG]

---

### Post by jocko on 2009-01-26
What happens if you run:
```
sudo /etc/init.d/alsa force-reload
```?

---

### Post by dragos240 on 2009-01-26
> **jocko said:**
> What happens if you run:
```
sudo /etc/init.d/alsa force-reload
```?


/etc/init.d/alsa: command not found
But when i did sudo alsa force-reload, it did this:
```

Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```

---

### Post by stchman on 2009-01-26
> **dragos240 said:**
> I don't know why, but after i removed the startup programs so xorg would start, it doesn't work. I'm pretty sure when i removed the startup programs, the sound didn't already start, how do you start ALSA?

Give us an lspci output here in this thread of the machine in question.  We need to know what kind of hardware it has.

---

### Post by dragos240 on 2009-01-26
> **stchman said:**
> Give us an lspci output here in this thread of the machine in question.  We need to know what kind of hardware it has.

I already have, i posted in on page 1 but here you go:
```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)


```

---

### Post by jocko on 2009-01-26
> **dragos240 said:**
> /etc/init.d/alsa: command not found
But when i did sudo alsa force-reload, it did this:
```

Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```
Ok. Apparently I was wrong about the command, but according to the output alsa *should* be working fine. The correct sound drivers are loaded. Exactly what did you remove to cause the sound to stop working? Alsa is not affected by xorg, so you must have done something else...

---

### Post by dragos240 on 2009-01-26
> **jocko said:**
> Ok. Apparently I was wrong about the command, but according to the output alsa *should* be working fine. The correct sound drivers are loaded. Exactly what did you remove to cause the sound to stop working? Alsa is not affected by xorg, so you must have done something else...

Hmm, i ran a command that apperently removed "startup programs". I don't remember the command, but other people didn't seem to have problems, also my brother's account can display sound, but mine can't.

---

### Post by jocko on 2009-01-26
> **dragos240 said:**
> Hmm, i ran a command that apperently removed "startup programs". I don't remember the command, but other people didn't seem to have problems, also my brother's account can display sound, but mine can't.

Exactly what do you mean in the first post when you say you "removed the startup programs so xorg would start"?
Do you mean you removed something to *prevent* xorg from starting, or did you remove something that *was preventing* xorg from starting?
Without knowing what you did, it's really difficult to guess here... but did you perhaps mess with the startup scripts in /etc/init.d/ or the links in /etc/rc2.d/? Or did you just change something in the gnome session? It would really help if you had any idea of what you did...

Perhaps you just disabled pulseaudio? Try running:
```
pulseaudio -C
```in a terminal.

---

### Post by dragos240 on 2009-01-26
> **jocko said:**
> Exactly what do you mean in the first post when you say you "removed the startup programs so xorg would start"?
Do you mean you removed something to *prevent* xorg from starting, or did you remove something that *was preventing* xorg from starting?
Without knowing what you did, it's really difficult to guess here... but did you perhaps mess with the startup scripts in /etc/init.d/ or the links in /etc/rc2.d/? Or did you just change something in the gnome session? It would really help if you had any idea of what you did...

Perhaps you just disabled pulseaudio? Try running:
```
pulseaudio -C
```in a terminal.

W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: [COLOR=Red]Daemon already running[/COLOR].
E: main.c: [COLOR=Red]pa_pid_file_create() failed.[/COLOR]

---

### Post by jocko on 2009-01-26
> **dragos240 said:**
> W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: [COLOR=Red]Daemon already running[/COLOR].
E: main.c: [COLOR=Red]pa_pid_file_create() failed.[/COLOR]

Are you *sure* you just haven't muted some alsa or pulseaudio control?
Both alsa and pulseaudio are running, so you *should* have sound.
To access the alsa mixer, use this command:
```
alsamixer -Dhw
```
And to access the pulseaudio device in alsa:
```
alsamixer -Dpulse
```

---

### Post by dragos240 on 2009-01-27
alsamixer: function snd_ctl_open failed for hw: No such file or directory

thats what i got when i tried alsamixer -Dhw
and when i tried alsamixer -Dpulse
No mixer elems found

---

### Post by jocko on 2009-01-27
And you say sound works on your brother's account on the same computer?
You didn't really answer my [questions]("http://ubuntuforums.org/showpost.php?p=6621554&postcount=17")... Exactly what did you do to mess it up?
If I understood you correctly, you did something to prevent X from loading, but you don't remember what you did? How did you find the instructions for what you did?
Can you still start x manually?```
sudo gdm
```Try this, it will remove any specific alsa or pulseaudio configurations you have in your account:
```
mv ~/.asoundrc ~/asoundrc.bak
mv ~/.asoundrc.asoundconf ~/asoundrc.asoundconf.bak
mv ~/.pulse ~/pulse.bak
```Then log out and log back in and see if anything changes, but I can't really do anything else than guess when you don't try to explain what you did...

---

### Post by dragos240 on 2009-01-27
I'm in x right now each time i log in, i login and type "startx" into the terminal. I'll try those commands.

EDIT: I tried GDM and it did the trick, i can hear things now, but i'm still confused why? The problem is fixed now, but i still want to know why the gnome display manager did the trick and why starting x manually didn't

---

