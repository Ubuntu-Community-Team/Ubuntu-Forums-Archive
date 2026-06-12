---
title: "I hate to say it, but this is another &quot;no sound&quot; post"
date: 2005-07-31
forum: Desktop Environments
---

### Post by WideEyedSleeper on 2005-07-31
alright then, this being my first post and first day with ubuntu I'm a little perplexed as to how to get the sound to work.
I've tried what was reccomended in other threads and I can't get it to work.
I have a cs4236 sound card.

Could someone please help me find out why **/dev/dsp doesn't exist**.

Here's my lspci:
```
******@Ubuntu504:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440LX/EX - 82443LX/EX Host bridge (rev 03)0000:00:01.0 PCI bridge: Intel Corp. 440LX/EX - 82443LX/EX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:00:0a.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
``` 

and my lsmod:
```
justin@Ubuntu504:~$ lsmod
Module                  Size  Used by
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
apm                    19948  1
ipv6                  229504  9
af_packet              20744  2
3c59x                  37160  0
i2c_piix4               8592  0
i2c_core               21264  1 i2c_piix4
uhci_hcd               30224  0
usbcore               107384  2 uhci_hcd
pci_hotplug            30512  0
intel_agp              20636  1
agpgart                31784  1 intel_agp
ns558                   5632  0
analog                 10784  0
gameport                4608  2 ns558,analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  2
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  5
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  705
processor              22708  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
``` 

Just ask if you need any other outputs.

---

### Post by heimo on 2005-07-31
What does *sudo modprobe snd-cs4236 *tell?

Something possibly useful:
[http://www.alsa-project.org/alsa-doc/alsa-howto/x834.htm](http://www.alsa-project.org/alsa-doc/alsa-howto/x834.htm)
[http://lists.debian.org/debian-laptop/2005/03/msg00146.html](http://lists.debian.org/debian-laptop/2005/03/msg00146.html)

---

### Post by WideEyedSleeper on 2005-07-31
modprobe clicks the speaker and gives no text output so it knows that there is a soundcard there. It no longer says that /dev/dsp doesn't exist, but through rhythmbox the mp3 is playing yet no sound comes out of the speakers. they are plugged into the right jack and turned up. 

I'll try the 2nd link you supplied.

---

### Post by WideEyedSleeper on 2005-07-31
still no output.

---

### Post by heimo on 2005-07-31
Open terminal (Applications->System Tools->Terminal) and run alsamixer - go through all the channels and settings, and check if any is muted (m key). Try changing channel counts,  IEC958 settings and so on - you're probably close to the solution.

Go to the System->Preferences->Multimedia Systems Selector, select different "Sinks" and try the test button. Anything?

---

### Post by WideEyedSleeper on 2005-07-31
Nothing still. I'm starting to concider reinstalling Slackware, cause atleast I know how to get the sound working there. Although Slack is out of date by a few months.

---

### Post by varunus on 2005-07-31
Why must manufacturers use ISA sound cards?

The problem here is that your sound card is not PCI, therefore it cannot be autodetected safely.

Here are a couple of pages that can help you (the last 2 are IBM thinkpad specific, but that comp has this sound card so try them out):

[http://alsa.opensrc.org/index.php?page=ThinkPad600](http://alsa.opensrc.org/index.php?page=ThinkPad600)
[http://www.wlug.org.nz/ThinkpadNotes](http://www.wlug.org.nz/ThinkpadNotes)

You could also try installing the debian alsa packages; they have "alsaconf" which can autodetect ISA cards, I think.

---

### Post by WideEyedSleeper on 2005-07-31
ok, I've got sound, but I need to run "sudo modprobe snd-cs4236" and "sudo /etc/init.d/alsa restart" every time I boot plus turn up everything with the mixer.
Any help with this?

---

### Post by heimo on 2005-07-31
[QUOTE=WideEyedSleeper]ok, I've got sound, but I need to run "sudo modprobe snd-cs4236" and "sudo /etc/init.d/alsa restart" every time I boot plus turn up everything with the mixer.
Any help with this?[/QUOTE]

Put snd-cs4236 in /etc/modules, you probably no longer need to restart alsa, but mixer levels won't get fixed wth this. You could try to 1) fix the levels, 2) sudo alsactl store 3) make sure alsactl restore is called during boot / login. * 

This is related
[http://ubuntuforums.org/showthread.php?t=52713&highlight=alsactl]("http://ubuntuforums.org/showthread.php?t=52713&highlight=alsactl")

*) Before doing anything for 3rd step, you could just try restarting and watch if levels were restored. Make sure you have alsa-utils installed.
/etc/init.d/alsa-utils is the script that should restore levels

---

### Post by WideEyedSleeper on 2005-08-01
It works now, thanks for your help. Adding snd-cs4236 to /etc/modules did it.

---

### Post by Julius on 2005-08-01
This is kinda OT, but the other day when I had finally got my Wi-Fi card successfully configured, I found out that the sound wasnt working at all. Everything seemed just fine, but it just didnt sound, no matter how loud the volume was.

Two days later, ocassionally, I ran the volume control that is in the multimedia apps... and I found out it was all muted.

I was highly dissapointed. I mean, what do things like that happen???

---

