---
title: "Mouse acting a bit weird..."
date: 2009-05-25
forum: General Help
---

### Post by Crafty Kisses on 2009-05-25
Alright guys so I bought a Razer Lachesis mouse and it's working as of now but I noticed when I reboot, the mouse doesn't work until I unplug it and plug it back into a USB port. Now I'm thinking it could be a module problem. I'm not sure though, here is my "lsmod" when I didn't unplug the mouse upon reboot:
```
usbhid                 47040  0 
ipt_MASQUERADE         11520  0 
xt_DSCP                12032  0 
xt_multiport           11904  0 
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
ipt_REJECT             11776  1 
ipt_LOG                14468  8 
xt_limit               11140  8 
xt_tcpudp              11776  13 
xt_state               10624  6 
ipt_addrtype           11136  0 
ip6table_filter        11264  1 
ip6_tables             29712  1 ip6table_filter
nf_nat_irc             10752  0 
nf_conntrack_irc       14648  1 nf_nat_irc
nf_nat_ftp             11520  0 
nf_conntrack_ftp       17592  1 nf_nat_ftp
lp                     19588  0 
parport                49584  2 ppdev,lp
iptable_nat            14724  0 
nf_nat                 30100  4 ipt_MASQUERADE,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      24216  9 iptable_nat,nf_nat
nf_conntrack           84752  9 ipt_MASQUERADE,xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         10496  1 nf_conntrack_ipv4
iptable_mangle         11520  0 
snd_hda_intel         557364  3 
iptable_filter         11392  1 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
ip_tables              28304  3 iptable_nat,iptable_mangle,iptable_filter
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
x_tables               31624  12 ipt_MASQUERADE,xt_DSCP,xt_multiport,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,iptable_nat,ip_tables
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               8123768  36 
pcspkr                 11136  0 
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
usb_storage            94912  0 
forcedeth              68368  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```
Now here is my "lsmod" once I unplugged it and plugged it back in:
```
Module                  Size  Used by
usbhid                 47040  0 
ipt_MASQUERADE         11520  0 
xt_DSCP                12032  0 
xt_multiport           11904  0 
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
ipt_REJECT             11776  1 
ipt_LOG                14468  8 
xt_limit               11140  8 
xt_tcpudp              11776  13 
xt_state               10624  6 
ipt_addrtype           11136  0 
ip6table_filter        11264  1 
ip6_tables             29712  1 ip6table_filter
nf_nat_irc             10752  0 
nf_conntrack_irc       14648  1 nf_nat_irc
nf_nat_ftp             11520  0 
nf_conntrack_ftp       17592  1 nf_nat_ftp
lp                     19588  0 
parport                49584  2 ppdev,lp
iptable_nat            14724  0 
nf_nat                 30100  4 ipt_MASQUERADE,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      24216  9 iptable_nat,nf_nat
nf_conntrack           84752  9 ipt_MASQUERADE,xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         10496  1 nf_conntrack_ipv4
iptable_mangle         11520  0 
snd_hda_intel         557364  5 
iptable_filter         11392  1 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
ip_tables              28304  3 iptable_nat,iptable_mangle,iptable_filter
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss
x_tables               31624  12 ipt_MASQUERADE,xt_DSCP,xt_multiport,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,iptable_nat,ip_tables
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               8123768  36 
pcspkr                 11136  0 
snd                    78792  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
usb_storage            94912  0 
forcedeth              68368  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```
I'd also like to give you the results of:
```
modprobe -l | grep mouse
```
Anyway, here are the results of that command:
```
kernel/drivers/usb/misc/idmouse.ko
kernel/drivers/input/mouse/appletouch.ko
kernel/drivers/input/mouse/bcm5974.ko
kernel/drivers/input/mouse/psmouse.ko
kernel/drivers/input/mouse/sermouse.ko
kernel/drivers/input/mouse/vsxxxaa.ko
kernel/drivers/input/mouse/gpio_mouse.ko
kernel/drivers/hid/usbhid/usbmouse.ko
```
So that's all the information I can really provide, if you need more information I'll be glad to provide it. As I stated before I think it's a module that's not being loaded at start, I just need to find what kernel module that is in order for it to boot at start.

---

### Post by Crafty Kisses on 2009-05-26
Sorry for the bump.

---

