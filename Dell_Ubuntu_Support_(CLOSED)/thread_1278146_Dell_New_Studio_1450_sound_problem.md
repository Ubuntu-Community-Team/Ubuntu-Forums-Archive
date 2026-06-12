---
title: "Dell New Studio 1450 sound problem"
date: 2009-09-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cnbiz850 on 2009-09-29
I know there is a lot of discussions related to sound problems and there have been ways to resolve them.  Some are regarding Dell's.  Unfortunately I can't resolve the problem with mine according to many discussions.  I write it here hoping someone can help with some specifics.

I just got it (P8700 CPU with DDR3 4GB RAM and 14 inch screen with ultra-sharp resolution and the "srs premium sound") and loaded 9.04 on it.  No big issues to get it working.  Then I discovered that there is no sound at all from the speakers.  (There is some low-volume sound on the ear-phones.)  I learnt that by finding the module tag and put it in alsa-base.conf file and things should work, but the problem is that my card is not included in the alsa document which contains the corresponding tags.

```
head -n 1 /proc/asound/card0/codec*
Codec: Realtek ID 665

```

It says ID 665 and on the brochure it says ALC665.  There is no 665.  I tried some tags associated with 660/662/663 having no luck.  I also upgraded alsa to the latest with a script on the net.

```
more /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Sep 29 2009 for kernel 2.6.28-15-server (SMP).

```

Still no luck.  And in that documents, there is no mention of 665 either.

Am I stuck, or could anyone please help?

The I installed osslinux and that produced some sound but with very low volume.


[Solution]: This is solved.  Please see post #18 for guidance.

---

### Post by cnbiz850 on 2009-10-14
I tried various systems including 9.04 32bits/64bits and 9.10 64bits.  Still no solution.  Seems it has to do with the ICH9 chipsets.

But guess what?  Surprisingly today, I received a package.  Opening it, I found a very portable USB speaker as a gift from Dell.  There are Dell and Intel logos on it.  It has its own sound card.  I plugged it in and it works on 9.10 64bits system.  I have no idea on why Dell sent it to me.  It was not indicated as a bonus package at the time of purchase.  Maybe they have received enough calls from Linux users about the sound problem (it works on Vista).  I hope it is the case.

Anyhow, I got a temporary solution.

---

### Post by sashhoney on 2009-10-23
hi
i was just browsing through your thread!
have you found any proper solution to your problem yet?
i mean have you got any solution of ALSA related problem with Dell Studio 14
i am having the same output as you mentioned, codec is Realtek ID 665 only
i am not as lucky as you to get a gift from dell though???

---

### Post by cnbiz850 on 2009-10-23
Nothing more than last report.  I guess maybe we have to wait for ICH9 related drivers.  If you find out more, please do report it.  Good luck.

---

### Post by slaiyer on 2009-10-29
has some one been able to solve this, because i have just bought a new dell studio 1450 and having the same problems....tried all i could find, and just concluded that the drivers need updating or proprietary.

it will be really healpful is there is a solution

i have jus upgraded to ubuntu 9.10 x64 thinking it will have it solved but the problem is still there.

---

### Post by secure on 2009-11-22
same problem but I'm new to ubuntu so don't have any idea to resolve this problem T T

---

### Post by litnit on 2009-12-05
Hey guys, anyone found any solution on this problem yet? Pls share, I am damn new here, don't know what should i do..

Thanks..

---

### Post by lawenlerk on 2009-12-10
Im looking to buy this laptop so i did some research too.

here's what i found but cant confirm

