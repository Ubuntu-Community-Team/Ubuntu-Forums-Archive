---
title: "Shutdown hangs at System halted"
date: 2012-05-23
forum: Desktop Environments
---

### Post by dustinr on 2012-05-23
Hello Forum,

I have been digging, searching and trying solutions others posted for quite a while now, I figured I will just ask. 

I am running Ubuntu 10.10 with a custom kernel I compiled. This custom kernel has had the ACPI completely disabled/not compiled. I did this for weird USB bus issues where the device 'slept'.

The custom kernel is everything I want it to be, except when I shutdown It will hand at System halted. I have quite splash OFF so I can see that everything exits with an 'OK'. This system can restart just fine, it is only the shutdown that does not behave.

I really think the ACPI being disabled is the culprit, though It seems to me that if it can restart, than it should be able to shutdown. here is a list of attempts I made at editing the Grub kernel options.

"enable_mtrr_cleanup mtrr_spare_reg_nr=1 " HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 pci=noacpi" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 noapic nolapic irqpoll apm=off" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 processor.nocst=1" HANG (seemed faster, this options deals with mullet core CPUs)
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 acpi_osi=" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 acpi_osi="Linux"" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 acpi_osi="Windows 2006"" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 acpi=ht" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 acpi_osi=\"Linux"\" syntax error…
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 --verbose text" VERY HELPFUL!
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 processor.nocst=1 acpi=ht" HANG
"quite splash acpi=off noapic nolapic" HANG
"quite splash pci=noacpi" HANG
"quite splash irqpoll" HANG
"nolapic" HANG
"processor.nocst=1" HANG
"acpid=off" HANG
"acpi=force" HANG
"" HANG

--verbose text = at HANG = 	rc main process (25146) continued by CONT signal
						plymoth main process (25147) continued by CONT signal

and probably more that I didnt record. 

I also have tried different combinations of my bios settings. here are the bios setting that were working before I did the recompile of the kernel.

BIOS  
		trusted platform module 				- enable
		Enhanced INtel SpeedStep Technology	 - enable
		Processor C stated					- enable
		OS ACPI C2 Report					- disabled
		deep S4/S5 						- disabled
		PCIe ASPM Support				        - disabled



If anyone has any ideas I would love to hear them. Please, if you want log information, or lsmod or lspci or anything, request it and I will get it to you.

Thanks for any help!

---

### Post by blackbird34 on 2012-05-23
Have you tried lots of ways of shutting down? There's the graphical user interface, and the command line:

```
sudo shutdown -h now
```

(more command line ways [here]("http://ubuntuguide.net/all-manner-of-shut-down-modes-in-ubuntu-linux") )

Another one that worked for me was installing [Synapse]("http://www.webupd8.org/2010/11/syanpse-is-here-new-semantic-launcher.html"), typing Ctrl+Space (its keyboard shortcut) and then the first letters of "Shut Down" and pressing Enter. 

Can't think of anything else...

---

### Post by dustinr on 2012-05-24
Thanks for the reply, I will try these different shutdown commands. However I do not want to shut down this way. I would really like to find a 'fix' or 'patch' for this issue so I can shutdown the GUI way using the panel. 

I have tried:
panel GUI option - HANG
sudo shutdown -h now - HANG
sudo poweroff - HANG
sudo halt - HANG
sudo init 0 - HANG

Any more ideas? I dont know all of the kernel GRUB options, as yall can see in my previous post I pretty much only know...

enable_mtrr_cleanup
mtrr_spare_reg_nr=1
pci=noapic
noapic
nolapic
irqpoll
apm=off
processor.nocst=1
acpi_osi=
acpi_osi="Linux"
acpi_osi="Windows 2006"
acpi+ht
--verbose text
acpid=off
acpi=force
acpi=off
""

These options I found online, so I cant guarantee that all of these are valid. Does anyone know of a link that has all the kernel GRUB boot options? 

I saw this suggestion to blacklist a wireless network driver rt2860sta.
sudo modprobe -rf rt2860sta
sudo modprobe rt2860sta
echo blacklist rt2800sta | sudo tee -a /etc/modprobe.d/blacklist.conf

^- this had no effect on my shutdown hanging.

