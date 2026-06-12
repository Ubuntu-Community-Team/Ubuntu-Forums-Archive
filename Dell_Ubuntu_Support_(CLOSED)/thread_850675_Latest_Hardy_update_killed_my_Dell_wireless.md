---
title: "Latest Hardy update killed my Dell wireless"
date: 2008-07-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by UnrulyGrrl99 on 2008-07-05
I was trying to get my wireless card (Dell 1395) working on my Dell XPS 1530 over the last few days with no luck. Before the latest update to Hardy, I could see the wireless interface, scan for networks, etc.  After the update, the "wifi" light is out on the laptop. I found these errors in dmesg:

[  160.750103] wl: Unknown symbol wlc_get
[  160.750263] wl: Unknown symbol wf_channel2mhz
[  160.750288] wl: Unknown symbol wlc_isr
[  160.750326] wl: Unknown symbol wlc_set
[  160.750372] wl: Unknown symbol wlc_statsupd
[  160.750409] wl: Unknown symbol bcm_bprintf
[  160.750521] wl: Unknown symbol wlc_dpc
[  160.750578] wl: Unknown symbol wlc_chipmatch
[  160.750618] wl: Unknown symbol wlc_reset
[  160.750688] wl: Unknown symbol wlc_sendpkt
[  160.750744] wl: Unknown symbol wlc_intrsrestore
[  160.750768] wl: Unknown symbol wlc_init
[  160.750794] wl: Unknown symbol bcm_parse_tlvs
[  160.750890] wl: Unknown symbol wlc_down
[  160.750928] wl: Unknown symbol wlc_iovar_getint
[  160.750964] wl: Unknown symbol wlc_iovar_setint
[  160.750999] wl: Unknown symbol wlc_up
[  160.751062] wl: Unknown symbol bcm_qdbm_to_mw
[  160.751087] wl: Unknown symbol bcm_mkiovar
[  160.751118] wl: Unknown symbol wlc_intrsoff
[  160.751143] wl: Unknown symbol bcm_mw_to_qdbm
[  160.751182] wl: Unknown symbol wlc_intrsupd
[  160.751206] wl: Unknown symbol wlc_ioctl
[  160.751240] wl: Unknown symbol wf_mhz2channel
[  160.751264] wl: Unknown symbol wlc_intrson
[  160.751288] wl: Unknown symbol wlc_attach
[  160.751336] wl: Unknown symbol wlc_iovar_op
[  160.751360] wl: Unknown symbol wlc_detach
[  160.751392] wl: Unknown symbol pktsetprio


When I try loading the "wl" module by hand (via modprobe), I get this error message:
"FATAL: Error inserting wl (/lib/modules/2.6.24-19-generic/volatile/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I found an older message about a problem with this card and that installing "bcm43xx-fwcutter" fixed it.  I tried that and it did not help.

this is the relevant lspci entry, if that matters:
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)


Has anyone else seen this since the latest Hardy updates?
or ever?  any suggestions?

thanks

---

### Post by Franc88 on 2008-07-06
I have a Dell 1525 and also lost my wireless connection when I updated to latest update.  I still see the driver in hardware manager and is check off enabled but under Status says "Not In Use".

I tried to reinstall wifi driver using b43-fwcutter but no luck.  I tried to boot from a prior update version and still the same.

Anyone have any ideas with a fix or workaround?  Seems to me the latest update screwed up the wifi driver from broadcom.  Is this the ubuntu community's way of getting back at broadcom for that stock backdating scandal?:confused:

---

### Post by Johnny1111 on 2008-07-06
Greetings, folks!

New to Ubuntu, coming from Fedora 9.

I too have the same problem--I have a Dell Inspirion 1720 with the Dell 1395 Wireless minicard.  Everything worked perfectly (the reason why I switched to Ubuntu), but after the updates done July 2-4 I too have no wifi.  When I click on the network indicator in the upper right hand corner of the screen, there is not even an option for wireless.  Hardware Drivers shows a check in the enable box, but there is a red dot to the right with the words "Drive not in use."  Please help!

Thanks in advance!

---

### Post by Beto on 2008-07-07
Same problem here with a Dell XPS M1530 and the regular Wireless card. 
In restricted drivers appears as enabled but with a red light as not in use.

