---
title: "ppracer problems with TNT2"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by vulpes76 on 2006-06-06
Hi hoping someone might be able to help me i'm running dapper and have installed the legacy nvidia drivers for my TNT2 32mb pci card. I have installed ppracer, the came comes up with a screen saying press any key, when i do i'm returned to the ubuntu desktop at maybe 800x600 rather than my normal 1280x1024 and the mouse no longer responds, anyone got any ideas how I can fix the problem? I have installed a car game trigger and that seems to work fine.

---

### Post by xfctr on 2006-06-09
I have exactly the same problem - TNT2, nvidia driver, same behaviour.
I usually have to use Ctrl-Alt-Backspace to restart X, sometimes even the keyboard hangs and I have to cold-reset.
Used to work Ok in breezy.

Here is some excerpt from dmesg, if someone could help:

[4296958.588000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4297142.504000] Inbound IN=eth0 OUT= MAC=4c:00:10:3b:bf:1b:00:30:48:53:d2:ba:08:00 SRC=140.113.125.36 DST=87.116.96.203 LEN=90 TOS=0x00 PRE
C=0xC0 TTL=108 ID=16044 PROTO=UDP SPT=17628 DPT=17560 LEN=70
[4297194.930000] NVRM: Xid: 13, 0002 beef5501 00000055 00000540 00203102 00000800
**[4297194.946000] Bad page state at free_hot_cold_page (in process 'ppracer', page c11bb6f4)**
[4297194.946000] flags:0x80000400 mapping:00000000 mapcount:0 count:0
[4297194.946000] Backtrace:
[4297194.946000]  [<c0151421>] bad_page+0x81/0xc0
[4297194.946000]  [<c0151d9c>] free_hot_cold_page+0x4c/0x150
[4297194.946000]  [<e10adf6f>] nv_vm_free_pages+0xa9/0x10a [nvidia]
[4297194.948000]  [<e10b132f>] nv_free_pages+0x290/0x2ae [nvidia]
[4297194.949000]  [<e0ea00aa>] _nv001716rm+0x4e/0x58 [nvidia]
[4297194.949000]  [<e0ea0089>] _nv001716rm+0x2d/0x58 [nvidia]
[4297194.950000]  [<e0e93916>] _nv001783rm+0x26/0x2c [nvidia]
[4297194.952000]  [<e0e7eaba>] _nv007585rm+0x9a/0xd4 [nvidia]
[4297194.953000]  [<e0e88a4b>] _nv001228rm+0x8b/0x9c [nvidia]
[4297194.954000]  [<e0fc0f14>] _nv004321rm+0x18/0x48 [nvidia]
[4297194.955000]  [<e0e88830>] _nv001233rm+0x88/0x19c [nvidia]
[4297194.956000]  [<e0e88871>] _nv001233rm+0xc9/0x19c [nvidia]
[4297194.957000]  [<e0e8125c>] _nv007602rm+0x40/0x5c [nvidia]
[4297194.957000]  [<e0ea66e6>] rm_disable_interrupts+0x42/0x54 [nvidia]
[4297194.958000]  [<e0e87974>] _nv001246rm+0x13c/0x260 [nvidia]
[4297194.959000]  [<e10b2884>] os_acquire_sema+0x48/0x51 [nvidia]
[4297194.961000]  [<e0e9fef6>] _nv001740rm+0x12/0x18 [nvidia]
[4297194.962000]  [<e0e82f4b>] _nv002889rm+0x33/0xa0 [nvidia]
[4297194.963000]  [<e0e82f82>] _nv002889rm+0x6a/0xa0 [nvidia]
[4297194.964000]  [<e0ea795d>] _nv001201rm+0x3d/0x618 [nvidia]
[4297194.964000]  [<e0ea7b43>] _nv001201rm+0x223/0x618 [nvidia]
[4297194.965000]  [<c015de57>] unmap_page_range+0xe7/0x120
[4297194.966000]  [<e0ea69f7>] rm_ioctl+0x23/0x38 [nvidia]
[4297194.967000]  [<e10afc70>] nv_kern_ioctl+0x369/0x3f3 [nvidia]
[4297194.968000]  [<c0104629>] die+0x9/0x190
[4297194.968000]  [<c0185153>] do_ioctl+0x93/0xa0
[4297194.968000]  [<c0104629>] die+0x9/0x190
[4297194.968000]  [<c018533b>] vfs_ioctl+0x6b/0x230
[4297194.968000]  [<c0104629>] die+0x9/0x190
[4297194.968000]  [<c0185588>] sys_ioctl+0x88/0xa0
[4297194.968000]  [<c0104629>] die+0x9/0x190
[4297194.969000]  [<c0103417>] sysenter_past_esp+0x54/0x75
[4297194.969000]  [<c0104629>] die+0x9/0x190
[4297194.969000] Trying to fix it up, but a reboot is needed

---

### Post by clee991 on 2006-10-03
me 3 !!

Exactly the same hardware and same problem. Has anyone come up with a solution.

---

### Post by jbtito03 on 2006-11-02
Hi guys..

just switched from fedora to ubuntu. Have to say its quite a piece of a distro.....

Well... everything works fine, just the 3d acc is not working at all.

I am using the legacy drivers, xorg.conf has the "nvidia" driver string and at reboot i see the nvidia logo. But, for example, the screensavers dont work at all...

In one forum thread i read something about nvidifb... so i modprobed it.. and now my lsmod says:

