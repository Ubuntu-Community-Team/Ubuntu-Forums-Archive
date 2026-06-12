---
title: "No sound on 9.10"
date: 2009-04-30
forum: General Help
---

### Post by kel_gb on 2009-04-30
Hi Guys

i have been happily using 8.04 for a few months when i noticed that the koala (9.10) has now been released, but no sooner did I upgrade I lost my audio.

I've tried playing films/music (through the audio jack on my PC) but there is no sound whatsoever. My speakers are fine (tested them), so I'm guessing the upgrade must have disabled the sound - I've checked to see if anything has been muted but no.

Has anyone else come across this issue or have some suggestions for a fix? 

Thanks
Kel

---

### Post by DeMus on 2009-04-30
> **kel_gb said:**
> Hi Guys

i have been happily using 8.04 for a few months when i noticed that the koala (9.10) has now been released, but no sooner did I upgrade I lost my audio.

I've tried playing films/music (through the audio jack on my PC) but there is no sound whatsoever. My speakers are fine (tested them), so I'm guessing the upgrade must have disabled the sound - I've checked to see if anything has been muted but no.

Has anyone else come across this issue or have some suggestions for a fix? 

Thanks
Kel

In the same week the whole world is upgrading to Jaunty 9.0.4 you upgrade to Koala 9.10? How do you do that?

---

### Post by lbelloq on 2009-04-30
Could you post lspci's output?
In case you don't know:
- Go to Terminal (Applications->Accesories->Terminal).
- Type "sudo lspci" (without quotes) and press ENTER.
- Copy the output and paste it here.

---

### Post by 91004 on 2009-04-30
> **kel_gb said:**
> Hi Guys

i have been happily using 8.04 for a few months when i noticed that the koala (9.10) has now been released, but no sooner did I upgrade I lost my audio.

I've tried playing films/music (through the audio jack on my PC) but there is no sound whatsoever. My speakers are fine (tested them), so I'm guessing the upgrade must have disabled the sound - I've checked to see if anything has been muted but no.

Has anyone else come across this issue or have some suggestions for a fix? 

Thanks
Kel

I think he traveled to the future and back :lolflag:   BTW who won the 2012 Presidential Election?

---

### Post by marshalium on 2009-04-30
> **kel_gb said:**
> Hi Guys

i have been happily using 8.04 for a few months when i noticed that the koala (9.10) has now been released, but no sooner did I upgrade I lost my audio.

I've tried playing films/music (through the audio jack on my PC) but there is no sound whatsoever. My speakers are fine (tested them), so I'm guessing the upgrade must have disabled the sound - I've checked to see if anything has been muted but no.

Has anyone else come across this issue or have some suggestions for a fix? 

Thanks
Kel

Ubuntu karmic 9.10 is very much in early development stages. In fact, there has has not even been an alpha release yet. So it is to be expected that things will break when you upgrade to it.

That been said, if you still want to run 9.10 and are having problems I suggest you check out the sub-forum specifically for people who are testing out the development release:
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

But if you want a stable system that works all the time, your best bet is to run one the versions of Ubuntu that is currently considered stable either 9.04 or 8.04LTS.

---

### Post by kel_gb on 2009-04-30
OK, I got the version number wrong - it's been a very long day!! :guitar:

---

### Post by kel_gb on 2009-04-30
Output of lspci

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

---

### Post by Monotoko on 2009-04-30
It is impossible to run it outside the terminal because of the environment variables, but couldnt you just add

```
exit
```

to the end of your file?

---

### Post by kel_gb on 2009-04-30
Doh, i'm definitely using Jaunty - and I was so enjoying 2012 (cheers 91104 - LOL)

---

### Post by lbelloq on 2009-04-30
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
That's your audio card. Can you post the output of "sudo lsmod"?

---

### Post by kel_gb on 2009-04-30
Output of sudo lsmod

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

---

### Post by kel_gb on 2009-04-30
Whoops - think that went a bit wrong, try again

output of sudo lsmod

Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
vboxdrv               117544  0 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
arc4                    9856  2 
ecb                    10752  2 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
rt61pci                29572  0 
crc_itu_t              10112  1 rt61pci
rt2x00pci              15616  1 rt61pci
rt2x00lib              37888  2 rt61pci,rt2x00pci
snd_seq_dummy          10756  0 
led_class              12036  1 rt2x00lib
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
mac80211              217208  2 rt2x00pci,rt2x00lib
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               19108  0 
joydev                 18368  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
psmouse                61972  0 
cfg80211               38032  2 rt2x00lib,mac80211
nvidia               7233756  36 
intel_agp              34108  0 
pcspkr                 10496  0 
wacom                  28808  0 
serio_raw              13316  0 
eeprom_93cx6           10240  1 rt61pci
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
agpgart                42696  2 nvidia,intel_agp
ppdev                  15620  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
usbhid                 42336  0 
usb_storage            82880  3 
r8169                  40836  0 
mii                    13312  1 r8169
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by lbelloq on 2009-04-30
> snd_hda_intel 435636 3
That's the module (driver) that controls your soud card. Seems it has no problems.
Check your audio configuration in the GUI (System->Preferences->Sound). See how's configured and post it here. Just write what appears there.

---

### Post by rrajath on 2009-04-30
This [link]("http://ubuntuforums.org/showthread.php?t=843012")  helped me. Hope it helps you too.

---

### Post by kel_gb on 2009-04-30
devices tab:

sound events - sound playback: auto detect
music and movies - sound playback: auto detect
Audio Conferencing - sound playback: auto detect
Audio Conferencing - sound capture: ALSA

Default mixer tracks: Capture - HDA Intel VT1708B Analogue
Device - master

Sounds tab: All set to default

---

### Post by lbelloq on 2009-04-30
Crap, I run out of ideas... any ALSA experts out there?
You might try to use rrajath's link, don't know if it will help but trying won't hurt.

---

### Post by kel_gb on 2009-04-30
No prob dude, thanks for trying

---

### Post by muhannadfa on 2009-04-30
hey dude i can give u big advice
u know crappy Vista > Microsoft >>> it's been much more better than this 9.04 jaunty
move back to 8.10, The 9.04 even it's released it's being alpha for most of users >>> we're all been testers nowadays no end-user release actually
:)
on my machine, Intel incompatibillty >> sound problem >> network device problems >> ipv6 problems >> 
on other machine >> nvidia incompatibilty >> ~ >> ~~ >> ~~

---

### Post by kel_gb on 2009-04-30
LOL - I hear u

I was hoping to 'downgrade' only prob is I don't know how without a clean install (or I guess live cd). Don't really want to spend ages backin up my data (or worse losing it altogether)

---

### Post by muhannadfa on 2009-04-30
u know what dude, i've an idea
Ubuntu 9.04 - Jaunty Jackalope is out! [COLOR="Red"]**[SIZE="6"]C[/SIZE]**[/COLOR]rab a copy today.. :lolflag:

---

### Post by kel_gb on 2009-05-01
Woo hoo - did a fresh install of Jaunty and is working fine. Seems there must've been an issue when I upgraded.

Thanks for all the suggestions guys

---

### Post by Calcipher on 2009-10-04
I too have this problem.  It seems to be related to 9.10 not working correctly with ICH7 sounds cards.  See bug report: [https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/441944](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/441944)

---

### Post by NJC on 2009-10-14
Thanks for bug report link. I downloaded Ubuntu 9.10 beta tonight (2.6.31-11) and this audio

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)did not work. I contributed to bug report as well.

---

### Post by zelhar on 2009-10-29
so is there a fix ?

---

### Post by zelhar on 2009-10-29
after another restart sound is back on. BUT, there is this annoying hissing sound coming out of the speakers even when no sound is played. Can I stop it somehow ?

---

### Post by Gaming4JC on 2009-10-29
diddo, same problem on a clients PC here. Here's the output for anyone interested. I updated from 9.04 to 9.10 via update manager and sound was wiped out:

```
g@g-desktop:~$ sudo lspci
[sudo] password for g: 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:03.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
g@g-desktop:~$ 


```