Somebody help!! Please!!

Regards,

---

### Post by stats on 2008-07-07
I have a 1395 card and got it working using ndiswrapper.
1.
```
echo blacklist bcm43xx | sudo tee -a /etc/modprobe.d/blacklist
```
2.
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```
3.
search for the dell 1395 windows XP (NOT Vista) drivers on [www.dell.com](www.dell.com) and download it
4 unzip <name of the file you downloaded>
5. System -> Administration -> Windows Wireless Drivers -> Install New Driver -> open bcmwl5.inf from DRIVER_US folder of the place you unzipped the windows driver to
6. 
```
sudo modprobe ndiswrapper
```
7. Check if wireless works now. If it does add the word 'ndiswrapper' to the end of /etc/modules so that it loads automatically

---

### Post by Franc88 on 2008-07-09
> **stats said:**
> 
3.
search for the dell 1395 windows XP (NOT Vista) drivers on [www.dell.com](www.dell.com) and download it
4 **unzip <name of the file you downloaded>**
5. System -> Administration -> Windows Wireless Drivers -> Install New Driver -> open bcmwl5.inf from DRIVER_US folder of the place you unzipped the windows driver to

I'm not sure how to unzip/run an exe file in linux.  Everytime I try to double click on it, it gives an error.

EDIT:  Got the .exe working by installing Wine.

The driver is now installed using ndiswrapper and now working again.  Thanks.

---

### Post by friendofpugs on 2008-07-09
Is there any other way of doing this besides the above solution? I'm a newb and it looks complicated. What's going on in the above steps? Will they eventually tweak the kernel or should I try the above? Thanks.:confused:

---

### Post by stats on 2008-07-09
the changes above are totally safe. you will not mess up your kernel/ your linux install. just follow the steps and you should be fine. try it, its quite easy.
@franc88: i did mean unzip the exe. its a self-extracting archive.
just do
unzip <name of file.exe> 
in the terminal, and it will unzip it.

---

### Post by Franc88 on 2008-07-09
> **stats said:**
> the changes above are totally safe. you will not mess up your kernel/ your linux install. just follow the steps and you should be fine. try it, its quite easy.
@franc88: i did mean unzip the exe. its a self-extracting archive.
just do
unzip <name of file.exe> 
in the terminal, and it will unzip it.

The driver that I found for the WinXP OS was an .exe and not a .zip.  It was an 89meg download for a simple driver which was unbelievable.  So you mean to say that running:

```
unzip <delldriver.exe>
```

in terminal will unzip and execute the .exe?  I'll have to try that next time.

None the less, I was able to install the driver after I was able to run the .exe. :)

---

### Post by perl1011 on 2008-07-09
> **stats said:**
> the changes above are totally safe. you will not mess up your kernel/ your linux install. just follow the steps and you should be fine. try it, its quite easy.
@franc88: i did mean unzip the exe. its a self-extracting archive.
just do
unzip <name of file.exe> 
in the terminal, and it will unzip it.

Um...yeah, safety is good, but seriously, this is way too complicated. I'm totally new to this, but wanted to try Ubuntu when I got my new Dell laptop. I don't even understand half of all this stuff or even what a kernel is. Does this mean I have to go back to windows? :( (sigh)

---

### Post by niiiick on 2008-07-09
> **stats said:**
> I have a 1395 card and got it working using ndiswrapper.
1.
```
echo blacklist bcm43xx | sudo tee -a /etc/modprobe.d/blacklist
```
2.
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```
3.
search for the dell 1395 windows XP (NOT Vista) drivers on [www.dell.com](www.dell.com) and download it
4 unzip <name of the file you downloaded>
5. System -> Administration -> Windows Wireless Drivers -> Install New Driver -> open bcmwl5.inf from DRIVER_US folder of the place you unzipped the windows driver to
6. 
```
sudo modprobe ndiswrapper
```
7. Check if wireless works now. If it does add the word 'ndiswrapper' to the end of /etc/modules so that it loads automatically

confirmed to work on inspiron 1525.  thanks!

---

