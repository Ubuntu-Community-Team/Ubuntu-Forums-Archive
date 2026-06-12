---
title: "Vostro 1000 wifi switch kerfuffle"
date: 2012-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by d_fiumano on 2012-06-12
Greetings ladies & gentlepeoples! Upgraded to 12.04 recently & I'm having one little problem that no one seems to know exactly how to fix.

I'm not exactly a noob, but I'm no Sheldon Cooper either.

Anyhoo, after updating, I find that my wifi no longer works. I tried rfkill & it told me everything was on, but I can't switch my wifi on physically; i.e. pressing the **Function key & F2 key** simultaneously and/or at the same time.

I've googled it and checked in all the forums & NO ONE seems to give an exact answer as to why this is happening nor how to fix it.

This is rather frustrating and I kinda need my wifi to work.

Any help would be greatly appreciated and here are my specs just in case:

[B]Dell Vostro 1000 running Ubuntu 12.04 (Precise)
Kernel Linux 3.2.0-24-generic
GNOME 3.4.1
3.7gb RAM
AMD Athlon 64 X2 Processor[/B]

P.S. If anyone can tell me how to put Ice Cream Sandwich on the HP Touchpad WITHOUT any virtual box nonsense, that would be awesome too!!

---

### Post by mikewhatever on 2012-06-13
To help, we need some wifi related info from you. Can you post the outputs of the following from a terminal window:

ifconfig

lspci -nnk | grep -iA2 net

lsmod | grep -e wl -e b43 -e ssb

rfkill list all

---

### Post by d_fiumano on 2012-06-13
Ok, Here's my setup