```

g@g-desktop:~$ sudo lsmod
[sudo] password for g: 
Module                  Size  Used by
radeon                342816  0 
drm                    96424  1 radeon
binfmt_misc            16776  1 
ppdev                  15620  0 
snd_hda_intel         435252  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
iptable_nat            13700  0 
snd_seq_oss            37760  0 
nf_nat                 25876  1 iptable_nat
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usblp                  20224  0 
snd_timer              29704  2 snd_pcm,snd_seq
psmouse                61972  0 
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
lp                     17156  0 
gspca_spca505          15616  0 
iptable_mangle         10880  0 
snd                    62756  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13444  0 
gspca_main             29952  1 gspca_spca505
videodev               41600  1 gspca_main
v4l1_compat            21764  1 videodev
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
iptable_filter         10752  0 
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
parport                42220  2 ppdev,lp
x_tables               23044  2 iptable_nat,ip_tables
dcdbas                 15264  0 
usbhid                 42336  0 
usb_storage            99648  0 
e100                   41740  0 
r8169                  40836  0 
mii                    13312  2 e100,r8169
intel_agp              34108  0 
agpgart                42696  2 drm,intel_agp
g@g-desktop:~$ 


```

For whatever it's worth the webcam is dead too, but that's off-topic. I gotta get sound for this poor person! 

Edit: It does seem to be an Intel audio issue, since I tested it on a few other PCs and they all work leaving the poor Intel Audio in the dust. If anyone ever finds a fix please post it here for the rest of us!!!  :D

---

### Post by Kimeras on 2009-10-30
After finding this issue on release version of 9.10, I found that I didn't have sound either.

Reading the bug report, I came across this:

[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/441944](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/441944)

> This problem has been temporarily resolved by disabling the proprietary Smart Link Software Modem driver available in Ubuntu's Hardware Drivers dialog (jockey-gtk).

This is actually a compatibility issue between alsa and the modem driver.

Sure enough, if you read the SmartLink Software Modem Driver, it actually describes this in some detail.

If this is the case for you, removing the restricted driver (System>Admin>Hardware Drivers) will immediately fix your sound problem.

---

### Post by zelhar on 2009-10-30
I just have an update that I have sound working now.

I oppenned mixer and unmuted "Internal Audio Analog Atereo (PulseAudio Mixer)"

This option is inaccessible from the normal kubuntu kmix so I used the ubuntu mixer. 

But I did notice one problem- I have this noise coming out of my speakers, even though I muted all the microphones. It is barely noticeable but still I wonder is this normal ?

---

### Post by ergunkocak on 2009-10-30
i have no sound after upgrading to 9.10 from 9.04. In Ubuntu mixer there is no sound hardware :( and here is my lsmod output :

```
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
vboxnetflt            100300  0 
vboxnetadp             93292  0 
vboxdrv              1708524  1 vboxnetflt
snd_hda_codec_si3054     5856  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  0 
snd_hda_codec          87584  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
arc4                    2144  2 
snd_pcm                93160  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
ecb                     3296  2 
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
joydev                 13088  0 
iwlagn                124832  0 
iwlcore               133248  1 iwlagn
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
uvcvideo               65260  0 
snd_seq                60608  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3872  0 
videodev               43360  1 uvcvideo
mac80211              210104  2 iwlagn,iwlcore
snd                    77096  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              21200  1 iptable_filter
sdhci_pci               8928  0 
soundcore               9088  1 snd
sdhci                  20484  1 sdhci_pci
jmb38x_ms              11300  0 
v4l1_compat            16804  2 uvcvideo,videodev
psmouse                57124  0 
x_tables               25832  1 ip_tables
v4l2_compat_ioctl32    13344  1 videodev
serio_raw               6596  0 
led_class               5256  2 iwlcore,sdhci
memstick               12528  1 jmb38x_ms
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
cfg80211              109144  3 iwlagn,iwlcore,mac80211
nvidia              10316904  40 
lp                     11908  0 
parport                40528  2 ppdev,lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
usbhid                 43968  0 
r8169                  38884  0 
mii                     6368  1 r8169
video                  23612  0 
output                  3680  1 video
intel_agp              32816  0 

```

can anyone help me ?

---

### Post by Ireon on 2009-10-30
There's no sound on my computer too. 
It took me some time to get the sound working on Jaunty (I had to tweak the alsa mixer controls, switch front and surround and the like), but the same thing is not working.
I followed a couple of troubleshooting instructions (re-installed everything alsa, de-activated pulse several times..).
So right now it comes down to this: I am pretty sure my sound card is recognized and that nothing is muted in alsa. Can someone help me?

---

### Post by snerd on 2009-10-30
Definitely some audio problems in 9.10. I posted another thread on my old Turtlebeach Santa Cruz Soundcard not having any sound, and to fix it I changed the profile in Sound hardware tab preference to Analog Surround 4.0 Output, and on the Output tab  I slid the Fade slider all the way over to the Front side. Maybe not a permanent fix, but it sounds good now.

---

### Post by bezolaam on 2009-10-30
hello.
my pc dont see audigy2 sz after upgrading, but it works with onboard soundcard.
I tried to find somewhere where I could switch back to audigy but I can't.
ubuntu 8,04 worked fine with audigy, without any configurations on driver searching.

lspci report:
.....
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:13.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
.....

How could I activate Audigy soundcard? anybody?

---

### Post by ergunkocak on 2009-10-30
my problem is solved after reinstalling alsa packages and restart :)

---

### Post by avotins on 2009-10-30
Hello!

The same problem, BUT... on sudo lspci I ain't no audio device at all. looks like system didn't find a sound card, or somthing... First Ubuntu in my life btw, so be gentle :)

---

### Post by Manksman on 2009-10-30
I too have just updated to 9.10 and found myself with no sound. I have reinstalled allsa and rebooted but to no avail. Under System --> preferences -->sound there is no hardware listed at all, under output it only has dummy. This is all most disappointing. 
Here is the lsmod output
Module                  Size  Used by
binfmt_misc            16776  1 
radeon                342816  0 
drm                    96424  1 radeon
snd_intel8x0           37532  0 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter         10752  0 
ppdev                  15620  0 
soundcore              15200  1 snd
ip_tables              19600  1 iptable_filter
shpchp                 40212  0 
lp                     17156  0 
i2c_sis96x             12420  0 
parport_pc             40100  1 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
x_tables               23044  1 ip_tables
parport                42220  3 ppdev,lp,parport_pc
psmouse                61972  0 
serio_raw              13444  0 
sis900                 28288  0 
mii                    13312  1 sis900
sis_agp                15360  1 
agpgart                42696  2 drm,sis_agp
floppy                 64324  0

---

### Post by didonc18 on 2009-10-30
hello,

I'm sorry for my english(i'm french)
I have an asus laptop with 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

and after update driver of modem by "peripherique driver" , i had no sound.

To resolve this problem, i had desactived the driver of modem and this OK.

Bye.

---

### Post by egroeg85 on 2009-10-31
I had no sound after upgrading 9.04 to 9.10 and this forum helped me with fix it:

[_http://ubuntuforums.org/showthread.php?t=1304710&page=4_]("http://ubuntuforums.org/showthread.php?t=1304710&page=4")

To briefly summarize-

First make sure you are booting from the newest kernel.

Check which ones are installed:
```
dpkg --get-selections | grep linux-image
```

See which one you're running:
```
uname -r
```

Edit your menu.lst file so that the kernel version numbers are up to date:
```
sudo gedit /boot/grub/menu.lst
```

Restart and see if that fixes it.  If not, you might need to go through these:

Alsa Guide:
[_http://ubuntuforums.org/showthread.php?t=205449_]("http://ubuntuforums.org/showthread.php?t=205449")

PulseAudio Guide:
[_http://ubuntuforums.org/showthread.php?t=789578_]("http://ubuntuforums.org/showthread.php?t=789578")

I did all of this to fix my problems, but if you're getting any sound at all after making sure you're booting from the right kernel, you might try the pulseaudio guide first.  I don't know that anything was wrong with alsa on my system.

Hopefully this helps.  Don't thank me, I'm just sharing information I gathered from wise and helpful people.

---

### Post by avotins on 2009-10-31
I've solved my problem by alsa upgrade to 21
this article helped - [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by haragatatsu on 2009-11-01
I have an old Dell (2001) that once had Windows ME (uggh!) on it.  I've had various versions of Linux OS's on it since 2004.  Been using different installations of Ubuntu since 2005 but have never had sound since leaving Windows.  I recently put 9.10 on it  and want to finally fix this sound problem.  Here are the specs:

**_lspci_**
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
02:0b.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
02:0c.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
02:0d.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

_**lsusb**_
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

_**cat /proc/asound/cards**_
 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xdf00, irq 3

**_cat /proc/asound/modules_**
 0 snd_ens1371

[U][B]aplay -l
[/B][/U]**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Please help!

---

### Post by zubaran on 2009-11-01
I spared much time when I read that sometimes the problem is in *modem Proprietary* software. After I switched off modem sound is back again.

---

### Post by mickeythefixer on 2009-11-05
I can confirm that the problem was the installation of the proprietary software modem driver. As soon as I removed it I had sound again! :D

---

### Post by Goggeli on 2009-11-06
Thank you so much Kimeras!!!! By removing the Smartmodem driver thing, my sound magically popped back, even without a reboot!

Hope it will work after next reboot though!;)

---

### Post by TheNessus on 2009-11-06
> **zubaran said:**
> I spared much time when I read that sometimes the problem is in *modem Proprietary* software. After I switched off modem sound is back again.
where do you turn it off? or what command?

---

### Post by blackhawkover on 2009-11-07
I had no sound after fresh install and then installed alsa, then I did an update and restarted. I don't know if any of these had anything to do with it, but it's working fine now. Thanks. Love the look of 9.10. Keep it up. :p

---

### Post by zubaran on 2009-11-07
> **TheNessus said:**
> where do you turn it off? or what command?

Just typing from memory (and don't have English GUI), but it should go like this:
Go to System ->Administration->Drivers (or something like this) it should summon window inside which you can activate/deactivate [I]proprietary  drivers.

[/I] Hope that it helps

---

### Post by cliffwarren on 2009-11-07
Ugh. I've done everything on this thread, and still no sound. I was also reading an article about 9.10 on Linux Journal, saying that 9.10 was way too buggy for general release. 

I either need to find a way to get sound, or go back to 9.04. How would I go back?

---

### Post by cathalcummins on 2009-11-13
**Note**: _I wrote this and in the process fixed it using suggestions from different threads. It shows my progress to the solution. If you want the resolution to my problem, skip right to the end._


Okay, so like a lot of people, I was happy using 9.04 and hadn't done my research on 9.10 and lazily upgraded. Now, there's no sound. I use an M-Audio Delta 44 PCI card with Breakout box and it was working fine with all previous versions [after a bit of wizardry ;-) ] but nada this time around.

I had put "disabling the onboard sound" task on the long finger for quite a while. But when this happened I decided to go in and get my hands dirty by disabling it in the BIOS. That went surprisingly well, so that Ubuntu is now only recognising the Delta 44 - quite happy about that.

So, as usual, before posting I decided to see what the general consensus was - and it looks like I'm not alone. Here is an alamagation of a few commands that the gurus requested:


%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

cathal@terminal38:~$ **sudo lspci**
[sudo] password for cathal: 
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

cathal@terminal38:~$ **lspci -v**
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 0900 [size=256]

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at dc00 [size=64]
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at dffff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at dfffec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 27
	Memory at dfffd000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d480 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at d400 [size=8]
	I/O ports at d080 [size=4]
	I/O ports at d000 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at c880 [size=16]
	Memory at dfffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 8234
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at dd000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at dffc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel
	Kernel driver in use: amd64_edac
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
	Subsystem: VIA Technologies Inc. Device d633
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at ec00 [size=32]
	I/O ports at e880 [size=16]
	I/O ports at e800 [size=16]
	I/O ports at e480 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ICE1712
	Kernel modules: snd-ice1712


%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

cathal@terminal38:~$ **sudo lsmod**
Module                  Size  Used by
nls_iso8859_1           5280  1 
nls_cp437               6976  1 
vfat                   13184  1 
fat                    59832  1 vfat
binfmt_misc            10220  1 
snd_ice1712            69572  0 
snd_ice17xx_ak4xxx      4320  1 snd_ice1712
snd_ak4xxx_adda         9472  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              9376  1 snd_ice1712
snd_ac97_codec        125720  1 snd_ice1712
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10928  1 snd_pcm
ac97_bus                2176  1 snd_ac97_codec
snd_i2c                 6464  2 snd_ice1712,snd_cs8427
iptable_filter          3872  0 
snd_mpu401_uart         8480  1 snd_ice1712
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hwmon_vid               3968  0 
snd                    77096  15 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_i2c,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
amd64_edac_mod         26688  0 
edac_core              48876  3 amd64_edac_mod
i2c_nforce2             8168  0 
k8temp                  5504  0 
soundcore               9088  1 snd
nvidia              10316904  36 
ppdev                   8232  0 
parport_pc             37352  1 
asus_atk0110            9472  0 
lp                     11908  0 
parport                40528  3 ppdev,parport_pc,lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
usbhid                 43968  0 
usb_storage            65952  2 
floppy                 65192  0 
forcedeth              61292  0

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

cathal@terminal38:~$ **cat /proc/asound/cards**
 0 [M44            ]: ICE1712 - M Audio Delta 44
                      M Audio Delta 44 at 0xec00, irq 19

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

cathal@terminal38:~$ **cat /proc/asound/modules**
 0 snd_ice1712

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

cathal@terminal38:~$ **aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

System ->Administration->Hardware Drivers only has only drivers for my NVIDIA graphics card, so I don't think this is the problem.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

cathal@terminal38:~$ **sudo lshw -C sound**
  *-multimedia            
       description: Multimedia audio controller
       product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
       vendor: VIA Technologies Inc.
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ICE1712 latency=64
       resources: irq:19 ioport:ec00(size=32) ioport:e880(size=16) ioport:e800(size=16) ioport:e480(size=64)

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

cathal@terminal38:~$ **uname -a**
Linux terminal38 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

I am dual booting xp and ubuntu 9.10 with a grub menu if that helps...

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
alsamixer - the mixer comes up, and I put everything I could up full.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

cathal@terminal38:~$ **envy24control**
using	 --- input_channels: 4
	 --- output_channels: 4
	 --- pcm_output_channels: 8
	 --- spdif in/out channels: 2

(envy24control:2875): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(envy24control:2875): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated


And the mixer comes up, I put everything up full here.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

cathal@terminal38:~$ **pulseaudio**
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

Not sure what this means...

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

In System -> Preferences -> Sound -> Hardware ICE1712[Envy24] comes up but under the "output" tab, it says only "dummy output" - could this be the issue?

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

I edited **/etc/default/pulseaudio** by changing

DISALLOW_MODULE_LOADING=1

to

DISALLOW_MODULE_LOADING=0


still nada
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

I updated the grub

>> **sudo apt-get install grub2**


%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

Then, after none of this worked, I decided to remove pulseaudio
>> sudo apt-get remove pulseaudio

I start getting those sweet little drum sounds - Huzzah!!!

**I think to celebrate, the first song to go on is The Greenhornes - There is an end... ;-)**

---

### Post by enzio on 2009-11-14
I have also seen some problems with sound in this release. With the k10temp module I get no sound even though everything looks to be fine. This problem occurs with both alsa and oss. Disabling k10temp restores sound.

Hope this helps....

---

### Post by Lonco on 2009-11-17
> **mickeythefixer said:**
> I can confirm that the problem was the installation of the proprietary software modem driver. As soon as I removed it I had sound again! :D

Thanks dude! I disabled it and its working great now!

---

### Post by poohman on 2009-11-22
I had exactly the same problem when I upgraded from jaunty to koala, could get my sound working for three days. 
System->Preferences->sound->output was always showing dummy
aplay -l showed no soundcards.....
I had earlier compiled my kernel in jaunty so when I noticed it was getting booted with the custom kernel, so I did an update-grub. Surprising even then it was noticed that the /boot/grub/menu.lst file was not updated. So i renamed the file and did an update-grub, now my menu.lst was different with the entry 2.6.31-14-generic. Restarted the system and the problem was solved.

---

### Post by killians31 on 2009-11-23
Hey guys, i am still having issues with my sound after i upgraded 9.04 to 9.10.

I have tried to update my grub file to the latest kernel, i have also updated the ALSA with no luck, removed pulse audio.. so im kinda stumped here!

It seems that my sound card isnt even being picked up.. It is outputting to the dummy output.

Any help would be GREATLY appreciated!

----------------------------------------------------------------------------------------------------------

ben@ubuntu:~$ cat /proc/asound/cards; sudo aptitude install paman gnome-alsamixer alsa-utils flashplugin-nonfree-extrasound; aplay -l;  sudo lshw -C sound;  ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn;  sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd;  lsmod | grep snd 
--- no soundcards ---
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

aplay: device_list:223: no soundcards found...
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f9ff8000-f9ffbfff
total 0
crw-rw----+  1 root audio 116, 2 2009-11-23 15:02 timer
crw-rw----+  1 root audio 116, 3 2009-11-23 15:02 seq
drwxr-xr-x   2 root root      80 2009-11-23 15:02 .
drwxr-xr-x  16 root root    3840 2009-11-23 15:19 ..
Sound Driver:3.8.1a-980706 (ALSA v1.0.20 emulation code)
Kernel: Linux ubuntu 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers: NOT ENABLED IN CONFIG
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9700M GT] [10de:064a] (rev a1)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
07:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
/sbin/alsactl
Cannot stat /dev/dsp: No such file or directory
Cannot stat /dev/dsp: No such file or directory
dpkg: *bin/slmodemd* not found.
snd_hda_intel          26920  0 
snd_hda_codec          75708  1 snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  11 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

---

### Post by DrQue on 2009-11-25
I was having the no sound problem with a computer I updated from 9.04 to 9.10.  Turns out when I did the update, I didn't place the new kernel in the boot menu.  I was prompted with a message about modifying the grub boot menu, and the default was to leave it as-is.  Running with the most up-to-date kernel took care of my sound issue.

Hope this helps.

---

### Post by killians31 on 2009-11-26
When i placed the new kernel into the boot loader, it corrected ALOT of the issues i was having with the upgrade, however it didn't correct the sound issue.

Anyone have any other ideas?

---

### Post by El_Cucuy on 2009-11-27
I'm having Issues my self sound was working (not well) then after the update manager no sound. ?

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
04:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)