[http://groups.google.com/group/ilug-tvm/browse_thread/thread/500ce5e1b2e4b145](http://groups.google.com/group/ilug-tvm/browse_thread/thread/500ce5e1b2e4b145)

The guy says installing oss solved it right away.

Can anyone test this out?

Thanks

---

### Post by marcond on 2009-12-12
Hello

I have the same problem with an Dell Studio 1450 (sold in Brazil) and have tested the OSS on it. **It _worked partially_, yes I got sound, but no microphone and the sound is like a old radio.** Not an old radio like the ones we had (we used to have FM radios, with good sound), but more like an old radio of my grandmother. I tried to tweak the oss mixer with no luck to get a better sound.

I used the step-by-step tutorial that can be found at:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

On the tutorial you can download either the .deb or compile yourself the OSS. I choosed compile the OSS on my machine, using the latest testing tarball method to get the source code.

I'm using here Kubuntu Karmic 9.10. Bellow are the lspci, lsmod, lspci -v from my system (**before** installing OSS). If you need more information, let me know.

Regards,
Marcond

[FONT=Courier New][FONT=Courier New]marcond@enterprise:~$ lsmod
Module                  Size  Used by
ufs                    76904  0      
qnx4                   10536  0    [/FONT]  
hfsplus                81032  0      
hfs                    50152  0      
minix                  33168  0      
ntfs                  101792  0      
vfat                   13184  0      
msdos                   9664  0      
fat                    59832  2 vfat,msdos
jfs                   190160  0           
xfs                   535136  0           
exportfs                5472  1 xfs       
reiserfs              247720  0           
cryptd                  8008  0           
aes_x86_64              8992  1           
aes_generic            28480  1 aes_x86_64
ppdev                   8232  0           
vboxnetadp              6528  0           
vboxnetflt             14288  0           
vboxdrv              1777740  2 vboxnetadp,vboxnetflt
snd_hda_codec_atihdmi     4320  1                    
bridge                 56384  0                      
stp                     3012  1 bridge               
snd_hda_codec_realtek   277860  0                    
arc4                    2144  2                      
bnep                   15168  2                      
ecb                     3296  2                      
snd_hda_intel          31880  3                      
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
iwlagn                124832  0                                                          
snd_hwdep               9352  1 snd_hda_codec                                            
snd_pcm_oss            44704  0                                                          
snd_mixer_oss          18976  1 snd_pcm_oss                                              
snd_seq_dummy           3460  0                                                          
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss                  
snd_seq_oss            33440  0                                                          
snd_seq_midi            8192  0                                                          
iwlcore               133312  1 iwlagn                                                   
snd_rawmidi            27360  1 snd_seq_midi                                             
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi                                 
btusb                  14260  2                                                          
joydev                 13088  0                                                          
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
led_class               5256  1 iwlcore                                                  
snd_timer              26992  2 snd_pcm,snd_seq                                          
mac80211              209912  2 iwlagn,iwlcore                                           
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                                     
uvcvideo               65260  0                                                                               
soundcore               9088  1 snd                                                                           
iptable_filter          3872  0                                                                               
ip_tables              21200  1 iptable_filter                                                                
videodev               43360  1 uvcvideo                                                                      
dell_wmi                3216  0                                                                               
v4l1_compat            16804  2 uvcvideo,videodev                                                             
cfg80211              109144  3 iwlagn,iwlcore,mac80211                                                       
x_tables               25832  1 ip_tables                                                                     
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm                                                         
coretemp                7072  0                                                                               
dell_laptop             9692  0                                                                               
v4l2_compat_ioctl32    13344  1 videodev                                                                      
psmouse                57124  0                                                                               
fglrx                2234552  30                                                                              
serio_raw               6596  0                                                                               
dcdbas                  9136  1 dell_laptop                                                                   
lp                     11908  0                                                                               
parport                40528  2 ppdev,lp                                                                      
usbhid                 43968  0                                                                               
tg3                   123748  0                                                                               
video                  23612  0                                                                               
output                  3680  1 video                                                                         
intel_agp              32816  0                                                                               
marcond@enterprise:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)  
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)  
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)  
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)       
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)          
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)          
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)          
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)  
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)  
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)  
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)                          
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)                   
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)              
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)                 
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]    
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]            
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
06:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection  
marcond@enterprise:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
        Subsystem: Dell Device 02e8                                                          
        Flags: bus master, fast devsel, latency 0                                            
        Capabilities: <access denied>                                                        
        Kernel modules: intel-agp                                                            

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
        Flags: bus master, fast devsel, latency 0                                               
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0                            
        I/O behind bridge: 00002000-00002fff                                                    
        Memory behind bridge: fc000000-fc0fffff                                                 
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff                    
        Capabilities: <access denied>                                                           
        Kernel driver in use: pcieport-driver                                                   
        Kernel modules: shpchp                                                                  

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
        Subsystem: Dell Device 02e8                                                           
        Flags: bus master, medium devsel, latency 0, IRQ 16                                   
        I/O ports at 1800 [size=32]                                                           
        Capabilities: <access denied>                                                         
        Kernel driver in use: uhci_hcd                                                        

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
        Subsystem: Dell Device 02e8                                                           
        Flags: bus master, medium devsel, latency 0, IRQ 21                                   
        I/O ports at 1820 [size=32]                                                           
        Capabilities: <access denied>                                                         
        Kernel driver in use: uhci_hcd                                                        

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
        Subsystem: Dell Device 02e8                                                           
        Flags: bus master, medium devsel, latency 0, IRQ 19                                   
        I/O ports at 1840 [size=32]                                                           
        Capabilities: <access denied>                                                         
        Kernel driver in use: uhci_hcd                                                        

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
        Subsystem: Dell Device 02e8                                                                         
        Flags: bus master, medium devsel, latency 0, IRQ 19                                                 
        Memory at fc304800 (32-bit, non-prefetchable) [size=1K]                                             
        Capabilities: <access denied>                                                                       
        Kernel driver in use: ehci_hcd                                                                      

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Dell Device 02e8                                                      
        Flags: bus master, fast devsel, latency 0, IRQ 22                                
        Memory at fc300000 (64-bit, non-prefetchable) [size=16K]                         
        Capabilities: <access denied>                                                    
        Kernel driver in use: HDA Intel                                                  
        Kernel modules: snd-hda-intel                                                    

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0                  
        I/O behind bridge: 00003000-00003fff                                          
        Memory behind bridge: f6000000-f7ffffff                                       
        Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff          
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0                  
        I/O behind bridge: 00004000-00004fff                                          
        Memory behind bridge: f8000000-f9ffffff                                       
        Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff          
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=06, subordinate=07, sec-latency=0                  
        I/O behind bridge: 00005000-00005fff                                          
        Memory behind bridge: fa000000-fbffffff                                       
        Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff          
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
        Subsystem: Dell Device 02e8                                                           
        Flags: bus master, medium devsel, latency 0, IRQ 20                                   
        I/O ports at 1860 [size=32]                                                           
        Capabilities: <access denied>                                                         
        Kernel driver in use: uhci_hcd                                                        

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
        Subsystem: Dell Device 02e8                                                           
        Flags: bus master, medium devsel, latency 0, IRQ 19                                   
        I/O ports at 1880 [size=32]                                                           
        Capabilities: <access denied>                                                         
        Kernel driver in use: uhci_hcd                                                        

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
        Subsystem: Dell Device 02e8                                                           
        Flags: bus master, medium devsel, latency 0, IRQ 18                                   
        I/O ports at 18a0 [size=32]                                                           
        Capabilities: <access denied>                                                         
        Kernel driver in use: uhci_hcd                                                        

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
        Subsystem: Dell Device 02e8                                                                         
        Flags: bus master, medium devsel, latency 0, IRQ 20                                                 
        Memory at fc304c00 (32-bit, non-prefetchable) [size=1K]                                             
        Capabilities: <access denied>                                                                       
        Kernel driver in use: ehci_hcd                                                                      

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
        Flags: bus master, fast devsel, latency 0                                  
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=0               
        Capabilities: <access denied>                                              

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
        Subsystem: Dell Device 02e8                                          
        Flags: bus master, medium devsel, latency 0                          
        Capabilities: <access denied>                                        
        Kernel modules: iTCO_wdt                                             

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
        Subsystem: Dell Device 02e8                                                            
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28                             
        I/O ports at 18f0 [size=8]                                                             
        I/O ports at 18e4 [size=4]                                                             
        I/O ports at 18e8 [size=8]                                                             
        I/O ports at 18e0 [size=4]                                                             
        I/O ports at 18c0 [size=32]                                                            
        Memory at fc304000 (32-bit, non-prefetchable) [size=2K]                                
        Capabilities: <access denied>                                                          
        Kernel driver in use: ahci                                                             

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
        Subsystem: Dell Device 02e8                                            
        Flags: medium devsel, IRQ 10                                           
        Memory at be000000 (64-bit, non-prefetchable) [size=256]               
        I/O ports at 1c00 [size=32]                                            
        Kernel modules: i2c-i801                                               