**ifconfig**:
eth1      Link encap:Ethernet  HWaddr 00:1d:09:ba:14:e0  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feba:14e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:390283 (390.2 KB)  TX bytes:59887 (59.8 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8404 (8.4 KB)  TX bytes:8404 (8.4 KB)

**lspci --k | grep -e wl -iA2 net**:
lspci: invalid option -- '-'
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
[B]
lsmod | grep -e wl -e b43 -e ssb[/B]:
ssb                    52752  1 b44
wl                   2568210  0 
lib80211               14381  1 wl

**rfkill list all**:
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

Hope this means something and thanks a heap-load!!

---

### Post by mikewhatever on 2012-06-13
Thanks! I've screwed up a bit with the second command (see the edit above), but no worries.

---

### Post by d_fiumano on 2012-06-13
Well, it disconnected everything for a second, then reconnected back to my wired connection. As for wifi, still nothing and fn+f2 still doesn't work

---

### Post by mikewhatever on 2012-06-13
OK, I think that I see the problem now. Your NIC uses the b44 module which requires the ssb module. On the other hand, wl conflicts with ssb. In short, you need to use another wireless driver, b43. Please deactivate the Broadcom STA driver, reboot, and install the **firmware-b43-lpphy-installer** from the repositories.

If it doesn't work, post the outputs of the following again:
```
lspci --nnk | grep -iA2 net

lsmod | grep -e wl -e b43 -e ssb

rfkill list all
```

---

### Post by d_fiumano on 2012-06-17
Ok,** STILL** nothing. I removed & reinstalled the drivers and here's the terminal outputs:

**lspci --nnk | grep -iA2 net**
lspci: invalid option -- '-'
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file

**lsmod | grep -e wl -e b43 -e ssb**
ssb                    52752  1 b44
wl                   2568210  0 
lib80211               14381  1 wl

**rfkill list all**
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by mikewhatever on 2012-06-17
Hm..., I don't remember saying anything about reinstalling drivers. Which driver have you remove and reinstalled? Have you installed the package I suggested above?

PS: Instead of typing commands, copy/paste them.

---

### Post by d_fiumano on 2012-06-17
Ok, I uninstalled the previous broadcom driver, and installed the one you suggested. I rebooted and still no wifi

---

### Post by mikewhatever on 2012-06-17
Can you post the outputs again.

```
ifconfig

lspci -nnk | grep -iA2 net

lsmod | grep -e wl -e b43 -e ssb

rfkill list all
```

---

### Post by d_fiumano on 2012-06-21
Ok, sorry for the long response! Last week was pretty hectic. Anyhoo, here's my outputs:

**ifconfig**
eth1      Link encap:Ethernet  HWaddr 00:1d:09:ba:14:e0  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feba:14e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:551995 (551.9 KB)  TX bytes:118019 (118.0 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10956 (10.9 KB)  TX bytes:10956 (10.9 KB)

**lspci -nnk | grep -iA2 net**
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
--
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:022a]
    Kernel driver in use: b44

**lsmod | grep -e wl -e b43 -e ssb**
ssb                    52752  1 b44
wl                   2568210  0 
lib80211               14381  1 wl
[B]
rfkill list all[/B]
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

Something tells me I screwed up somewhere...

---

### Post by mikewhatever on 2012-06-23
It looks like the **wl** module is still loaded. Is it disabled in the Aditional Drivers?
You can use **sudo rmmod wl** ro remove it temporarily.

---

### Post by d_fiumano on 2012-06-25
Heyo! I tried **sudo rmmod wl **& it didn't work. I got this "**ERROR: Module wl does not exist in /proc/modules**". not quite sure what to do at this point.

---

### Post by mikewhatever on 2012-06-25
Well, I was refering to the following
```
lsmod | grep -e wl -e b43 -e ssb
ssb 52752 1 b44
wl 2568210 0
lib80211 14381 1 wl
```

which shows **wl** as still loaded. Perhaps that was before rebooting.

By the way, someone had a similar question at AskUbuntu.com. Perhaps that answer will explain things better then I can: [http://askubuntu.com/a/38700/20054](http://askubuntu.com/a/38700/20054)

---

### Post by wildmanne39 on 2012-06-26
Hi, this should work for 12.04.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
The b43 is included in the [COLOR="Red"]linux-firmware-nonfree[/COLOR] package in 12.04.
Then reboot.
If it still does do connect please post:
```
nm-tool
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thanks

---

### Post by d_fiumano on 2012-06-28
Well, STILL no fn+f2 for wifi:angry:

Here are the outputs:

nm-tool

#NetworkManager Tool

State: connected (global)

- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:1D:09:BA:14:E0

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             68.237.161.12#

#rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes#

#lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17693  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                87692  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
radeon                804372  3 
snd                    78855  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    76949  1 radeon
k8temp                 13057  0 
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 radeon
edac_core              53746  0 
sp5100_tco             13791  0 
edac_mce_amd           23709  0 
parport_pc             32866  0 
bnep                   18281  2 
rfcomm                 47604  0 
i2c_piix4              13301  0 
bluetooth             180104  10 bnep,rfcomm
ppdev                  17113  0 
shpchp                 37277  0 
wmi                    19256  1 dell_wmi
binfmt_misc            17540  1 
video                  19596  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
b44                    36276  0 
sdhci                  33205  1 sdhci_pci
pata_atiixp            13204  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
ssb                    52752  1 b44#

Thanks again for all your help!!

---

### Post by wildmanne39 on 2012-06-28
Hi, 
You have a softblock and a hardblock, for the softblock please do:
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
you will need to reboot then do the following for the hardblock try the physical key and check it with:
```
rfkill list all
```

Did this command complete without error's:
```
sudo apt-get install linux-firmware-nonfree
```
It is very late here, I am off until tomorrow.
Thanks

---

### Post by d_fiumano on 2012-07-04
Ok, now I KNOW something is wrong. now rfkill is not working at all....I am veeeeeeery close to my boiling point. What am I doing wrong?!

---

### Post by wildmanne39 on 2012-07-05
Hi, take a deep breath and relax I suspect you may be missing firmware and possibly have two drivers loaded still.

Please post the output of:
```
lsmod | grep -e b43 -e ssb -e wl
sudo iwlist scan
```
```
dmesg | egrep 'b43|firm|radio|switch|wlan0'
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you
Thanks

---

### Post by d_fiumano on 2012-07-05
Okie dokie, here are my outputs:

**lsmod | grep -e b43 -e ssb -e wl**
ssb                    52752  1 b44

**sudo iwlist scan**
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.
[B]
dmesg | egrep 'b43|firm|radio|switch|wlan0'[/B]
[    1.557864] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.557880] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[   15.397008] Console: switching to colour frame buffer device 160x50

---

### Post by wildmanne39 on 2012-07-05
Hi, were there any errors when you ran this command from post 17?
```
sudo apt-get install linux-firmware-nonfree
```
if not sure run this one and watch for errors:
```
sudo apt-get install --reinstall linux-firmware-nonfree
```

---

### Post by d_fiumano on 2012-08-06
Sorry for such a late reply!! I didn't see any errors, but STILL no wifi. fn+f2 refuses to work...dangerously close  to punching a gaping hole in the wall...](*,)

---

### Post by wildmanne39 on 2012-08-06
Hi, run this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security then reply back,  and attach the netinfo.txt file.
Thanks

---

### Post by d_fiumano on 2012-08-13
Okie Dokie! Here's the file!!

---

### Post by wildmanne39 on 2012-08-13
Hi, please do:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
remove [COLOR="Red"]blacklist b43[/COLOR]
save gedit and close.
Then Reboot.

If it does not connect then install rfkill and run the script again.
Thanks

---

### Post by d_fiumano on 2012-08-13
HOLYCRAPITWORKED!!!!!:grin: Thanks a heap-load!!!!!

---

### Post by wildmanne39 on 2012-08-13
Hi, glad to help! the script made it a lot easier to see the problem, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