Module                  Size  Used by
isofs                  36424  0 
udf                    88136  1 
nls_iso8859_1           5280  1 
crc_itu_t               2336  1 udf
nls_cp437               6976  1 
vfat                   13184  1 
fat                    59832  1 vfat
binfmt_misc            10220  1 
snd_intel8x0           36872  4 
snd_ac97_codec        125720  1 snd_intel8x0
ac97_bus                2176  1 snd_ac97_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_mpu401              9288  0 
snd_mpu401_uart         8480  1 snd_mpu401
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  2 snd_mpu401_uart,snd_seq_midi
amd64_edac_mod         26688  0 
iptable_filter          3872  0 
ppdev                   8232  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
parport_pc             37352  1 
lp                     11908  0 
ip_tables              21200  1 iptable_filter
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_nforce2             8168  0 
edac_core              48876  1 amd64_edac_mod
asus_atk0110            9472  0 
ns558                   6688  0 
x_tables               25832  1 ip_tables
parport                40528  3 ppdev,parport_pc,lp
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gameport               13712  2 ns558
snd                    77096  20 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 13088  0 
k8temp                  5504  0 
soundcore               9088  1 snd
nvidia              10316904  36 
snd_page_alloc         10928  2 snd_intel8x0,snd_pcm
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
usb_storage            65984  1 
usbhid                 43968  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
floppy                 65192  0 
sky2                   55556  0 
forcedeth              61292  0

---

### Post by mikebiller@gmail.com on 2009-11-28
I am having a similar problem I have an Acer netbook Aspire one and I was trying to get my bluetooth working with skype and now I have no sound at all it just says dummy output in sound preferences. it had pulse audio before and I tried uninstalling and re installing the pulse audio driver and after reboot same thing no sound. This is the forum I followed to try and set that up...[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

Thanks
Mike Biller



Here is the output from sudo lsmod

Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
snd_hda_codec_realtek   202336  1 
snd_hda_intel          26560  0 
snd_hda_codec          78300  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7392  1 snd_hda_codec
iptable_filter          3100  0 
snd_pcm_oss            37312  0 
snd_mixer_oss          16188  1 snd_pcm_oss
snd_pcm                74976  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
arc4                    1660  2 
ecb                     2524  2 
snd_seq_oss            29280  0 
snd_seq_midi            6624  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ath5k                 124260  0 
snd_seq                51088  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                 10272  0 
snd_timer              21540  2 snd_pcm,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
mac80211              181236  1 ath5k
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
acerhdf                 8116  0 
mmc_block              10592  0 
ath                     8060  1 ath5k
uvcvideo               59080  0 
psmouse                56500  0 
snd                    60900  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               36736  1 uvcvideo
soundcore               7264  1 snd
v4l1_compat            14496  2 uvcvideo,videodev
jmb38x_ms               9600  0 
serio_raw               5280  0 
sdhci_pci               7100  0 
lp                      8964  0 
snd_page_alloc          9060  2 snd_hda_intel,snd_pcm
sdhci                  17472  1 sdhci_pci
cfg80211               93052  3 ath5k,mac80211,ath
led_class               4096  2 ath5k,sdhci
memstick               10072  1 jmb38x_ms
btusb                  11856  2 
parport                35340  2 ppdev,lp
usbhid                 38208  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52576  2 
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221064  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

---

### Post by mikebiller@gmail.com on 2009-11-28
I figured it out I removed this 
pcm.btheadset {
        type bluetooth
        device 00:33:44:DD:EE:FF 
        profile &#8220;auto&#8221;

from here sudo gedit ~/.asoundrc and restarted and I have sound again...Dumb mistake...

thanks anyway

---

### Post by whistlerspa on 2009-11-28
I got rid of everything related to Pulse Audio and installed everything i could find using ALSA and sound now works on everything that i need it too.

---

### Post by Fillivan on 2009-12-03
I tried everything and nothing works, but then after i removed the modem software and restarted, for try No. N, and thought of  i running:
sudo /sbin/alsa force-reload 
and eureka!!! sound working, I hope this helps :)

---

### Post by garvinrick4 on 2009-12-03
Did 3 installs or upgrades to 9.10 and this worked each time. 9.10 Just have to do
Part A.  Just follow instructions.  Reboot when done. 

sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio


Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)
All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.
9.10
1. Backup (and then delete) your previous configuration files:
Code:

$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound* 
$ sudo rm /etc/asound.conf

Warning: As always, use caution when removing files on your system. Any typos can potentially cause data loss.
Note: Don't worry if some of these files did not exist on your system.


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:
Code:

 $ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio

3. Ensure the evil "libflashsupport" library is not installed:
Code:

$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound

Note: the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks!

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
Note: Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

Note: If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:
Code:

$ pulseaudio & pavucontrol

6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):

Code:

$ alsamixer -Dhw

Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.

7. Continue to Part B if you are running Hardy Heron (8.04), or Part C if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect!

---

