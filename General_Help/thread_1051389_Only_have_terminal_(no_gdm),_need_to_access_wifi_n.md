---
title: "Only have terminal (no gdm), need to access wifi network"
date: 2009-01-26
forum: General Help
---

### Post by MatMan on 2009-01-26
I didn't know if this should go in hardware, desktop, or networks so I chucked it in general.

I was trying to fix a sound bug on my HP laptop which started after installing skype (but that is another story). I was using this guide

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

and apparently muffed it. There is a section:

(1) Remove these packages
Code:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
(2) Reinstall those same packages
Code:
sudo apt-get install linux-sound-base alsa-base alsa-utils

VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:
sudo apt-get install gdm ubuntu-desktop

##end

I didn't lose my desktop, I rebooted, now I lost my desktop. I have logged in to terminal, run 

sudo apt-get gdm ubuntu-desktop 

but to no avail. It gives "error can't retrieve files" (or similar) because I am not on a network (i suspect).

So I:
iwconfig

get:

wlan0     IEEE 802.11abgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:10:36:5E:95   
          Bit Rate=24 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=70/100  Signal level:-66 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

then 

iwconfig wlan0 ap 00:1C:10:36:5E:95

and get denied permission. So,

sudo iwconfig wlan0 ap 00:1C:10:36:5E:95

then retry 

sudo apt-get install gdm ubuntu-desktop

but still it can't retrieve the files.


How annoying. Anyone got ideas? Also, has anyone else has sound problems pop up after installing skype?

oh yeah, running Intrepid Ibex on a HP laptop DV2700.

cheerio,

mat.

---

### Post by x22 on 2009-01-26
my startup script looks like this (WEP)

ifconfig wlan0 up
iwconfig wlan0 essid chris
iwconfig wlan0 channel 11
iwconfig wlan0 mode managed
iwconfig wlan0 key 1234567890
iwconfig wlan0 key open
dhclient wlan0

---

### Post by MatMan on 2009-01-26
sorry for being a muppet, but is that what you type in at the terminal to make your wifi connect?

---

