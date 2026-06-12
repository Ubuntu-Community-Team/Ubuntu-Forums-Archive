---
title: "/dev/dsp disappeared ?"
date: 2005-03-08
forum: Desktop Environments
---

### Post by Ste on 2005-03-08
```
stephen@godspeed:~ $ vlc
VLC media player 0.8.1 Janus
[00000269] mpeg_audio decoder: MPGA channels:2 samplerate:48000 bitrate:128
[00000270] oss audio output error: cannot open audio device (/dev/dsp)
[00000270] main audio output error: couldn't find a filter for the conversion
[00000270] main audio output error: couldn't set an output pipeline

```

The power went in my house and when I reboot and try and watch videos or use xmms the story is almost similar. I can switch xmms to ALSA but I'd prefer not to.

Also can't reinstall the fglrx package for whatever reason but I'd like to get the oss eror sorted first. Can anyone shed any light ?

ALso an lsmod
```
stephen@godspeed:~ $ lsmod
Module                  Size  Used by
rfcomm                 36252  0
l2cap                  24324  5 rfcomm
bluetooth              46340  4 rfcomm,l2cap
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
ipt_limit               2688  7
iptable_mangle          2944  1
ipt_LOG                 6656  4
ipt_MASQUERADE          3584  0
iptable_nat            24648  1 ipt_MASQUERADE
ipt_TOS                 2560  5
ipt_REJECT              6528  0
ip_conntrack_irc       71856  0
ip_conntrack_ftp       72624  0
ipt_state               2048  4
ip_conntrack           43668  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          3840  1
ip_tables              17408  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
button                  6800  0
ac                      4996  0
battery                10244  0
af_packet              20744  2
emu10k1_gp              3840  0
gameport                4608  1 emu10k1_gp
snd_emu10k1            81668  2
snd_rawmidi            22944  1 snd_emu10k1
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         64608  1 snd_emu10k1
snd_pcm                84872  2 snd_emu10k1,snd_ac97_codec
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
snd                    50276  11 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer,snd_hwdep
soundcore               9824  1 snd
3c59x                  37160  0
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
joydev                  9408  0
usbhid                 29376  0
uhci_hcd               30224  0
usbcore               107384  3 usbhid,uhci_hcd
via_agp                 9216  1
agpgart                31784  1 via_agp
parport_pc             34372  1
md                     43728  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
lp                     10792  0
parport                33480  2 parport_pc,lp
tsdev                   7488  0
evdev                   9088  0
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
mousedev               11160  1
psmouse                19336  0
ext3                  120200  1
jbd                    53912  1 ext3
ide_generic             1664  0
via82cxxx              12956  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   26164  628
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
crc32                   4352  1 fbcon
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

```

---

### Post by alastair on 2005-03-08
Not much of an idea really ...

but you could try sticking the module in and see what happens i.e.

sudo modprobe snd_pcm_oss

for instance. Perhaps "tail -f" the /var/log/syslog, and see what's printed.

On the other hand, if you can get ALSA to work then use that. OSS is deprecated anyway, and will disappear eventually.

---

### Post by Ste on 2005-03-09
modprobe got it going but after restart it's back to the same.
Is there anyway I can start it at boot ?

---

### Post by gyaresu on 2005-03-11
[QUOTE=Ste]modprobe got it going but after restart it's back to the same.
Is there anyway I can start it at boot ?[/QUOTE]

I got here via a similar Debian problem.
It's all about the 'udev' rather than 'devfs' way of doing things.

I am getting around this at the moment by inserting snd_pcm_oss in the /etc/modules file. That should insert the driver and create the device nodes 'dsp' 'adsp' 'audio' and 'mixer' into /dev/ at start up. 

That has got to be the dodgy way of doing it because it's the oss sound system and not alsa.
But at 3am it'll do.

Thanks be to alastair.

regards

---