### Post by abqhandyman on 2009-12-03
lbelloq: you seem like you know what you're talking about.  I have the same problem as OP:
dan@dan-desktop:~$ sudo lspci
[sudo] password for dan: 
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
02:09.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
dan@dan-desktop:~$ sudo lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
xt_limit                2176  8 
xt_tcpudp               2780  7 
ipt_LOG                 5344  8 
ipt_MASQUERADE          2204  0 
xt_DSCP                 2844  0 
ipt_REJECT              2812  1 
nf_conntrack_irc        4992  0 
nf_conntrack_ftp        6880  0 
xt_state                1820  6 
usblp                  12636  0 
iptable_nat             5500  0 
nf_nat                 17808  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13352  9 iptable_nat,nf_nat
nf_conntrack           67608  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
iptable_mangle          3452  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  1 
ip_tables              11692  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16544  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
k8temp                  4188  0 
shpchp                 32272  0 
ppdev                   6688  0 
parport_pc             31940  1 
serio_raw               5280  0 
joydev                 10272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
hid_microsoft           3328  0 
usbhid                 38208  0 
usb_storage            52576  1 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
floppy                 54916  0 
amd64_agp               9796  1 
agpgart                34988  3 ttm,drm,amd64_agp
dan@dan-desktop:~$

---

### Post by pieguy on 2009-12-06
Forget 9, I'm going back to 8.10, the best and most reliable version.

---

### Post by GrizzlyBear on 2009-12-06
Hello.

I had the same problem with alsa.
I have Kubuntu 9.10, and afteh about a month, my sound just stopped working.
Thought that I'll be forced to reinstall Linux, after trying to repair sound without results.

But, fortunately i found this link:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

and what i did from that site was download "gnome-alsamixer".

```
user:~$ sudo apt-get install gnome-alsamixer
```

then just type in terminal:

```
user:~$ gnome-alsamixer
```


It appears that i had "mutted" sound. I didn't know why, because in the standard mixer in Kubuntu this "speaker" in systray, everything was ok, and I checked alsa drivers, where everything was installed properly.
After running gnome-alsamixer I saw, that i have marked "mute" below the "master volume".
Just unchecked it, take all of the bars to the "top",
and everything is running back and loud :P:P

I hope that will help.
/Best Regards

---

### Post by killians31 on 2009-12-14
Thanks for the reply's, unfortunately i have yet to get my sound working :(

I have tried to completely uninstall pulse audio, and re-install everything from alsa, but still no luck!

I would really prefer not to do a fresh install of ubuntu (as it took many tries to pick up all of my Linux distributions within grub). Would a fresh install have better odds of picking up my audio card?

Thanks!

---

### Post by Hampster on 2009-12-15
Hi Team,
Well talk about a messy situation.  This is day four and I don't know where to go next.  I have basically lost my speaker icon altogether from up in the top panel. I also can't get anywhere with System Preferences Sound.  I just get message " Waiting for sound system to respond " 
The situation now is Sound.  
Skype sound working but scrappy.  
Rythumbox sound perfect to my old ears...??
Movie Player Video okay No sound.
MPlayer No video but sound okay. 
No Sound Controls anywhere to be found.
So how did I get here? You may well ask.  I can't remember every step but there have been lots.
I started by reading about 20 different threads and then launched into trying all sorts.  Up graded to 9.10 on the fly and the nightmare began...  I have removed and upgraded restarted shaved my head and fired instructions like a madman with a endless supply of bullets firing in randon directions.
Frustrated doesn't cut it.  An old workmate of mine once stood up, took a couple of paces back, drew his service revolver and shot his comp. He's okay now but I know how he feels.
I usually fluff my way through minor problems by reading the forums but this now appears to be a major problem that has been around for several months and still no update fix.  What's happening?
I am resisting many urges at the moment. Namely the urge to go back to Juanty or heaven forbid Windows but on the off chance there is some kind soul in this forum here is my comp statis.. Can't sit here all day so we have time....
Anyone????
ross@ross-laptop:~$ sudo lspci
[sudo] password for ross: 
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9200M G] (rev b1)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ross@ross-laptop:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
	Subsystem: ASUSTeK Computer Inc. Device 1a87
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 4f00 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1a87
	Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1a87
	Flags: 66MHz, fast devsel, IRQ 14
	I/O ports at 4900 [size=64]
	I/O ports at 4d00 [size=64]
	I/O ports at 4e00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: 66MHz, fast devsel

00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1a87
	Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1a87
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7
	Memory at fce80000 (32-bit, non-prefetchable) [size=512K]

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 1a87
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fce7f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 1a87
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fce7ec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1903
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fce78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1215
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 29
	Memory at fce7d000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c080 [size=8]
	Memory at fce7e800 (32-bit, non-prefetchable) [size=256]
	Memory at fce7e400 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 1a87
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 28
	I/O ports at c000 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at b880 [size=8]
	I/O ports at b800 [size=4]
	I/O ports at b480 [size=16]
	Memory at fce72000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fcf00000-fdffffff
	Prefetchable memory behind bridge: 00000000de000000-00000000efffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=05, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe000000-feafffff
	Prefetchable memory behind bridge: 00000000fa000000-00000000fbffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: feb00000-febfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9200M G] (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 16b2
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at de000000 (64-bit, prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a3b:1067
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

ross@ross-laptop:~$ sudo lsmod
Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
snd_hda_codec_nvhdmi     4860  1 
snd_hda_codec_realtek   200576  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10272  0 
snd_hda_intel          26560  0 
snd_hda_codec          78300  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7392  1 snd_hda_codec
arc4                    1660  2 
snd_pcm_oss            37472  0 
ecb                     2524  2 
snd_mixer_oss          16188  1 snd_pcm_oss
snd_pcm                75168  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
snd_seq_oss            29216  0 
snd_seq_midi            6656  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      7036  2 snd_seq_oss,snd_seq_midi
snd_seq                50896  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21540  2 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    60164  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k                 258744  0 
mac80211              181076  1 ath9k
ath                     8060  1 ath9k
iptable_filter          3100  0 
soundcore               7264  1 snd
snd_page_alloc          9124  2 snd_hda_intel,snd_pcm
nvidia               9586440  39 
agpgart                34988  1 nvidia
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
asus_laptop            17400  0 
led_class               4096  2 ath9k,asus_laptop
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
psmouse                56500  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
i2c_nforce2             6784  0 
cfg80211               93052  3 ath9k,mac80211,ath
shpchp                 32272  0 
usbhid                 38208  0 
usb_storage            52576  1 
video                  19380  0 
output                  2780  1 video
forcedeth              54152  0 
ross@ross-laptop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfce78000 irq 22
ross@ross-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel
ross@ross-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ross@ross-laptop:~$ sudo lshw -C sound
  *-multimedia            
       description: Audio device
       product: MCP79 High Definition Audio
       vendor: nVidia Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       version: b1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fce78000-fce7bfff
ross@ross-laptop:~$ uname -a
Linux ross-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
ross@ross-laptop:~$ envy24control
The program 'envy24control' is currently not installed.  You can install it by typing:
sudo apt-get install alsa-tools-gui
envy24control: command not found
ross@ross-laptop:~$ pulseaudio
The program 'pulseaudio' is currently not installed.  You can install it by typing:
sudo apt-get install pulseaudio
pulseaudio: command not found
ross@ross-laptop:~$ sudo apt-get install grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  grub2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,610B of archives.
After this operation, 270kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/universe grub2 1.97~beta4-1ubuntu4.1 [2,610B]
Fetched 2,610B in 0s (3,732B/s)
Selecting previously deselected package grub2.
(Reading database ... 197647 files and directories currently installed.)
Unpacking grub2 (from .../grub2_1.97~beta4-1ubuntu4.1_i386.deb) ...
Setting up grub2 (1.97~beta4-1ubuntu4.1) ...

---

### Post by ronintetsuro on 2009-12-15
I'm running 9.10 as well, and here's what I've figured out, as a new and novice linux user:

9.10 w/ pulseaudio = multimedia controls on keyboard work, sound icon in tray, no sound
(edit: Ubuntu 'drumroll' sound plays at the login screen, but no audio from there, including startup sound)

9.10 w/o pulseaudio = multimedia controls don't work, sound icon is gone, audio works perfectly 
(edit: and by perfectly, I mean it stutters from time to time)

Also, without pulse, you cannot access your sound settings to edit anything. So if you don't have external physical controls for your sound, you're hosed. At least, so far as I've figured out.

If anyone has any ideas, I'd love to hear them. (keep in mind, I'm a novice linux user) ;)

---

