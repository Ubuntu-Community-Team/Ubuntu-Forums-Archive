---
title: "Need help with sound issues"
date: 2009-03-21
forum: General Help
---

### Post by psychomichael on 2009-03-21
I've been struggling with sound issues ever since late into 7.10 after the kernel was changed. 

I'm using Ubuntu 8.04 (Gnome) now and still have problems. I used the live disc for Kubuntu 8.04 and the sound was doing the same thing: sloooowww soooouunnd...seriously, it's like listening to a record that's set too slow. 

I have tried nearly everything including taking it to a friend who works with Linux and it's driving me absolutely insane! :evil:


Can anyone help? I'm so frustrated that I'm about ready to leave Ubuntu forever in search of a linux that will work for me.

---

### Post by Vaphell on 2009-03-21
where are the details? :-)

---

### Post by hyper_ch on 2009-03-21
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by psychomichael on 2009-03-21
> **hyper_ch said:**
> It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use separate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

I've tried to be direct but then I get no answer at all...kinda like this thread:

[http://ubuntuforums.org/showthread.php?t=1043254](http://ubuntuforums.org/showthread.php?t=1043254)

---

### Post by psychomichael on 2009-03-21
> **Vaphell said:**
> where are the details? :-)

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009cc05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86d486d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18890   151733893+  83  Linux
/dev/sdb2           18891       19457     4554427+   5  Extended
/dev/sdb5           18891       19457     4554396   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00002058

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    b  W95 FAT32

Disk /dev/sdd: 250.0 GB, 250057252864 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfae5b407

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS
michael@darkmage:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
05:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
05:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

```
michael@darkmage:~$ cat /proc/asound/cards
 0 [CMI8738MC8     ]: CMI8738-MC8 - C-Media PCI CMI8738-MC8
                      C-Media PCI CMI8738-MC8 (model 68) at 0xbc00, irq 21
```

---

### Post by psychomichael on 2009-03-21
continued:

```
michael@darkmage:~$ lsmod
Module                  Size  Used by
isofs                  36388  0 
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
binfmt_misc            12808  1 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ipv6                  267780  16 
ppdev                  10372  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
usblp                  15872  0 
nvidia               4718832  32 
agpgart                34760  1 nvidia
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
snd_cmipci             38528  3 
gameport               16008  1 snd_cmipci
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12928  1 snd_cmipci
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_cmipci
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  19 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               7940  0 
soundcore               8800  1 snd
button                  9232  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
i2c_nforce2             7680  0 
i2c_core               24832  2 nvidia,i2c_nforce2
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
evdev                  13056  3 
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136840  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  9 
usb_storage            73664  2 
libusual               19108  1 usb_storage
pata_amd               14212  0 
sata_nv                27528  3 
ata_generic             8324  0 
floppy                 59588  0 
forcedeth              51980  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
pata_acpi               8320  0 
libata                159344  4 pata_amd,sata_nv,ata_generic,pata_acpi
scsi_mod              151436  6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
ehci_hcd               37900  0 
ohci_hcd               26640  0 
usbcore               146412  6 usblp,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
michael@darkmage:~$ 


```

---

