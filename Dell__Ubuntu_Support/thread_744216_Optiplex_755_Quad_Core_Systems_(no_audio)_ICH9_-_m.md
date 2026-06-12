---
title: "Optiplex 755 Quad Core Systems (no audio) ICH9 - might not roll out 100+ systems....."
date: 2008-04-03
forum: Dell  Ubuntu Support
---

### Post by SLK55_AMG on 2008-04-03
We have about 4 of them in house, and are debating whether to roll out to 100+ people or not.  However, everything is working fine w/ these systems except one component.....Sound.


I have been trying for 3 weeks to get soundworking with:

Ubuntu 7.10
Dell Optiplex 755 (Intel Core 2 Quad)




Need help, I'm about to give up on this, and just let them run w/ vista, which have normal functioning sound.

ryan@cisco:~$ sudo lsmod
Module                  Size  Used by
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0
cpufreq_powersave       2688  0
cpufreq_conservative     8072  0
cpufreq_ondemand        9612  0
cpufreq_stats           7232  0
cpufreq_userspace       5280  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
ac                      6148  0
container               5504  0
video                  18060  0
sbs                    19592  0
button                  8976  0
bay                     6912  0
dock                   10656  1 bay
battery                11012  0
lp                     12580  0
ipv6                  273892  20
snd_hda_intel         262552  1
snd_pcm_oss            44800  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4996  0
snd_seq_oss            35328  0
snd_seq_midi            9728  0
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
xpad                    9988  0
fglrx                1547660  24
snd                    56452  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
heci                   59916  0
pcspkr                  4224  0
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
parport_pc             37412  1
parport                37448  3 ppdev,lp,parport_pc
serio_raw               8068  0
psmouse                39952  0
e1000_ich9            188736  0
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
intel_agp              25620  0
agpgart                35016  2 fglrx,intel_agp
evdev                  11136  4
ext3                  133896  1
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0
sr_mod                 17828  0
cdrom                  37536  1 sr_mod
sd_mod                 30336  3
usbhid                 29536  0
hid                    28928  1 usbhid
ata_generic             8452  0
ehci_hcd               36492  0
ata_piix               17540  2
uhci_hcd               26640  0
floppy                 60004  0
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
usbcore               138632  5 xpad,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0
processor              32072  1 thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor
ryan@cisco:~$

ryan@cisco:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c1

ryan@cisco:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ryan@cisco:~$


ryan@cisco:~$ lshw
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel



any ideas?

I've spent 3 weeks trying to get audio working on 4 test systems before we purchase 96 or so more 755's, but sound simply will not work on our test machines...........sound does work on these machines out of the box with XP/Vista, but why not 7.10 Ubuntu.  This is extremely frustrating.  Bios versions are A06 after a manual upgrade from A01.


I notice that there is an A08 upgrade, but it is in executable only format, and dell does NOT offer an ISO version of the A08 executable bios patch.  ISo offering is more enterprise/corporate targeted.  I do know about the tool developed by the dell dev to convert exe to ISO, but a tad cumbersome....


Need help! :)

---

### Post by SLK55_AMG on 2008-04-03
I was reading here:


[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133)



My 1420 is working fine. Make sure your mixer outputs are not muted. My favorite mixer is gnome-alsamixer which clearly shows which outputs are muted.

sudo apt-get install gnome-alsamixer

After checking that your outputs are not muted, you can play the startup tune:


------


I decided to apt-get install gnome-alsa-mixer, and it turns out "mono" was muted? and that seems to have fixed internal speakers?  Sound seemed good, but I don't know if this is a gimped usage of my sound card,,,,"mono" sort of makes me think its running in some crippled mode?

---

### Post by martinimike on 2008-05-13
i currently have this problem.  everything shows up via [FONT="Fixedsys"]lspci[/FONT] and [FONT="Fixedsys"]cat /dev/sndstat[/FONT]  

the songs display properly in the Amarok equalizer so it seems everything is actually working but the rear audio jack is not turned on.

however, when i plug into the front headphone jack on the 755, audio output is normal.   

is there something additional that needs to be done to make both audio outputs function simultaneously?

thanks in advance.


michael

```
root@libsystems:/dev# cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux libsystems 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA Intel at 0xfebdc000 irq 16

Audio devices:
0: AD198x Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Analog Devices AD1984
```

```
root@libsystems:/dev# lspci
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 2400 XT
03:02.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
```

```
systems@libsystems:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

ETA

well, i certainly fee like the n00b.  after opening KMix for the umpteenth time, i noticed that the third tab "Switches" had two radio buttons labeled Front and Headphones, the former of which was not on.  This "Front" is apparently the back output audio jack.

i beg your pardon for the simple mistake but hopefully someone else will be spared the shame.  :-)

---