Hopefully someone can think of a way to help me, 
Thanks.

---

### Post by dustinr on 2012-05-24
A little more information:

Motherboard: Intel Corporation - DQ67EP
CPU: Intel Pentium G620 @ 2.6GHz / 64 bit compatible
RAM: 4GB
Operating System: Ubuntu 10.10
Kernel: 2.6.35.14-custom

Here are some outputs. I tried to attach my kernel configs but it failed. If yall think it could be useful let me know and I will try again.

output from lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0102] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:16.2 IDE interface [0101]: Intel Corporation Cougar Point IDE-r Controller [8086:1c3c] (rev 04)
00:16.3 Serial controller [0700]: Intel Corporation Cougar Point KT Controller [8086:1c3d] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.6 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 7 [8086:1c1c] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a4)
00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c4e] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c02] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 04)
03:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)

```

output from lsmod 
```

Module                  Size  Used by
parport_pc             26276  0 
ppdev                   5368  0 
joydev                  8615  0 
pcspkr                  1498  0 
binfmt_misc             6413  1 
snd_hda_codec_intelhdmi     9510  1 
snd_hda_codec_realtek   217221  1 
usbhid                 35841  0 
hid                    66645  1 usbhid
uvcvideo               54854  1 
snd_usb_audio          84672  1 
snd_usbmidi_lib        17009  1 snd_usb_audio
videodev               43066  2 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
snd_hda_intel          21161  2 
snd_hda_codec          85618  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  2 snd_usb_audio,snd_hda_codec
i915                  288337  3 
snd_pcm                68700  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17740  2 snd_usbmidi_lib,snd_seq_midi
drm_kms_helper         29563  1 i915
snd_seq_midi_event      6047  1 snd_seq_midi
drm                   167507  3 i915,drm_kms_helper
snd_seq                46801  2 snd_seq_midi,snd_seq_midi_event
snd_timer              18561  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    47971  17 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7218  0 
soundcore                880  1 snd
snd_page_alloc          7184  2 snd_hda_intel,snd_pcm
intel_agp              26610  2 i915
psmouse                57717  0 
parport                31435  3 parport_pc,ppdev,lp
serio_raw               4022  0 
i2c_algo_bit            4960  1 i915
agpgart                31585  2 drm,intel_agp
e1000e                128700  0 
ahci                   17411  2 
ehci_hcd               48120  0 
libahci                21117  1 ahci

