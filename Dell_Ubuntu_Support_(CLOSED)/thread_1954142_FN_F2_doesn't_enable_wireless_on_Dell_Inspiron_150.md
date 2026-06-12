---
title: "FN F2 doesn't enable wireless on Dell Inspiron 1501"
date: 2012-04-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jhogan on 2012-04-07
I recently installed Precise on my 1501 and the wireless light is not lit. When I type FN F2, nothing happens. This laptop had been running Vista before for several years and the wireless was near perfect. I've checked the BIOS settings to make sure that wireless is enable. I followed the instructions here [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access) to get the drivers installed correctly. The driver installation seems fine. It just appears that the network card is turned off.

Here is the output from iwconfig if that helps:

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

eth0      no wireless extensions.


Thanks in advance.

---

### Post by mikewhatever on 2012-04-07
Have you verified which driver is actually loaded?

How about the outputs of the following:

lspci -nnk | grep -iA2 net

rfkill list all

lsmod

---

### Post by jhogan on 2012-04-07
> **mikewhatever said:**
> Have you verified which driver is actually loaded?

How about the outputs of the following:

lspci -nnk | grep -iA2 net

rfkill list all

lsmod

Thanks for responding.

lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
        Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
        Kernel driver in use: b43-pci-bridge
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
        Subsystem: Dell Device [1028:01f5]
        Kernel driver in use: b44


rfkill list all
1: dell-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no


lsmod
Module                  Size  Used by
b43                   342643  0
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
nls_utf8               12493  1
isofs                  39553  1
des_generic            21191  0
md4                    12523  0
bnep                   17830  2
rfcomm                 38139  0
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0
ppdev                  12849  0
nls_iso8859_15         12664  1
cifs                  257905  2
snd_hda_codec_idt      60251  1
snd_hda_intel          32765  3
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dell_wmi               12601  0
joydev                 17393  0
sparse_keymap          13658  1 dell_wmi
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                733693  3
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop            13671  0
soundcore              14635  1 snd
sp5100_tco             13495  0
dcdbas                 14098  1 dell_laptop
psmouse                72846  0
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
serio_raw              13027  0
k8temp                 12905  0
i2c_piix4              13093  0
drm                   197692  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
video                  19068  0
mac_hid                13077  0
wmi                    18744  1 dell_wmi
shpchp                 32325  0
ati_agp                13242  0
arc4                   12473  2
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
b44                    31364  0
sdhci_pci              18324  0
sdhci                  28241  1 sdhci_pci
pata_atiixp            12999  1
ssb                    50691  2 b43,b44

---

### Post by mikewhatever on 2012-04-08
The only problem I can see is the lines in red:

```
rfkill list all
1: dell-wifi: Wireless LAN
[COLOR="Red"]Soft blocked: yes
Hard blocked: yes[/COLOR]
3: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

```

...make sure wifi isn't disabled in the BISO, and try unblocking it with the following:

```
rfkill unblock all
```

Hope that works.

---

### Post by jhogan on 2012-04-08
When I ran it as root, that did manage to unblock the device - at least as far as rfkill was concerned.

1: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

However, wicd still reports "No wireless networks found." and there are no wireless networks listed in the graphical desktop network manager in Unity. I'm going to try the steps in the top rated answer here [http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working](http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working) and see what happens.

---

### Post by jhogan on 2012-04-08
The instructions at that link didn't work. Basically, all I ended up doing was:

Commenting out  "blacklist bcm43xx" from /etc/modprobe.d/blacklist.conf

Installed b43-fwcutter

Rebooted

---

### Post by jhogan on 2012-04-25
Can anyone recommend a good wireless expresscard for my Inspiron with good Linux support. I noticed there are some USB ones but I don't want a fragile stick stuck in my laptop. I think it would eventually get broken. There don't seem to be very many wireless expresscards out there.

---

### Post by SeijiSensei on 2012-04-25
> **jhogan said:**
> Can anyone recommend a good wireless expresscard for my Inspiron with good Linux support.

I have a 640m with an [Intel 3945ABG]("http://www.txcesssurplus.com/servlet/the-2799/Intel-Pro-Wireless-3945/Detail") card.  It's worked flawlessly for years now. I specifically paid to upgrade to the Intel card because I knew the drivers were open-sourced and well-maintained.

However there are [reports]("http://en.community.dell.com/support-forums/laptop/f/3518/p/18362254/18485240.aspx#18485240") that a 1501 won't boot with this card.  However the [4965]("http://www.ebay.com/itm/Intel-Wireless-WiFi-4965AGN-MM2-Card-4-Dell-Inspiron-1420-1501-1520-1521-/320786601190") [reportedly]("http://ubuntuforums.org/showthread.php?t=1582039") works in a 1501.  Apparently the 1501 runs an AMD motherboard which isn't happy with the 3945.  My 640m is all-Intel.

---