01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
        Subsystem: Dell Device 02e8                                                         
        Flags: bus master, fast devsel, latency 0, IRQ 31                                   
        Memory at d0000000 (32-bit, prefetchable) [size=256M]                               
        I/O ports at 2000 [size=256]                                                        
        Memory at fc000000 (32-bit, non-prefetchable) [size=64K]                            
        [virtual] Expansion ROM at fc020000 [disabled] [size=128K]                          
        Capabilities: <access denied>                                                       
        Kernel driver in use: fglrx_pci                                                     
        Kernel modules: fglrx, radeon                                                       

01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
        Subsystem: Dell Device 02e8
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fc010000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
        Subsystem: Dell Device 02e8
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: tg3
        Kernel modules: tg3

06:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
        Subsystem: Intel Corporation Device 1121
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at fa000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

marcond@enterprise:~$
[/FONT]

---

### Post by lawenlerk on 2009-12-13
So after compiling oss by yourself it still sounds like an old radio?

hmm...funny how dell supports linux yet uses unsupported hardware.
I hope they come up with a solution soon.

---

### Post by marcond on 2009-12-14
> **lawenlerk said:**
> So after compiling oss by yourself it still sounds like an old radio?

hmm...funny how dell supports linux yet uses unsupported hardware.
I hope they come up with a solution soon.

