---
title: "[PICS] Dell Inspiron 2200 (WiFi PROBS)"
date: 2010-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by retro_killa on 2010-02-10
I just got my CD in the mail from Ubuntu 9.10 32bit. I did a clean install wiped out the windows OS & I now have Linux on this laptop. The internet works when the cable is plugged into the Ethernet port but when plunged in the built in WiFi will not find or show anything :( 

I am having a heck of a time getting my WiFi set up please enjoy the screen shots

So this is what I did 

[[IMG]http://img682.imageshack.us/img682/996/screenshotci.png[/IMG]](http://img682.imageshack.us/i/screenshotci.png/)

then 

[[IMG]http://img682.imageshack.us/img682/8937/screenshothardwaredrive.png[/IMG]](http://img682.imageshack.us/i/screenshothardwaredrive.png/)

& then I restarted / booted ubuntu 

[[IMG]http://img534.imageshack.us/img534/4308/screenshotrestart.png[/IMG]](http://img534.imageshack.us/i/screenshotrestart.png/)

Still not able to use my WiFi :/ & yes I happen to have a wireless router that is working on on a windows XP laptop with out any probs.. 

HELP PLZ !!!! 



I went ahead & did this just to help you all help me ;) 
lsmod
nm-tool
lshw -C Network

```
warren@Dell-Inspiron-2200:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
arc4                    1660  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
ecb                     2524  2 
pcmcia                 36808  0 
snd_seq_dummy           2656  0 
dell_wmi                2564  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
b43                   122168  0 
mac80211              181140  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
psmouse                56500  0 
serio_raw               5280  0 
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
hid_a4tech              2652  0 
usbhid                 38208  0 
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
ssb                    35364  1 b43
e100                   32420  0 
mii                     5212  1 e100
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
warren@Dell-Inspiron-2200:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:90:4B:E6:E1:11

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:14:22:C4:57:50

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


warren@Dell-Inspiron-2200:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:19 memory:dfdfe000-dfdfffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:c4:57:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.2 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:dfdfd000-dfdfdfff ioport:df40(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:e6:e1:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
warren@Dell-Inspiron-2200:~$ lshw -C Network

```

---

### Post by retro_killa on 2010-02-10
help please :o

---

### Post by retro_killa on 2010-02-10
bump bump

---

### Post by coffeeaddict22 on 2010-02-10
Hi,
Looks like your card is disabled.  At a guess, there's a hardware switch on your machine somewhere, and it's off.

Nice screenshots, by the way!

---

### Post by ownasaur on 2010-02-11
I own a 2200, and I have to say everything works fine.... after I installed all the updates. 

Good luck!

---

### Post by retro_killa on 2010-02-11
> **coffeeaddict22 said:**
> Hi,
Looks like your card is disabled.  At a guess, there's a hardware switch on your machine somewhere, and it's off.

Nice screenshots, by the way!

I have no clue where the switch would be on this laptop :-({|=

> **ownasaur said:**
> I own a 2200, and I have to say everything works fine.... after I installed all the updates. 

Good luck!

Do you happen to know where the on/off switch for the WiFi is on the laptop ?

---

### Post by ownasaur on 2010-02-11
I don't see a physical switch anywhere in this machine, it should be on by default... just run the updates and try loading the wi-fi drivers after.

---

### Post by retro_killa on 2010-02-11
> **ownasaur said:**
> I don't see a physical switch anywhere in this machine, it should be on by default... just run the updates and try loading the wi-fi drivers after.

I ran the updates & the WiFi is still off :(

---

### Post by retro_killa on 2010-02-11
Help me please.... I would like to get this laptop online via WiFi.

PS... I am on a different laptop right now running Windows 7 & I hate it. 

So please help me thanks

:)

---

### Post by SoFl W on 2010-02-11
On my machine if I press and hold the key with the blue "Fn" and press the "F2" key that toggles Wifi.  (Press it once and wait a SEVERAL seconds to see if WiFi starts.)

Check to see if the broadcom drivers are in /lib/firmware/   FIRST
See if this thread helps you:
[http://ubuntuforums.org/showthread.php?t=759100](http://ubuntuforums.org/showthread.php?t=759100)

---

### Post by pfranks on 2010-02-12
Forgive me for asking the obvious questiion, but are you sure you are trying to load the correct drivers? In my experience Dell machines usually use Broadcom for the wired LAN and either a Dell own brand or Intel for the WiFi.

I went and checked the Inspiron 2200 driver downloads on the Dell site (for XP) and I don't see any Broadcom drivers on a quick check.

---

### Post by nipsnertz on 2010-02-12
I also have a Dell Inspiron 2200 with Ubuntu 9.1 loaded a few days ago.  Like you, I cannot get the built in wifi card to work but I have seen forum threads that show that others have been able to get this laptop wifi working.   This laptop does have a hardkey sequence for turning the wifi on and off (ALT-F2 )  but this does not work with Ubuntu.  Also, there is a BIOS setting to turn Wifi on and off at startup but mine is set for on and I expect that unless you changed your bios settings your bios are probably set for on also.

The windows driver for this laptop is the    bcmwl5.inf       file which can be downloaded from Dell.  I installed this using ndiswrapper but I still cannot get my WIFI to work.  

Any help is appreciated.

---

### Post by coffeeaddict22 on 2010-02-13
Retro,
Just had another look.  You've done something odd, or you're running unusual hardware.  In lshw -C network, you've got two interfaces to the wireless, and that's a great way of making sure neither work.  Have you plugged in another card?

nips:  Need more info.  Ndiswrapper is usually no longer required, but can be used.  The command ```
nm-tool
``` will tell us most of what we need to know, but ```
lshw -C network
``` is also useful as a start point.  Run both in a terminal (Applications/Accessories/terminal), and post back the output (between CODE tags- the hash icon above will put them in your message).

Have a look at the wiki as well.  It's reasonably up to date (there's a bit in there that no longer applies, but it's still useful to know what steps are now automated):
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by nipsnertz on 2010-02-13
Thanks for your reply.  I ran the Ubuntu updates and now my WIFI works if I turn encription off.   I am still not able  to get WAP to work and  I need to use a  WAP network.   Some threads that I found seemed to say that WAP is not working with ndiswrapper  installed drivers.   Does anyone know a work-around.
 
Thanks

---