### Post by PinkFloyd102489 on 2008-07-10
I fixed mine earlier using a Guide in the Wiki on an Inspiron 1720, bcm4328. Had to change the order in which some of the modules loading, putting the ndiswrapper module before the ssd module.

Otherwise, it works fine. :)

---

### Post by superm1 on 2008-07-10
In an effort to better understand this problem, can someone with this problem post the following information:

1)
```
lspci -nn
```2) 
```
dpkg -l | grep linux-restricted
```3)
```
uname -a
```4)
```
dmesg | grep wl
```

---

### Post by superm1 on 2008-07-10
For a pre-emptive (proper) solution, please activate hardy-proposed.  This should be copied into hardy-updates soon too.

[https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930](https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930)

---

### Post by friendofpugs on 2008-07-10
> **perl1011 said:**
> Um...yeah, safety is good, but seriously, this is way too complicated. I'm totally new to this, but wanted to try Ubuntu when I got my new Dell laptop. I don't even understand half of all this stuff or even what a kernel is. Does this mean I have to go back to windows? :( (sigh)

The problem is being resolved as I type: [https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930]("https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930"). Long story short - they fixed the bug and are moving the patch into the update stream, so the automatic updates should fix the kernel very soon, in a few days at the latest. Hence, I'm waiting for it myself instead of messing around with the above solution.
BTW, be sure to have automatic updates enabled in Ubuntu. Once the patch comes through, it will fix itself. :)
One thing you've got to remember with Ubuntu (and Linux in general) is that this is a community-wide endeavor w/o the backing of mega corporations, so you've got to be patient and give things time. IMHO, it's a small price to pay for a fantastic OS that's super secure and has ton's of free quality programs. 
Just give it some time.

---