### Post by Hampster on 2009-12-16
Heh Team Novice Sprayers of bullets....   success.  I am not sure exactly what I did but I ended up with a few extra listings in my applications 
/sound and video like Echomixer and Envy24 Control HDSPconf HDSP Mixer and Remedigicontrol all of which I have zero knowledge about and I am not about to try any of them. I also reinstalled pulseaudio and wallah... the first thing i noticed was that I got the speaker Icon back and everything works.  But I am not celebrating yet. Still to check Skype which started me off on this nightmare journey...  Good luck all.

---

### Post by predd on 2009-12-16
> **Kimeras said:**
> After finding this issue on release version of 9.10, I found that I didn't have sound either.

Reading the bug report, I came across this:

[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/441944](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/441944)



Sure enough, if you read the SmartLink Software Modem Driver, it actually describes this in some detail.

If this is the case for you, removing the restricted driver (System>Admin>Hardware Drivers) will immediately fix your sound problem.

thanks. this was the solution to my sound problem on my hp pavilion dv9590 with ubuntu 9.10.

---

### Post by aimwin on 2009-12-22
I have the same problems.

I fixed it by, (reinstall alsa)
 
1. Open Terminal ( Application > Accessories > Terminal )

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Then "Shut Down" the computer.

2. Turn on Computer the Open Terminal again.

sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop

Then "Shut Down" the computer.

3. goto System > Preferences > Sound

   goto Hardware tab
   and goto Profile:
   Select "Analog Stereo Duplex"

That fixed my Audio

Ref: from [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by General660 on 2009-12-22
I am writing this after 8 months of absolute frustration with sound in the 9.04 and 9.10 versions of Ubuntu. I have been using Ubuntu since 6.06 came out, and up till april, I have always been happy with linux. I would like to know why the sound became "broken" in this years versions. Before, as they used to say, everything just worked. I do use both Linux and windows, as I do some gaming. But with windows, the sound "just works". This is a newer system, just built last year, dualcore@ 3 Ghz per core, 4Gb of ram,new Asus motherboard, sata hard drives, and Soundblaster and Realtek sound devices. I have went thru the forums, spending about 8 to 10 hours a week trying everything I can find to get sound on here, and so far, all for nothing. Ubuntu is on a separate drive, not dual-booted.
 Today, I finally gave up and went back to Ultimate 2.1, based on 8.10, and right off, I have sound, no issues. The forums are full of people who have issues with no sound, intermittent sound, and some things working.
 Can someone tell me why new versions are being released that DON'T WORK?
I saw in the forums people mentioning Pulseaudio was a major part of the problem. If this is so broken, why is it even used? In 8.10 and before, it all worked. I suggest either fix it, or drop it for something that doesn't require jumping through a thousand hoops to make it work.
Progress is NOT adding inoperable software. 
 I would really like this problem resolved, and if you can tell me why this is so broken right now, answer me in the forums.:mad:

---

### Post by killians31 on 2009-12-22
> **aimwin said:**
> I have the same problems.

I fixed it by, (reinstall alsa)
 
1. Open Terminal ( Application > Accessories > Terminal )

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Then "Shut Down" the computer.

2. Turn on Computer the Open Terminal again.

sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop

Then "Shut Down" the computer.

3. goto System > Preferences > Sound

   goto Hardware tab
   and goto Profile:
   Select "Analog Stereo Duplex"

That fixed my Audio

Ref: from [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


THANKS!! finally, i got my sound working!

kinda strange, but...i only did the first step, and sound began working.....

regardless, thanks!

---

### Post by bellial on 2009-12-22
Well... on my quest to get my sound going, I just can't login with my user anymore. I don't know what went wrong, I can login as root normally, and even created a new user for testing, and couldn't login in with it either. My /home is very important to me, and i was hoping to get the ubuntu going without needing to reinstall everything, with or without sound. Any help?

---

### Post by Scoops07 on 2009-12-28
> **aimwin said:**
> I have the same problems.

I fixed it by, (reinstall alsa)
 
1. Open Terminal ( Application > Accessories > Terminal )

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Then "Shut Down" the computer.

2. Turn on Computer the Open Terminal again.

sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop

Then "Shut Down" the computer.

3. goto System > Preferences > Sound

   goto Hardware tab
   and goto Profile:
   Select "Analog Stereo Duplex"

That fixed my Audio

Ref: from [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


This work for me as well, while also deactivating the Smartlink Modem found in Hardware drivers..

Thanx

---

### Post by susanw on 2009-12-28
When you've got your sound issues cleared a little bit, or maybe before, this fix for reinstalling pulse audio/alsa maybe worth a look at. After following it (logging out and in before step 5 was necessary) it cleared up the sound issues I was having - lack of sound after running the PC for a while, muted on login and firefox losing sound randomly.

[http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+%26amp;+pavucontrol](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+%26amp;+pavucontrol)

Susan

---

### Post by jeduffey on 2009-12-29
> **Kimeras said:**
> After finding this issue on release version of 9.10, I found that I didn't have sound either.

Reading the bug report, I came across this:

[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/441944](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/441944)



Sure enough, if you read the SmartLink Software Modem Driver, it actually describes this in some detail.

If this is the case for you, removing the restricted driver (System>Admin>Hardware Drivers) will immediately fix your sound problem.

This solved it for me on my Toshiba M400 Portege Tablet. Very happy camper. Thanks for the help.

---

### Post by bellial on 2009-12-30
It turned out that my problem was a conflict between pulseaudio and alsa. Removed pulseaudio (again) and everything worked like magic.

---

### Post by mad_dogs_bite on 2009-12-30
> **aimwin said:**
> I have the same problems.

I fixed it by, (reinstall alsa)
 
1. Open Terminal ( Application > Accessories > Terminal )

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Then "Shut Down" the computer.

2. Turn on Computer the Open Terminal again.

sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop

Then "Shut Down" the computer.

3. goto System > Preferences > Sound

   goto Hardware tab
   and goto Profile:
   Select "Analog Stereo Duplex"

That fixed my Audio

Ref: from [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Thanks, this worked for me as well; although I fear some random day I will find that my sound doesn't work again. I've had it before, but then I could always solve it by restarting alsa, or else by rebooting. This time I had to use this quite brute solution... I really hope they get the sound right for 10.04 :P

---

### Post by dictum9 on 2010-01-03
The same thing here, the same card and it's not recognized with 9.10. At times it works but usually it cuts out. A reboot doesn't help.

Any resolution to this bug?

---

### Post by KamakazieX on 2010-01-08
.02 cents.. I have a 9.10 AMD64 desktop with a 945 GTP board on my XBMC TV dedicated 9.10 AMD64 ubuntu and desktop. I did notice after patches the sound was muted... I think you guys are overlooking the simplest troubleshootng steps, configs are probably defaulted after an alsa update?.. Crank the software volume up!

---

### Post by ryseshan on 2010-01-20
Hai Friends,

I also faced same problem with no sound in 9.10.  I got solved from the file downloaded it fixed my sound problem. I am hereby giving u the link for the site so that u can download the file and fix ur sound problem in 9.10

[http://www.h3manth.com/content/sound-card-not-detected-ubuntu-910-fix-it](http://www.h3manth.com/content/sound-card-not-detected-ubuntu-910-fix-it)

---

### Post by Renntag on 2010-01-21
9.10 clean install on former WIN2k machine. 

I had sound, then after a reboot, no sound. 
Another Reboot, sound but video resolution lost. 
Another reboot, sound and optimal resolution returned. 

I know this doesnt help anyone, but I thought it perhaps interesting to share. 

I am fairly new to Ubuntu. Thank you to everyone that contributes here. 
This is a huge help.

---

### Post by prad.mote on 2010-01-23
Hi all,
just before two days i installed ubuntu 9.10 but there is no sound 
my speakers are fine but no sound.i need help
this is my lspci output:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

---

### Post by drdrez on 2010-01-24
Hello all:

I have always liked ubuntu and wanted to gradually phase it in full time usage but haven't because of other members of my family using the desktop.  Now i have a new HP laptop g71 (Intel Core2duo 320 GB sata, 4 GBs ram, Wireless N built in, Intel HD integrated graphics GMA 4500MHD with 1695 total graphics memory and 64 MB dedicated)

I installed 9.04 but there was no support for my wifi card and sound, then decided to do a clean install of 9.10 and found everything i was looking for.. The interface was very nice, i liked the color scheme.  it picked up my wifi, webcam (had to install cheese to use it), installed 3d graphics driver and compiz works Great and detected the presence of my sound card and internal mic.  But like many others i have a problem with not getting any sound output.  I tried going through the process of replacing ALSA with OSS 4 but this time it didn't detect the presence of my sound card.  so i reinstalled 9.10 cleanly and have it as a dual boot option.  Is there anyone who did manage to successfully get their sound working on this version number?

Thank you in advance.

Andres

---

### Post by drdrez on 2010-01-24
> **mad_dogs_bite said:**
> Thanks, this worked for me as well; although I fear some random day I will find that my sound doesn't work again. I've had it before, but then I could always solve it by restarting alsa, or else by rebooting. This time I had to use this quite brute solution... I really hope they get the sound right for 10.04 :P

Quick update...i did the above and it did not work, however it occured to me to use headphones and i have sound, still no sound through the speakers.  so i am not sure if the above fix did anything because i did not try headphones before but i just wanted to let ppl with sound problems know to try using a pair of headphones if they have sound through there

---

### Post by 16frogs on 2010-02-05
hi, this link fixed the no sound problem for me. [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) the link displayed in step1 of the above procedure explains how to update alsa from version 1.0.20 to the last version which is 1.0.22.1. ubuntu 9.10 comes with the later version. I had a clean install on a new Dell studio xps 1645 laptop. hope it works for you too.

---

### Post by Texasdad on 2010-02-16
I just installed ubuntu--and now I have no sound on my computer. I have Dynex 5.1 sound card in the computer--and it worked well with the Xp that I had. I'd hate to reinstall ubuntu--it took a while to do so for me. Any link tht I can use to "check " my system? 

I am a newbie---
please advise, thanks, Texasdad

---

### Post by Texasdad on 2010-02-16
Texasdad: this is what I get when I run sudo ispci v

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
    Capabilities: [88] Subsystem: Dell Device 0238
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [140] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ff00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [d0] Power Management version 2
    Kernel driver in use: i915
    Kernel modules: i915

00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]
    Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at fe00 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at fd00 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at fc00 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fb00 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
    Subsystem: Dell Device 0238
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] Vendor Specific Information <?>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at fa00 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at f900 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at f800 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
    Subsystem: Dell Device 0238
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fdffd000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] Vendor Specific Information <?>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
    Capabilities: [50] Subsystem: Dell Device 0238

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
    Subsystem: Dell Device 0238
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 0238
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f700 [size=8]
    I/O ports at f600 [size=4]
    I/O ports at f500 [size=8]
    I/O ports at f400 [size=4]
    I/O ports at f300 [size=16]
    I/O ports at f200 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] Vendor Specific Information <?>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
    Subsystem: Dell Device 0238
    Flags: medium devsel, IRQ 11
    Memory at fdffc000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell Device 0238
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f000 [size=8]
    I/O ports at ef00 [size=4]
    I/O ports at ee00 [size=8]
    I/O ports at ed00 [size=4]
    I/O ports at ec00 [size=16]
    I/O ports at eb00 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] Vendor Specific Information <?>
    Kernel driver in use: ata_piix

