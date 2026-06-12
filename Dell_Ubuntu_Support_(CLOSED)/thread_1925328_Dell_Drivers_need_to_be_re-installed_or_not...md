---
title: "Dell Drivers need to be re-installed or not..??"
date: 2012-02-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by satyamM on 2012-02-14
I have installed Ubuntu 10.04 few days back and it seems some things are not working....like Bluetooth, Wi-Fi, WebCam and may be some other things.....where do I get these things?.....do i have to install dell drivers again which was given at the time of buying..?...Please help..!! Thanks.

---

### Post by satyamM on 2012-02-14
please some one reply.....i need desperate help from some one who knows these things.....!!!!!!!!   :(

---

### Post by mikewhatever on 2012-02-14
Can you post the computer model and specs. Without that info, it's hard to answer such questions.

---

### Post by satyamM on 2012-02-16
[_@mikewhatever _]("http://ubuntuforums.org/member.php?u=160645")

my computer is Dell Inspiron N5010.....i3,3GB,320GB HDD (now replaced with two year old bought 160gb Toshiba HD because this one got crashed...)....clock speed is 2.39 GHz....!!!!!!!

---

### Post by mikewhatever on 2012-02-17
OK, so this is a relatively new computer. Why would you need to reinstall drivers?

---

### Post by satyamM on 2012-02-21
[_@mikewhatever_]("http://ubuntuforums.org/member.php?u=160645") 

Actually I have removed Windows-7 and installed Ubuntu 10.04 in my laptop...thats why I am asking if Dell drivers need to be re-installed or not..!!!

Plus I am also having issues with Movie player.....Songs get played easily....but movies do not get played.....asks for some  "g-streamer0.10 bad"  package...tried to install it many times but error comes as "Package not found....and blah blah.."......

Can you help me in this..?....I am working on a proxy server which asks for proxy to get access for Internet.

---

### Post by mikewhatever on 2012-02-21
Dell, most likely, only provides drivers for Windows, and reinstalling those on Ubuntu wouldn't make sense, nor would it work. That said, if you have something for Ubuntu, it might be worth trying. 
Another thing to try is installing a newer kernel, which should provide better driver support for newer hardware.
For example, you could try installing **linux-image-generic-lts-backport-oneiric**, which has been backported to 10.04 from 11.10.

Gstreamer packages provide codecs to play lots of video and audio formats. Something must be wrong with your internet connection, if it fails to install. The proxy could be a problem, check out the howto for configuring APT below.

[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

[http://ubuntuforums.org/showthread.php?t=83401](http://ubuntuforums.org/showthread.php?t=83401)

---

### Post by wildmanne39 on 2012-02-21
Hi, these issues need to be dealt with one at a time, I will help with wireless.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod 
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by satyamM on 2012-02-22
[@wildmann]("http://ubuntuforums.org/member.php?u=508533")

These are the results I got:


```

1. cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux ubuntu 2.6.32-39-generic #86-Ubuntu SMP Mon Feb 13 21:47:32 UTC 2012 i686 GNU/Linux

2. lspci -nnk | grep -iA2 net

12:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
    Kernel driver in use: wl
    Kernel modules: wl
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  02)
    Kernel driver in use: r8169
    Kernel modules: r8169



3.  iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:244
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0



4.  rfkill list all

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



5.  lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_idt      52074  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74297  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  289683  3 
lib80211_crypt_tkip     7596  0 
dell_wmi                1793  0 
drm_kms_helper         29329  1 i915
drm                   163779  4 i915,drm_kms_helper
psmouse                63677  0 
uvcvideo               57438  0 
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54244  17  snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             6888  0 
dcdbas                  5422  1 dell_laptop
wl                   2637448  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
serio_raw               3978  0 
intel_agp              24375  2 i915
soundcore               6620  1 snd
i2c_algo_bit            5028  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32680  2 
r8169                  34140  0 
mii                     4381  1 r8169

```

---

### Post by wildmanne39 on 2012-02-22
Hi, please do:
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
watch for errors, then Under the desktop menu System > Administration > Hardware/Additional Drivers, the STA drivers need to be activated for use. 
Reboot
Thanks

---

### Post by satyamM on 2012-02-23
@[wildmanne39]("http://ubuntuforums.org/member.php?u=508533")

Thanks for replying. Here is the code which it showed on doing** sudo apt-get update**

```
   
satyam@ubuntu:~$ sudo apt-get update
[sudo] password for satyam: 
Get:1 http://ppa.launchpad.net lucid Release.gpg [316B]             
Hit http://in.archive.ubuntu.com lucid Release.gpg                            
Hit http://archive.canonical.com lucid Release.gpg
Ign http://ppa.launchpad.net/c-korn/ppa/ubuntu/ lucid/main Translation-en_IN
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_IN   
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN
Get:2 http://ppa.launchpad.net lucid Release.gpg [316B]                    
Hit http://archive.canonical.com lucid Release                                
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN
Ign http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/ lucid/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN
Get:3 http://archive.canonical.com lucid/partner Packages [15.4kB]
Get:4 http://ppa.launchpad.net lucid Release [13.9kB]                          
Ign http://ppa.launchpad.net lucid Release                                     
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN    
Hit http://in.archive.ubuntu.com lucid-security Release.gpg                
Get:5 http://ppa.launchpad.net lucid Release [13.9kB]
Ign http://ppa.launchpad.net lucid Release                                     
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IN 
Hit http://ppa.launchpad.net lucid/main Packages                           
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IN
Hit http://ppa.launchpad.net lucid/main Sources      
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IN
Hit http://ppa.launchpad.net lucid/main Packages     
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com lucid-updates Release.gpg
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IN
Get:6 http://in.archive.ubuntu.com lucid-proposed Release.gpg [198B]
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com lucid-backports Release.gpg                   
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com lucid Release                                 
Hit http://in.archive.ubuntu.com lucid-security Release                        
Hit http://in.archive.ubuntu.com lucid-updates Release                         
Get:7 http://in.archive.ubuntu.com lucid-proposed Release [58.3kB]             
Hit http://in.archive.ubuntu.com lucid-backports Release                       
Hit http://in.archive.ubuntu.com lucid/main Packages                           
Hit http://in.archive.ubuntu.com lucid/restricted Packages                     
Hit http://in.archive.ubuntu.com lucid/universe Packages                       
Hit http://in.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://in.archive.ubuntu.com lucid/main Sources                            
Hit http://in.archive.ubuntu.com lucid/restricted Sources                      
Hit http://in.archive.ubuntu.com lucid/universe Sources                        
Hit http://in.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://in.archive.ubuntu.com lucid-security/main Packages                  
Hit http://in.archive.ubuntu.com lucid-security/restricted Packages            
Hit http://in.archive.ubuntu.com lucid-security/universe Packages              
Hit http://in.archive.ubuntu.com lucid-security/multiverse Packages            
Hit http://in.archive.ubuntu.com lucid-security/main Sources                   
Hit http://in.archive.ubuntu.com lucid-security/restricted Sources             
Hit http://in.archive.ubuntu.com lucid-security/universe Sources               
Hit http://in.archive.ubuntu.com lucid-security/multiverse Sources             
Hit http://in.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://in.archive.ubuntu.com lucid-updates/restricted Packages             
Hit http://in.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://in.archive.ubuntu.com lucid-updates/multiverse Packages             
Hit http://in.archive.ubuntu.com lucid-updates/main Sources                    
Hit http://in.archive.ubuntu.com lucid-updates/restricted Sources              
Hit http://in.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://in.archive.ubuntu.com lucid-updates/multiverse Sources
Get:8 http://in.archive.ubuntu.com lucid-proposed/main Packages [139kB]
Get:9 http://in.archive.ubuntu.com lucid-proposed/restricted Packages [14B]
Get:10 http://in.archive.ubuntu.com lucid-proposed/universe Packages [20.0kB]
Get:11 http://in.archive.ubuntu.com lucid-proposed/multiverse Packages [1,333B]
Get:12 http://in.archive.ubuntu.com lucid-proposed/main Sources [53.4kB]       
Get:13 http://in.archive.ubuntu.com lucid-proposed/restricted Sources [14B]    
Get:14 http://in.archive.ubuntu.com lucid-proposed/universe Sources [7,229B]   
Get:15 http://in.archive.ubuntu.com lucid-proposed/multiverse Sources [912B]   
Hit http://in.archive.ubuntu.com lucid-backports/main Packages                 
Hit http://in.archive.ubuntu.com lucid-backports/restricted Packages           
Hit http://in.archive.ubuntu.com lucid-backports/universe Packages             
Hit http://in.archive.ubuntu.com lucid-backports/multiverse Packages           
Hit http://in.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://in.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://in.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://in.archive.ubuntu.com lucid-backports/multiverse Sources            
Fetched 281kB in 29s (9,565B/s)                                                
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't 
be verified because the public key is not available: NO_PUBKEY 71346C8340130828
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't
 be verified because the public key is not available: NO_PUBKEY EC7B7B7D4439DBD6
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Last few lines here show some error..Dont know what they are....Can you please help me in that..??



On doing**   sudo apt-get install bcmwl-kernel source **I get following

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by møllerik on 2012-02-23
I've tryed to follow the description and all seemed to be ok. But after rebooting nothing is changed on my labtop
Dell Vostro 1720 - The terminal looks like this:
erik@erik-Vostro-1720:~$ cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.10 
DISTRIB_CODENAME=oneiric 
DISTRIB_DESCRIPTION="Ubuntu 11.10" 
Linux erik-Vostro-1720 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux 
erik@erik-Vostro-1720:~$ lspci -nnk | grep -iA2 net 
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03) 
	Subsystem: Dell Device [1028:02c0] 
	Kernel driver in use: r8169 
-- 
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c] 
	Kernel modules: wl, ssb 
erik@erik-Vostro-1720:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

erik@erik-Vostro-1720:~$ rfkill list all 
0: dell-wifi: Wireless LAN 
	Soft blocked: yes 
	Hard blocked: yes 
erik@erik-Vostro-1720:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_hda_codec_idt      60049  1 
binfmt_misc            17292  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              28932  2 snd_pcm,snd_seq 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
psmouse                73673  0 
i915                  509519  2 
serio_raw              12990  0 
drm_kms_helper         32889  1 i915 
drm                   192194  3 i915,drm_kms_helper 
soundcore              12600  1 snd 
lib80211               14570  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm 
i2c_algo_bit           13199  1 i915 
video                  18908  1 i915 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp 
usb_storage            44173  2 
uas                    17699  0 
ahci                   21634  2 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci 
crc_itu_t              12627  1 firewire_core 
libahci                25727  1 ahci 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci 
r8169                  43104  0 
erik@erik-Vostro-1720:~$ sudo apt-get update 
[sudo] password for erik: 
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick InRelease 
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                           
Ignorerer [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                          
Ignorerer [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                  
Ignorerer [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                 
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main TranslationIndex 
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted TranslationIndex 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                           
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main Translation-da_DK 
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main Translation-da 
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main Translation-en_US 
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main Translation-en 
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted Translation-da_DK 
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted Translation-da 
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted Translation-en_US 
Ignorerer cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted Translation-en 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                           
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                           
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                       
Havde [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                             
Ignorerer [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed InRelease                 
Ignorerer [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                            
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                             
Havde [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                         
Havde [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                 
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                    
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg                   
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed Release.gpg                   
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                             
Havde [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                             
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg                  
Havde [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                            
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                             
Havde [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages               
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                        
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release                       
Havde [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                      
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex               
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                 
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex        
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed Release                       
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                 
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release                      
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                           
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources                     
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources                       
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources                     
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages                     
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                 
Ignorerer [http://dl.google.com](http://dl.google.com) testing InRelease                               
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages               
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages                 
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages               
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                  
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex            
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex            
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex              
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources                   
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources             
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                            
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                      
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex               
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources               
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources             
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages             
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages       
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages         
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages       
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                            
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                      
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex               
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex          
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex    
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex    
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex      
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources                  
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources            
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources              
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources            
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages            
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                            
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                      
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex               
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages      
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages        
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages      
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex         
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex   
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex   
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex     
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/restricted i386 Packages      
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/main i386 Packages            
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/multiverse i386 Packages      
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/universe i386 Packages        
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/main TranslationIndex         
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/multiverse TranslationIndex   
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/restricted TranslationIndex   
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/universe TranslationIndex     
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted i386 Packages     
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main i386 Packages           
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse i386 Packages     
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe i386 Packages       
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main TranslationIndex        
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex  
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted TranslationIndex  
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe TranslationIndex    
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-da                    
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en                    
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-da              
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en              
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-da              
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en              
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-da                
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en                
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en            
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en      
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en      
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en        
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en           
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en     
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en     
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en       
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/main Translation-en           
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/multiverse Translation-en     
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/restricted Translation-en     
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-proposed/universe Translation-en       
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Translation-en          
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Translation-en    
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-da_DK              
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-da_DK       
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Translation-en    
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-da                 
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US              
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-da          
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US       
Havde [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Translation-en      
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                 
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en          
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-da_DK 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-da 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-da_DK 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-da 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-da_DK 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-da 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en 
Henter:1 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189 B] 
Henter:2 [http://dl.google.com](http://dl.google.com) testing Release [2,513 B] 
Henter:3 [http://dl.google.com](http://dl.google.com) testing/non-free i386 Packages [793 B] 
Ignorerer [http://dl.google.com](http://dl.google.com) testing/non-free TranslationIndex               
Ignorerer [http://dl.google.com](http://dl.google.com) testing/non-free Translation-da_DK 
Ignorerer [http://dl.google.com](http://dl.google.com) testing/non-free Translation-da 
Ignorerer [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_US 
Ignorerer [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en 
Hentede 3,495 B på 56s (62 B/s) 
Indlæser pakkelisterne... Færdig 
erik@erik-Vostro-1720:~$ sudo apt-get install bcmwl-kernel-source 
Indlæser pakkelisterne... Færdig 
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig 
bcmwl-kernel-source er i forvejen den nyeste version. 
0 opgraderes, 0 nyinstalleres, 0 afinstalleres og 2 opgraderes ikke. 
erik@erik-Vostro-1720:~$ 
Wireless light is still not and wicd Network Manager still says "no wireless network."
I've tried everything to get wireless connection again, but since it went down a month ago, nothing helped. Could it be a mistake by wireless switch or is it a general defect in Ubuntu, it seems that a large number of Ubuntu users are having problems with wireless connection. Among other things, I had to uninstall the built-in network driver and put wicd instead.
Hoping for a solution, it seems that everyone else can get help, so maybe there is hope out there.
E.rik

---

### Post by wildmanne39 on 2012-02-23
Hi satyamM, please try this to fix the update errors:
```
sudo apt-get clean
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40130828 4439DBD6
sudo apt-get update
```
if you get no erros then run the commands in my previous post to get wireless working.
Thanks

---

### Post by wildmanne39 on 2012-02-23
Hi møllerik, first you need to make sure your wireless switch is on, it is showing it is off, then run this command please:
```
echo "blacklist dell_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
then reboot.

If you need more help please start your own thread and you can leave a link to it here but I am about to be very busy out of town for awhile so I am not be able to get back to you.
Thanks

---

### Post by satyamM on 2012-02-24
> **wildmanne39 said:**
> Hi satyamM, please try this to fix the update errors:
```
sudo apt-get clean
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40130828 4439DBD6
sudo apt-get update
```if you get no erros then run the commands in my previous post to get wireless working.
Thanks

[@wildmanne39]("http://ubuntuforums.org/member.php?u=508533")


Here is code what I get when I apply ur said commands..

```

satyam@ubuntu:~$ sudo apt-get clean
satyam@ubuntu:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40130828 4439DBD6
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40130828 4439DBD6
gpg: requesting key 40130828 from hkp server keyserver.ubuntu.com
gpg: requesting key 4439DBD6 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


```

Now what to do..??

---

### Post by wildmanne39 on 2012-02-25
> **satyamM said:**
> [@wildmanne39]("http://ubuntuforums.org/member.php?u=508533")


Here is code what I get when I apply ur said commands..

```

satyam@ubuntu:~$ sudo apt-get clean
satyam@ubuntu:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40130828 4439DBD6
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40130828 4439DBD6
gpg: requesting key 40130828 from hkp server keyserver.ubuntu.com
gpg: requesting key 4439DBD6 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


```

Now what to do..??Hi, I am not sure why that did not work, but it means you are having problems with authentication for security to be able to download packages from those repositories.

After you ran this command:
```
sudo apt-get install bcmwl-kernel source
```
did you go to desktop menu System > Administration > Hardware/Additional Drivers, to activate the driver, and then did you reboot with your wired connection unplugged?.

If so please post the output of:
```
nm-tool
sudo iwlist scan
lsmod | grep wl
``` 
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n75
```
Thanks

---

### Post by satyamM on 2012-02-26
@[wildmanne39]("http://ubuntuforums.org/member.php?u=508533")

Hi...didn't know what happened.....but today when I booted my laptop in wi-fi connection area...it detected the Wi-Fi.....I was just surprised and was remembering you when it started working so smoothly...!!! 

Thanks for your help wildmanne39..!!!... 

I will be posting some more issues in few days as these days I am having my exams..!!..!!

Thanks again..!!  :)

---

### Post by wildmanne39 on 2012-02-26
Hi, I am glad it is working and I am about to be busy for a while myself. 

Remember it is best to start a new thread and have only one issue per thread.

Also always mark your resolved threads as solved.
Thanks

---