### Post by ikrit42 on 2008-07-10
> **stats said:**
> I have a 1395 card and got it working using ndiswrapper.
1.
```
echo blacklist bcm43xx | sudo tee -a /etc/modprobe.d/blacklist
```
2.
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```
3.
search for the dell 1395 windows XP (NOT Vista) drivers on [www.dell.com](www.dell.com) and download it
4 unzip <name of the file you downloaded>
5. System -> Administration -> Windows Wireless Drivers -> Install New Driver -> open bcmwl5.inf from DRIVER_US folder of the place you unzipped the windows driver to
6. 
```
sudo modprobe ndiswrapper
```
7. Check if wireless works now. If it does add the word 'ndiswrapper' to the end of /etc/modules so that it loads automatically

This also worked on my xps m1330- Before, Ubuntu didn't even realize my wifi card existed, now all i need to do is remember my wpa password :/

---

### Post by silkstone on 2008-07-10
I didn't have this problem but I've just run Update Manager and the new restricted module package is now available for download and installation (you don't need the hardy-proposed repo anymore).

---

### Post by stats on 2008-07-10
can confirm that the driver is in the repo
for those who installed ndiswrapper:
1.Update & upgrade using update-manager/synaptic/adept etc
2.
```
sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```
3. Remove the ndiswrapper line from /etc/modules
4. Disable wireless from the network manager applet and then
```
sudo modprobe -r ndiswrapper
```
If it cribs about module being in use, it means you have not disabled wireless
5. Restart, if there were any kernel upgrades
6. System->Administration->Hardware Drivers
I see a wl driver here. Make sure it says enabled and is in use.

worked for me with dell 1395 on inspiron 1525

---

### Post by perl1011 on 2008-07-10
> **friendofpugs said:**
> One thing you've got to remember with Ubuntu (and Linux in general) is that this is a community-wide endeavor w/o the backing of mega corporations, so you've got to be patient and give things time. IMHO, it's a small price to pay for a fantastic OS that's super secure and has ton's of free quality programs. 
Just give it some time.

Roger that...point taken. Overall, I think this whole subversive counterculture ;) is cool (even though I'm a dork and will likely get kicked out of forums for giving the technogeeks hives and eye cramps from rolling their eyes at me). Though...really, it's a pretty big bug, isn't it. I mean, what good is a laptop without wireless? Is this typical of Ubuntu? I'm just curious...need to set/adjust my expectations. (and keep my dual boot!) Thanks :)

---

### Post by perl1011 on 2008-07-10
> **silkstone said:**
> I didn't have this problem but I've just run Update Manager and the new restricted module package is now available for download and installation (you don't need the hardy-proposed repo anymore).

Hmmm...I just ran it, but no update for this came through. Is there something special one needs to do to get this module? Thanks...

---

### Post by UnrulyGrrl99 on 2008-07-10
I just did the latest updates and all is well again!  No ndis or anything had to be installed.  I just waited for the updates to complete on linux-restricted-modules, ran "sudo modprobe wl" from a terminal, and the wifi light lit up.  i can see/scan for all the nearby wireless networks again.

thanks to everyone for their great tips about ndis wrapper and about the early fix (hardy-proposed) a few days ago.

---

### Post by superm1 on 2008-07-11
> **perl1011 said:**
> Roger that...point taken. Overall, I think this whole subversive counterculture ;) is cool (even though I'm a dork and will likely get kicked out of forums for giving the technogeeks hives and eye cramps from rolling their eyes at me). Though...really, it's a pretty big bug, isn't it. I mean, what good is a laptop without wireless? Is this typical of Ubuntu? I'm just curious...need to set/adjust my expectations. (and keep my dual boot!) Thanks :)
No this is not common, but the oversight that caused it to happen has been corrected now.  It shouldn't happen in the future.

---

### Post by Beto on 2008-07-15
I still have problems that seems to be related to this.

I installed the XP drivers through ndiswrapper for a while until the bug got fixed with the latest upgrade. Then I performed the ndiswrapper uninstall procedure explained in this thread and with the latest upgrade everything went back to normal... I thought... Now, every time I power on my notebook I don't have wireless and the wl driver is checked and in red as in "not in use". I have to disable it and then re-enable it for it to work as it should... and this happens EVERY time I have to restart the notebook. It is really annoying and I don't know what to do for it to work as it did before the bug was introduced.

Any help?

Regards,
--
Beto

---

### Post by superm1 on 2008-07-15
> **Beto said:**
> I still have problems that seems to be related to this.

I installed the XP drivers through ndiswrapper for a while until the bug got fixed with the latest upgrade. Then I performed the ndiswrapper uninstall procedure explained in this thread and with the latest upgrade everything went back to normal... I thought... Now, every time I power on my notebook I don't have wireless and the wl driver is checked and in red as in "not in use". I have to disable it and then re-enable it for it to work as it should... and this happens EVERY time I have to restart the notebook. It is really annoying and I don't know what to do for it to work as it did before the bug was introduced.

Any help?

Regards,
--
Beto
Try typing "depmod -a" after the driver is loaded and working.

---

### Post by Beto on 2008-07-16
> **superm1 said:**
> Try typing "depmod -a" after the driver is loaded and working.

Thanks for helping but the problem is still there. I hate it!

I started ubuntu, disabled the wl driver and then I re-enabled it. The Wifi worked so I started a Terminal and typed "sudo depmod -a"

I had no messaged but just a prompt. I guess that is how depmod works. I restarted the notebook and again I didn't have the Wifi working.

Any other possible solution?

Regards,
--
Beto

---

### Post by superm1 on 2008-07-16
> **Beto said:**
> Thanks for helping but the problem is still there. I hate it!

I started ubuntu, disabled the wl driver and then I re-enabled it. The Wifi worked so I started a Terminal and typed "sudo depmod -a"

I had no messaged but just a prompt. I guess that is how depmod works. I restarted the notebook and again I didn't have the Wifi working.

Any other possible solution?

Regards,
--
Beto
Did you by chance accidently blacklist 'wl' at some point?

Try

```
grep wl /etc/modprobe.d -R
```

If you get anything more than

/etc/modprobe.d/arch/i386:alias parport_lowlevel parport_pc
/etc/modprobe.d/arch-aliases:alias parport_lowlevel parport_pc

than you might have blacklisted it

Also, check /etc/default/linux-restricted-modules-common.  Is wl listed in there as blocked?

---

### Post by Beto on 2008-07-16
> **superm1 said:**
> Did you by chance accidently blacklist 'wl' at some point?

Try

```
grep wl /etc/modprobe.d -R
```

If you get anything more than

/etc/modprobe.d/arch/i386:alias parport_lowlevel parport_pc
/etc/modprobe.d/arch-aliases:alias parport_lowlevel parport_pc

than you might have blacklisted it

Also, check /etc/default/linux-restricted-modules-common.  Is wl listed in there as blocked?


With "grep wl /etc/modprobe.d -R" I got exactly what you typed, but in the inverse order:
/etc/modprobe.d/arch-aliases:alias parport_lowlevel parport_pc
/etc/modprobe.d/arch/i386:alias parport_lowlevel parport_pc

Then I checked the linux-restricted-modules-common file and nothing looks blacklisted. This is the file:
--------------------------------------
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
-------------------------------------------------------

Any other help?.... I'm getting crazy here!!!

Thanks!
--
Beto

---

### Post by superm1 on 2008-07-17
> **Beto said:**
> With "grep wl /etc/modprobe.d -R" I got exactly what you typed, but in the inverse order:
/etc/modprobe.d/arch-aliases:alias parport_lowlevel parport_pc
/etc/modprobe.d/arch/i386:alias parport_lowlevel parport_pc

Then I checked the linux-restricted-modules-common file and nothing looks blacklisted. This is the file:
--------------------------------------
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
-------------------------------------------------------

Any other help?.... I'm getting crazy here!!!

Thanks!
--
Beto
You're running me out of ideas.. ;)

OK, when you boot up, I wonder if possibly another module is loading automatically that is conflicting.

After a fresh boot, type

```
lsmod
```

and see if any of that output is a wireless driver (maybe ndiswrapper wasn't fully removed). then try to manually load wl without jockey

```
sudo modprobe wl
```

check

```
dmesg | tail
```

for any info about what happened when trying to load it.  If it errors out, try to depmod once more and reload it.

---

### Post by Beto on 2008-07-17
I think we are going on the right track and you may be onto something...
When I typed "lsmod" after a fresh boot I got this:

-------------------------------
Module                  Size  Used by
ipv6                  267780  10 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
vboxdrv                77504  0 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_ondemand        9740  1 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
hci_usb                16540  2 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
uvcvideo               58116  0 
snd_hda_intel         344728  3 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
nvidia               7825536  36 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
video                  19856  8 
output                  4736  1 video
i2c_core               24832  1 nvidia
snd_seq_dummy           4868  0 
sky2                   47492  0 
ndiswrapper           192920  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
sdhci                  19076  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               51460  1 sdhci
serio_raw               7940  0 
wmi_acer                9644  0 
battery                14212  0 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
ac                      6916  0 
intel_agp              25492  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
dcdbas                  9504  0 
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                34760  2 nvidia,intel_agp
evdev                  13056  8 
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  4 
pata_acpi               8320  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
ata_generic             8324  0 
ahci                   28420  3 
ata_piix               19588  0 
libata                159344  4 pata_acpi,ata_generic,ahci,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  7 hci_usb,uvcvideo,**ndiswrapper**,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
------------------------------------------------------------

You are right, ndiswrapper is still there but I have no idea how to get rid of it.

When typing "sudo modprobe wl" I got the wireless working and this is the "dmesg | tail" ouput:
********************
[   54.842528]  domain 0: span 03
[   54.842530]   groups: 02 01
[  102.671281] ieee80211_crypt: registered algorithm 'NULL'
[  102.680047] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  102.680074] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[  102.903247] ieee80211_crypt: registered algorithm 'TKIP'
[  102.903330] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.18.0
[  106.217630] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  106.267246] NET: Registered protocol family 17
[  107.768756] eth1: no IPv6 routers present
*********************

So, what to do next?

TIA!
--
Beto

---

### Post by Beto on 2008-07-17
Hi, I tried something that worked, but as a newbie I'm not sure if this is the best solution or it might give me problems in the future.

I edited /etc/modules and added "wl" (it wasn't there) as the last module to be loaded. Now it works. Is this the best solution? at least I'm happy it is working.

Please advice.
Regards,
--
Beto

---

### Post by falcon61102 on 2008-07-18
That works or if you are using ndiswrapper to load your drivers, then you would need to put that in there as well.

---

### Post by Beto on 2008-07-19
Ok, but is it a good solution or just a patch that might give problems in the future?

Regards,
--
Beto

---

### Post by falcon61102 on 2008-07-19
It shouldn't give you problems in the future.  That file is what modules are loaded on startup and if you are using ndiswrapper to control your wireless card, then you are going to want to start it when you start your computer.  Even if you update your drivers in the future, that line in /etc/modules will continue to load ndiswrapper with the new drivers.  If that's what gets it to work, then it's a good solution.

---

### Post by tw0shoes on 2008-07-19
I'm having a similar issue as everyone else here. My wireless was working but is no longer.

Output of:  dmesg | tail

```
[  167.363097] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  167.363110] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  174.992389] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  174.992402] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  182.035710] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  182.035723] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  189.151080] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  189.151094] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  197.187684] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  197.187696] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).

