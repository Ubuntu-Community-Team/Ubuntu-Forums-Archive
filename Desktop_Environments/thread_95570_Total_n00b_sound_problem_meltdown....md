---
title: "Total n00b sound problem meltdown..."
date: 2005-11-26
forum: Desktop Environments
---

### Post by ionizd on 2005-11-26
Help, please! At startup I get a message box with the following message:Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.
The volume control also has a red "X" thing on it and reads, "mixer not found."  Any thoughts?

---

### Post by cwaldbieser on 2005-11-26
[QUOTE=ionizd]Help, please! At startup I get a message box with the following message:Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.
The volume control also has a red "X" thing on it and reads, "mixer not found."  Any thoughts?[/QUOTE]
I guess the obvious question is, does /dev/dsp exist on your system?  Try opening the terminal and type:
```

$ ls /dev | grep dsp

```
If you don't get any results, that probably means your sound device is not configured correctly.  Do you know what kind of sound card you have?

---

### Post by ionizd on 2005-11-27
I have an old Creative Soundblaster awe 64 ISA card, model# CT4500

---

### Post by cwaldbieser on 2005-11-27
[QUOTE=ionizd]I have an old Creative Soundblaster awe 64 ISA card, model# CT4500[/QUOTE]
Well, if /dev/dsp is not showing up, it probably means your sound drivers are not loading correctly.

Try this command to see if your system is actually detecting the card:
```
$ lspci
```

Then try this command to see if there are any sound drivers loaded:
```
lsmod | grep snd
```

---

### Post by ionizd on 2005-11-27
jason@guineapig:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:04.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:04.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:04.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0c.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:00.0 VGA compatible controller: S3 Inc. Savage 4 (rev 02)
jason@guineapig:~$
 I don't think it's detecting the card-I do know the card works, though. Could the fact that I've got an ISA card be the problem?

---

### Post by cwaldbieser on 2005-11-27
[QUOTE=ionizd]jason@guineapig:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:04.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:04.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:04.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0c.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:00.0 VGA compatible controller: S3 Inc. Savage 4 (rev 02)
jason@guineapig:~$
 I don't think it's detecting the card-I do know the card works, though. Could the fact that I've got an ISA card be the problem?[/QUOTE]

Yeah, lspci will list PCI cards, so you are probably right.  You could try poking around in the /proc filesystem to see if the card is detected:

```

$ less /proc/devices
$ less /proc/interrupts

```

There are some other hardware detection commands I can't recall at the moment, plus I think there is a device manager in the Gnome Desktop, somewhere.

---

### Post by ionizd on 2005-11-27
Here are the results from the first command:
Character devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 29 fb
128 ptm
136 pts
180 usb
216 rfcomm
254 devfs

Block devices:
  1 ramdisk
  2 fd
  3 ide0
  9 md
 22 ide1
253 device-mapper
254 mdp
And here are the results from the second:
           CPU0
  0:   23897044          XT-PIC  timer
  1:        946          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  7:          0          XT-PIC  parport0
  8:          1          XT-PIC  rtc
 11:       6779          XT-PIC  uhci_hcd:usb1, eth0
 12:      63294          XT-PIC  i8042
 14:      25595          XT-PIC  ide0
 15:    1063249          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0

 I hope y'all know what all this means!:???:

---

### Post by az on 2005-11-27
Try this:
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

---

### Post by ionizd on 2005-11-29
[QUOTE=azz]Try this:
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)[/QUOTE]
 Went there, followed directions for manually loading awe 64 drivers and it didn't work. I tried switching cards out with another ISA card (that's all I got left!:( ), a Soundblaster 16 value. Tried to manually load drivers for that and got the same result. This is the first few lines of what my machine spat back at me:
jason@guineapig:~$ modprobe snd-sb16
WARNING: Error inserting soundcore (/lib/modules/2.6.12-9-386/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.12-9-386/kernel/sound/soundcore.ko): Operation not permitted
FATAL: Error inserting snd (/lib/modules/2.6.12-9-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.12-9-386/kernel/sound/core/snd-rawmidi.ko): Operation not permitted

---