```

---

### Post by dustinr on 2012-05-25
bump

---

### Post by dustinr on 2012-05-29
bump

---

### Post by anonymous5 on 2012-05-29
> **dustinr said:**
> Hello Forum,

I have been digging, searching and trying solutions others posted for quite a while now, I figured I will just ask. 

I am running Ubuntu 10.10 with a custom kernel I compiled. This custom kernel has had the ACPI completely disabled/not compiled. I did this for weird USB bus issues where the device 'slept'.

The custom kernel is everything I want it to be, except when I shutdown It will hand at System halted. I have quite splash OFF so I can see that everything exits with an 'OK'. This system can restart just fine, it is only the shutdown that does not behave.

I really think the ACPI being disabled is the culprit, though It seems to me that if it can restart, than it should be able to shutdown. here is a list of attempts I made at editing the Grub kernel options.

"enable_mtrr_cleanup mtrr_spare_reg_nr=1 " HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 pci=noacpi" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 noapic nolapic irqpoll apm=off" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 processor.nocst=1" HANG (seemed faster, this options deals with mullet core CPUs)
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 acpi_osi=" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 acpi_osi="Linux"" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 acpi_osi="Windows 2006"" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 acpi=ht" HANG
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 acpi_osi=\"Linux"\" syntax error…
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 --verbose text" VERY HELPFUL!
"enable_mtrr_cleanup mtrr_spare_reg_nr=1 processor.nocst=1 acpi=ht" HANG
"quite splash acpi=off noapic nolapic" HANG
"quite splash pci=noacpi" HANG
"quite splash irqpoll" HANG
"nolapic" HANG
"processor.nocst=1" HANG
"acpid=off" HANG
"acpi=force" HANG
"" HANG

--verbose text = at HANG = 	rc main process (25146) continued by CONT signal
						plymoth main process (25147) continued by CONT signal

and probably more that I didnt record. 

I also have tried different combinations of my bios settings. here are the bios setting that were working before I did the recompile of the kernel.

BIOS  
		trusted platform module 				- enable
		Enhanced INtel SpeedStep Technology	 - enable
		Processor C stated					- enable
		OS ACPI C2 Report					- disabled
		deep S4/S5 						- disabled
		PCIe ASPM Support				        - disabled



If anyone has any ideas I would love to hear them. Please, if you want log information, or lsmod or lspci or anything, request it and I will get it to you.

Thanks for any help!


In the kernel configuration, under ACPI don't disable everything at once. Only disable/enable two options at a time and compile/reboot to test. I know it's a lengthy process but this is how you'll know for sure the problem.

---

### Post by dustinr on 2012-05-30
Looks like that is what I have to do. I found this link that someone might find useful. It is a huge list of all the different kernel boot options. These options are to be entered into your grub file just like the acpi=off would be.

[http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php]("http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php")

I will be compiling the Kernel 3.0 and using it with my ubuntu 10.10 Does anyone have any thoughts or concerns on using this newer kernel with ubuntu 10.10? I will post any updates.

---

### Post by dustinr on 2012-05-31
OK,

I used the kernel 3.0.0 for my recompiling. 

I made a few changes inside the kernel ".config".
    Inside ACPI options I disabled both AC Adapter and Battery because this computer is always plugged in ( desktop )

I also changed a option inside the video section. I enabled the bootup logo just because I noticed it and I was curious.

The setting that affects the USB bus I think is the "Run-Time PM core functionality" This was disabled by default in the .config I had.

I believe the power setting are how I want them, though it seems if I had just installed the new kernel with out any changes I would receive the same effect. *** I make this assumption because of the files that are inside the "power" directory inside the /sys/devices/pci0000:00/..... usb directory. 

When I experienced the usb sleep problems before, I could see alot of files in that power directory. Files like autosuspend, runtime, level, , control, and some others I cant remember. I would try to edit these files, I was able to change the settings, but I would still experience problems. And I was not able to edit the files at time of boot up so I decided to try ( my first attempt ) to recompile kernel with out any acpi. After i booted to the 'new' kernel I got the effects I wanted with this, but my shutdown would hang. 

SO, I think the settings are how I want them because with the 3.0.0 kernel inside the power directory I only see one file. That file is named persist and it has a value of 1.

Can someone confirm if kernel 3.0.0 has only one file inside the power directory? The directory is difficult to find, but here is the PWD of it for this paticular device/bus number... 

/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/power

I would like to know if everyone who has 3.0.0 has only one file, or if my custom compiled kernel caused the one file.

So far so good with the new kernel, I will post anymore details when I get them. I hope someone can benefit from this, because it was a major headache for me. Why can the usb port stay powered on by default... :/


anyways. Enjoy!!!

---

### Post by dustinr on 2012-05-31
here is a script that someone can use to find the specific directory of a specific usb device.

you need lshal installed.

run lsusb to find the name of your device. change the name in the script where you see NAME_OF_YOUR_DEVICE.

```
#!/bin/sh

debug=0

lshal > /tmp/hal.txt
line=`cat /tmp/hal.txt | grep -ni NAME_OF_YOUR_DEVICE | head -1 | cut -d: -f1`

if [ "${debug}" != "0" ]
then
    echo ${line}
fi

start_line=`expr ${line} - 6`

if [ "${debug}" != "0" ]
then
    echo ${start_line}
fi

tail_line=`wc -l /tmp/hal.txt | cut -d' ' -f1`
tail_line=`expr ${tail_line} - ${start_line}`

if [ "${debug}" != "0" ]
then
    echo ${tail_line}
fi

cat /tmp/hal.txt | tail -${tail_line} > /tmp/hal.1.txt

sys_path_str=`cat /tmp/hal.1.txt | grep linux.sysfs_path | head -1`
echo ${sys_path_str} | cut -d "'" -f2

exit 0

```

this will get you to a directory that has the power directory in it. You can then go into the power dir and see if it only has one file called persist. again I am wanting to test kernel 3.0.0

---

