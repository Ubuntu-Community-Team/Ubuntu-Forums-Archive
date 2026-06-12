---
title: "No sound Newbie"
date: 2005-05-09
forum: Desktop Environments
---

### Post by ted on 2005-05-09
I'm hoping someone may be able to help me. I have been trying out a few of the distros, because I want to learn how to use Linux. I have tried Xandros, Ubuntu, and Kubuntu. I really like Kubuntu, but I can't seem to get any sound. I had sound with Xandros and with windows. I have tried a Cd and an Mp3, nothing. I believe the music is playing but nothing is coming out of the speakers, and yes the are hooked up. I have onboard audio ac'97 on a 845gv/ich4 motherboard. I have tried searching the other forums, but their solutions are over my head. Here is some info, maybe it will help.


2.6.10-5-386
lsmod
Module Size Used by
i915 18304 1
drm 59412 2 i915
proc_intf 4100 0
freq_table 4100 0
cpufreq_userspace 4572 0
cpufreq_ondemand 6172 0
cpufreq_powersave 1920 0
video 16260 0
sony_acpi 6280 0
pcc_acpi 11264 0
button 6800 0
battery 10244 0
container 4608 0
ac 4996 0
vga16fb 12488 1
vgastate 8576 1 vga16fb
ipv6 229504 9
af_packet 20744 2
sd_mod 16784 0
sis900 18436 0
snd_intel8x0 29984 1
snd_ac97_codec 64608 1 snd_intel8x0
snd_pcm_oss 47652 0
snd_mixer_oss 16768 1 snd_pcm_oss
snd_pcm 84872 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 23300 1 snd_pcm
snd 50276 8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_ oss,snd_pcm,snd_timer
soundcore 9824 1 snd
snd_page_alloc 9604 2 snd_intel8x0,snd_pcm
hw_random 5524 0
shpchp 86116 0
pci_hotplug 30512 1 shpchp
ehci_hcd 29444 0
usb_storage 64064 0
usblp 12032 0
scsi_mod 119936 2 sd_mod,usb_storage
uhci_hcd 30224 0
usbcore 107384 5 ehci_hcd,usb_storage,usblp,uhci_hcd
intel_agp 20636 1
agpgart 31784 3 drm,intel_agp
floppy 54864 0
pcspkr 3816 0
rtc 12216 0
md 43856 0
evdev 9088 0
dm_mod 53116 1
tsdev 7488 0
capability 5000 0
commoncap 7808 1 capability
psmouse 19336 0
mousedev 11160 1
parport_pc 34372 1
lp 10792 0
parport 33480 2 parport_pc,lp
ide_cd 38532 0
cdrom 36508 1 ide_cd
ext3 120968 1
jbd 54168 1 ext3
ide_generic 1664 0
piix 9988 1
ide_disk 18176 3
ide_core 118988 5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix 26164 543
thermal 13576 0
processor 22708 1 thermal
fan 4612 0
fbcon 34048 71
font 8448 1 fbcon
bitblit 5120 1 fbcon
vesafb 6948 0
cfbcopyarea 3968 2 vga16fb,vesafb
cfbimgblt 3072 2 vga16fb,vesafb
cfbfillrect 3584 2 vga16fb,vesafb


I hope this info helps. I must say this sound problem is giving me a crash course in Linux and Kubuntu. If anyone has any ideas, let me know them in the simplest terms possible, I've only been using linux a few days (hours). Thanks again for all of your help.

---

### Post by linux_fish on 2005-05-09
Are you using a Live CD or installed version? and Kubuntu or Ubuntu?

---

### Post by ted on 2005-05-09
I am using the installed version of kubuntu.

---

### Post by linux_fish on 2005-05-09
sorry, forgot to ask; Are you trying to play MP3s or an audio CD?

---

### Post by ted on 2005-05-09
I have tried both mp3's and audio cd's.

---

### Post by linux_fish on 2005-05-09
I have a similar set up on a spare computer. I'll see if I have any luck and will get back to you ASAP. Let me know if you resolve the issue before then.

---

### Post by abhaysahai on 2005-05-10
In the KDE Control Center, goto Sound & Multimedia.
   1) under that is Sound System, try Test Sound in that and check if you are getting sound. 
   2) In the System Notifications, Check Apply to all applicaitons and click on TurnOn All  Sounds. 

Ensure that you are getting sound. Then install  gstreamer-plugins. 
gstreamer-mad is required to play mp3.

Abhay

---

### Post by ted on 2005-05-10
I went into sound system and hit test sound, nothing. I then went to system notifications and checked Apply to all applicaitons and clicked on TurnOn All Sounds, went back to sound system and hit test sound and once again nothing. I got tired after 3 days of trying to get the sound working and downloaded and installed Novell desktop Linux, booted up and like Xandros it had sound. I haven't given up on Kubuntu, but it sure seems like there are an awful lot of issues with the sound. It seems like a lot of people are coming to these forums just to get help with sound issues. If anybody can think of what else I could try to get sound from Kubuntu, I sure would appreciate it.

---