Yes, I hope so.

About the machine, here goes my 1-cent review: everything else works remarkably well, WiFi, bluetooth, suspend, hibernation and so on, out of the box, with a clean Kubuntu Karmic install. The machine runs very cool, compared with my previous laptop, a Toshiba, that was always hot.

The only compaints I have about this machine are A) the TOTAL lack of any led, i.e. you cannot see if the HD is being read/write, caps lock status, etc and B) the angle of the webcam, wich is flat with the screen, instead of being slightly curved down like a Toshiba that my wife have. So, if you place the screen directly at sight line the webcam will pick your head at the lower-half of the video.

Well, nothing TOO problematic, only minor details.

And, if you can, get the HD+ LED display (1600x900), it's awesome.

About the sound problem I think that is mostly related with the codec used on this machine, which is Realtek's ALC665, and as far as I know isn't supported yet on ALSA.

Regards,
Marcond

---

### Post by lawenlerk on 2009-12-14
> **marcond said:**
> Yes, I hope so.

About the machine, here goes my 1-cent review: everything else works remarkably well, WiFi, bluetooth, suspend, hibernation and so on, out of the box, with a clean Kubuntu Karmic install. The machine runs very cool, compared with my previous laptop, a Toshiba, that was always hot.

The only compaints I have about this machine are A) the TOTAL lack of any led, i.e. you cannot see if the HD is being read/write, caps lock status, etc and B) the angle of the webcam, wich is flat with the screen, instead of being slightly curved down like a Toshiba that my wife have. So, if you place the screen directly at sight line the webcam will pick your head at the lower-half of the video.

Well, nothing TOO problematic, only minor details.

And, if you can, get the HD+ LED display (1600x900), it's awesome.

About the sound problem I think that is mostly related with the codec used on this machine, which is Realtek's ALC665, and as far as I know isn't supported yet on ALSA.

Regards,
Marcond

Hey did u try suse on ur comp? Like this guy said,