02:01.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
    Subsystem: MEDIATEK Corp. Device 1705
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at df00 [size=32]
    I/O ports at de00 [size=128]
    Capabilities: [80] Power Management version 1
    Kernel driver in use: ICE1724
    Kernel modules: snd-ice1724

---

### Post by Renntag on 2010-02-25
> **lbelloq said:**
> Could you post lspci's output?


I am enjoying 9.10 minus this No Sound issue. 

lspci's output:

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:08.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax Modem (rev 08)
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)


Any help greatly appreciated.

---

### Post by Talat777n on 2010-02-27
Thank you very much for this [link]("http://ubuntuforums.org/showthread.php?t=843012"), very useful link to resolve sound problem

---

### Post by okuzster on 2010-03-01
no sound here to,  lspci output:


00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 3100 Graphics
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
03:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)



thanks

---

### Post by vtmet on 2010-03-01
New to using Linux...Computer got a trojan that kept making it power down that we couldn't shake...After reformatting HD, Windows XP still crashed...Reformatted again, and installed Unbuntu 9.10...no more crashing, and is now a lot faster than it ever was with Windows...

I've figured out how to make the computer mostly functionable, however, there is no sound at all...

Don't know what this info means, but here it is (if anyone can decipher and let me know how to fix it)...Thanks

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8310 and 88W8000G [Libertas] 802.11g client chipset (rev 07)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:04.0 Mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 13)
01:09.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
04:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

---

### Post by Mnew2Linux on 2010-04-02
Hello; I'm having the same issue with an upgrade from 9.04.  There is a difference here with me, however.  I am dual booting a WinXP SP3 machine (on HD (0,0)) and the newly upgraded Ubuntu 9.10 (on HD (1,0)).  The Windows machine had sound prior to the upgrade to 9.10; after that, no dice.  So I decided to do a little search on this error and came across this thread, please assist. 

sudo lspci output:
> 00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:08.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


sudo lsmod output:
> Module                  Size  Used by
nls_utf8                1568  1 
isofs                  31620  1 
binfmt_misc             8356  1 
snd_usb_audio          84224  1 
snd_usb_lib            16284  1 snd_usb_audio
snd_hwdep               7200  1 snd_usb_audio
iptable_filter          3100  0 
snd_intel8x0           30168  2 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_ca0106             34240  2 
snd_ac97_codec        101216  2 snd_intel8x0,snd_ca0106
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  5 snd_usb_audio,snd_intel8x0,snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  3 snd_usb_lib,snd_ca0106,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               7089800  34 
ppdev                   6688  0 
usblp                  12636  0 
gspca_zc3xx            47580  0 
gspca_main             22812  1 gspca_zc3xx
videodev               36736  1 gspca_main
v4l1_compat            14336  1 videodev
joydev                 10240  0 
serio_raw               5280  0 
shpchp                 32272  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  24 snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_intel8x0,snd_ca0106,snd_pcm
parport_pc             31940  1 
i2c_nforce2             6784  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  2 
forcedeth              54152  0 
floppy                 54916  0 
nvidia_agp              6200  1 
agpgart                34988  2 nvidia,nvidia_agp


Prior to me recognizing I didn't have sound I noticed a lot of entries in the grub loader that I wanted to clear up (my OCD kicked in).  So I sudo gedit /boot/grub/menu.lst and commented out the entries I didn't want to see.  I then went to my Windows side to do a few updates and noticed I had no sound.  I'm not sure there is a correlation but I checked device manager in XP for issues with sound devices...no dice.  Checked msconfig>startup to see if I messed up somewhere...no dice.  I restarted and went to the Ubuntu side, still no sound.  I uncommented what I commented out in menu.lst.  I'm at a loss.  

Again, please assist; let me know if any of you have experienced a similar issue with WinXP and 9.10.  Thanks!

---

### Post by lidex on 2010-04-03
Go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
There are some known generic sound issues in Karmic and this thread addresses them. Report back here with your progress.

---

### Post by Mnew2Linux on 2010-04-03
That can't be it, looks like I'm running the right kernel: 2.6.31-20-generic

---

### Post by lidex on 2010-04-03
Unfortunately that's not the only thing...you need to work through the entire page to eliminate the usual suspects...it's called troubleshooting

---

### Post by Mnew2Linux on 2010-04-03
Could you say that again?  Trouble what?  :lolflag:  You mean I actually have to do work?  Ok, I agree, that was a lame attempt; I'll go back and check it out.  I only noticed the first part and thought that was the end of the road.  

On a side note, do you think that my Windows side would be affected by the sound issues?

> **lidex said:**
> Unfortunately that's not the only thing...you need to work through the entire page to eliminate the usual suspects...it's called troubleshooting

---

