---
title: "wireless-migració de ipw a iwlwifi"
date: 2008-04-06
forum: Catalan Team
---

### Post by abosch on 2008-04-06
Hola, 

a casa em connecto a xarxa amb fil. Des del primer moment ha anat com una seda. Tanmateix, la setmana passada, en intentar de fer-ho via wifi ... 

abosch@abb-portatil:~$  lspci | grep Network
01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

abosch@abb-portatil:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5120  1
nls_cp437               6784  1
vfat                   14080  1
fat                    54300  1 vfat
usb_storage            73024  1
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
isofs                  36412  0
udf                    87204  0
ipv6                  273892  10
i915                   25856  2
drm                    83348  3 i915
af_packet              24840  2
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0
acpi_cpufreq           10568  1
cpufreq_userspace       5280  0
cpufreq_ondemand        9612  1
cpufreq_conservative     8072  0
cpufreq_stats           7232  0
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0
asus_acpi              17308  0
ac                      6148  0
video                  18060  0
sbs                    19592  0
dock                   10656  0
button                  8976  0
container               5504  0
battery                11012  0
sbp2                   24072  0
parport_pc             37412  0
lp                     12580  0
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         341784  1
joydev                 11328  0
snd_pcm_oss            42784  0
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
snd_seq_dummy           4996  0
snd_seq_oss            35456  0
snd_seq_midi            9632  0
snd_rawmidi            25888  1 snd_seq_midi
sdhci                  18828  0
ipw3945               119840  1
snd_seq_midi_event      8704  2 snd_seq_oss,snd_seq_midi
mmc_core               28420  1 sdhci
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24964  2 snd_pcm,snd_seq
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
serio_raw               8068  0
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               11940  0
pcspkr                  4224  0
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
psmouse                39952  0
intel_agp              25620  1
agpgart                35016  3 drm,intel_agp
snd                    56740  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
evdev                  11136  6
ext3                  133896  3
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0
sr_mod                 17828  0
cdrom                  37536  1 sr_mod
sd_mod                 30336  7
ata_generic             8452  0
usbhid                 29536  0
hid                    28928  1 usbhid
ohci1394               36528  0
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0
r8169                  32260  0
ata_piix               17540  4
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               26640  0
usbcore               138632  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor
               

llegeixo [aqui]("https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy?highlight=%28Corporation%29%7C%28Intel%29%7C%28Connection%29%7C%28Network%29%7C%283945ABG%29%7C%28PRO%2FWireless%29")

vaig bé? Entenc que esperant unes setmanes i actualitzant a la HH s'arreglaria, però voldria fer-ho abans.

 /etc/udev/rules.d/70-persistent-net.rules       veig que no és igual ... 

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1a:92:78:ba:35", NAME="eth0"

# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}==[COLOR="Red"]"00:19:d2:2b:c9:dc"[/COLOR], NAME="eth1"

Continuo igualment ?

gràcies, 
Alex

---

### Post by patrickfromspain on 2008-04-07
ep, perque has de tocar res de l'udev??? El modul ipw hauria de funcionar, al menys despres d'habilitarlo en els controladors restringits.

De totes formes.. aquest post que has escrit es molt poc entenedor. No s'enten perque et falla, quan o com. No s'enten que demanes o que vols fer.

Torna a començar i explican's el que necessites saber i perque.

salut!

PD: el controlador ipw hauria de funcionar sense problemes. I per fer servir l'iwl no has de tocar res de l'udev ni res de hardy heron ni res..

EDITO: si vols fer anar l'iwl, jo nomes faria aixo:

Then add the following to /etc/modprobe.d/blacklist :

# disable ipw3945 old intel3945 driver 
blacklist ipw3945
blacklist ieee80211
blacklist ieee80211_crypt

Add the following to /etc/modules :

# new intel3945 iwlwifi driver 
iwlwifi_mac80211
iwl3945

---

### Post by abosch on 2008-04-08
disculpeu el missatge tant poc entenedor.  Hi torno:

L'altre dia volia conectar-me a una xarxa sense fil i no podia. La xarxa requeria una contrasenya (q tenia). Com que no podia conectar-m'hi vaig començar a cercar fins a topar amb l'article a dalt enllaça't. No veia massa clar què fer i si ho havia de fer, així abans volia preguntar-vos-ho. 

Tot aquest rotllo, i aquesta tarda (ara mateix) estic conectat a una wifi sense problemes ... :shock:  

patrickfromspain, 

... aprofitant el fil, el dia que no podia conectar vaig guardar les ordres que he llegit ajuden a  solucionar el prob.  si et sembla de donar continuitat al fil les penjo, sinò el faig 'solved'


gràcies
Alex

---

