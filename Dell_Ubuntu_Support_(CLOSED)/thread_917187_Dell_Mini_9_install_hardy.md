---
title: "Dell Mini 9 install hardy"
date: 2008-09-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dmfield on 2008-09-11
I took delivery of a UK provided Dell Mini 9 today, and didn't even try the Windows XP boot. This is my experience for getting Ubuntu Hardy to work.

1) You cant install straight 8.04 it borks out with a modprobe error, you seem to have to use 8.04.1

2) the install is smooth, and runs through ok

**3) Wifi **
to get this working, i had to install all the updates, then enable multiverse and universe run an apt-get update then install all the updates and reboot.

**4) Sound **

> sudo nano /etc/modprobe.d/alsa-base

add the line to the end

>  options snd-hda-intel model=dell

reboot the pc

on reboot double click on the sound icon in the toolbar

increase the speaker volume

**5) webcam**

This works in ekiga and skype

**6) etherenet**

works out of the box

**7) compiz**

Works fine after the updates

This is being typed on the Dell Mini 9 in the Ubuntu firefox window

First impressions, good kit, very light, keyboard aint  for writing war and peace.. good job

---

### Post by jespdj on 2008-09-12
Is the Mini Inspiron with Ubuntu Netbook Remix not yet available in the UK?

Good to hear that you can install Ubuntu Hardy without too much trouble.

The bad thing about buying a netbook with Windows XP is that you make the manufacturer think that people actually want netbooks with Windows instead of with Linux....

---

### Post by anjilslaire on 2008-09-12
Great review, thanks!

How well does the full blown Ubuntu run?
Do you have 512 or 1gig Ram?
What size of SSD drive? 4gig? 8? 16? How much space does the install take?

---

### Post by Flyers2391 on 2008-09-12
> **jespdj said:**
> **The bad thing about buying a netbook with Windows XP is that you make the manufacturer think that people actually want netbooks with Windows instead of with Linux....**

This is exactly why I'm going to wait it out ... just for the principle of it

---

### Post by dmfield on 2008-09-12
First may i state, where i agree with the comment about buying the windows makes the manufacturer think people want5 to buy the window2s version, the sad fact is the windows version will sell, however as far as i'm concerned, i'm an early adopter.

What you actually have to ask yourself is why did they only offer the 16gb offering in the uk? with xp only for 2 weeks before the ubuntu release?

Anyway, i sold the xp to a sales guy at work.. 

The netbook ubuntu version will not be around for another week apparently, and i needed a new laptop.

The full blow hardy works quickly, and as well as on my dell 1501, 1gb and 16gb of ssd.

---

### Post by anjilslaire on 2008-09-12
1gig, 16gig SSD. Got it. I really want one now :)

BTW, it's *full blown*, ie "complete". My bad.

---

### Post by Dogers on 2008-09-13
Got mine yesterday too, thought I'd add my experience to this thread also.  I installed mine via USB ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) which took ages, but everything was up to date as hoped :)

> **dmfield said:**
> 
**3) Wifi **
to get this working, i had to install all the updates, then enable multiverse and universe run an apt-get update then install all the updates and reboot.


Worked out of the box for me. The restricted drivers notice popped up, but was already enabled - the wireless networks were listed and I just needed to enter my key :)

> **dmfield said:**
> 
**4) Sound **
(snip)
increase the speaker volume

I had to also increase the MASTER channel via alsamixer on the command line, a quick "alsactl store" sorted that permanently. Was confusing the stuff out of me as to why nothing seemed to be working, but no errors being listed!

> **dmfield said:**
> 
First impressions, good kit, very light, keyboard aint  for writing war and peace.. good job

Agreed - the 2/3 width . and / keys are a small disappointment, but otherwise very good!

---

### Post by dmfield on 2008-09-13
hi, how is your webcam? mine seems to hang when i load egika, i might reload uing usb

could you do an lsmod, lsusb and lspci for me and post them here  to see what i may have different

lsmod

Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
i915                   32512  2 
drm                    82452  3 i915
af_packet              23812  6 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
vboxdrv                68376  0 
ppdev                  10372  0 
ipv6                  267780  12 
acpi_cpufreq           10796  1 
cpufreq_ondemand        9740  2 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
mmc_block              14980  2 
uvcvideo               59656  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
psmouse                40336  0 
hci_usb                16540  2 
serio_raw               7940  0 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
sdhci                  19076  0 
mmc_core               51460  2 mmc_block,sdhci
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
battery                14212  0 
evdev                  13056  8 
ac                      6916  0 
video                  19856  0 
output                  4736  1 video
dcdbas                  9504  0 
snd_seq_dummy           4868  0 
ieee80211_crypt_tkip    11648  0 
wl                   1062164  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
button                  9232  0 
pcspkr                  4224  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
snd_rawmidi            25760  1 snd_seq_midi
agpgart                34760  3 drm,intel_agp
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
ata_generic             8324  0 
ata_piix               19588  2 
pata_acpi               8320  0 
libata                159344  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  3 sg,sd_mod,libata
ehci_hcd               37900  0 
r8169                  32900  0 
uhci_hcd               27024  0 
usbcore               146028  5 uvcvideo,hci_usb,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev ff)


lsusb

Bus 005 Device 002: ID 0c45:63e5 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by anjilslaire on 2008-09-13
@ dmfield:

What method did you use to install? And how much space does it take on th 16gig SSD?

I'll have to read up on that  unetbootin again. I've read it but had no need to do it (yet).

---

### Post by Dogers on 2008-09-13
Webcam seems to be fine, I can load ekiga, cancel the wizard, hit the camera button and see myself..!

Also, for future reference (probably myself searching in a few weeks..) the wireless was being odd this morning - it was connecting but not receiving an IP. Turns out the PSK had been forgotten, so removing the network from the WLAN manager and readding fixed it! Not sure if thats a bug in Ubuntu or the HW, it's not something I've had with other HW on Hardy.


Output below:
```
andrew@minime:~$ lsmod
Module                  Size  Used by
michael_mic             3456  2 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
af_packet              23812  8 
nls_iso8859_1           4992  0 
nls_cp437               6656  0 
vfat                   14464  0 
fat                    54556  1 vfat
usb_storage            73664  0 
libusual               19108  1 usb_storage
ipv6                  267780  10 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  2 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
loop                   18948  0 
joydev                 13120  0 
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
psmouse                40336  0 
serio_raw               7940  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
ieee80211_crypt_tkip    11648  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
wl                   1062164  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
sdhci                  19076  0 
mmc_core               51460  1 sdhci
battery                14212  0 
ac                      6916  0 
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
evdev                  13056  7 
dcdbas                  9504  0 
snd_seq_oss            35584  0 
button                  9232  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
pcspkr                  4224  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                34760  3 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_piix               19588  2 
ata_generic             8324  0 
libata                159344  3 pata_acpi,ata_piix,ata_generic
r8169                  32900  0 
scsi_mod              151436  4 usb_storage,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  6 usb_storage,libusual,uvcvideo,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```
```

andrew@minime:~$ lsusb
Bus 005 Device 002: ID 0c45:63e5 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

```
andrew@minime:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by dmfield on 2008-09-13
hi, i plugged a usb cdrom drive into the netbook, and booted from the default cd, so the install took the same amount of space as a standard ubunt install 

how did you guys install via usb, because the webcam keeps hanging, and now the sd card wont recognise..

---

### Post by anjilslaire on 2008-09-13
Here's the official documentation
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

I haven't gotten one yet, I'm hoping in the next couple of months but I'm reading up & getting prepared.

---

### Post by mendieta on 2008-09-13
Guys

Thanks a lot for sharing. How does the **keyboard **feel? Is it any solid? How about the rest of the hardware?

This is my main trouble with the (early model) eeepc 701 (7 incher). It was comfortable but felt shaky. Indeed, it was unusable after a cleanup (I spilled orange juice). But Asus doesn't sell a replacement. I bought a replacement off ebay (apparently new), it only worked one more month. Right now, only half the keys work. 

I had enough, I am not dumping any more money on the eee. I'll by another low-cost ultraportable running Linux as soon as I can. Ubuntu is preferable, so the Mini-9 is the best choice. Your input is truly appreciated!

---

### Post by Dogers on 2008-09-14
Keyboard feels solid, but small :)

dmfield: I used this tool: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It downloads and sets up your USB pen with whatever you want, you just need to hit 0 when the mini is booting and tell it to boot from the USB key.

And another note for future reference: ssh hangs when trying to login, when connected via wireless. This seems to be a known bug in the "wl" driver - there's a fix already included in Intrepid for it. Don't know when/if it's coming to Hardy :(

---

### Post by LLauranzonIII on 2008-09-14
> **dmfield said:**
> hi, i plugged a usb cdrom drive into the netbook, and booted from the default cd, so the install took the same amount of space as a standard ubunt install 

how did you guys install via usb, because the webcam keeps hanging, and now the sd card wont recognise..

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

this is the easiest way i've seen to do it from usb.  i've tried it and it works great.

speaking of the dell mini, i just ordered mine last night.  got the ubuntu OS of course.  got 1GB mem and 16GB SSD.  looking forward to getting it.  will be a while, said estimated shipping of 10/20.  wonder if that's because of high demand or because they are still making them.

good review of it on notebook reviews:

[http://www.notebookreview.com/default.asp?newsID=4578&review=Dell+Inspiron+Mini+9](http://www.notebookreview.com/default.asp?newsID=4578&review=Dell+Inspiron+Mini+9)

---

### Post by dmfield on 2008-09-14
[LLauranzonIII]("http://ubuntuforums.org/member.php?u=168257")

I was quoted a delivery date of 18th Sept for mine, when it was ordered on the 4th.. The extended date i think is just dell CYA.

Interesting point to note.

If you load hardy 8.04.1 from a CD using a USB CD rom drive the Wireless, webcam and several other bits don't seem to work, however is you use the usb ool mentioned above to load the OS onto the unit, it works fine. Not sure whats going on there, both the CD and the USB are from the same ISO image..

Keyboard.. I have big fingers, and its a little annoying with the right shift key, hoever i've trained myself to just use the left one, feels tactile. 

Just gone back to using my Dell 1501 and the screen feels huge.

Had a play with KDE4 last night on the device, and it also seems to load and run, screen real estate seems to be more. as i've noticed some apps lie Evolution, are a bit hit and mis when adding a new mail account as they are designed for a larger screen, something the gnome team might want to think about.

Also tryed th netbook remix, not for me personally... feels like you are using a pda.

---

### Post by srt4play on 2008-09-14
Does it have any heat issues (particularly on the keyboard and touchpad)? Some of the reviews I've read on it state that it does get hotter compared to other netbooks.

---

### Post by dmfield on 2008-09-14
yes, as you would expect, it is a little hot on the base, not the keyboard, 

Something that has really impressed me, i used zattoo on my Dell 1505 with an ati graphics card which clips like a made man when you use compiz, i watched the whole F1 GP today in a coffee shop on oxford st while the wife went shopping, with no clipping or issues. fullscreen.

---

### Post by Hoshnasi on 2008-09-16
So, I'm confused.  There are a bunch of Mini 9 in the states that were sent out for reviews.  Like on [youtube]("http://www.youtube.com/watch?v=5M37j5BnERw").  If the Mini 9 is suppose to ship with Ubuntu Remix what versions do these youtube review setups have?  If its not Remix, can we expect different performance from the mini running Remix and vice-versa?

---

### Post by wolfkeeper on 2008-09-16
I don't think the Ubuntu versions have shipped yet, only the XP version. I've yet to see a review with Ubuntu running on the device out of the box.

I ordered the Ubuntu version, but my ship date is October 10th.

---

### Post by Hoshnasi on 2008-09-16
> **wolfkeeper said:**
> I don't think the Ubuntu versions have shipped yet, only the XP version. I've yet to see a review with Ubuntu running on the device out of the box.

I ordered the Ubuntu version, but my ship date is October 10th.

Dude, I linked a review to the Mini 9 running Ubuntu.  With the Dell Launcher.

---

### Post by McLogic on 2008-09-17
> **Hoshnasi said:**
> There are a bunch of Mini 9 in the states that were sent out for reviews.  Like on youtube.  If the Mini 9 is suppose to ship with Ubuntu Remix what versions do these youtube review setups have? 

The Ubuntu system is NOT shipping yet, only XP systems are going to customers. Dell does have review copies out with Ubuntu. The video you like to is from [Laptop Magazine]("http://www.youtube.com/watch?v=5M37j5BnERw").

Dell made their own interface/launcher, it is not the stock Netbook Remix, but who really knows (not me).



**Touchscreen** is missing from Dell Mini 9.

---

### Post by wolfkeeper on 2008-09-17
That youtube review was pretty useless, IMO. It really didn't tell me or show me anything that I haven't seen elsewhere. I'm more interested in seeing a review from an Ubuntu power user than a magazine or "news" site.

---

### Post by Hoshnasi on 2008-09-17
I'm trying to get to a larger point here.

We know that Dell sent out review minis loaded with Ubuntu.  Also, there are more video reviews online with the Ubuntu mini.  I just copied the first link I found.

So if we know they HAVE shipped Ubuntu minis, we can assume two things.

One, the DELL distro isn't complete or not ready for mass consumption and the review minis are NOT the same as what the consumer will get.

Or two, DELL is done with the Ubuntu for the Mini and they are just holding back to give Microsoft the early adopter revenue for people who won't wait.  

I assume the later actually.  I think DELL has been ready to go with the Ubuntu from the moment the review Minis went out.

---

### Post by dmfield on 2008-09-17
It may be a conspiricy theory but it might be both. Dell have recently stated they are going to continue selling Windows XP on their systems. This would be acceptable to Microsoft if they get first dibs on the mini 9 for a few weeks, for as you say ,those of us who just cant wait. This doesnt make Dell evil, just sensible. they never said the mini 9 was only going to have ubuntu on it, and you've got to admit Microsoft will be pushing a better advertising package than Canonical. Simple maths really.

I dont agree with it, however in a credit crunch, and a nee netbook market, numbers count, and Dell need numbers. catch up with Acer, Asus and HP.

On the subject of the netbook remix of ubuntu, not a fan myself.. but i'd like the drivers they use..

---

### Post by Hoshnasi on 2008-09-17
> **dmfield said:**
> It may be a conspiricy theory but it might be both. Dell have recently stated they are going to continue selling Windows XP on their systems. This would be acceptable to Microsoft if they get first dibs on the mini 9 for a few weeks, for as you say ,those of us who just cant wait. **This doesnt make Dell evil, just sensible.** they never said the mini 9 was only going to have ubuntu on it, and you've got to admit Microsoft will be pushing a better advertising package than Canonical. Simple maths really.

I dont agree with it, however in a credit crunch, and a nee netbook market, numbers count, and Dell need numbers. catch up with Acer, Asus and HP.

On the subject of the netbook remix of ubuntu, not a fan myself.. but i'd like the drivers they use..

I'm not a fan boy or anything, I don't think they are evil. I see lots of reasons why Dell would let windows have a crack that the early adopters.  Nor am I pushing a conspiracy theory.  I'm just trying to understand why Ubuntu is pre-order.  Had it been that it wasn't ready that could be good news.  Maybe the consumer version will get better battery life.  Who knows.

---

### Post by dmfield on 2008-09-17
my apologies if you thought i was inferring ou were a fanboy. all the Dell Mini 9 you have seen reviews of are prereleases, the os will be different, but not much, a tweak or two here and there.

---

### Post by notwen on 2008-09-18
Instead of making all these speculations from videos on the internet, we could just hold out and wait for the units to ship.  

Maybe even have a forum user share their personal experience w/ whatever variant of Ubuntu Dell/Canonical has thrown together once they receive theirs.  I'll be ordering one myself sooner or later,  likely sometime around the holiday season/new year.

---

### Post by dmfield on 2008-09-18
Now, i'm interested in the 3G capabilities of the Unit, the net is full or reports of having SIM card capabilities for 3G, i guess i need a card to slip in the bottom of the unit, but i don't know which one. I am already a Vodaphone 3G subscriber, and would be happy to top lugging my Linksys 3g Router around, or knocking out the USB dongle, and have the card inside the PC.

Anyone have any realworld information on this?

---

### Post by mfm3 on 2008-09-18
> **notwen said:**
> Instead of making all these speculations from videos on the internet, we could just hold out and wait for the units to ship.  

Maybe even have a forum user share their personal experience w/ whatever variant of Ubuntu Dell/Canonical has thrown together once they receive theirs.  I'll be ordering one myself sooner or later,  likely sometime around the holiday season/new year.
What a novel idea. I'm in. In fact, I have ordered mine and it's due before the end of October, if no one else beats me to it I'll post about the "mini OS powered by Ubuntu." I thought about getting the XP mini and wiping it, but nah, I'd rather not give Dell the idea that the XP mini is what I want. Too bad they won't just slap plain 'ol 8.04.1 on there and send it to me already! Oh well.

---

### Post by notwen on 2008-09-18
> **mfm3 said:**
> What a novel idea. I'm in. In fact, I have ordered mine and it's due before the end of October, if no one else beats me to it I'll post about the "mini OS powered by Ubuntu." I thought about getting the XP mini and wiping it, but nah, I'd rather not give Dell the idea that the XP mini is what I want. Too bad they won't just slap plain 'ol 8.04.1 on there and send it to me already! Oh well.

Sweet, gratz on your purchase and am looking forward to hear your thoughts on it.  =]

---

### Post by wolfkeeper on 2008-09-18
I've seen two photos from users with the XP version that shows Dell dropped the 3G/WWAN mini-PCI socket from the production version (the pre-production versions sent to reviewers had the extra mini-PCI slot, while the production version has no socket soldered to the mainboard.) Personally while it would have been nice I was planning to tether my Blackberry for data when needed.

I pre-ordered the Ubuntu version the day they were announced and got a 10/10 shipping date, so it sounds like there's a good number of pre-orders out there.

---

### Post by mfm3 on 2008-09-18
Yeah, maybe dell will surprise us all and ship them early. I've actually had a buddy receive his dell way before they said it would ship. Here's hoping!

---

### Post by Hoshnasi on 2008-09-18
A rep contacted me to confirm my order when I asked her about the delay and if the mini will ship early she said.

"Dell set the ship date very high to prevent over extending themselves, since the OS won't even be available to us till sep. 15-19.  But historically, if it follows our other releases will ship before the date on the site."

---

### Post by felixgonschorek on 2008-09-19
Ordered mine on tuesday and it arrived today (germany) - the first statement form dell was, that it will arrive on oct. 7th or sooner, now it took only three days!

i ordered the xp version, too. booted xp once only to see that it's messed up with trial software. now the ubuntu installation is 99% finished. gotta reboot, cu :)

---

### Post by solitaire on 2008-09-19
Vodafone will be shipping the HSDPA emabled Mini 9 from October..

It's free with a £25 month mobile data plan (1Gb monthly limit 2 year contract).

[http://www.reghardware.co.uk/2008/09/18/vodafone_prices_up_mini_9/](http://www.reghardware.co.uk/2008/09/18/vodafone_prices_up_mini_9/)

---

### Post by anjilslaire on 2008-09-19
> **felixgonschorek said:**
> Ordered mine on tuesday and it arrived today (germany) - the first statement form dell was, that it will arrive on oct. 7th or sooner, now it took only three days!

i ordered the xp version, too. booted xp once only to see that it's messed up with trial software. now the ubuntu installation is 99% finished. gotta reboot, cu :)

Let us know how it runs after you get up & going fully :)

---

### Post by akafudge on 2008-09-19
Guys, can I prepare a USB stick when I only have XP? I don't have an external cd either.

Thanks

Jonathan

---

### Post by wolfkeeper on 2008-09-19
I'm guessing this will work?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by akafudge on 2008-09-19
Thanks Wolfkeeper, I was being a prick and downloaded the Linux version and wondered why it did not work hence the post :-)

Cheers buddy.

---

### Post by dirkoneill on 2008-09-19
My XP version just arrived today. It was scheduled to ship on Sept 22nd so this was a nice surprise. I'm going to wait a few days to wipe XP. I want to see how everyone else fares. I do have a few questions for those brave souls.

Does the microphone work on the 0.3MP web cam in Ubuntu?
Has anyone enabled the Ubuntu Remxi UI? Do you like it better?

---