Module Size Used by
nvidiafb 58012 0
i2c_algo_bit 9480 1 nvidiafb
nls_utf8 2304 1
nls_cp437 6016 1
vfat 13440 1
fat 54556 1 vfat
binfmt_misc 11784 1
nfsd 231844 13
exportfs 6016 1 nfsd
lockd 65800 2 nfsd
sunrpc 160188 8 nfsd,lockd
cpufreq_userspace 4372 0
cpufreq_stats 5892 0
freq_table 4996 1 cpufreq_stats
cpufreq_powersave 2048 0
cpufreq_ondemand 6944 0
cpufreq_conservative 7200 0
video 16644 0
tc1100_wmi 7428 0
sbs 15776 0
sony_acpi 5516 0
pcc_acpi 13184 0
i2c_ec 5376 1 sbs
hotkey 10660 0
dev_acpi 11140 0
button 7056 0
battery 10756 0
container 4736 0
ac 5892 0
asus_acpi 16792 0
sg 35356 0
sd_mod 21648 2
ipv6 257632 21
dm_mod 60088 4
md_mod 78740 0
lp 11972 0
nvidia 3931148 8
tsdev 8256 0
usb_storage 73408 1
scsi_mod 141320 3 sg,sd_mod,usb_storage
af_packet 21768 2
snd_via82xx 28696 1
gameport 15368 1 snd_via82xx
snd_ac97_codec 96672 1 snd_via82xx
snd_ac97_bus 2432 1 snd_ac97_codec
snd_mpu401_uart 8704 1 snd_via82xx
snd_pcm_oss 46080 0
snd_pcm 80520 3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc 10504 2 snd_via82xx,snd_pcm
snd_mixer_oss 18560 1 snd_pcm_oss
snd_seq_dummy 4100 0
snd_seq_oss 34304 0
snd_seq_midi 9088 0
snd_rawmidi 25600 2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event 7808 2 snd_seq_oss,snd_seq_midi
snd_seq 53360 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 23172 2 snd_pcm,snd_seq
snd_seq_device 8972 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
libusual 15632 1 usb_storage
parport_pc 36132 1
parport 37320 2 lp,parport_pc
i2c_viapro 8980 0
snd 55428 13 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_pcm _oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi ,snd_seq,snd_timer,snd_seq_device
psmouse 40072 0
shpchp 40856 0
pci_hotplug 31284 1 shpchp
usbhid 42464 0
i2c_core 22288 4 nvidiafb,i2c_algo_bit,i2c_ec,i2c_viapro
via_agp 10368 1
agpgart 33456 2 nvidia,via_agp
soundcore 9952 1 snd
rtc 12596 0
serio_raw 7300 0
evdev 10496 1
pcspkr 3072 0
floppy 60676 0
via_rhine 23940 0
mii 6016 1 via_rhine
ext3 138632 2
jbd 55700 1 ext3
ehci_hcd 32520 0
uhci_hcd 23176 0
usbcore 130304 6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
ide_generic 1536 0
ide_disk 17664 4
ide_cd 32416 1
cdrom 37792 1 ide_cd
via82cxxx 9604 0 [permanent]
generic 4868 0
thermal 14600 0
processor 26028 1 thermal
fan 5124 0
fbcon 40480 0
tileblit 2944 1 fbcon
font 8448 1 fbcon
bitblit 6272 1 fbcon
softcursor 2432 1 bitblit
vesafb 8348 0
capability 5000 0
commoncap 7808 1 capability

but still... no 3d....

can someone help... pleaseee....

Distro... edgy elf 6.10

bye

---

### Post by SharpBlade on 2006-11-08
Hello,

I am experiencing the same problems as you guys.  My config is Dapper + NVIDIA TNT2.

What I did to get 3D acceleration:
-Using Synaptic, installed package **nvidia-glx-legacy**.
-Using Synaptic, removed the package including the generic nvidia driver.
-Ran **nvidia-glx-config enable** from a terminal window:
```
sudo nvidia-glx-config enable
```
-Replaced "**nv**" by "**nvidia**" as the value for the video driver in xorg.conf.
-Commented out **Load "DRI"** in xorg.conf.
-Restart X server (Ctrl-Alt-Back arrow).
-Start Planet Penguin from a terminal window:
```
ppracer
``` -> X server hangs after pressing a key from the intro screen of ppracer, also the mouse is disabled.  I am then forced to restart the X server to recover.

It seems though that the 3D acceleration is well installed as the command **glxgears** runs without any problem (it displays the rotating gears as you would expect).  Note: it returned around 270 fps for my configuration when I entered the command **glxgears -printfps** from a terminal window:
```
glxgears -printfps
```


Unlike xfctr, I forgot to run **dmesg** to check whether or not any error had been thrown.  On the other hand, I browsed through file **/var/logXorg.0.log**.  I am not sure it is of any help but here are a few things I came across:


-In the middle of file /var/logXorg.0.log, the following messages can be found:
[b](II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy[/b]


-There are a couple of error messages regarding /dev/wacom.


-The last few lines of file /var/logXorg.0.log:
[b]AUDIT: Wed Nov  8 22:27:57 2006: 8827 X: client 2 rejected from local host
AUDIT: Wed Nov  8 22:27:57 2006: 8827 X: client 4 rejected from local host
AUDIT: Wed Nov  8 22:27:57 2006: 8827 X: client 3 rejected from local host
AUDIT: Wed Nov  8 22:27:57 2006: 8827 X: client 2 rejected from local host[/b]


Has anybody moved a little closer to the resolution?

---

