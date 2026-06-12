---
title: "Sound is _not_leaving them speakers, despite lots of troubleshooting - please help..."
date: 2006-09-02
forum: Desktop Environments
---

### Post by motin on 2006-09-02
The sound has suddenly stopped reaching my pc speakers... One week ago it worked just fine, and then it stopped, possibly after an update, I don't know, but I know that I have not been trying to manipulate sound or midi related parts of my system.* 

Conditions (after I have killed the esd-process, which starts up everytime I start the computer - at the same time disabling xmms to use the sound device which is seen as busy then - despite autospawn=0):
- XMMS, and for example "cat /dev/urandom > /dev/dsp", performs just as if sound was generated, . 
- fuser /dev/dsp and lsof /dev/dsp generates an empty output
- all channels are set to "on" in the alsamixer and the volumes are turned up
- sound works great in XP when booting into windows instead
- it doesnt matter if i try to play the sound (in xmms) through alsa, oss or jack
- nowhere is there any switch to use digital sound or similar to be found
- IEC958 is not selected
- there is only one soundcard installed ("alsamixer -c 1" fails)
- an "strace -p `pidof cat`" while running "cat /dev/urandom > /dev/dsp", shows a steady stream of reads and writes in an orderly steady and fairly slowly manner
- booting with an older kernel (the one used before the latest updates) does not make any difference
- update: sound is working with headphones plugged in! but still:
- no sound leaves the speakers (without the headphones...)

Please help, I am out of clues*. In windows I would have tried to uninstall the device in device manager and then reinstall it, but that for instance I do not know how to do in Linux... 

