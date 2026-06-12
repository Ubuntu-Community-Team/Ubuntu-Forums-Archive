---
title: "Sound not working on Sony VAIO VGC-RC110G"
date: 2009-05-31
forum: General Help
---

### Post by fireflake78 on 2009-05-31
I'm using Ubuntu 9.04 on a Sony VAIO VGC-RC110G. I checked in Volume Control, Sound, etc but can't get the sound to work at all! I suspect that I need to install the sound driver in Ubuntu, but I have no idea what my sound card is, and the sound works fine in my Vista Ultimate partition.

When I ran lspci in Terminal, here's what I got:

```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
05:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```What is my sound card, and where can I get the driver, please?! I'm completely new to Ubuntu, so a thorough, step-by-step guide to getting the audio working would receive much thanks.

I hope the above information is sufficient.

---

### Post by armitage1337 on 2009-06-08
I've got an RC110G as well. It's had the same problem with sound in Ubuntu for over 3 years now. I have no idea why the Ubuntu developers haven't fixed it yet.

Anyway, to get it to work, run the following commands in a terminal:```
sudo echo "options snd-hda-intel model=vaio" >> /etc/modprobe.d/alsa-base.conf
``````
sudo /sbin/alsa reload
```

You will have to plug the audio cable into the "Woofer/Center" jack, rather than the "Front" jack for some reason. Also, the audio is very quiet, so you might have to amplify the signal after it leaves the computer.

---

### Post by WJason on 2009-06-11
Thanks!  This is the most straight-forward answer I've seen to this question.  Unfortunately, when I type in the command I get "Permission Denied" for a response.  How to I execute the commands with the proper permission?:)

I managed to add the options line to alsa-base.conf using gedit.  Rebooted--and still no sound.  :-(

---

