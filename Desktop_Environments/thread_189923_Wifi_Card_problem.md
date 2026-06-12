---
title: "Wifi Card problem"
date: 2006-06-05
forum: Desktop Environments
---

### Post by RobertBIrish on 2006-06-05
I have a Toshiba laptop with an Intel Pro Wireless B220G card and it will not connect even though Ubuntu sees the card and recognizes it and it is set as active in Network tools. It is on DHCP just like my ethernet card which I have no problem with. I am a newby to Linux but I am very computer literate so any help woulld be greatly appreciated.

---

### Post by murataht on 2006-06-05
use system->administration->networking to check if the ssid and wep keys are set correctly.  hope this may help. 

also, maybe you have to set wpa if your wifi use wpa. but i don't know how to set wpa. 

good luck.

---

### Post by RobertBIrish on 2006-06-05
I appreciate the help WEP is enabled but I get nothing Guess I will keep waiting

---

### Post by judgekaster on 2006-06-05
i suggest the following:

a) check first if it sees any accesspoints near you. do this by issuing the following in a terminal:

```

iwlist wlan0 scan

```

assuming that wlan0 is your wireless interface (check that by doing a "iwconfig")

b) if it sees an accesspoint, make sure that all options, i.e. essid, WEP key etc are set correctly. you may usually do that through the network-admin tool. in a terminal, you can use "iwconfig", i.e. 

```

$ sudo iwconfig wlan0 key <yourAPkey>
$ sudo iwconfig wlan0 essid <APname>

```

check if these were set correctly by typing

```

$ sudo iwconfig wlan0

```

c) try to connect to the network by

```

$ sudo dhclient wlan0

```

You should get a response from the DHCP server. Otherwise, you may want to check your logs while trying to connect, i.e. open another terminal and type

```

$ tail -f /var/log/messages /var/log/syslog

```

Hope this helps.

---

### Post by RobertBIrish on 2006-06-05
I appreciate the help it keeps saying there is no such card but if I look in Device Manager there it is. I also used Atomatix would that do anything to hrt me?

---

### Post by RobertBIrish on 2006-06-05
Would also like to say I have never been big on Linux but Dapper Drake is so easy to use I f I could get past this Wifi problem I will never go back to Windows.

---

### Post by judgekaster on 2006-06-05
what does 

```

$ iwconfig

```
give you?

---

### Post by RobertBIrish on 2006-06-05
robertbirish@roberts-laptop:~$ $ iwconfig
bash: $: command not found
robertbirish@roberts-laptop:~$ $ iwconfig
bash: $: command not found
robertbirish@roberts-laptop:~$

---

### Post by RobertBIrish on 2006-06-05
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=10703&stc=1&d=1149558662[/IMG]

---

### Post by cromestant on 2006-06-05
It seems that the card is found, but not installed.
Check the output of lsmod and see if there are any modules there loaded for the card, also ifconfig should show you the adapters that have been setup correctly.
You should theoreticaly have eth0, lo, and wlan0 or ath0 something like that.

If they are not installed, then you must install the proper module for that card
check this out : [driver page.]("http://ipw2200.sourceforge.net/")

Should be in synaptics.

once you hace installed this, you might need to load the modules, this is done with modprobe, but might not be necesary, in the ink there should be a how too. ( sorry I don;t have a lot of time now to read it thourougly).

Hope this helps

---

### Post by judgekaster on 2006-06-05
dear RobertBIrish,

a) Seems you do not have wireless-tools installed. You can install these by 

```

$ sudo apt-get install wireless-tools

```

b) Then again, try:

```

$ iwconfig

```

---

### Post by RobertBIrish on 2006-06-05
Okay this is what it says now

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      radio off  ESSID:"IrishHome"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by cromestant on 2006-06-05
well aparently your wifi is eth0, which is quite strange , since it "sees" your ssid network name. Now you just have to configure it, like it says on the previous posts, what does lsmod list?

---

### Post by RobertBIrish on 2006-06-05
robertbirish@roberts-laptop:~$ lsmod
Module                  Size  Used by
nls_utf8                2176  1
ntfs                  103536  1
nls_cp437               5888  1
isofs                  37688  1
udf                    88452  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
ipv6                  265600  6
i915                   20608  1
drm                    73236  2 i915
acpi_cpufreq            6792  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 acpi_cpufreq,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
af_packet              22920  4
md_mod                 72532  0
sbp2                   24196  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
arc4                    2048  1
ieee80211_crypt_wep     4992  1
pcmcia                 40508  0
joydev                 10048  0
tsdev                   8000  0
sdhci                  14848  0
ipw2200               107308  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
mmc_core               30104  1 sdhci
usbhid                 38368  0
usb_storage            74176  1
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              22940  1
sky2                   37504  0
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
psmouse                36228  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
serio_raw               7300  0
agpgart                34888  3 drm,intel_agp
rtc                    13492  0
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
sg                     37920  0
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               32008  0
uhci_hcd               33680  0
usbcore               129668  5 usbhid,usb_storage,ehci_hcd,uhci_hcd
sr_mod                 16932  1
cdrom                  38560  1 sr_mod
sd_mod                 19984  5
generic                 5124  0
ata_piix               11012  7
ahci                   17668  0
libata                 78992  2 ata_piix,ahci
scsi_mod              139496  7 sbp2,usb_storage,sg,sr_mod,sd_mod,ahci,libata
thermal                13576  0
processor              23360  2 acpi_cpufreq,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

---

### Post by cromestant on 2006-06-05
Well it's up :

ieee80211_crypt_wep 4992 1
ipw2200 107308 0
ieee80211 37064 1 ipw2200
ieee80211_crypt 6272 2 ieee80211_crypt_wep,ieee80211

these are all wifi related modules, and the ipw 2200 is the specific "driver "for the card...
you should be good to go

---

### Post by RobertBIrish on 2006-06-05
Unfortunately it is still not working getting frustrated, everything else works great.

---

### Post by cromestant on 2006-06-05
When you open the network config utility ont gnome, do you see the adapter?
if so, do you have the fields to input ssid, and wep key?
if so, fill those out, and see if it works.

Another thing, when I first set up mine ( pcmcia dlink) i don't understand why, even though the modules were loaded and the configs were set, it didn't work, until i reboot.. strange, you might want to try this.

---

### Post by RobertBIrish on 2006-06-05
[http://www.ubuntuforums.org/attachment.php?attachmentid=10707&stc=1&d=1149566268](http://www.ubuntuforums.org/attachment.php?attachmentid=10707&stc=1&d=1149566268)

---

### Post by RobertBIrish on 2006-06-05
I will try to reboot and see I really appreciate all of the time you are taking with me!!

---

### Post by RobertBIrish on 2006-06-06
Still nothing

---

### Post by cromestant on 2006-06-06
Well, I can't seem to put my finger on it... 
On gentoo, I had to disable the ethernet card for it to work with wireless... ( son't know why exactly, just know that it worked), 
so maybe you can try it:

ifconfig eth1 down
ifconfig eth0 down
ifconfig eth0 up
then check the config againa, and try to ping something ( ping google.com)
( to re-enable the net card, do ifconfig eth1 up)

Hope it helps, if not, I am out of ideas ( but it is setup, might just be a config issue)

---

### Post by murataht on 2006-06-06
are you sure the wep key is hexidemical?
maybe it is ascii.

---