```

I went to that website and performed
```
      sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh 
```
except that it was bcm43-fwcutter, not b43-fwcutter

Thanks

---

### Post by tw0shoes on 2008-07-19
I figured out the issue I think. 
Thanks.

---

### Post by clbaines on 2008-07-21
ndiswrapper will work fine. Give it a try. The above instructions are good.

---

### Post by smalldog on 2008-07-29
Dear all, I have puchased a new Dell vostro 2 weeks ago. I am very luck, I didn't necessary  to perform any upgrade. Therefore, I hadn't any experience of killing wireless LAN.
I have install a 32bit 8.04 ubuntu directly. The wireless card seems does work properly at first. Since my route is using WPA encryption. After 3 days investigation and trying by using b43, ndiswrapper and etc. I have found a way out. 
Firstly, you must have identical wireless hardware as me, you can verify it as below command. 
Secondly, you must avoid any driver contention - unload any wireless LAN drivers as below.
 
**lshw -C network**
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:c6:4d:4c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.12.101 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:08:cb:f9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes
**lspci -nn | grep Broadcom**
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)
**lsmod | grep wl**
wl                   1062164  0 
ieee80211_crypt         7040  2 wl,ieee80211_crypt_tkip

[B]lsmod | grep b43
lsmod | grep ndis
[/B]
"Should report nothing"

Since the system reported that the hardware drivers (nvidia & wl) are loaded and working properly. The x-server working well, so I think the wireless LAN card should work but somewhere I must missed. 
I using another desktop computer with wireless LAN installed and running kismet to monitor the activity of both my router & my laptop computer. Evertime when I try to associate to the AP, the kismet showed the frame has transmitted from my laptop. It is concluded that it must be the problem of association. 
So I decide that firstly that withdraw any protection of wireless LAN.
1) No hidden SSID
2) No WEP/WPA
3) No mac filtering
Luckily, the wireless LAN is working. I order to simplify my life, I using the pre-install utility - NetworkManager to perform connection. It also working well.
After that I have tried to a big step jumping to enable all of above mentioned protection to the wireless connection, but no luck any more. 
So, I do it again step by step again.
1) Enable MAC filtering on the router. - Wireless working without problem
2) Enable hidden SSID on the router - longer time for associate but OK. 3) Enable WPA on the router - using wpa_supplicant for WPA authentication, due to cannot recognize the driver wl. So I using WEP instead of WPA to encrypt my WLAN and it working well after a bit slowly authentication. 

I am still trying to enhance the security to WPA. Hopefully, Broadcom can release more information on how to using their newly developed driver to let us explode the ability of the broadcom chipset. 

Good luck to everyone.

---

### Post by Ichido on 2008-07-31
My 2 Dell Inspirons 1525n, with the 3945 Wireless Card, Wireless worked great until Yesterday's Updates.
Now I have two laptops without Wifi!
I suspect the "Updates" Killed both of my laptop's wifi :( 

output from "dmesg | tail" from one of my 2 laptops:

[   70.924157] sky2 eth1: enabling interface
[   70.930385] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   73.048413] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   73.048555] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[   73.049623] iwl3945: Radio disabled by HW RF Kill switch
[   73.049741] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[   86.438315] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   86.438458] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[   86.439560] iwl3945: Radio disabled by HW RF Kill switch
[   86.439678] ACPI: PCI interrupt for device 0000:0b:00.0 disabled

Can anyone help?
Thank God my Desktop is on Ethernet Cable :)

---

### Post by superm1 on 2008-07-31
> **Ichido said:**
> My 2 Dell Inspirons 1525n, with the 3945 Wireless Card, Wireless worked great until Yesterday's Updates.
Now I have two laptops without Wifi!
I suspect the "Updates" Killed both of my laptop's wifi :( 

output from "dmesg | tail" from one of my 2 laptops:

[   70.924157] sky2 eth1: enabling interface
[   70.930385] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   73.048413] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   73.048555] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[   73.049623] iwl3945: Radio disabled by HW RF Kill switch
[   73.049741] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[   86.438315] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   86.438458] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
[   86.439560] iwl3945: Radio disabled by HW RF Kill switch
[   86.439678] ACPI: PCI interrupt for device 0000:0b:00.0 disabled

Can anyone help?
Thank God my Desktop is on Ethernet Cable :)
There is currently a bug in hardy-proposed and linux-backports-modules I believe.  If you have it activated, remove lbm.

---

### Post by Ichido on 2008-07-31
Would you please explain your post:

There is currently a bug in hardy-proposed and linux-backports-modules I believe. If you have it activated, remove lbm.

How do I find out if the "linux-backports-modules" are Activated?
How do I remove "lbm"?
thanks

---

### Post by lynchman on 2008-08-02
I had the same problem the last few days.  It was about 3 weeks since I updated - and the update killed my wireless.  I updated to proposed yesterday and then I needed to manually load the wl module, and then my wireless starting working again.

---

### Post by Ichido on 2008-08-04
> **lynchman said:**
> I had the same problem the last few days.  It was about 3 weeks since I updated - and the update killed my wireless.  I updated to proposed yesterday and then I needed to manually load the wl module, and then my wireless starting working again.

Can you please explain:
"I updated to proposed" and How do I manually load the "wl"?
Many thanks.

---

### Post by superm1 on 2008-08-04
> **Ichido said:**
> Can you please explain:
"I updated to proposed" and How do I manually load the "wl"?
Many thanks.
More or less:

1) Create a blacklist file in /etc/modprobe.d/blacklist-bcm43 that contains these contents
```
blacklist b43
blacklist ssb
blacklist b43legacy
```

2) Update initramfs
```
sudo update-initramfs -u
```

3) Activate hardy-proposed in System->Administration->Software Sources

4) Perform all updates (make sure you get a linux, linux-ubuntu-modules, and linux-restricted-modules update).

5) Profit

---

### Post by TimDaniels on 2008-08-09
The Duck update killed my M1330's Wi-Fi, too.  Wi-Fi had been working fine (as long as it was in roaming mode) with Gutsy, but it disappeared with the Duck update.  The Update Manager kept saying that my system was up-to-date until I checked "Pre-release updates" in the "Updates" tab of the Software Sources administrative utility.  Then Update Manager said that there were 55 updates available.  I installed those updates, restarted the system, and... nada.  Wi-Fi is still not available.  Do I have to do this "blacklist" stuff?  Why would something have to be blacklisted to enable a driver update for Broadcom Wi-Fi?

*TimDaniels*

---

### Post by deja on 2008-08-12
I had similar problems with my M1330.

I was using NDIS wrapper, and was told the restricted drivers came out, so I uninstalled NDIS.  Then I had to manually modprobe -r ndiswrapper.

I was left with the aforementioned problem of the wl driver being "active" but not "in use" in the restricted drivers panel on startup that had to be disabled and reenabled.  Adding wl to the /etc/modules file fixed this. 

Hope this is of some help.

---

### Post by TimDaniels on 2008-08-12
> **deja said:**
> I had similar problems with my M1330.

[....] Adding wl to the /etc/modules file fixed this.

OK, checking the thread mode, I see that you're replying to me.  Would you please elaborate on where to get the "wl" file?

*TimDaniels*

---

### Post by bregenspan on 2008-10-11
> **TimDaniels said:**
> OK, checking the thread mode, I see that you're replying to me.  Would you please elaborate on where to get the "wl" file?

*TimDaniels*

The wl file is a module/driver that you should already have if you have an up-to-date copy of Hardy (and you should definitely have if you updated to the latest proposed version).

---

