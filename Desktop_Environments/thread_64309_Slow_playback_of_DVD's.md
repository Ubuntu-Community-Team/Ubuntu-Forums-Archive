---
title: "Slow playback of DVD's"
date: 2005-09-10
forum: Desktop Environments
---

### Post by daller on 2005-09-10
Hi All,

I've tried to get both Kaffeine and Okle to play my dvd's properly, but the video can't keep the standard framerate... (The picture "lacks" - or what its named)

How can I fix this?

I've installed libdvdcss2 and kaffeine-xine (does any of you have problems with gstreamer???)

---

### Post by Tschaeck on 2005-09-10
[QUOTE=daller]Hi All,

I've tried to get both Kaffeine and Okle to play my dvd's properly, but the video can't keep the standard framerate... (The picture "lacks" - or what its named)

How can I fix this?

I've installed libdvdcss2 and kaffeine-xine (does any of you have problems with gstreamer???)[/QUOTE]
 has your dvd-drive DMA enabled?

you can check this with "hdparm -i /dev/hdx"

---

### Post by hibatsu on 2005-09-12
Mine is quite slow too.
The hdparm output looks like this:

```

hibatsu@solanki:~$ hdparm -i /dev/hdc

/dev/hdc:

 Model=_NEC DVD+RW ND-6100A, FwRev=104D, SerialNo=
 Config={ Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

 * signifies the current active mode

```

---

### Post by rcerreto on 2005-09-12
Very likely you aren't accessing the DVD via DMA.
Kubuntu does not set it by default.
The real trick is that you have to load the MB chipset modules *before* loading ide-cd, ide-common etc.
Look at /etc/modules and add a line to load the chipset module before the lines starting with ide-*something*
In my case it's "piix" (IBM Thinkpad T41) but yours could be different.
You'll have to guess somehow: try typing 'lsmod' from a terminal and give a look at the output. You should see the module name listed on the same line together with ide-cd and/or ide-common ed/or ide-core.
At worse try posting your /etc/modules and lsmod output.
Maybe someone knows better.
Once you achieve to load the modules in the right order, you're ready to set DMA access.

sudo hdparm -d1 /dev/hdx

will set DMA access until next reboot.
To set it permanently you'll have to edit /etc/hdparm.conf

Then your DVDs will play great.

HTH

---

### Post by daller on 2005-09-12
---

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse

---

**AND**

---

mga                    57600  1
drm                    59412  2 mga
binfmt_misc            11272  1
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  11
af_packet              20744  2
via_rhine              19972  0
mii                     4736  1 via_rhine
snd_via82xx            25248  2
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  2 snd
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
via_ircc               24340  0
irda                  168000  1 via_ircc
crc_ccitt               2176  1 irda
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  3 ehci_hcd,uhci_hcd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
via_agp                 9216  1
agpgart                31784  2 drm,via_agp
pcspkr                  3816  0
rtc                    12216  0
analog                 10784  0
gameport                4608  2 snd_via82xx,analog
floppy                 54864  0
evdev                   9088  0
md                     43856  0
tsdev                   7488  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
via82cxxx              12956  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   26164  530
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  71
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  1
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

---

Now what shall I do? - And why is this not default?

---

Should /etc/modules look like this?

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

via82cxxx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse

---

### Post by yoloosis on 2005-09-12
Try
```
sudo hdparm -c1d1 /dev/hdx
```
It enables 32bits and DMA. Try to play a DVD after. If it play well, there is a /etc/hdparm.conf : if think you have to tweak it to enable 32bits transferts and DMA after the boot.

---

### Post by mlomker on 2005-09-12
[QUOTE=yoloosis]It enables 32bits and DMA. Try to play a DVD after. If it play well, there is a /etc/hdparm.conf : if think you have to tweak it to enable 32bits transferts and DMA after the boot.[/QUOTE]

hdparm.conf doesn't work, from my experience.  Add the same command to the end of /etc/init.d/bootmisc.sh instead.

It's not default because older IDE controllers don't support those modes and turning them on could prevent those machines from working at all.

---

### Post by daller on 2005-09-13
[QUOTE=mlomker]hdparm.conf doesn't work, from my experience.  Add the same command to the end of /etc/init.d/bootmisc.sh instead. working at all.[/QUOTE]

This is the only thing I have do alter? - or some of the above replies to?

I have to add "hdparm -c1d1 /dev/hdx" to "/etc/init.d/bootmisc.sh" or what?

---

### Post by mlomker on 2005-09-14
[QUOTE=daller]I have to add "hdparm -c1d1 /dev/hdx" to "/etc/init.d/bootmisc.sh" or what?[/QUOTE]

That'll do it.  Just add the commands before the **exit** entry at the end of the file.  You'll see the output on your screen during boot-up.

Here's what I have at the end of mine:

```

#
# Set hdparm for IDE drives
#

hdparm -d1c1 /dev/hdc
hdparm -d1c1 /dev/dvd
hdparm -c1d1m16 /dev/hda

: exit 0

```

---

### Post by rcerreto on 2005-09-15
[QUOTE=daller]---



Should /etc/modules look like this?

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

via82cxxx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse[/QUOTE]

Yes, exactly

If you don'l load via82cxxx before ide-* any attempt to enable DMA access to your CD/DVD will likely fail.
Why that? Don't know.
I guess it uses by default very conservative settings in order to have the best chances to get a  working system.

Whether to enable it permanently via hdparm.conf or /etc/init.d/bootmisc.sh is anybody's choice. In my case hdparm.conf worked but I guess the other option is ok too.

After modifying /etc/modules and rebooting, type:

sudo hdparm -d1[c1] /dev/hd[c|d|whatever]

the output will say whether DMA is now on or off

If it's ON you just have to set it permanently, if it's still OFF then....  Houston, we have a problem!

---

### Post by mlomker on 2005-09-16
[QUOTE=rcerreto]Whether to enable it permanently via hdparm.conf or /etc/init.d/bootmisc.sh is anybody's choice. In my case hdparm.conf worked but I guess the other option is ok too.
[/QUOTE]

I heard from a coworker that there are command-line switches for the /etc/modules lines that you can use as well.  I haven't looked at that.

---

### Post by sfabel on 2005-09-27
OK, I've got the opposite problem. Now that I enabled DMA on my DVD, playback is fast. May it be that it's because of my power horse PC (dual-core amd64 3800+) or due to something else, how can I play it slower?

Thanks,
Stephan

---

### Post by mlomker on 2005-09-27
>  or due to something else, how can I play it slower?

That could be a problem related to powernowd.  Does your system clock keeps accurate time?  

I wonder if disabling power management in the BIOS would disable the frequency scaling?  I'm just speculating...I don't know for sure.

---

### Post by rlange on 2005-10-04
[QUOTE=yoloosis]Try
```
sudo hdparm -c1d1 /dev/hdx
```
It enables 32bits and DMA. Try to play a DVD after. If it play well, there is a /etc/hdparm.conf : if think you have to tweak it to enable 32bits transferts and DMA after the boot.[/QUOTE]


linux noob here. Hoary 5.04. I did try sudo hdparm -c1d1 /dev/hdc  and here is output:

root@ubuntu:/home/rick # sudo hdparm -c1d1 /dev/hdc

/dev/hdc:
 setting 32-bit IO_support flag to 1
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 IO_support   =  1 (32-bit)
 using_dma    =  0 (off)

I am wrong in thinking I can change this in a root terminal session??
thanks

---