[http://www.linuxquestions.org/questions/susenovell-60/realtek-alc-665-sound-10.3-11.0-64-bit-anybody-got-it-to-work-651910/](http://www.linuxquestions.org/questions/susenovell-60/realtek-alc-665-sound-10.3-11.0-64-bit-anybody-got-it-to-work-651910/)

> 
Hi there
I loaded the new LiveCD 64 bit version and re-installed.
Sound now working perfectly -- make sure you enable the right master volume --it's more complicated than 10.3. TV card also working without having to disable XGL.

cheers

-k

Btw, thanks for the review. I really needed that. Somehow couldn't find any other good reviews on the studio 14

---

### Post by secure on 2009-12-22
thank you very much
I follow 
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
and It's work
(I install OSS by download .deb from [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) )
and It's work sound very good :):)

---

### Post by s1d on 2009-12-23
Hi,

I too bought a Dell Studio 1450 some time back and have been struggling to get the sound on.
I am currently running Ubuntu Karmic amdx64 version.
Anyone able to resolve this yet?
And yes...I don't want the OSS solution.

---

### Post by fabiobh0 on 2010-01-02
I managed to get a temporary solution by installing OSS as described here:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Now I get loud and clear sound, but the controls are not working properly.

---

### Post by wtpau on 2010-01-06
Hi guys!

I brought 1450 2 weeks ago and installed Ubuntu 9.10 64bit version on it (dual boot with window 7).

On Win 7 everything works fine. However on ubuntu I got no sound from speaker, low volume sound from the headphone jack.

I hope the next 10.04 release could resolve this issue.

---

### Post by marcond on 2010-01-20
Hello everybody

Just to report the current status:

1) I've attempted to install Suse, and it doesn't solve the sound problem.
2) The OSS solution works, but actually has problems with the controls.
3) The current ALSA doesn't have support for ALC665.

I'm researching this topic slowly 'cos I am very busy. I've also sent an email to Realtek developed team, that got answered. They asked me to download and test the latest realtek linux drivers from [www.realtek.com](www.realtek.com). I did this, but in fact these drivers are almost (if not exactly) an snapshot from Alsa 1.21 or something (the latest Alsa version by now). So the sound drivers from realtek didn't worked.

If someone out there is brave enough, the databook for ALC665 can be downloaded directly from Realtek through this link:

[ftp://WebUser:7p5XTFw@152.104.238.19/pc/audio/ALC665_DataSheet_1.0.pdf](ftp://WebUser:7p5XTFw@152.104.238.19/pc/audio/ALC665_DataSheet_1.0.pdf)

That's it by now. By the way, the date of the datasheet file is Dec 28, 2009. So the chipset is really pretty new.

Regards
Marcond

---

### Post by alokcool on 2010-01-29
Now Problem is solved by installing latest alsa driver which supports ALC 665 From realtek website
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

After installing these drivers I'm getting sounds from speakers as well as on headphones.

Follow these steps but compile the alsa driver,alsa library and alsa plugins from the files provided by realtek

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

Now enjoy Audio on your studio 1450 with ubuntu

---

### Post by marcond on 2010-02-01
CONFIRMED!!!

I've compiled the LinuxPkg_5.14rc2.tar.bz2 from Realtek as suggested and it worked fine, sound recognized and working.

Thanks for the tip Alokcool!
Marcond

> **alokcool said:**
> Now Problem is solved by installing latest alsa driver which supports ALC 665 From realtek website
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

After installing these drivers I'm getting sounds from speakers as well as on headphones.

Follow these steps but compile the alsa driver,alsa library and alsa plugins from the files provided by realtek

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

Now enjoy Audio on your studio 1450 with ubuntu

---

### Post by s1d on 2010-02-23
It works!
Thanks a lot alokcool :)

