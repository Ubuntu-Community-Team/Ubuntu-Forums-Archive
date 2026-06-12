---
title: "Dell Inspiron 15R 5520 Wireless Device Not Detected"
date: 2012-06-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by samrit on 2012-06-25
I bought dell inspiron 5520 15R last week and i am a newbie in unbuntu platform.  i installed win7 as well as ubuntu 12.04 (64BIT). But my wireless device is not detected in ubuntu while it is working fine in windows os. 
my wireless device is : dell wireless 1704 802.11B 2.4GHZ . is this the compatible problem with ubuntu. what would be the solution. do i need to isntall another version of ubutnu..

---

### Post by samrit on 2012-06-25
I bought dell inspiron 5520 15R last week and i am a newbie in unbuntu platform.  i installed win7 as well as ubuntu 12.04 (64BIT). But my wireless device is not detected in ubuntu while it is working fine in windows os. 
my wireless device is : dell wireless 1704 802.11B 2.4GHZ . is this the compatible problem with ubuntu. what would be the solution. do i need to isntall another version of ubutnu..

---

### Post by cariboo on 2012-06-25
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Bucky Ball on 2012-06-25
Welcome.

FYI: Duplicate posting is against forum rules. I have asked mods to merge your two threads. ;)

> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.

Like he said! Cariboo beat me to it ...

---

### Post by necrom on 2012-06-26
> **samrit said:**
> I bought dell inspiron 5520 15R last week and i am a newbie in unbuntu platform.  i installed win7 as well as ubuntu 12.04 (64BIT). But my wireless device is not detected in ubuntu while it is working fine in windows os. 
my wireless device is : dell wireless 1704 802.11B 2.4GHZ . is this the compatible problem with ubuntu. what would be the solution. do i need to isntall another version of ubutnu..

I have got this problem too. Please help me.:confused:

---

### Post by wildmanne39 on 2012-06-26
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Frosch09 on 2012-06-29
Hi wildmanne39

I have the same problem on a new Dell Inspiron 15R 5520. Here are my results from the commands you sent: 

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux fdw2012 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux
``````
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:056a]
    Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
    Subsystem: Dell Device [1028:0016]

``````
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:648d Microdia 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. 

``````
lo        no wireless extensions.

eth0      no wireless extensions.

``````
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
```
Module                  Size  Used by
parport_pc             32114  0 
rfcomm                 38139  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52516  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
fglrx                2909855  0 
snd_timer              28931  2 snd_pcm,snd_seq
dell_laptop            17767  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14098  1 dell_laptop
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
rts5139               279622  0 
mei                    36570  0 
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               67203  0 
soundcore              14635  1 snd
psmouse                72919  0 
videodev               86588  1 uvcvideo
wmi                    18744  1 dell_wmi
i915                  414655  2 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
lp                     17455  0 
video                  19068  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
serio_raw              13027  0 
parport                40930  3 parport_pc,ppdev,lp
mac_hid                13077  0 
r8169                  56321  0 

```Thanks for your help.

---

### Post by Bucky Ball on 2012-06-29
@Frosch09;

Welcome,

Please post a new thread with a descriptive title and an explanation of your problem rather than hijacking this one. You will get more help that way. Just gets confusing with two OPs. ;)

---

### Post by wildmanne39 on 2012-06-29
Hi Frosch09, post a link here to the new thread and I will see if I can help, but I have been looking for a driver for that device and I have not found one yet.
Thanks

---

### Post by samrit on 2012-07-02
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you



thanks for your reply. i am still can't find the solution. 

when i execute the commands the result are the same what friend "Frosch09" have already posted.. if u can find please share..

---

### Post by Frosch09 on 2012-07-02
Here is the new thread as suggested by wildmanne39 and Bucky Ball: 

[http://ubuntuforums.org/showthread.php?t=2014096](http://ubuntuforums.org/showthread.php?t=2014096)

---

