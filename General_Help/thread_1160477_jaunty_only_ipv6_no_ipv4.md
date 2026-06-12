---
title: "jaunty only ipv6 no ipv4?"
date: 2009-05-15
forum: General Help
---

### Post by tacutu on 2009-05-15
Hi all,
I'm trying to configure 9.04 on my brand new laptop but I can't seem to get it to connect to the net. Neither the wireless nor the wired network work.

ifconfig tells me that the network interfaces have only inet6 addresses, no ipv4. Is there any way to force ipv4 on these interfaces? I tried searching the forums but I found nothing useful.

TIA.

---

### Post by TheExplorer on 2009-05-15
Could you please be more specific about your system. Do you have network-manager up and running? Did you try to tell it your network configuration?

---

### Post by tacutu on 2009-05-15
hi.
yes, i have network manager running and trying to connect to the router, but eventually giving up. I have dhcp on the router, which works fine for a 2nd computer running Ubuntu 8.04 (for both wired and wireless)

---

### Post by marche96 on 2009-06-08
Having the same issue here.
Here's the output of lsmod:

```
Module                  Size  Used by
cbc                    11648  231 
aes_i586               15744  232 
aes_generic            35880  1 aes_i586
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
kvm                   152640  0 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
arc4                    9856  2 
ecb                    10752  3 
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
ath9k                 263224  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              217208  1 ath9k
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7233756  38 
uvcvideo               63240  0 
psmouse                61972  0 
cfg80211               38032  1 mac80211
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                42696  1 nvidia
video                  25360  5 
serio_raw              13316  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
shpchp                 40212  0 
led_class              12036  1 ath9k
usb_storage            82880  0 
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

This is the part that got me; straight from the output of dmesg
```
wlan0: no IPv6 routers present

```
From what I hear this is built into the kernel; which was a stupid decision in my opinion, considering I don't have the cash to buy a IPv6 router, or I can't buy my school and local shops IPv6 routers. Dd I have to downgrade just to get the option of IPv6 in a kernel module? I just reformatted and made my laptop cozy.

---

### Post by Iowan on 2009-06-08
> **marche96 said:**
> 
From what I hear this is built into the kernel; which was a stupid decision in my opinion, considering I don't have the cash to buy a IPv6 router.I don't own a IPv6 router either -  yet I'm happily using Ubuntu.  Jaunty is NOT IPv6-only... 

I had a similar [problem]("http://ubuntuforums.org/showthread.php?t=1156441") on my laptop.  You can see if what fixed mine fixes yours. My older DHCP server didn't know what to do with rfc3442 line - so it didn't do ANYTHING.  Otherwise, could you post results of **lshw -C network**? It'd also be useful to see results of **sudo dhclient** (might need to select interface).

---

### Post by alphacrucis2 on 2009-06-08
> **marche96 said:**
> Having the same issue here.
Here's the output of lsmod:

```
Module                  Size  Used by
cbc                    11648  231 
aes_i586               15744  232 
aes_generic            35880  1 aes_i586
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
kvm                   152640  0 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
arc4                    9856  2 
ecb                    10752  3 
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
ath9k                 263224  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              217208  1 ath9k
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7233756  38 
uvcvideo               63240  0 
psmouse                61972  0 
cfg80211               38032  1 mac80211
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                42696  1 nvidia
video                  25360  5 
serio_raw              13316  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
shpchp                 40212  0 
led_class              12036  1 ath9k
usb_storage            82880  0 
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

This is the part that got me; straight from the output of dmesg
```
wlan0: no IPv6 routers present

```
From what I hear this is built into the kernel; which was a stupid decision in my opinion, considering I don't have the cash to buy a IPv6 router, or I can't buy my school and local shops IPv6 routers. Dd I have to downgrade just to get the option of IPv6 in a kernel module? I just reformatted and made my laptop cozy.

IPv4 is built in to the kernel too. Your problem has nothing to do with IPv6.

---