There seem to be some additional options in realtek's install guide about enabling hda options.
But it works perfectly with the procedure given in [http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

---

### Post by R2ROE on 2010-03-18
Is it possible to provide a little step by step for us noobs. I downloaded the driver from the realtek web site, but im stuck in Step 2. Turn on sound support from kernel config 
    (soundcore module, default turn on)
I have no idea where kernel config is at, or how to access it. So I was wondering if you could provide a little step by step for us noobs

Thanks

---

### Post by ybbob549 on 2010-03-24
i got a dellstudio 1450.sound is not working in it on instaling ubuntu 9.10 64-bit version.

i neeed ur help...i expect my problem will be resolved with atleast ubuntu 10.04

---

### Post by cnbiz850 on 2010-04-25
A problem of the solution is that Firefox has not sound when playing video.  Anyone know what to do?

---

### Post by biplab on 2010-05-06
CONFIRMED.............CONFIRMED................CONFIRMED..................CONFIRMED

My Dell new studio 1450 works pretty well with ubuntu 10.04 LTS (AMD64),except the sound. After a lot of googling, the problem is SOLVED. Please follow the following steps:

1. *[Click here to download Realtek driver from Realtek website]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")*[B][URL="http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false"]
[/URL][/B] 
2. Accept Terms and Conditions and click next (it will bring you to the next page)

3. in the new page, scroll down and find **Unix (linux) title** , and there you will be able to see this info : **Description** = Linux driver (2.6), **Version** = 5.15rc1, in a table. Click one of "**GO**" links in the row of the table. It will download the driver, "LinuxPkg-5.15rc1.tar.bz2".

4. _Find the driver and extract it on the file system_

5. Now, _start your terminal program_ and navigate to the extracted folder:
    
   cd Downloads/real*/alsa-driver-1.0.xx         
                        
6. configure:
     
    sudo ./configure --with-cards=hda-intel                                 

7. make:
     
    sudo make                                 

8. install:
  
    sudo make install       
                          
9. You need not compile the rest of the stuffs in the realtek directory (e.g., alsa-libs, alsa-utils, etc..).

10. Now you may exit from your terminal and **restart** your computer. 
       When it reboot again, you will hear ubuntu's login sound as usual... 

11. [SIZE=2]More information about the driver can be found in readme.txt file under    
    extracted driver folder.                      [/SIZE]           

[COLOR=Red]**Trouble-shooting after installation info:**[/COLOR]
     
                    [SIZE=2]If you did some updates to kernel (also when update manager did some updates to kernel), your sound may lost again but don't be panic, just follow step 6 to 9 again to regain your sound.[/SIZE]
Have a nice day and enjoy your ubuntu day!. :KS[IMG]http://georgia.ubuntuforums.org/images/smilies/guitar.gif[/IMG]

---

### Post by biplab on 2010-05-06
CONFIRMED.............CONFIRMED................CONFIRMED..................CONFIRMED

My Dell new studio 1450 works pretty well with ubuntu 10.04 LTS (AMD64),except the sound. After a lot of googling, the problem is SOLVED. Please follow the following steps:

1. *[Click here to download Realtek driver from Realtek website]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")*[B][URL="http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false"]
[/URL][/B] 
2. Accept Terms and Conditions and click next (it will bring you to the next page)

3. in the new page, scroll down and find **Unix (linux) title** , and there you will be able to see this info : **Description** = Linux driver (2.6), **Version** = 5.15rc1, in a table. Click one of "**GO**" links in the row of the table. It will download the driver, "LinuxPkg-5.15rc1.tar.bz2".

4. _Find the driver and extract it on the file system_

5. Now, _start your terminal program_ and navigate to the extracted folder:
    
   cd Downloads/real*/alsa-driver-1.0.xx         
                        
6. configure:
     
    sudo ./configure --with-cards=hda-intel                                 

7. make:
     
    sudo make                                 

8. install:
  
    sudo make install       
                          
9. You need not compile the rest of the stuffs in the realtek directory (e.g., alsa-libs, alsa-utils, etc..).

10. Now you may exit from your terminal and **restart** your computer. 
       When it reboot again, you will hear ubuntu's login sound as usual... 

11. [SIZE=2]More information about the driver can be found in readme.txt file under    
    extracted driver folder.                      [/SIZE]           

[COLOR=Red]**Trouble-shooting after installation info:**[/COLOR]
     
                    [SIZE=2]If you did some updates to kernel (also when update manager did some updates to kernel), your sound may lost again but don't be panic, just follow step 6 to 9 again to regain your sound.[/SIZE]
Have a nice day and enjoy your ubuntu day!. :KS[IMG]http://georgia.ubuntuforums.org/images/smilies/guitar.gif[/IMG]

---

### Post by madhums on 2010-05-13
Download [http://mirror.ipgn.com.au/drivers/sound/realtek/LinuxPkg-5.15rc1.tar.bz2](http://mirror.ipgn.com.au/drivers/sound/realtek/LinuxPkg-5.15rc1.tar.bz2)

Extract, go into the folder “realtek-linux-audiopack-5.15&#8243;

<code>
sudo sh install
</code>

thats it! restart!

---

### Post by cnbiz850 on 2010-05-16
> **cnbiz850 said:**
> A problem of the solution is that Firefox has not sound when playing video.  Anyone know what to do?

And Firefox video also causes sound to die.  I am running 64bit Karmic.  The flash player was 32bit and now I got the 64bit version, but it makes no difference on the sound.  Anyone has a solution?

---

