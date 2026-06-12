---
title: "No sound"
date: 2005-10-04
forum: Desktop Environments
---

### Post by KevRus on 2005-10-04
Help!  I can't seem to get sound to work in Ubuntu...

I've tried adding acpi_irq_isa=7 to the kopt/kernel lines in the /boot/grub/menu.lst file but it doesn't seem to work...I know there are probably tons of threads on this but I've searched and searched but can't seem to find an answer.

When I click Volume Meter under Sound & Video, I get an error saying "Cannot connect to sound daemon.  Please run 'esd' at a command prompt."

When I click Volume Control under Sound & Video, I get an error saying "No volume control elements and/or devices found."

I'm also having a graphics problem and have to use Vesa drivers to use Gnome, but I'll get to that later....I'm not planning on doing anything graphic extensive for a while, but I'd like to have sound ASAP.:???:

---

### Post by Mr Frosti on 2005-10-05
Try the following steps and/or provide additional information:

1) Click "System" -> "Preferences" -> "Sound". Is there a check in the box asking if you wish to start the sound server? If so, esd should be running.

2) Run esd from a terminal. To do this, press "Alt + F2" and type in "gnome-terminal". Click "Run" and then enter in "esd". Paste the output back in this thread for use later. 

3) What type of soundcard do you have? Run "lspci" from a terminal to find out.

4) Can you play a sound file from outside of Gnome? Install "mpg123" and then do the following:

End Gnome by pressing "Ctl + Alt + F1" and then typing "sudo /etc/init.d/gdm stop". Now, run mpg123 (sound file). Do you hear output?

Hope this helps a little...

---

### Post by renedox on 2005-10-05
also, is PCM set to a value other than 0?

---

### Post by KevRus on 2005-10-05
1) Yes, there is a check box asking to start the sound server, and it's activated.

2) I get a "No file or directory" error when I run esd

3) It isn't on the list, but I'll paste it anyways:

> 0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 554d
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 556d
0000:06:01.0 Communication controller: Conexant: Unknown device 2f20
0000:06:05.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 61)
0000:06:08.0 Ethernet controller: Intel Corp.: Unknown device 1064 (rev 03)

4) I am not able to play the sound outside of GNOME.

And renedox, how do I check what value it's set to?

---

### Post by KevRus on 2005-10-05
Anything else I can do? ^_^

---

### Post by KevRus on 2005-10-06
I'm sorry for bumping yet again, but I still am unable to fix this problem. :(

---

### Post by h-sqrd on 2005-10-09
I'm having the same issue as well - does anyone have any insight on this subject?

---

### Post by h-sqrd on 2005-10-11
After following some advice and following the directions here: 
[https://wiki.ubuntu.com//DebuggingSoundProblems/](https://wiki.ubuntu.com//DebuggingSoundProblems/)
and here:
[https://wiki.ubuntu.com/DebuggingHardwareDetection](https://wiki.ubuntu.com/DebuggingHardwareDetection)

I have more information and questions about my issue.

Below is the information provided by the scripts explained in the links - aparently the system can't find my sound card and I'm having a difficult time finding information on how to get it to recognize it.

```

user@computer:~/bin$ aplay -l
aplay: device_list:200: no soundcards found...

user@computer:~/bin$ ./aadebug
ALSA Audio Debug v0.0.9 - Tue Oct 11 00:23:32 EDT 2005
http://alsa.opensrc.org/?page=aadebug

Kernel ----------------------------------------------------
Linux computron 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

Loaded Modules --------------------------------------------

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Warning: /proc/asound does not exist
This indicates that ALSA is not installed correctly
Check various logs in /var/log for a clue as to why

Dev Snd ---------------------------------------------------
Warning: /dev/snd does not exist

CPU -------------------------------------------------------
model name      : Pentium III (Katmai)
cpu MHz         : 498.802

RAM -------------------------------------------------------
MemTotal:       516528 kB
SwapTotal:      570268 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)

user@computer:~/bin$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0d.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
0000:00:0e.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04)
0000:00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
0000:02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


```

I've googled for information and searched here on the forums without avail - I'm not well versed with sound cards; I'm using the default that came with my system which is a CS4237B chipset I believe.

Anyway, links, tips or tricks would be much appreciated.

Thanks.

---