### Post by az on 2005-11-29
[QUOTE=ionizd]Went there, followed directions for manually loading awe 64 drivers and it didn't work. I tried switching cards out with another ISA card (that's all I got left!:( ), a Soundblaster 16 value. Tried to manually load drivers for that and got the same result. This is the first few lines of what my machine spat back at me:
jason@guineapig:~$ modprobe snd-sb16
WARNING: Error inserting soundcore (/lib/modules/2.6.12-9-386/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.12-9-386/kernel/sound/soundcore.ko): Operation not permitted
FATAL: Error inserting snd (/lib/modules/2.6.12-9-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.12-9-386/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.12-9-386/kernel/sound/core/snd-rawmidi.ko): Operation not permitted[/QUOTE]



Did you use sudo?

ex:

sudo modprobe snd-sb16


# I edited the wiki page to include sudo in the first example.

---

### Post by ionizd on 2005-11-29
O.K, now we're getting somewhere. This is what I got:
jason@guineapig:~$ sudo modprobe snd-sb16
Password:
FATAL: Error inserting snd_sb16 (/lib/modules/2.6.12-9-386/kernel/sound/isa/sb/snd-sb16.ko): No such device
FATAL: Error running install command for snd_sb16
 Wrong driver for my sb 16 value? Hmmm...

---

### Post by az on 2005-11-29
Either wrong driver, the thing is disabled in the bios or the irq or port address conflicts with some other hardware and you have to do it yourself.

What about trying that first card again?

---

### Post by ionizd on 2005-12-03
Thanks for all the help so far. It's gotten some results, but we're not out of the woods yet.
 I tried the Awe64 card again, this time enabling PnP O/S in bios, and attempted again to load the proper module. It did this:
[I]jason@guineapig:~$ sudo modprobe snd-sbawe
jason@guineapig:~$[/I]
 This doesn't tell me much, but it's a different result so I'm encouraged. I still don't have sound, so I go back to the beginning of this thread and follow the directions.
I  open the terminal and type:
*$ ls /dev | grep dsp*
 And I get this:
[I]jason@guineapig:~$ ls /dev | grep dsp
dsp
jason@guineapig:~$[/I]
 What does this mean? Okay, so next step:
[I]jason@guineapig:~$ lsmod |grep snd
snd_sbawe              28096  0
snd_opl3_lib            9856  1 snd_sbawe
snd_sb16_dsp            9856  1 snd_sbawe
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  2 snd_sb16_dsp,snd_pcm_oss
snd_timer              21764  2 snd_opl3_lib,snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd_sb16_csp           18304  1 snd_sbawe
snd_sb_common          14336  3 snd_sbawe,snd_sb16_dsp,snd_sb16_csp
snd_hwdep               8608  2 snd_opl3_lib,snd_sb16_csp
snd_mpu401_uart         6784  1 snd_sbawe
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  3 snd_sbawe,snd_opl3_lib,snd_rawmidi
snd                    48644  13 snd_sbawe,snd_opl3_lib,snd_sb16_dsp,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_sb16_csp,snd_sb_common,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
jason@guineapig:~$[/I]   
 This is different than before, Looks like the drivers are loaded. Next:
*$ less /proc/devices*
Resulting in:
[I]Character devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 29 fb
116 alsa
128 ptm
136 pts
180 usb
216 rfcomm
254 devfs

Block devices:
  1 ramdisk
  2 fd
  3 ide0
  9 md
 22 ide1
253 device-mapper
254 mdp[/I]
 Sound is listed! Next:
[I]$ less /proc/interrupts
 Resulting in:
          CPU0
  0:    2465518          XT-PIC  timer
  1:       2450          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:          0          XT-PIC  SoundBlaster
  7:          1          XT-PIC  parport0
  8:          1          XT-PIC  rtc
 11:       1569          XT-PIC  uhci_hcd:usb1, eth0
 12:     138075          XT-PIC  i8042
 14:      12865          XT-PIC  ide0
 15:     106239          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0[/I]
 Sound blaster is listed here as well! So, now what?
BTW, this is on the Wiki:
That worked so, I added "snd-es18xx" to /etc/modules so that it would be loaded at boot time.
sudo gedit
 When I type in this code, It tells me this:
[I]jason@guineapig:~$ sudo gedit
sudo: gedit: command not found
jason@guineapig:~$[/I]
 How do I add the module to the bootup? Also, I do have sound now, through the system notification sound test function.

---

### Post by mo_x on 2005-12-03
I assume you use Kubuntu (KDE), use the following:
sudo kwrite /etc/modules

---

### Post by ionizd on 2005-12-03
Ha! That's got it. It now seems that everything works. Thanks for everyone's help. Now, I learn how to use this O/S.:D :KS :D

---

