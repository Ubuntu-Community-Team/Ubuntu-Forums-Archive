---
title: "How do i edit grub"
date: 2006-09-27
forum: Desktop Environments
---

### Post by banko on 2006-09-27
Hey guys,

I just got xubuntu running on my dad's old TravelMate 212T, and I have run into a few problems....

Number one, the only way I can get the system to boot is if i manually add: [ acpi=off ] at the boot screen.  I would like set this up in grub so I don't have to manually enter it everytime.

Second, is the DVD drive is being recognized as a CD drive.  Disks gives a model: [ MX-7002Bc ]

Third, is sound is not working.  I don't know anything about Xfce so if someone can give me some direction as to how to get the information you need in order to help me set it up, that would be fantastic.

Wireless was dectected, setup perfectly.  And the system seems reasonably fast considering the low RAM.  Good job guys!

Unfortunately, my display seems caped at 800x600 which is probably right for this old beast, but do to the lack of monitor space I would ike to remove the top and bottom panel... or at least one of them.  In gnome it's rather simple, you just right click and remove panel.... no such option in xfce, or atlease from what I can see.

---

### Post by ayoli on 2006-09-27
> **banko said:**
> 
Number one, the only way I can get the system to boot is if i manually add: [ acpi=off ] at the boot screen.  I would like set this up in grub so I don't have to manually enter it everytime.
To add this to grub:
```
sudo gedit /boot/grub/menu.lst
```
then find a line starting with *defoptions* add your option to it:
```
defoptions=acpi=off
```
> **banko said:**
> 
Third, is sound is not working.  I don't know anything about Xfce so if someone can give me some direction as to how to get the information you need in order to help me set it up, that would be fantastic.
type in a terminal:
```
lspci
```
will show you all your devices models
and:
```
lsmod
```
will show you all the loaded modules

---

### Post by banko on 2006-09-27
lspci:

> 0000:00:00.0 Host bridge: ALi Corporation M1621 (rev 01)
0000:00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (rev 01)
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:13.0 CardBus bridge: O2 Micro, Inc. OZ6812 CardBus Controller (rev 05)
0000:00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 5d)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)


lsmod:

> Module                  Size  Used by
apm                    21228  1
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
ipv6                  265728  6
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
lp                     11844  0
r818x                  84620  0
ieee80211_rtl          83464  1 r818x
joydev                 10048  0
tsdev                   8000  0
pcmcia                 40508  0
floppy                 62148  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
i2c_ali1535             7428  0
pcspkr                  2180  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
i2c_ali15x3             7940  0
psmouse                36100  0
yenta_socket           28428  2
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               21904  2 i2c_ali1535,i2c_ali15x3
serio_raw               7300  0
rtc                    13492  0
snd_ali5451            24460  1
snd_ac97_codec         93088  1 snd_ali5451
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  1 snd_pcm
ali_agp                 7168  1
agpgart                34888  1 ali_agp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci_hcd               21892  0
usbcore               130692  2 ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
generic                 5124  0
alim15x3               12428  0 [permanent]
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

---

### Post by banko on 2006-09-27
your instructions for the menu were perfect thanks.  Any thoughts at all about removing taskbars in Xfce?

---

### Post by orb9220 on 2006-09-27
[http://www.xfce.org/index.php?page=documentation&lang=en#faq](http://www.xfce.org/index.php?page=documentation&lang=en#faq)
click on faq then it's third one down. If that is what you mean.

---

### Post by Kateikyoushi on 2006-09-27
> **banko said:**
> your instructions for the menu were perfect thanks.  Any thoughts at all about removing taskbars in Xfce?
 
Right click on the menu select customise panel.
Choose which panel you want to remove and click the - to remove it.

---

### Post by banko on 2006-09-27
OK I feel like an idiot, how did I miss something so obvious.  Thanks.  Just the sound and dvd left.  Any of you guys develop for Ubuntu?  I would like to give something back as I have used their software on over ten computers now.

I have 6 Static Broadband IP addresses at my office that I'm not using.  Do you know if they need more people to host downloads?

---