### Post by lidex on 2010-04-03
;) Could be. I was just looking at a thread involving a soundblaster that only works in linux after booting into windows. I imagine it's a firmware issue.

---

### Post by Mnew2Linux on 2010-04-03
It doesn't make sense to me though; again, when I had Jaunty it worked there and in XP.  The only other thing that I can think of is that when I upped to Karmic, my sound card didn't like it and decided to not work for anything.  Wouldn't hurt to try safe mode and see if there is any sound there (though I'm not sure if safe mode will have sound; 'bout to find out!)...

P.S. None of the other troubleshooting options helped.

---

### Post by Mnew2Linux on 2010-04-03
No sound in safe mode (duh) and no sound in Karmic; square one?

> **Mnew2Linux said:**
> It doesn't make sense to me though; again, when I had Jaunty it worked there and in XP.  The only other thing that I can think of is that when I upped to Karmic, my sound card didn't like it and decided to not work for anything.  Wouldn't hurt to try safe mode and see if there is any sound there (though I'm not sure if safe mode will have sound; 'bout to find out!)...

P.S. None of the other troubleshooting options helped.

---

### Post by lidex on 2010-04-03
OK. Have you installed the alsa backports? This is an add-on card, right?

---

### Post by Mnew2Linux on 2010-04-04
Just tried the backports and still no sound.  Yes, the card is an add on.

---

### Post by lidex on 2010-04-06
Sorry for the delay. Can we have some more detailed info?
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Mnew2Linux on 2010-04-07
Here you go:

[URL="http://www.alsa-project.org/db/?f=9868f66c02c7d6b67b5c0b7c0c742ced144ee6b6"]http://www.alsa-project.org/db/?f=9868f66c02c7d6b67b5c0b7c0c742ced144ee6b6
[/URL]

```
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=9868f66c02c7d6b67b5c0b7c0c742ced144ee6b6

Please inform the person helping you.
```

---

### Post by lidex on 2010-04-07
Can you post the output of this command please?
```
cat /etc/modprobe.d/alsa-base.conf
```

Looks like your soundcards are recognized. Can you disable onboard audio in bios?
Also, have you tried alsamixer, toggling between soundcards with the F6 key?
```
alsamixer
```

And/or set defaults in pulseaudio volume control? You did part A here?[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by linden940 on 2010-04-08
coming into this one late...just tossing this one out there...have you tryed headphones? did you get sound? did you try more than one port on the computer?

this is just random but it looks like alot of ppl are trying and nothing is helping..maybe its something on the simpler side

---

### Post by Mnew2Linux on 2010-04-09
Output of cat /etc/modprobe.d/alsa-base.conf:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

```

I did not do Part A; I'm trying now but running into a few problems...
e.g., I tried to manually open the PulseAudio Device Chooser (Applications>Sound & Video>PulseAudio Device Chooser).  It opened but I cannot access it.  I see it in the top right of my screen (help me with the name) but I cannot access it.  Here's the output of **pavucontrol**:
```
lee@lee-desktop:~$ pavucontrol

(pavucontrol:4354): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
lee@lee-desktop:~$
```

and **pulseaudio & pavucontrol**:

```
lee@lee-desktop:~$ pulseaudio & pavucontrol
[1] 4373
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:4374): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed

[1]+  Exit 1                  pulseaudio
```

I think I might have done something wrong along the way...I will try to disable on-board audio; I'm not sure what you mean by the F6 key but I guess I'll try that too...


> **lidex said:**
> 

Looks like your soundcards are recognized. Can you disable onboard audio in bios?
Also, have you tried alsamixer, toggling between soundcards with the F6 key?
```
alsamixer
```

And/or set defaults in pulseaudio volume control? You did part A here?[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by Mnew2Linux on 2010-04-09
I'm not sure what trying headphones would do for the sound.  Doesn't it all come from the same source?

> **linden940 said:**
> coming into this one late...just tossing this one out there...have you tryed headphones? did you get sound? did you try more than one port on the computer?

this is just random but it looks like alot of ppl are trying and nothing is helping..maybe its something on the simpler side

---

### Post by Mnew2Linux on 2010-04-09
So I disabled the on-board sound, logged into Karmic and voila, I now have sound.  I wanted to see if my XP Pro side had sound but I'm not so lucky.  I then rebooted and changed the on-board back to auto and Karmic still has sound.  Very odd to me that after all of this, I now have sound...now I have to clean up the grub cause it's lookin' nasty.  

Two questions:
1. How do I get sound back in Windows? 
2. Why would my sound all of a sudden start working like this?  (I honestly just did the on-board switch in the bios)

Thanks

---

### Post by Improviz on 2010-04-14
Hey guys, coming into this late. Like a few others here, I've got an old Dell 8200 with a Santa Cruz card in it. Alsamixer runs but doesn't seem to see the card. There doesn't seem to be onboard sound that I can find. This was a 'wipe drive and only install 9.10' type of deal. It's my first go-round with Ubuntu (or Linux for that matter).  Trying to get the comp working for a disabled friend, all is good, even the wireless, but no sound.  If finding an old Sound Blaster card is the answer, I'll try to locate one. 
Otherwise, has anyone had any luck with any of the various schemes posted here? I'm willing to go through all the troubleshooting, but if someone else has proven it to be ineffective, I wouldn't mind saving my time.  Appreciate any pointers.

---

### Post by dictum9 on 2010-04-17
> **lidex said:**
> Sorry for the delay. Can we have some more detailed info?
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```Enter your user password when prompted. Provide a link for the output or post it here using code tags.

Broken link:

Firefox can't find the server at git.alsa-project.org.

---

### Post by dictum9 on 2010-04-17
No sound at all in Ubuntu 9.10. Used to be able to get sound via headphones, now nothing at all. 
Any idea what to try?

Here is lspci, lsmod and /etc/modprobe.d/alsa-base.conf output.


# more lspci.out
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10272  0 
snd_hda_codec_idt      59844  1 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_intel          26920  8 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
iptable_filter          3100  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  3 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
b43                   122136  0 
mac80211              181076  1 b43
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
dell_wmi                2564  0 
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
cfg80211               93052  2 b43,mac80211
ricoh_mmc               3676  0 
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
led_class               4096  2 b43,sdhci
psmouse                56500  0 
serio_raw               5280  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  23 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  3 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usbhid                 38208  0 
b44                    28684  0 
i915                  221064  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
mii                     5212  1 b44
ssb                    35300  2 b43,b44
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp




# more  /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

---

### Post by lidex on 2010-04-18
> **Mnew2Linux said:**
> So I disabled the on-board sound, logged into Karmic and voila, I now have sound.  I wanted to see if my XP Pro side had sound but I'm not so lucky.  I then rebooted and changed the on-board back to auto and Karmic still has sound.  Very odd to me that after all of this, I now have sound...now I have to clean up the grub cause it's lookin' nasty.  

Two questions:
1. How do I get sound back in Windows? 
2. Why would my sound all of a sudden start working like this?  (I honestly just did the on-board switch in the bios)

Thanks

There's a chance windows was configured to the first soundcard it picked up which would be the onboard. In any case, I would boot into windows and look at device Manager. If you see any remnants of that remove them and reboot to see if windows recognizes the second card and loads the correct driver.

---

### Post by lidex on 2010-04-18
> **dictum9 said:**
> No sound at all in Ubuntu 9.10. Used to be able to get sound via headphones, now nothing at all. 
Any idea what to try?


alsa-project.org is bringing me down!
Can you post the output of these commands for me:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by ilyas_benyaich on 2011-09-04
Okay , I know it's been ages since the last reply but II had to deal with  this issue  just before the upgrade from 9.10 to 10.4.

My pc hanged , so I had to turn it off the "ugly way" (via the power button) .

After the reboot,  I lost the sound on my speakers and this helped :

try to go to system->preferences->sound

Under the material tab try this :

If you see something like analog "analog stereo outpout" , try to change it to something more like "Analog Stereo Output 5.1" or "Analog Stereo Output 7.1" . 

I have two codecs , one is from Realtek and the other is from Intel .

Anyway ,I hope this will help someone...

---