* Update: alankila mentioned this: [http://www.tigert.com/archives/2006/08/28/linux-sound-and-multimedia/](http://www.tigert.com/archives/2006/08/28/linux-sound-and-multimedia/) (that Line Jack Sense had something to do with it) and I  just remembered that I got this problem just by the same time I found the Line Jack Sense setting and (of course had to…) tried it, I just remembered. 

Thank you!

lsmod gives:
```
Module                  Size  Used by
snd_rtctimer            3372  0
ipt_TCPMSS              4640  1
ipt_tcpmss              2432  1
ipt_state               2016  1
bsd_comp                6272  0
ipt_MASQUERADE          3840  1
pppoe                  15712  0
pppox                   3816  1 pppoe
ppp_synctty            11872  1
n_hdlc                 10052  1
ppp_async              13280  0
crc_ccitt               2240  1 ppp_async
ppp_generic            33556  9 bsd_comp,pppoe,pppox,ppp_synctty,ppp_async
slhc                    7456  1 ppp_generic
binfmt_misc            13064  1
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
ppdev                   9668  0
i915                   21664  1
drm                    78484  2 i915
speedstep_centrino      8752  1
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
ip_nat_irc              2784  0
ip_nat_ftp              3552  0
ip_conntrack_irc        6992  1 ip_nat_irc
ip_conntrack_ftp        8176  1 ip_nat_ftp
ipt_LOG                 7392  7
iptable_mangle          2976  0
iptable_filter          3104  1
iptable_nat             8228  1
ip_nat                 20652  4 ipt_MASQUERADE,ip_nat_irc,ip_nat_ftp,iptable_nat
ip_tables              23744  8 ipt_TCPMSS,ipt_tcpmss,ipt_state,ipt_MASQUERADE,i pt_LOG,iptable_mangle,iptable_filter,iptable_nat
ip_conntrack           54136  8 ipt_state,ipt_MASQUERADE,ip_nat_irc,ip_nat_ftp,i p_conntrack_irc,ip_conntrack_ftp,iptable_nat,ip_nat
nfnetlink               6808  2 ip_nat,ip_conntrack
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   14496  1
fat                    55548  1 vfat
ipv6                  286976  26
dm_mod                 63256  1
md_mod                 76052  0
af_packet              24520  6
fuse                   41328  0
snd_emu10k1_synth       8096  0
snd_emu10k1           134756  1 snd_emu10k1_synth
snd_emux_synth         39968  1 snd_emu10k1_synth
snd_seq_virmidi         8384  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_hwdep               9952  2 snd_emu10k1,snd_emux_synth
snd_util_mem            4928  2 snd_emu10k1,snd_emux_synth
snd_seq_dummy           3908  0
snd_seq_oss            37216  0
snd_seq_midi            9600  0
snd_rawmidi            26848  3 snd_emu10k1,snd_seq_virmidi,snd_seq_midi
snd_seq_midi_event      7520  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                58160  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul ,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emu10k1,snd_emux_synth,snd _seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sr_mod                 17988  0
sbp2                   25060  0
scsi_mod              145960  2 sr_mod,sbp2
parport_pc             37988  0
lp                     12356  0
parport                39400  3 ppdev,parport_pc,lp
pcmcia                 41948  0
joydev                 10432  0
tsdev                   8032  0
8139cp                 24032  0
yenta_socket           30124  1
rsrc_nonstatic         14624  1 yenta_socket
ipw2200               113548  0
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211              38952  1 ipw2200
ieee80211_crypt         6528  1 ieee80211
hci_usb                18004  2
ieee80211_1_1_13       39880  0
ieee80211_1_1_13_crypt     7040  1 ieee80211_1_1_13
sdhci                  16096  0
8139too                29056  0
mii                     6176  2 8139cp,8139too
bluetooth              54084  7 rfcomm,l2cap,hci_usb
mmc_core               31816  1 sdhci
snd_intel8x0           35772  2
psmouse                40004  0
snd_ac97_codec        100224  2 snd_emu10k1,snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_ oss
snd_timer              26884  4 snd_rtctimer,snd_emu10k1,snd_seq,snd_pcm
serio_raw               7748  0
snd                    60004  18 snd_emu10k1,snd_emux_synth,snd_seq_virmidi,snd_ hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec ,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  3 snd_emu10k1,snd_intel8x0,snd_pcm
intel_agp              24700  1
agpgart                36784  3 drm,intel_agp
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
evdev                  10176  2
ext3                  148104  5
jbd                    65876  1 ext3
ide_generic             1504  0
ohci1394               37524  0
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               36104  0
uhci_hcd               35408  0
usbcore               139076  4 hci_usb,ehci_hcd,uhci_hcd
ide_cd                 35780  0
cdrom                  41408  2 sr_mod,ide_cd
ide_disk               19136  8
generic                 5124  0
piix                   11652  1
thermal                13768  0
processor              26888  2 speedstep_centrino,thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

```

Edit: About the concept of removing from Device Manager as in windows:
<alankila> that concept doesn't really exist on linux
<alankila> it is always possible to use the rmmod command to remove individual module files from the kernel provided nothing is using them
<alankila> if you then issue modprobe with the same driver name, the kernel would attempt to reload it. The results of the operation usually appear in dmesg, usually as short acknowledgement that something occured, like a hardware was found
<alankila> it is unlikely to solve anything.
Thanks alankila for clearing that out!

PS Earlier I posted in the Hardware-section, Video & Sound ([http://www.ubuntuforums.org/showthread.php?t=247031)](http://www.ubuntuforums.org/showthread.php?t=247031)), but I guess this is the correct forum since that forum was just for "Problems with hardware not being detected or supported during or after install."

Partial abstract of IRC chat with helpful alankila, in case it could help someone else:
```
<alankila> My best bet is still that the error is related to mixer settings. What exactly is wrong is harder to say. There is a finite number of those settings. For Creative cards, trying to destroy ALSA's stored mixer state and allowing it to reinitialize it at boot can help.
<motin> alankila: great hint!
<alankila> the mixer state can be at /etc/alsactl.state or /var/lib/alsa/asound.state
<motin> yeah it really acts like a mixer problem
<alankila> it's hard to destroy because the Linux system tends to store current settings to it at end of normal shutdown.
<motin> i'll shutdown gdm and do it from there
<alankila> one way to prevent this process is to change the file /etc/init.d/alsa-utils to say "exit 0" after the #! line
<motin> or just backup, delete and restart gdm? ctrl alt backspace? you think that would do it?
<alankila> this prevents the init scripts from fiddling with asound.state, allowing you to reboot computer and get rid of whatever stored settings you had
<alankila> if that allows you to make it work, then you can make it work, remove the exit 0 command, and try shutting down and rebooting and see whether it comes up working next time. Or it might not do anything. Hard to know for sure.
<alankila> It's possible someone made a mistake in the linux kernel and your hardware is temporarily nonworking due to that.
<alankila> especially if you don't know what you updated recently.
<motin> alankila: I was on a 3 month trip and just updated everything that was available
<motin> hey...
<motin> i should try booting into an older kernel
<alankila> if it's possible, yes, that's a very good idea.
<motin> i'll do that before attempting to restore the alsa mixer state
<motin> see you in a bit
<motin> you have been very helpful!
```

---

### Post by motin on 2006-09-02
SOLVED

The Line Jack Sense thing gave me a good hint in what was wrong. Besides the Line Jack Sense and Mic Boost settings in the mixer, there is actually one additional one called Headphone Jack Sense not shown, accessible through alsamixergui. 

So what happened was I had added the Line JS switch earlier, resulting in no sound, then while troubleshooting used the alsamisxergui to switch on all channels - thus unknowingly enabled the Headphone JS switch (also disabling sound to other than headphones), and then switching the Line JS off from the Ubuntu mixer, resulting in ruling out Line JS as the error. 

Aaah... But know it works, and I am off again to work with the company of Herbie Hancock

Thank you alankila and stock on IRC for all help!

---