### Post by anjilslaire on 2008-09-19
I'm thinking when I get one (hoping by Christmas) I'll load Xubuntu on it. Less resources, but a full OS goodness. Anyone else try Xubuntu, or are we all sticking to vanilla Ubuntu?

---

### Post by jbloodwo on 2008-09-19
I like the thought of xubuntu.  xfce is much lighter than GNOME.  
the other choice if you are hardcore would be windowmaker or afterstep.  I just orderd a mini9 with the dell customized ubuntu so i dought i will wipe it.  I might however install xfce or afterstep to use in place of Gnome.

---

### Post by skroops on 2008-09-20
Anyone have any luck getting sound working on the mini 9 with hardy?  I can't get anything with OSS or ALSA.

edit: nevermind, found the solution on the first post....

---

### Post by Steve_Barker on 2008-09-20
I looked at the price of the mini, and the 1525 with Ubuntu, and decided for the minnimal extra cost, might as well get a full sized laptop.

It arrived yesterday and seems, excellent - except there is hardly any volume to the sound - any idea how I can make it louder?

---

### Post by orx on 2008-09-20
Hi,

does the mini have an internal microphone ?
Can't get it working with skype ...   :confused:

I've increased the volume of internal via alsamixer like written here: 
[https://lists.ubuntu.com/archives/ubuntu-us-md/2008-September/000370.html](https://lists.ubuntu.com/archives/ubuntu-us-md/2008-September/000370.html)

but no luck.
Maybe there isn't any build in mic, just the jack ?

---

### Post by skroops on 2008-09-20
> **Steve_Barker said:**
> I looked at the price of the mini, and the 1525 with Ubuntu, and decided for the minnimal extra cost, might as well get a full sized laptop.

It arrived yesterday and seems, excellent - except there is hardly any volume to the sound - any idea how I can make it louder?

Normally it's better to start a new thread for questions like that.
This looks like it might be a solution: 

[http://ubuntuforums.org/showthread.php?t=872038]("http://ubuntuforums.org/showthread.php?t=872038&highlight=inspiron+1525+volume")

or this

[http://ubuntuforums.org/showthread.php?t=908440]("http://ubuntuforums.org/showthread.php?t=908440&highlight=inspiron+1525+volume")

---

### Post by jbloodwo on 2008-09-20
> **Steve_Barker said:**
> I looked at the price of the mini, and the 1525 with Ubuntu, and decided for the minnimal extra cost, might as well get a full sized laptop.

It arrived yesterday and seems, excellent - except there is hardly any volume to the sound - any idea how I can make it louder?
I have a Vostro 1400 that is my primary system... I Know that there is not that much price difference when you bump the memory and ssd size.  however, I am getting this for what it is intended.  IM'g from the sofa and using at coffee bean and tea leaf or peets coffee to study and take notes.  
Also, it is the perfect size to take to church for taking sermon notes.
---Edit---
oops i should not have replied.

---

### Post by DyingSoul on 2008-09-20
i like this mini 9 and was planning to buy. but my main focus of buying a notebook is to use linux (specially ubuntu). 

so can anyone ensure me..
if i copy the ubuntu cd to my usb drive (pen drive) and install it from there..will i be facing any problem? will i be able to install it properly? will it work without any trouble?

---

### Post by superm1 on 2008-09-20
> **DyingSoul said:**
> i like this mini 9 and was planning to buy. but my main focus of buying a notebook is to use linux (specially ubuntu). 

so can anyone ensure me..
if i copy the ubuntu cd to my usb drive (pen drive) and install it from there..will i be facing any problem? will i be able to install it properly? will it work without any trouble?
If you haven't bought it yet, and are planning to use it with Linux, purchase it with Linux.  You will get formal support, and it will run a lot better.

---

### Post by Ubialect on 2008-09-20
Hello,
thanks for the review !

> **superm1 said:**
> If you haven't bought it yet, and are planning to use it with Linux, purchase it with Linux.  You will get formal support, and it will run a lot better.

I bought this mini in france (only XP preinstall is available and no preorder yet) and installed Ubuntu 8.04.1 on it. The system works pretty well so I wonder what do you mean by "A lot better" ?
But, more important, will dell and Ubuntu distribute the mini9  adapted version of Ubuntu ?

---

### Post by DyingSoul on 2008-09-20
> **superm1 said:**
> If you haven't bought it yet, and are planning to use it with Linux, purchase it with Linux.  You will get formal support, and it will run a lot better.
i haven't bought it yet..planning to buy..bt there's no notebook in Bangladesh which has Linux installed in it (i'm from Bangladesh & it's hard to find linux in notebooks)..they provide either Windows or no OS..so i hav to set my mind.

i think i hav to buy mini 9 with Windows installed in it..so, should i buy..? or go for regular 14.1" laptops..?

if i buy a mini 9 with windows installed in it..i'll remove that OS and setup ubuntu. will that be a problem regarding performance and support..?

what do u gys suggest..?

---

### Post by superm1 on 2008-09-20
> **Ubialect said:**
> Hello,
thanks for the review !



I bought this mini in france (only XP preinstall is available and no preorder yet) and installed Ubuntu 8.04.1 on it. The system works pretty well so I wonder what do you mean by "A lot better" ?
But, more important, will dell and Ubuntu distribute the mini9  adapted version of Ubuntu ?
The installed image includes a non trivial amount of customization to make it run better than vanilla 8.04.1 will run.
This means a handful of kernel patches that aren't yet in SRUs, user experience customization, and being built for the correct architecture (lpia).

---

### Post by LLauranzonIII on 2008-09-21
here is a good review of it:

[http://www.notebookreview.com/default.asp?newsID=4578&review=Dell+Inspiron+Mini+9](http://www.notebookreview.com/default.asp?newsID=4578&review=Dell+Inspiron+Mini+9)

---

### Post by stefan-b on 2008-09-24
Thanks for sharing guys.

I bought my Mini 9 in France (only the XP version is available here). I installed Hardy from USB stick without problems.

**Wifi:** No WiFi on the freshly installed system. After upgrade I got partial WiFi support: I could connect to my neighbors' open network :-$  but not to my WPA-protected network. I had to install ndiswrapper + Windows driver to make it work.

**Sound:** the same problem but now it's ok (thanks dmfield).

**Webcam:** works fine with ekiga, skype and cheese.

The only problem I have is **bluetooth**. I have a built-in [bluetooth card](http://support.euro.dell.com/support/edocs/systems/ins910/en/sm/btooth.htm#wp1179885) that worked with Windows. Now I can't see it. Neither lsusb nor lspci show something that looks like a bluetooth card. On the other hand I have bluetooth kernel module loaded. Here is some output:

```

# lsmod | grep bluetooth
bluetooth              61156  4 rfcomm,l2cap

# dmesg | grep Bluetooth
[   38.221832] Bluetooth: Core ver 2.11
[   38.222810] Bluetooth: HCI device and connection manager initialized
[   38.222819] Bluetooth: HCI socket layer initialized
[   38.273815] Bluetooth: L2CAP ver 2.9
[   38.273827] Bluetooth: L2CAP socket layer initialized
[   38.387610] Bluetooth: RFCOMM socket layer initialized
[   38.387640] Bluetooth: RFCOMM TTY layer initialized
[   38.387646] Bluetooth: RFCOMM ver 1.8

# hcitool dev
Devices:


```

I am a little bit :confused:  Do you guys have bluetooth cards in your machines and could you make them work? Any ideas and suggestions are welcome.

---

### Post by sagat on 2008-09-24
Installed it in the wee hours of this morning after making a bootable USB with hardy on it (DyingSoul it worked nicely), leaving xp on for dual boot congestion on the 8GB drive. Will wipe the entire thing once I can get the Dell specific build for the machine. I tweak Ubuntu to the non-Dell Netbook Remix version and everything appears to be working great. The issue with the sound mentioned previously and some weird network searching such as not recognising the ethernet cable has been removed. Everything else - card slot, camera worked perfectly upon rebooting following installation of all updates.

---

### Post by dmfield on 2008-09-24
I've been playing a bit more with the system, and have to say, KDE4.1 with a few minor tweaks works VERY well on the Dell Mini 9, the Ubuntu interface can be a bit big for the small screen, KDE 4.1 does work better on a smaller screen. 

Befor i get flamed, this is only an opinion, and your perfectly within your rights to not like KDE, and stick to Gnome, i'm posting this for  Choice.

I've updated the Community Wiki at 

[https://help.ubuntu.com/community/DellMini9#KDE%204.1](https://help.ubuntu.com/community/DellMini9#KDE%204.1)

**KDE 4.1**

  
 
**Why?**

 I've found the KDE 4 interface to be beter with the 1280x600 screen resolution, Gnome is a great interface, but using packages such as Gimp and Evolution don't scale down corectly, so clicking on next and cancel buttons can be a bit of guesswork. 
 
**Installing Kubuntu**

 The KDE 4.1 version of Kubuntu can be downloaded from here,  
[http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download) 
like Ubuntu, we are looking to use the 8.04.1 release of Kubuntu, you will also need to choose the option marked 
*Kubuntu 8.04 KDE4 Remix - Featuring the cutting edge KDE 4 with community support only* 
Boot from the CD, and install the complete OS, reboot when the installation is complete. 
This part of the install can also be done, with the downloaded ISO, and the information found on [Install from USB Stick]("https://help.ubuntu.com/community/Installation/FromUSBStick") 
However to get the wifi to work, you will need to run 

[LIST]
[*]**sudo apt-get update** **sudo apt-get upgrade** 
[/LIST]
Then reboot the PC, alternatively, the Ethernet port should work fine. 
 
 
**Updating the packages**

 Once rebooted, the default Kubuntu 4.1 install isn't the prettiest one, however we can ensure things are a lot more streamlined, by installing the additional packages from the Launchpad repositories. 
Open the Konsole app and enter the command 

[LIST]
[*]**sudo nano /etc/apt/sources.list** 
[/LIST]
and add the line 

[LIST]
[*]**deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main** 
[/LIST]
to the nd of the list, save the file, and exit 
Update the repostitory 

[LIST]
[*]**sudo apt-get update** 
[/LIST]
Once the update has complete, you will need to update some packages. 

[LIST]
[*]**sudo apt-get install kubuntu-kde4-desktop kdeplasma-addons amarok-kde4 and kontact-kde4 kate-kde4 kmail-kde4** 
[/LIST]
I've installed a few extra packages from the norm, the **Amarok 2** is still flaky at time of writing, let all these packages install and reboot the PC, the login screen might still look a bit strange, compared to the rest of the layout, which should now have the more up to date backdrop. 
Open Konsole again, and type  

[LIST]
[*]**sudo apt-get update** **sudo apt-get upgrade** 
[/LIST]
With this done, not only is the interface more streamlined, applications and dialog boxes which would normally open larger than the screen size will become scalable. 
Install all the updates, and reboot. You should now have a cleaner looking system, to get the soundard working, followin the above instructions, for fixing the soundcard. 
 
 
**Additional Packages**

 some additional packages whick you may wish to install, in order to make KDE 4.1 just that little more "appealing" are 
***kpowersave**            - provides a system tray icon displaying remaining power ***kscreensaver-kde4**     - provides screen savers 
 
 
**Interface changes**

 
[LIST]
[*]**GTK-QT** 
[/LIST]
To improve the look of GTK (Gnome) apps, use the gtk-qt-engine-kde4 ackage, which makes the apps look a little more slick. 

[LIST]
[*]**sudo apt-get install gtk-qt-engine-kde4** 
[/LIST]
 

[LIST]
[*]**FONT SIZES** 
[/LIST]
The default font sizes are very large, and I'd recommend editing the font sizes in the System Settings section, to about 8, keep the fonts however as changing them can make the system look a little strange.e 
 

[LIST]
[*]**LANCELOT** 
[/LIST]
If you're not a fan of th new KDE menu, thats ok, its a plasmoid, and cna be change easily, using [Lancelot]("http://lancelot.fomentgroup.org/download") as you've already added the necessary repostory, this can be installed quickly, (From Konsole) 

[LIST]
[*]**sudo apt-get install plasmoid-lancelot** 
[/LIST]
Then add the new Widget on the Deskbar plasmoid. 
 

[LIST]
[*]**Cairo Dock** 
[/LIST]
Cairo-dock is an animated application launch bar for the desktop comparable to Mac OS X's Dock, or Rocket Dock (for those of you who come from Windows). 
It is compatible with Compiz-Fusion, Beryl, Compiz, and also Xcompmgr, but it can run without a composite manager (with fake transparency). Cairo-Dock can run under GNOME, KDE, and XFCE. 
More information about Cairo-Dock can be found here [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock) 
 

[LIST]
[*]**Change the Login Screen back to GDM** 
[/LIST]

[LIST]
[*]**Usplash change** 
[/LIST]
KDE 4 will change the USplash (graphical boot and shutdown) theme to Kubuntu. Run these two commands to switch back to the Ubuntu theme, the first will prompt you to select the theme you want: 

[LIST]
[*]**sudo update-alternatives --config usplash-artwork.so** **sudo update-initramfs -u** 
[/LIST]
 
 
[B]
[/B]

---

### Post by RookiePaul on 2008-09-25
Hi Guys,

I have a Dell Mini 9 and I have dual booted it using Wubi with 8.04.  Everything seems to be good but I can't get the wireless working.  I have done all the updates.  I even tried going the ndiswrapper route.  I am now back on the restricted drivers route.

When I perform iwlist scan it tells me that none of the interfaces support scanning.  It's starting to do my head in.

Any ideas?

Many thanks.

---

### Post by lanewinfield on 2008-09-26
Well, I just got my Mini 9 a couple days ago, and while I haven't installed linux (truly and used it) on  one of my computers yet, I may soon take the dive.

I'm a mac person (didn't use to be&#8212;built computers, played games, and the like), so Windows XP is crap to me now.

I got Ubuntu onto a USB drive (easy enough) and I booted to that to see what it was like, and I definitely liked what I saw. Much smoother and more beautiful than Windows, and ran really like a charm.

There really is only one reason why I'm holding back on installing it: the trackpad is almost unusable on it! I tried changing the settings and I just couldn't get it to a reasonable level. It seems stuck between so slow that it's like moving a boulder across the screen and so fast that I'd never be able to click in the right place.

Anybody have any suggestions how I could fix that if I decided to dual boot?

EDIT: Oh, and also, in return for some help, I'd love to answer any questions people have about the hardware or my personal opinion on the device. Just let me know what you're wondering about!

---

### Post by RookiePaul on 2008-09-26
Well the trackpad seems ok to me under Ubuntu 8.04.  It's a hell of a lot more responsive in ubuntu than in XP.  In all seriousness the machine flies with Ubuntu on it, much faster loading firefox and other software than it's counterpart in XP.  If I could only get the wifi to work I'd ditch XP altogether and opt for a single ubuntu boot.

---

### Post by orx on 2008-09-26
i had the 'SSH hangs and then discons after typing password' Problem over wlan.
this solved it with ndiswrapper:

[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)

---

### Post by skroops on 2008-09-26
Been running hardy on the mini 9 for a little while now, and I've only run into a few minor problems:

* Suspend sometimes causes a kernel panic.

* Sometimes weird stuff happens when writing text.  I've tried setting syndaemon to suppress touchpad input for 1 second after typing, which helps.  For some reason though, random words or parts of words will appear in the middle of typing.  This stuff might be in the clipboard, but it might not.  No idea what's going on here.

* Many windows don't fit on the screen, and I can't find the option to allow me to move it up past top of screen with alt+drag.  I think this is a compiz thing but still can't find the option, especially when I can't see the compiz config dialogs the whole way.  Catch-22

* WPA enterprise not working, probably not mini 9 related: [http://ubuntuforums.org/showthread.php?p=5859957](http://ubuntuforums.org/showthread.php?p=5859957)

* Wireless takes a while to come back on after suspend (maybe 2 minutes?)

Good things about ubuntu on the mini 9:
* Fast.  Sometimes it takes a moment for the apps to start, but I haven't experienced any slowdown, and I'm a tab freak.  Bootup feels pretty quick, wake from suspend is very fast.

* Screen real estate is actually pretty good.  I have both top and bottom panels enabled and don't feel cramped at all.

* Battery power is excellent.  OS estimates 3:50 for a full charge, it feels much longer.  and even at 15% charge you still have plenty of uptime.

My two cents, if anyone has solved some of my issues, please let me know.

---

### Post by dmfield on 2008-09-26
If you are having wifi issues, i can say there does appear to be a bug with the wifi, and i'm trying to fiure out what. Id be interested to know, if the wl appears under Hardware Drivers in the System menu. mine says it knows of a restricted driver called wl, but its not in use, this happens under KDE 4.1 or Gnome.

I found that if i put a USB Wifi stick into the device, booted, and then attached to a wifi network, then rebooted the PC, the restricted driver would then change from not using to using.

The reason i think there is a bug, i work for a company in the UK, and we develop a fully encrypted USB Stick thin client solution and e are migrating from Debian Etch to Ubuntu, and on our pre alpha release, the wifi works, but Ubuntu isn't using the resticted driver. however inists that it must use it. As part of this build we are stripping apps out of Ubuntu and kernal modules. so on Monday i'll see if i con figure out a way of kick starting the resticted driver.

---

### Post by skroops on 2008-09-26
> **dmfield said:**
> If you are having wifi issues, i can say there does appear to be a bug with the wifi, and i'm trying to fiure out what. Id be interested to know, if the wl appears under Hardware Drivers in the System menu. mine says it knows of a restricted driver called wl, but its not in use, this happens under KDE 4.1 or Gnome.

The wl driver is enabled and in use on my mini9

I've had the problem your describing on my inspiron 1525 though, after a fresh install of hardy.  At one time I got it working by some random enabling/disabling of the restricted driver along with reboots.  The most recent time I installed hardy on it, it got solved when I ran the updates.

---

### Post by mypup on 2008-09-26
I tried the kubuntu route but had some issues so i just installed hardy off the cd took some time but I am wondering what tweaks i need to do to make it play nice with the ssd. I hope someone will make an iso so noobs like me can have an easy route to getting things right. [http://img.flashtux.org/img132691f98cxe3d338d7.png]("http://img.flashtux.org/img132691f98cxe3d338d7.png") <screencap compiz works well and sound is ok I have only had it running for a few hours so Im sure i will have other issues I need to correct. I hope someone will go into detail on what all needs to be done. Thanks for all the tips on sound ect.

---

### Post by dmfield on 2008-09-26
mypup, can you list your issues
and whats the bar running under the gnome panel

---

### Post by mypup on 2008-09-26
thats conky still needs work for ip and network as for issues I just need to know if the cd install will be kind to the ssd (as too minimize writes) and the scale of windows in applications I will have to look over more. I would like to know how to get skype installed. Sorry I am fairly new to linux and need all the help i can get. I would also like to know if there is an irc channel up for the dell mini anywhere if someone knows or any other forums out. I do have to reconnect to my wifi each time it doesnt connect automatically. I would like to install wine as to run office 2003 but would like to install it to a sd card if possible? then what would i need to do to make it see it as a hard drive.

---

### Post by gregconquest on 2008-09-26
Can bootloaders, like BootIt NG, or maybe just grub or LILO, be installed on SSD's just like regular hard drives?

I'd like to dual boot -- between the DELL-customized ubuntu (netbook remix?) and kubuntu . . . not interested in trying this with WinXP. With a 16GB SSD, I think space will be OK.

I also plan to put a 16GB SDHC in my ubuntu mini 9 and use that for data storage.

Greg

PS I also want to try installing VMware and running a virtual WinXP I've already been using. I got a 2GB RAM SODIMM already to help in this. The two things I worry about: 1) read/write speed for my 8GB virtual WinXP presumably being run from the SDHC. 2) scaling down the resolution of WinXP to run on the mini. If it doesn't work, it is no great loss.

---

### Post by dmfield on 2008-09-27
To answe some of your questions

**Skype**[INDENT]This one is easy, the key here is adding the Medibunti repository, which not only gives you Adobe Acrobat reader, W32Codecs, libdvdcss2 (i have an external DVD Drive) and of course skype to name but a few The community webpage is at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) its really easy to follow, 
[/INDENT]**Wine/Office 2003**[INDENT]No need to condone any use of a windows package, as Linux is all about choice, the fact you can run them, and not vice versa is more amusing to me. However, what i'd recommed to get this running is [WineDoors]("http://www.getdeb.net/app/Wine-Doors"), from the excellent [Get Deb]("http://get-deb.net") site. Wine doors offers you a great point and click interface for seting up wine with all the necessary windows packages, once loaded installing WinOff2003 is a doddle. I've heard tell, that Office 2007 now installs with wine.

[IMG]http://www.getdeb.net/media.php?id=364&type=screens&w=425&h=350[/IMG]

If you'd like an alternative to MS Office or  OpenOffice however, just take a gander at [IBM/Lotus Symphony]("http://symphony.lotus.com/") who have listened to the community and recently added an [Ubuntu Installer ]("http://symphony.lotus.com/software/lotus/symphony/home.nsf/ubuntu")for the software (deb file) which wll make things easier for you.
[/INDENT]**SD Card mount as part of the hard disk**[INDENT]This will involde a little command line work, howeve not a lot. you'll need to create a folder, and ad the folder and sd card to th fstab which sets what drives to mount onboot. as unlike windows you don't have c: d: etc, lifes a file as they say, well in this case a folder. )sorry if you know this, but someone else reading may not)

Open up a terminal window.

make sure you are in your home folder

> cd ~make a new directory (name and location are optional)

> mkdir datanow we need to edit the fstab file, and create the "mountpoint" becareful, there do be dragons in here, and i'm basing this on my dell mini 9, i'll to check what the device is listed as (as a confirmation) put the SD Card in the machine, once the nautilus window pps us, its then mounted, and type in to the Termainal window

> mountThe last line of the test which appears said this at the start

> /dev/mmcblk0p1so now again n terminal i enter

> sudo nano /etc/fstab**[COLOR=Red]Be Careful[/COLOR]** [B][COLOR=Red]type 

> sudo cp /etc/fstab /etc/fstab.origto make a backup of this file, if you are not sure or have never done this before[/COLOR][/B]

at the end of the fsab file enter this

> /dev/mmcblk0p1    /home/[COLOR=Red]**<your folder>**[/COLOR]/data   vfat   user,auto,exex 0 0Where i have entered [COLOR=Red]**<your folder> **[COLOR=Black]you put the name of your home folder, so my entry acually looks like his

[/COLOR][/COLOR]
> /dev/mmcblk0p1    /home/[COLOR=Red]**david**[/COLOR]/data   vfat   user,auto,exex 0 0Save the file (Ctrl X, you will be prompted to save/overwite the file, answer yes)

next time you reboot, your SD card will be mounted on the data folder, its a windows compatile format, so can be used on other devices such as a video camera, and if you don't ut it in, won't stop linux from booting, it will just ignore the fstab entry
[/INDENT]I hope that goes some way to answering some of your questions.

---

### Post by mypup on 2008-09-27
dmfield thank you so much, without your help I would have not gotten everything working. You have been a great help and made this so much easier for me to install. Thanks again.

---

### Post by anjilslaire on 2008-09-27
> **gregconquest said:**
> I got a 2GB RAM SODIMM already to help in this

So has it been confirmed we can put a single 2gig ram chip in ourselves rather than be stuck with 1gig maximum? Does having 2gig feel speedier on the Mini 9?

---

### Post by doggyworld on 2008-09-28
Yes.. I have put 2gb in mine and it works great.  Although I'm on Windows XP at the moment.. :)  Waiting for someone to get the Dell Ubuntu for the Mini. :)

---

### Post by beni on 2008-09-28
I bought a Dell mini 9 with XP. Did a fresh install of Ubuntu 8.04.1 via USBStick and completely happy with it now ^^ everything ran smoothly, much faster than it did in XP. I got wifi, sound, webcam working. But the **microphone** doesn't work so I can't make a functional Skype call :( does anyone know how to fix it? I tried to use an external microphone and it worked so I guess it must be some problem with the microphone driver.

---

### Post by orx on 2008-09-28
I think there is no internal mic.

I've even asked a blogger who still has XP on the mini ...

---

### Post by dmfield on 2008-09-28
there is NO internal mic, so its a trip to amazon i would guess.

Also for the lilo/grub question, you can use boot loaders on the ssd its just like a normal hard disk. i would suggest however you dont need an ubuntu partition AND a kubuntu partition, as if you load ubuntu, then follow my previous kde41 instructions from the section where you add the launchpad repository.

then when you boot, you can click on the session menu within the login screen, and choose to run either kde or ubuntu.

[IMG]http://www.matusiak.eu/numerodix/blog/wp-content/uploads/gdm1.png[/IMG]


they are the same os, unlike windows you can run multiple gui's on the same underlying os.

---

### Post by gregconquest on 2008-09-28
> **orx said:**
> I think there is no internal mic.

I've even asked a blogger who still has XP on the mini ...

According to:
[http://support.euro.dell.com/support/edocs/systems/ins910/en/sm/mic.htm#wp1180150]("http://support.euro.dell.com/support/edocs/systems/ins910/en/sm/mic.htm#wp1180150")
> NOTE: The analog microphone is not present if you have ordered the optional camera. Instead, you will have digital array microphones with the camera.

So, there appears to be a mic in either version.

Greg

---

### Post by dmfield on 2008-09-28
i retract my previous statement on the microphones. 

Double click on the sound level icon in the taskbar, and choose 

Edit/Preferences choose internal source

An options tab should appear, choose mic or front mic and make sure the internal mic boost is set to high.

was able to use skype then..

---

### Post by beni on 2008-09-28
awesome! thanks you guys :D this is my best Ubuntu experience ever, everything works well and fast!

---

### Post by gwbennett on 2008-09-28
> **gregconquest said:**
> Can bootloaders, like BootIt NG, or maybe just grub or LILO, be installed on SSD's just like regular hard drives?

I'd like to dual boot -- between the DELL-customized ubuntu (netbook remix?) and kubuntu . . . not interested in trying this with WinXP. With a 16GB SSD, I think space will be OK.


Short answer. Yes. That will work fine. I am dual booting win xp and Ubuntu. However, the situation you are describing (wanting KDE and Gnome) doesn't necessarily require a dual boot setup.

You might consider just installing KDE4 from within Gnome. Then when you log in you can choose either. Would use a lot less space that way too, cause you'd only be installing 2 DE's instead of 2 operating systems that are in reality the same.

But to answer your question, yes you can do it the way you suggested. And I also put a 16 GB SDHC card in, and mounted my /home to a partition there. So I have about 3 GB free in Windows XP, 3 GB free in Ubuntu, and 16 GB free in my /home directory within Ubuntu.  Works wonderfully.

---

### Post by hardcrash2 on 2008-09-28
anjilslaire - definitly confirmed on 2gb stick. swapped mine in 5 minutes after getting mini. recognized in xp and in ubuntu 8.04.1, installed as soon as i got home. 

My only issue is bluetooth. not working with any bluetooth device. tried logitech mouse and wiimote.

---

### Post by rlwilen on 2008-09-28
it not any here in USA I think it would get there before get here When i see it there i will till and should be there to well talk to you lattter

---

### Post by mypup on 2008-09-29
I have not been able to use blue tooth either, if anyone comes up with a solution please pass it on. Also I have a question about running the desktop version of Ubuntu 8.04 LTS (hardy) is it ok to run as installed from the iso or do I need to do something (tweak it) to make it not write so much to the ssd and does the remix version minimize writes on the ssd and should I be using it when I can get a copy somewhere for the mini ? Thanks for all the help I just want to do whats best for the machine to make it last as long as possible.

---

### Post by budius on 2008-09-30
I've just bought mine with the XP (here in UK the Ubuntu version comes only with the 8gb SSD) but I was thinking if anyone that bought the Ubuntu version would make an .iso out of the CD and post for us? Torrent or one of those 'rapidshare' like websites.

Cause in that CD for sure got ALL the necessary drives plus the dell 'cute' interface!

thanks :guitar:

---

### Post by dmfield on 2008-09-30
MyPup what do you want to do with the bluetooth? And i'll see if i can et it working. I've got it working wih my bluetooth headset.

---

### Post by alih on 2008-09-30
Hi,
I also can't get bluetooth working, pings don't go over pand connection :confused:

Also, "sudo hcid -n" says:
[INDENT] hcid[6138]: Bluetooth HCI daemon
 hcid[6138]: Could not become the primary owner of org.bluez
 hcid[6138]: Unable to get on D-Bus[/INDENT]
org.bluez is visible in qdbusviewer.
/etc/dbus-1/system.d/bluetooth.conf does contain the necessary permission:
[INDENT]<policy user="root"><allow own="org.bluez"/></policy>[/INDENT]

Do you have an idea what's wrong?

---

### Post by anjilslaire on 2008-10-01
> **budius said:**
> but I was thinking if anyone that bought the Ubuntu version would make an .iso out of the CD and post for us? Torrent or one of those 'rapidshare' like websites.

Cause in that CD for sure got ALL the necessary drives plus the dell 'cute' interface!


Since Dell will be shipping these with licensed codecs for some multimedia formats, I would think they would frown on someone imaging their install disc. 
Better to wait for their official release with all drivers sans codecs.

---

### Post by mypup on 2008-10-01
dmfield I really dont have a need for the bluetooth at the moment just would like to know how when the time comes I rarely use it much on any machine but would be a plus since I have it. Im not sure if you all have seen this video at jkmobile where he installed a 32gb ssd myself I hate to admit it but i dual-boot xp and hardy on m 16gb my doze partition is only 4gb using 1.5gb currently the rest is for Ubuntu which is more than enough. But some may be interested in more space they have 32gb and 64gb I believe they are 100 dollars for the 32gb and 199 for the 64gb ssd and the same speeds as the original dell drives. see here->[http://jkkmobile.blogspot.com/2008/09/32bg-ssd-on-dell-mini-9.html]("http://jkkmobile.blogspot.com/2008/09/32bg-ssd-on-dell-mini-9.html") and the drives ship worldwide here-> [http://www.mydigitaldiscount.com/CategoryProductList.jsp?cat=Browse+By+Brand%3AMyDigitalSSD%3AMyDigitalSSD+PCI+Express+PCI-e+SSDs:Dell+Inspiron+Mini+9+PCI-e+SSDs]("http://www.mydigitaldiscount.com/CategoryProductList.jsp?cat=Browse+By+Brand%3AMyDigitalSSD%3AMyDigitalSSD+PCI+Express+PCI-e+SSDs:Dell+Inspiron+Mini+9+PCI-e+SSDs") sorry for the long link was at work and in a hurry my bad.

---

### Post by dmfield on 2008-10-01
just bought a 64gb one, so cheers for that link. I've been playing with bluetooth today, and managed to get my bluetooth headset to pair up for skype which was kind of cool, will how to tomorrow, heroes is back on in a minute

---

### Post by mypup on 2008-10-02
Im wondering if anyone could make an iso of hardy that would be mastered for the dell mini? Since I am a noob I have no idea what I should do. For example I had first installed hardy on my mini with the default installation setup. So last night while reading I found that I should not use the ext3 file system and no swap as well. Currently I have one ext2 partition with no other tweaks. I have been reading more about how to minimize writes ect but havent a clue on all the ends and outs to setup this in the proper manner. So it would be great for me and others like me that have little to no experience to have someone with the knowledge and skills to make an iso for the mini. I would greatly appreciate it if someone would help us out to provide us with a great Ubuntu experience.

---

### Post by snowpine on 2008-10-02
> **mypup said:**
> Im wondering if anyone could make an iso of hardy that would be mastered for the dell mini? Since I am a noob I have no idea what I should do. For example I had first installed hardy on my mini with the default installation setup. So last night while reading I found that I should not use the ext3 file system and no swap as well. Currently I have one ext2 partition with no other tweaks. I have been reading more about how to minimize writes ect but havent a clue on all the ends and outs to setup this in the proper manner. So it would be great for me and others like me that have little to no experience to have someone with the knowledge and skills to make an iso for the mini. I would greatly appreciate it if someone would help us out to provide us with a great Ubuntu experience.

Your best bet is to lobby Dell to make their special Mini 9 Ubuntu available as a download. I know there are others on the board who would gladly join you on that effort. Currently as far as I know it would be illegal to re-distribute without Dell's permission. I definitely envision that within the coming months, we'll see a lot of "user remixes" for the Mini 9, just as has happened with the EEE.

---

### Post by gregconquest on 2008-10-02
> **mypup said:**
> Im wondering if anyone could make an iso of hardy that would be mastered for the dell mini? Since I am a noob I have no idea what I should do. For example I had first installed hardy on my mini with the default installation setup. So last night while reading I found that I should not use the ext3 file system and no swap as well. Currently I have one ext2 partition with no other tweaks. I have been reading more about how to minimize writes ect but havent a clue on all the ends and outs to setup this in the proper manner. So it would be great for me and others like me that have little to no experience to have someone with the knowledge and skills to make an iso for the mini. I would greatly appreciate it if someone would help us out to provide us with a great Ubuntu experience.

This is a good idea, but why not just order the system with ubuntu to begin with? It's a win-win situation if you do -- ubuntu becomes more popular and you get a more stable, easier-to-set-up system.

I've also noticed that at least the webcam is different in the two systems. The 1.3MP webcam has only been available with linux. If there are other hardware differences, buying a Windows mini 9 and then wiping the drive and installing ubuntu is a lose-lose situation. You end up with a system that takes an inordinate amount of effort to get running IF EVER, and no one ever even knows you're running linux. You're just another Windows licensee.

Greg Conquest

---

### Post by mypup on 2008-10-02
I really didnt want to get flamed but I got mine with xp because they are not shipping Ubuntu here yet. I also dual-boot mine currently and while the legalities of sharing the dell interface I understand I thought maybe someone would remaster an iso of there tweaked free version. I have mine now with one ext2 partition with noatime edited fstab. Im am a noob to linux and thought maybe someone with skills could share in there experiences.

---

### Post by snowpine on 2008-10-02
> **mypup said:**
> I really didnt want to get flamed but I got mine with xp because they are not shipping Ubuntu here yet. I also dual-boot mine currently and while the legalities of sharing the dell interface I understand I thought maybe someone would remaster an iso of there tweaked free version. I have mine now with one ext2 partition with noatime edited fstab. Im am a noob to linux and thought maybe someone with skills could share in there experiences.

Sorry, I didn't mean to flame you and hope you didn't interpret it in that way. :) My point was, Dell has made this (allegedly) awesome Ubuntu remix for the Mini 9, and it would be a nice gesture on their part if they let you have it too, since you were one of their first customers for the Mini 9.

If you check out post #1 of this thread, it sounds like very few "tweaks" are required to get Ubuntu up and running on the Mini 9. Most features work out of the box. It would be easier and quicker to just follow the tips and tricks in this thread than to mess with a remastered iso. I haven't ordered my Mini 9 yet because I am waiting to read reviews once the Ubuntu version ships.

---

### Post by anton_es on 2008-10-02
thing is, here in austria zou only get the mini with ubuntu with a 8gb ssd and 0.3mp camera. the win version has the 1.3 and 16gb ssd........
so i went for the xp version which arrived in 2 dazs !

im typing this on the mini running a live-ubuntu usb-stick with the latest intrepid build. everything works except the sound but i dont care, its only a live session.

i managed to get the remix working and now im waiting 4 8.10 to get final
a netbook iso for the dell would be awesome, removing programs after install gets old quick....

does anybody know if dell gives out their install iso for customers of the xp version...

that would be awesome, until then: unetbootin rocks

---

### Post by jbloodwo on 2008-10-02
I dont know what License dell is using on the ribbon bar and dell web chat so from a sharing standpoint i will totaly ignore those 2 components.  My understanding is that the Dell releases of ubuntu have licensed CODECS for at least MP3 and CSS.  There is a chance it may also legally support media player.
Also because there are not any in the wild wet we don't know what other license restricted tweaks there are in the system.
If Dell was (were) willing to make an iso for the system for download at the very least it would be CODEC crippled.

As for 8.10.... I am hoping that this is not why dell has ship dates so far out on the ubuntu models.  I orderd this because 8.4 is a LTS version... LTS versions are long term support versions.
--- form ubuntu wiki ---
LTS is an abbreviation for “Long Term Support”.

We issue a new desktop and server release every six months. That means you'll always have the latest and greatest applications that the open source world has to offer.

Ubuntu is designed with security in mind. You get free security updates for at least 18 months on the desktop and server.

With the Long Term Support (LTS) version you get three years support on the desktop, and five years on the server. There is no extra fee for the LTS version, we make our very best work available to everyone on the same free terms. Upgrades to new versions of Ubuntu are and always will be free of charge. 
---
I figure the life on a net book is about 3 years so when the product hits EOL (End Of Life)  I will just get a net netbook that by then may have at least a dual core attom and who knows mabey even a quad and at least 64 gig of flash and final 802.11n.  so whay would you want 8.10 just to have 8.10?

---

### Post by tuawsteve on 2008-10-02
@lanewinfield -- 

I'm also a "Mac guy", having used 'em for 24 years. My really subversive reason for buying a Mini 9 is to try to get OS X running on it. I'm using Paul O'Brien's experience with the MSI Wind as my guide. I'm quite tech savvy (I'm a certified Apple consultant), but not a coder so if things go south I'm sure I'll be using Linux. 

Cheers,

Steve

---

### Post by jbloodwo on 2008-10-02
> **tuawsteve said:**
> @lanewinfield -- 

I'm also a "Mac guy", having used 'em for 24 years. My really subversive reason for buying a Mini 9 is to try to get OS X running on it. I'm using Paul O'Brien's experience with the MSI Wind as my guide. I'm quite tech savvy (I'm a certified Apple consultant), but not a coder so if things go south I'm sure I'll be using Linux. 

Cheers,

Steve
Several ppl have put OSx on the thing... i think that basically all that is not currently not working is suspend.  
Onece that is working i will get a 32 gig flash card and try to install...

but for now it is Dell MiniOS.

---

### Post by dmfield on 2008-10-03
Im willing to be flamed for this comment, but to all those people who keep telling us not to buy the mini 9 because its got xp on it and your funding microsoft, i have to say you ar missing the point.

Computing with alternative os's is not mainstream, its why so many people got involved with them to start with, to drop out of the mainstream.

Now this is a personal vinew, not a mainstream one, i'm more than happy to buy the xp box, be an early adopter, and "strugle" getting ubuntu on the device, because it homes my linux skills, it makes me think, and to be brutally honest, microsoft is there, it will alwasys be there, and will be the primary os for a long time. let it be, linux is not designed to be number 1, just as an alternative.

look at the EEEpc, did this become popular because of its os? no because of the number of websites showing you how toput every form of os under the sun on the dammed thing, i'd have to guess its the challenge for many people.

if you want the easy road, and the dell os, thenthis is also your choice, and please feel free to make it. however having used the ubuntu netbook respin, albeit not the customised dell one, you will be insalling normal ubuntu very quickly.

the m$ tax, well im pretty sure i've used a few less than legit microsoft products over the years, so consider that £50 as a compensation.

can we get over the "im waiting for the dell with ubuntu, because i don't like microsoft" threads or take them elsewhere, and stick to the issues with geting ubuntu 8.04.1 on a dell mini 9, or any other os (really macos ?) and enjoy the challenge. its fun.

---

### Post by barrangatan on 2008-10-03
Hi I'm new to the forum but have been using Debian/Ubuntu for a while. I also just got a Dell Mini recently, and am actually typing this on it. Yes the keyboard is a bit cramp, and I'm still having problems with the placement of certain keys (like ' and |) but all in all, it is a well built netbook with lots of potential and charm.

Immediately after I received the unit I installed Xubuntu Hardy on it. And as many users have already found out, using unetbootin and a USB drive is the easiest way to install Ubuntu on these netbooks. I did run into a couple of problems while installing:

**Wifi**: 
The included broadcom (wl) module, while worked with open wireless network, did not work with any WPA network that I was able to try. Instead, I had to resort to the official Broadcom-released driver found [here]("http://www.broadcom.com/support/802.11/linux_sta.php").

**Hibernate**:
Hibernate did not work for me out of the box, while suspending works quite well overall.  Each time I tried hibernating, the system would simply power down.  Instead I opted to use software hibernate (uswsusp) and it works great. More info can be found [here]("http://blog.paulbetts.org/index.php/2007/02/1the1/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/")

**External VGA Monitor**
I've been using the Dell Mini at work by hooking it to an external VGA monitor. I found an excellent post on the forum [here]("http://ubuntuforums.org/showthread.php?t=871372") (from the 2nd reply by ajmorris) on how to use a little bash script to turn on/off the VGA display whenever it is connected, and map the script to the Fn-8 (XFree86Display) key on the unit. Works like a charm. The only caveat? External display resolution maxes out at a paltry 1024x794

**Bluetooth**
Still have not figured out about how to access the bluetooth adapter yet. As others have already mentioned, nothing in the lspci or lshw output include anything that is explicitly listed as a bluetooth adapter.  But I
m heartened to hear that others have found a way to make theirs work and can't wait to read their replies.

Best to all
BN

---

### Post by dmfield on 2008-10-04
There are a lot of posts here about what doesn't work on this device, so i thought i'd surmise what DOES work. with ubuntu 8.04.1

**Sound**

See post 1, copy, paste reboot works, and is very good speaker quality

**Webcam**

Out of the box (OOTB) support for skype, Ekiga
[B]
wifi[/B]

Install updates, disable hardware driver, reboot, enable hardware driver, reboot done.

**Flash Full Screen**

With compiz over wifi, this is a minor miricle, no clipping and not jerky full screen. BBC Iplayer works just great as does Zattoo and Miro

**Compiz**

OOTB wobbly windows

**Windows Media Plugins**

Work a dream, medibuntu, firefox 3 job done[B]

Bluetooth[/B]

People tell us it doesnt work because a command line says it doesnt, but no one says what they want bluetooth for, personally i use it for skype headset and it works ok, nothing to do, 

[B]External display
[/B]
Plug it in press Fn F8 and it works in 1024x768


**USB **

Works[B] fine

Ethernet[/B] 

OOTB


Now, do an install of xp home without the drivers disk, all of the above work without any "drivers disk" and straight from the repositories, no special drivers needed

Bluetooth - no
Proper screen resolution - no
Wifi - no
webcam - no
usb - no
sound - no
External display - no
Ethernet - no

Why the comparison? well its interesting what does work off one cd with Ubuntu, however imagine if you lost that xp drivers cd.. and need to reload xp in about, oh, lets say 6 months...

---

### Post by alih on 2008-10-05
> **barrangatan]nothing in the lspci or lshw output include anything that is explicitly listed as a bluetooth adapter.[/quote]

Have you tried lsusb?  said:**
> but no one says what they want bluetooth for,
Hmm... did I mention PAN? I want TCP/IP connection over bluetooth to my freerunner. On my other box, I just do pand -s, then pand -c on the mobile, and set IPs. This doesn't work with the Dell Mini though - pings don't go through.

---

### Post by benlen on 2008-10-05
I also had problems with WPA, but this solution helped me:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by dmfield on 2008-10-05
There are some instructions to setup pan at:

[http://www.viciouslime.co.uk/articles/3-howtos/19-howto-bluetooth-networking-pan-on-ubuntu](http://www.viciouslime.co.uk/articles/3-howtos/19-howto-bluetooth-networking-pan-on-ubuntu)

if the pings are notworking check the iptables at the end.

---

### Post by coldswell on 2008-10-06
> **barrangatan said:**
> 
**Wifi**: 
The included broadcom (wl) module, while worked with open wireless network, did not work with any WPA network that I was able to try. Instead, I had to resort to the official Broadcom-released driver found [here]("http://www.broadcom.com/support/802.11/linux_sta.php").


Thanks for the tip BN, I think I'll try this to get mine working. You couldn't tell me exactly how to manually install the driver could you? Sorry, I'm pretty new to Ubuntu.

---

### Post by skroops on 2008-10-06
> **mypup said:**
> So last night while reading I found that I should not use the ext3 file system and no swap as well. Currently I have one ext2 partition with no other tweaks. I have been reading more about how to minimize writes ect but havent a clue on all the ends and outs to setup this in the proper manner..

I keep reading this, but I wonder if it's really necessary.  After all, my mini shipped with xp and NTFS... does ext3 really write that much more than NTFS?  If not then you shouldn't really _need_ tweaks.

---

### Post by skroops on 2008-10-06
> **coldswell said:**
> Thanks for the tip BN, I think I'll try this to get mine working. You couldn't tell me exactly how to manually install the driver could you? Sorry, I'm pretty new to Ubuntu.


I have the same problem, this is supposedly an error with the wl driver in 8.04.  I am updating it now by following this post starting from step 4: [http://ubuntuforums.org/showthread.php?p=5524663#post5524663](http://ubuntuforums.org/showthread.php?p=5524663#post5524663)

I cant test it until tomorrow. gl

---

### Post by coldswell on 2008-10-06
I tried the instructions on that page, i went through it all no problems but it still didn't work.

I have finally got it working now. All I did was use ndiswrapper and loaded the windows driver file, rebooted and hey presto it worked perfectly and was minimum effort.

---

### Post by dmfield on 2008-10-07
The WL Driver. 

I'm working on a project at work at the moment, putting a secure Ubuntu 8.04 onto a USB stick, to create an encrypted thin client. And we are looking to have this work across the board on Netbooks, the Dell Mini 9 being one we have for testing (as its mine)

The wl.ko module, resides in a modules folder called Volatile, which Debian setup to have things like antivirus updates and things which would change a lot over the period of the distros life in. I find this strange as the driver would surely be better placed in unstable? Which it is, because if you run a modprobe wl on a fresh Ubuntu install, and run a dmesg, it comes up with a whole heap of error messages about invalid symbols. These are resolved one an update is done on the system.

So i think this driver is unstable at best, hence the issues with WPA, which Linux in general has issues with especialy if you run hidden SSID's and the like. 

Personally my advice would be, if you know your not going to be attaching to WPA Wifi networks, then keep the wl driver, however if you are using the system on WPA networks, the use the Ndiswrapper approach.

---

### Post by skroops on 2008-10-07
> **coldswell said:**
> I tried the instructions on that page, i went through it all no problems but it still didn't work.

I have finally got it working now. All I did was use ndiswrapper and loaded the windows driver file, rebooted and hey presto it worked perfectly and was minimum effort.

It didn't work for me either, and ndiswrapper just makes me unbootable.

So I installed intrepid, and it worked out of the box (more or less, actually i custom installed with a cli install and then *sudo apititude install ubuntu-desktop --without-reccomends *in order to save disk space)

I then had to manually remove uswsusp to get sleep working.

Somewhere along the line I seem to have gotten a big bonus, as now my battery reports 5.5 hours remaining at 100% as opposed to the 4 hours I was getting on intrepid.  I haven't done a real test to confirm this time, but I think it's accurate.

---

### Post by tuawsteve on 2008-10-09
With regards to my earlier post, I have Leopard up and running on the Mini 9. The features that aren't working properly at this time:
--Sleep mode
--Power down (need to hold down the power button to have proper shutdown)
--Ethernet

Everything else (webcam, Wi-Fi, USB, sound, etc...) is running smoothly. What a quiet machine! It's great! :-)

TUAWSteve

---

### Post by wolfkeeper on 2008-10-09
Last I heard the card reader didn't work as well, is that the case in your install?

---

### Post by himuraken on 2008-10-11
Update for anyone interested...

I ordered a Mini9 with XP for my wife, and a Mini9 Ubuntu for myself. Both were ordered around 8:00pm on the first day they were available for purchase. With the exception of OS both units are identical, 16GB SSD, 1.3 webcam, and 1GB of RAM. Within an hour I had my estimated shipping dates: Sep 19 for the XP and Oct 10th for the Ubuntu. The XP system shipped an entire day early on the 18th. As of today (OCT 11th) my ship date has been changed from OCT 10th to Nov 7th. After calling Dell and politely working my way up the ranks of support and managers, I was told that the webcam / Ubuntu combo is causing the hold up. Apparently, and this is from the words of a Dell Support Manager, they haven't gotten the webcam working yet. This was after being told that the OS wasn't readily available....right... So they went on to explain that once they figure out how to get the webcam working in Linux, they will ship it. Props go to Dell for offering products that they claim work, exist, etc,...Taking my money...Not shipping a product... And not even sending an email to explain the hold up.

---

### Post by skroops on 2008-10-11
That they haven't gotten the webcam working sounds like an after-the-fact lie.  Considering the plethora of linux hardware compatibility problems, they would have ensured that the webcam works properly with linux *before* offering it.  Not to mention that the first post in this thread claims the webcam is already working in default hardy.

---

### Post by feranick on 2008-10-16
> **skroops said:**
> That they haven't gotten the webcam working sounds like an after-the-fact lie.  Considering the plethora of linux hardware compatibility problems, they would have ensured that the webcam works properly with linux *before* offering it.  Not to mention that the first post in this thread claims the webcam is already working in default hardy.


The webcam (1.3MP) works perfectly out of the box on my Ubuntu Dell mini (default installation).

---

### Post by jbloodwo on 2008-10-16
> **feranick said:**
> The webcam (1.3MP) works perfectly out of the box on my Ubuntu Dell mini (default installation).

the .3 is working for me.   I need to take teh microsd out of my cetro a and put that in the adapter and see if with the dell load the card reader is working.

---

### Post by frani23 on 2008-10-17
Okay, on the camera subject:  I ordered mine last week and the camera wasn't even an option on any of the versions...So, I guess they aren't offering it right now, but when ordering it, there was a "no camera option" screen (if that makes sense) when choosing the options so maybe in the future it will become available again...but I guess they were having a problem with the cameras...

Okay, now onto my real question:
I just got mine today (yay!) but I can't get the wireless internet to work.  I tried manually configuring it and after a couple of tries I got it to actually find the networks.  So now I can connect to a network but I cannot use the internet.  Well, now that I think about it, I could connect before I turned it off.  Now its doing the same thing (I click on my router's name, it asks for the password and I type it (have tried with all variations), it acts like it is connecting and then it prompts me for a password again.  I posted this question somewhere else and someone suggested opening a terminal (which I had to look up how to do, lol) and writing ping 72.14.207.99.  It didn't work like he/she said...so idk...PLEASE help!  I was so excited to get my mini 9!  But internet was the main reason why I wanted it!  So bummed!  Also, please use simple terms and try to write things out please cause I am totally new to lynux(if thats how you spell it).  Thanks in advance!

---

### Post by jaduret on 2008-10-17
I have been following this thread which has been the most informative. I have summarized my experience [http://netbookdellubuntu.blogspot.com/]("http://netbookdellubuntu.blogspot.com/"). For me, everything works find!

---

### Post by gregconquest on 2008-10-17
> **jbloodwo said:**
> the .3 is working for me.   I need to take teh microsd out of my cetro a and put that in the adapter and see if with the dell load the card reader is working.

jbloodwo, what is a "cetro a"?

---

### Post by mendieta on 2008-10-19
> **feranick said:**
> The webcam (1.3MP) works perfectly out of the box on my Ubuntu Dell mini (default installation).

Thanks for the update, Feranick!

I am glad people are starting to get their Ubuntu Dell Minis. I've been drooling over the video here:
[http://yourblog.direct2dell.com/2008/09/22/green-light-for-ubuntu-powered-inspiron-mini-shipments/](http://yourblog.direct2dell.com/2008/09/22/green-light-for-ubuntu-powered-inspiron-mini-shipments/)

I'll buy an Ubuntu Mini as soon as I can spare some cash, assuming the hardware is rugged (I'll check in a while with you guys, my eee proved lovely but the hardware too shaky, mostly dead after 9 months)

By the way, I don't feel it's productive to flame Dell. They are a huge public company, and as such, they respond to the interests of their shareholders. But they do understand that promoting Linux is in their best interest in the long run. And they do understand how Linux needs to be helped: teaming up with Leading distros like RedHat, SUSE and Ubuntu:
[http://www.dell.com/linux](http://www.dell.com/linux)

Here is a list of Dell Linux projects:
[http://linux.dell.com/projects.shtml](http://linux.dell.com/projects.shtml)

A good summary of Dell's involvement is available:
[http://linux.dell.com/](http://linux.dell.com/)

And, back to the Mini, the XP based models can be configured with Ubuntu, as of today, at least in the US, $40 cheaper, which seems fair. Thank you Dell, I'll vote with my wallet soon.

Cheers!

---

### Post by Rallg on 2008-10-19
I got the XP version with no webcam, plus Bluetooth. Sorry, comrades, but I needed XP for a proprietary application that WINE doesn't like. My regular laptop has Vista stripped, Ubuntu 8.04 entirely.

On the mini 9, using unetbootin with a downloaded iso of 8.10 beta, I created a 4Gb 8.10 partition. To my surprise, WiFi worked "the first time" before any updates and without my own intervention. I haven't tried Bluetooth yet (not on XP, either). I can't imagine why a mini 9 user would need Compiz, whether or not it works.

In my case, I put GRUB on the Ubuntu partition, so that the MBR is unchanged. Then, I used the "boot Linux using XP boot loader" method, widely known. Even though my mini 9 came with an XP install CD, I couldn't use it without puchasing an external CD drive, in the event I fumbled the ubuntu installation.

The appearance is very, very good. Only complaint is that some windows appear with their title bar invisible, due to the short screen length. They can't be moved using ordinary mouse.

If you were thinking of putting 8.04 on the mini 9, it might be better to wait for 8.10.

I didn't bother with the media codecs, since I don't need them.

---

### Post by alih on 2008-10-21
dmfield, thanks for the bluetooth guide! Sorry I'm late on that - had a keyboard problem, Dell sent me a replacement. (You can take the keyboard off without voiding the warranty - that's just great).

Now everything works for me except for hibernation, but that's just because the installer made the swap smaller than 1G.

Found this blog about Ubuntu on Dell Mini:  
[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by dmfield on 2008-10-26
Today i've installed Intrepid RC, wow, from the outset, i'm impressed, from the get go, i have not had to plug in a wired cable, as thedre is a driver which worked and allowed me to attach to my wep wifi, so i could install the propritory broadcom driver.

Webcam, good to go..

The big bonus, Bluetooth, i had to install a few bluetooth and obex packages from synaptic, however i can now attach to my skypephone s2 via bluetooth, swap files..

Not sure about this network manager 0.7 3g experience, however going to be doing a bit on that at work this week.. 

There some little gnome nuances too, add new wallpapers, and there is a bookmark to the standard directory in gnome which stores wallpapers, same with icons..

I've heavily customised this distro, added a lot of files, Ubuntu have done a great job with this. I wonder how muchof this is what has caused the delay on the ubuntu shipped dells.

---

### Post by padde0711 on 2008-11-05
> **dmfield said:**
> The big bonus, Bluetooth, i had to install a few bluetooth and obex packages from synaptic, however i can now attach to my skypephone s2 via bluetooth, swap files..

I'm still trying to get Bluetooth working. Could you please tell me what exactly you installed? Output of 'lsmod' would also be highly appreciated.

---

### Post by dmfield on 2008-11-11
Sorry been a while since i did it, but load everything obex and bluetooth related from synaptic

> Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
af_packet              25728  4 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
rfcomm                 44432  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  16 rfcomm,bnep
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  0 
cpufreq_powersave       9856  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      11396  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
mmc_block              17924  2 
dcdbas                 15008  0 
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
evdev                  17696  11 
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
btusb                  19736  3 
bluetooth              61924  11 rfcomm,bnep,sco,l2cap,btusb
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
serio_raw              13444  0 
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
psmouse                45200  0 
battery                18436  0 
snd_seq_dummy          10884  0 
video                  25104  0 
output                 11008  1 video
ieee80211_crypt_tkip    17024  0 
ac                     12292  0 
wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  2 mmc_block,sdhci
pcspkr                 10624  0 
button                 14224  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
intel_agp              33724  1 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                42184  3 drm,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
ata_generic            12932  0 
r8169                  35972  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic
scsi_mod              155212  3 sd_mod,sg,libata
dock                   16656  1 libata
usbcore               148848  5 uvcvideo,btusb,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

---

### Post by bluetoothgoose on 2009-03-22
> **skroops said:**
> 

* Sometimes weird stuff happens when writing text.  I've tried setting syndaemon to suppress touchpad input for 1 second after typing, which helps.  For some reason though, random words or parts of words will appear in the middle of typing.  This stuff might be in the clipboard, but it might not.  No idea what's going on here.



Did you ever find a solution to this problem?  I have the exact same issue.

---

### Post by ugm6hr on 2009-03-22
> **bluetoothgoose said:**
> Did you ever find a solution to this problem?  I have the exact same issue.

This is because of mousepad tapping during typing.

Use syndaemon to suppress tapping when typing:

System -> Prefs -> Sessions
Startup Progs tab
Add
syndaemon -i 4 -d -t -K

Then Alt+Fn+S:
syndaemon -i 4 -d -t -K

This should sort the problem out for you.

---

### Post by Blanchard on 2009-04-08
I am new to Ubuntu and just received my Dell Mini 9 and want to get it using my wireless network.

I have a question about this shown below;

3) Wifi 
to get this working, i had to install all the updates, then enable multiverse and universe run an apt-get update then install all the updates and reboot.

So is he referring to the Ubuntu updates?

What are multiverse and universe?

What is an apt-get update?

Can someone give me more details?

---

### Post by ugm6hr on 2009-04-08
Nothing is required to get the wifi working on a default Ubuntu installation.

If you have installed Ubuntu manually, you need to ensure you enable the "firmware", which can be done from System -> Admin -> Hardware Drivers with an ethernet cable plugged in.

---

### Post by anjilslaire on 2009-04-08
Indeed, in fact even installing Intrepid manually gets the wifi working enough to get the updates that allow the Hardware Drivers to download & apply the proprietary Broadcom STA driver for improved wireless performance.

---

### Post by freykatt on 2009-04-19
[/B][/B]
Ok, just gotta pat myself on the back.  I received my mini 9, 8gig, 512mb, no webcam, w/durned ole xp, HAH, finally, finally succeded in installing Mint, , then decided I didn.t like it, so, after 3 or 4 tries and 3 diffrerent   thumb drives, sucksessfully (yeah I kinow, spelling. but spelling accurately descrides my efforts, it did suck) created an 8.10 thumb drive iso.  It manually installed effortlessly witth everything working inclluding wireless, that is except for sound, still plugging away at that.  Just gotta say, for this dumb ole country boy, this blows away            uhhhh, forgot the name of that other ole ?operating system, but you know what I mean.  Great going, kudos to those that have labored away creating this great distro.   73's to all ya'll.      cuzzin dick

---

### Post by snowpine on 2009-04-19
> **freykatt said:**
> [/B][/B]
Ok, just gotta pat myself on the back.  I received my mini 9, 8gig, 512mb, no webcam, w/durned ole xp, HAH, finally, finally succeded in installing Mint, , then decided I didn.t like it, so, after 3 or 4 tries and 3 diffrerent   thumb drives, sucksessfully (yeah I kinow, spelling. but spelling accurately descrides my efforts, it did suck) created an 8.10 thumb drive iso.  It manually installed effortlessly witth everything working inclluding wireless, that is except for sound, still plugging away at that.  Just gotta say, for this dumb ole country boy, this blows away            uhhhh, forgot the name of that other ole ?operating system, but you know what I mean.  Great going, kudos to those that have labored away creating this great distro.   73's to all ya'll.      cuzzin dick

Sound in 8.10 is an easy fix:

In a terminal type:
sudo gedit /etc/modprobe.d/alsa-base

At the end of alsa-base file add:
options snd-hda-intel model=dell

(source: [http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html))

---

### Post by freykatt on 2009-04-19
C****Snowpine, Thank you.  Now, for the dumb  question.  Not having done any CL before, I tried this, got request for password, ???, tried my usual PW, no good, so unable to go further.  I haven' found anything suggesting what password I should use.  What am I missing?    Thanks again snowpine.   Dick

---

### Post by snowpine on 2009-04-19
> **freykatt said:**
> C****Snowpine, Thank you.  Now, for the dumb  question.  Not having done any CL before, I tried this, got request for password, ???, tried my usual PW, no good, so unable to go further.  I haven' found anything suggesting what password I should use.  What am I missing?    Thanks again snowpine.   Dick

You should use your regular user password. Are you the only user account on the computer? The first account that you created during the installation process should have sudo privileges.

---

### Post by freykatt on 2009-04-19
Ok, I have now some white noise thru the speakers on mini 9, but no sound.  The settings I have found all seem to be set but nothing happens.  Anybody got a clue??      Thanks            Dick

---

