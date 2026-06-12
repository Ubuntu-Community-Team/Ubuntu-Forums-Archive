---
title: "Inspiron 15R 5520 failure to detect wireless device"
date: 2012-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Frosch09 on 2012-07-01
Hallo,

 I have a problem with the wireless device on a Dell  Inspiron 15R 5520 using ubuntu 12.04 (32bit). It seems that the wireless device  is not detected at all by Ubuntu. It is neither listed in the dropdown menue for network settings, nor can I choose it in the menue for system settings, where only cable and proxy are listed.  The wireless works fine under windows 7,  though. I assumed that all hardware should be recognized by Ubuntu since  the computer is listed as certified in Ubuntu's hardware list, although  with a pre-installed Ubuntu: [http://www.ubuntu.com/certification/hardware/201201-10377/](http://www.ubuntu.com/certification/hardware/201201-10377/)

Here are a few results from commands that have been suggested for the problem in an earlier thread ([http://ubuntuforums.org/showthread.php?t=2010710](http://ubuntuforums.org/showthread.php?t=2010710)): 

```
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux fdw2012 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

``````
lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:056a]
    Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
    Subsystem: Dell Device [1028:0016]

``````
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:648d Microdia 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. 

``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


``````
rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

``````
lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52516  1 
joydev                 17393  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2909855  0 
rts5139               279622  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
psmouse                72919  0 
serio_raw              13027  0 
i915                  414655  2 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
mei                    36570  0 
i2c_algo_bit           13199  1 i915
wmi                    18744  1 dell_wmi
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
r8169                  56321  0 

```[FONT=monospace]
Thanks for all suggestions!
[/FONT]

---

### Post by mikewhatever on 2012-07-02
Looks like you have an unsupported device:

Network controller [0280]: Broadcom Corporation Device [14e4:4365]

Perhaps a kernel update will fix it, not really sure.

[https://answers.launchpad.net/ubuntu-certification/+question/200767](https://answers.launchpad.net/ubuntu-certification/+question/200767)

---

### Post by Bucky Ball on 2012-07-02
Can you plug in with a cable, do an update then check in 'Additional Drivers'?

---

### Post by Frosch09 on 2012-07-02
Hi Bucky Ball, 

Thanks for you reply. By update you mean a kernel update with this command? 

```
sudo apt-get install --reinstall linux-image-$(uname -r) 
```As to now, there is only a proprietory graphics driver listed for "additional drivers"

Thanks!

---

### Post by Bucky Ball on 2012-07-02
No. I mean a simple update. To upgrade packages as well (if available and you should always run the update command first):

```
sudo apt-get update
sudo apt-get upgrade
```Stick with the kernel you have and you know is working for now. You don't want to confuse the issue by installing a kernel which may have other issues and break the system in some other way (or cause a totally different wireless problem). And maybe you could also post back the result of:

```
sudo lshw -C network
```Thanks.

PS: In Software Centre, do you have b43-fwcutter and b43-firmware-installer (that last one could be wrong but do a search for b43 and you'll find it)?

---

### Post by wildmanne39 on 2012-07-02
Hi, I to believe as well at the moment your device is not supported by ubuntu the only option you have is to use ndiswrapper, I have not helped anyone with ndiswrapper before so it is really not my area of expertise but here is a link.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Thanks

---

### Post by Frosch09 on 2012-07-02
Thank you both wildemann39 and Bucky Ball
    
    I tried Bucky's suggestion. And there was no different result in     additional drivers. There are various b43 options in the software     centre. I installed the two you mentioned but there was no effect on     the wireless so far. And none of the listed packages' descriptions     indicated that it is designed for the 4365 device. 
    
    The result from the commad reads as follows as far as the wireless     is concerned: 
    
    ```
sudo lshw -C network
      
      *-network UNGEFORDERT
           Beschreibung: Network controller
           Produkt: Broadcom Corporation
           Hersteller: Broadcom Corporation
           Physische ID: 0
           Bus-Informationen: pci@0000:08:00.0
           Version: 01
           Breite: 64 bits
           Uhr: 33MHz
           Fähigkeiten: pm msi pciexpress bus_master cap_list
           Konfiguration: latency=0
           Ressourcen: memory:c1500000-c1507fff
    
```    @wildeman
    If you are right and the device is currently unsupported, will it be     likely that a proper driver will become available within reasonable     time? I fear that ndiswrapper is not really an option for me. I still wonder, why the machine is certified for Ubuntu 11.10 and does not work with 12.04. 
    
    Thanks for all your help!

---

### Post by wildmanne39 on 2012-07-02
Hi, it is very hard to tell, you can have a look at the link in post 2.

If you know the driver the device used in 11.10 then we might be able to add it.
Thanks

---

### Post by Bucky Ball on 2012-07-02
Yea, do you still have 11.10 installed by any chance? You could run this again:

```
sudo lshw -C network
```

... in 11.10 and that would give you the driver being used and other details. I also wonder why, if it 'just worked' in 11.10, it is not doing the same in 12.04. Can't imagine its drivers would have been taken out. But then, 12.04 is new and there will be glitches. ;)

---

### Post by Frosch09 on 2012-07-03
Thanks for all your answers. Since I bought this computer only last week I don't have 11.10 on it. Can it be possible that Dell changed the device since certification? The one listed here for Inspiron 5520 looks different to me: [http://www.ubuntu.com/certification/hardware/201201-10377/components/](http://www.ubuntu.com/certification/hardware/201201-10377/components/). On the other hand, the description in the link from post 2 clearly states that the same device worked in 11.10. 

It seems however that developers are working on the problem. The Problem with Broadcom [14e4:4365] was dealt with here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/921911](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/921911) and then moved to here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863051) since both devices seem to require the same driver. I guess I'll just have to wait and hope. 

Thanks for  your time and effort!

---

### Post by wildmanne39 on 2012-07-03
Hi, I imagine the driver may be present but the device needs to be added to ubuntu, but we can not attempt to do that without knowing which driver it needs.

---

### Post by Frosch09 on 2012-07-03
Ok, now I see the problem. But should the the device really have been implemented in 11.04 pre-install version, can information about the driver not be dug out somehow and be added to 12.04 fairly easily?

---

### Post by wildmanne39 on 2012-07-03
Hi, asked my friend the expert and he said ndiswrapper is the only way to get your device to work right now and still it might not.
Thanks

---

### Post by samrit on 2012-07-04
> **Frosch09 said:**
> Hallo,

 I have a problem with the wireless device on a Dell  Inspiron 15R 5520 using ubuntu 12.04 (32bit). It seems that the wireless device  is not detected at all by Ubuntu. It is neither listed in the dropdown menue for network settings, nor can I choose it in the menue for system settings, where only cable and proxy are listed.  The wireless works fine under windows 7,  though. I assumed that all hardware should be recognized by Ubuntu since  the computer is listed as certified in Ubuntu's hardware list, although  with a pre-installed Ubuntu: [http://www.ubuntu.com/certification/hardware/201201-10377/](http://www.ubuntu.com/certification/hardware/201201-10377/)

Here are a few results from commands that have been suggested for the problem in an earlier thread ([http://ubuntuforums.org/showthread.php?t=2010710](http://ubuntuforums.org/showthread.php?t=2010710)): 

```
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux fdw2012 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

``````
lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:056a]
    Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
    Subsystem: Dell Device [1028:0016]

``````
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:648d Microdia 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. 

``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


``````
rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

``````
lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52516  1 
joydev                 17393  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2909855  0 
rts5139               279622  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
psmouse                72919  0 
serio_raw              13027  0 
i915                  414655  2 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
mei                    36570  0 
i2c_algo_bit           13199  1 i915
wmi                    18744  1 dell_wmi
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
r8169                  56321  0 

```[FONT=monospace]
Thanks for all suggestions!
[/FONT]
if you found the soln plz do share.. i am stucked with the same situation..

---

### Post by wildmanne39 on 2012-07-04
Hi, please see post 13, that is the only chance of getting your device to work in ubuntu at this time.
Thanks

---

### Post by Frosch09 on 2012-07-04
So far there are no reports that ndiswrapper really functions. Since I don't want to take the risk of smashing my system right now, I am not going to try it. Please see these two links with reports on unsuccessfull installations with ndiswrapper:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863051/comments/69](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863051/comments/69)
[http://forum.ubuntu-fr.org/viewtopic.php?id=966811](http://forum.ubuntu-fr.org/viewtopic.php?id=966811)
... Its hard to tell however whether these attempts have been carried out properly without more information.

---

### Post by wildmanne39 on 2012-07-04
Hi, that is up to you but if you install ndiswrapper and it does not work it will not break your system, we just give you the commands to remove it, but I am not the person to help you with installing ndiswrapper since you are scared of it to begin with and it is not experienced with it.
Thanks

---

### Post by M1773N5 on 2012-07-12
I have this same problem too. I took the easy route though and just bought a Wireless N usb that supported Linux. Patriot, NETIS, and Sabrent make one and eBay has an assortment of them for less than $10. I used the Sabrent and no drivers were required.

---

### Post by 67GTA on 2012-07-16
It is certified ONLY if it came preinstalled with Linux. Dell only uses hardware that is know to work with Linux in their systems that are preinstalled with Linux. The 5520 could have Atheros, Broadcom, or Intel wireless cards. Not all model #'s have the exact same hardware.

---

### Post by thotz on 2012-07-17
> **M1773N5 said:**
> I have this same problem too. I took the easy route though and just bought a Wireless N usb that supported Linux. Patriot, NETIS, and Sabrent make one and eBay has an assortment of them for less than $10. I used the Sabrent and no drivers were required.

Me too :) But I hope there will be a driver soon from Broadcom.

I also wrote them that they should release drivers for their products for Linux.

---

### Post by vipul121 on 2012-07-17
hi
i am having same problem 
i am really new to ubuntu please help me

---

### Post by rogi86 on 2012-07-23
Hi,

I'm too having the same problem on my new Dell Inspiron n5720 17r. I got it with preinstalled Ubuntu 11.10 where everything works ok. After **adding** Mint 13 Maya 64-bit with cinnamon wireless is dead. 
On Ubuntu 11.10 I find that the driver is called **wl0**
I don't know if this would help, but there is a bug report which I'm waiting to resolve: 
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809")

---

### Post by cessnaflyer on 2012-07-23
I have a Dell d400 laptop i am having the same problem getting the onboard wifi card to work as well. I believe it is the broadcom 4306 card. played with it for 3 days, went to my local flea market on sunday since there is usually a guy there with dell recovery disks, was going to just put windows back on it even though i cant stand windows.... couldnt find him so bought another pcmi card and so far it works reasonably well. drops the connection sometimes, but the wifi in my local starbucks is known to act stupid at times so dont know if it is a wifi card issue or the wifi at the starbucks. tend to think it is an issue with the wifi at starbucks since it always reconnects on a restart and drops at different times usually when the wifi indicator goes below 2 bars of signal strength for longer than a few seconds. I have talked to a few people that use ubuntu and other forms of linux and they ALLsay that broadcom devices are a royal pain in the a**

---

### Post by Bucky Ball on 2012-07-23
Well, your colleagues haven't used Linux in awhile. That used to be the case but Broadcom and the majority of their wireless cards, since the advent of the b43 driver, play nice. ;)

Very new hardware of any brand can be problematic, even with co-operative vendors. Seems to be Win, then Mac, then Linux for drivers. ;)

---

### Post by ub2011 on 2012-07-23
I too have a new 15R 5520 that i just installed 11.10 on.   Wireless does not work.  dmesg reports

 iwlagn 0000:02:00.0: request for firmware file 'iwlwifi-2030-5.ucode' failed.

There is a  *2030-6.ucode in /lib/firmware but no  -5   .... sigh

I had hoped since 15R was Ubuntu certified that Ubuntu would work, but I guess a model still has lots of different hardware options, so the certification only applies if you can match the config of the certified model.  ugh
 
I also have a horizontal flicker line at the top of the display  (3 or 4 pixles in height)

I'm running updated 11.10   3.0.0-23-generic-pae 
hardwired ethernet works

---

### Post by rogi86 on 2012-07-30
> **ub2011 said:**
> I too have a new 15R 5520 that i just installed 11.10 on.   Wireless does not work.  dmesg reports

 iwlagn 0000:02:00.0: request for firmware file 'iwlwifi-2030-5.ucode' failed.

There is a  *2030-6.ucode in /lib/firmware but no  -5   .... sigh

I had hoped since 15R was Ubuntu certified that Ubuntu would work, but I guess a model still has lots of different hardware options, so the certification only applies if you can match the config of the certified model.  ugh
 
I also have a horizontal flicker line at the top of the display  (3 or 4 pixles in height)

I'm running updated 11.10   3.0.0-23-generic-pae 
hardwired ethernet works
I think iwlwifi is for intel wireless cards! If you have broadcom wireless then you'll be needing bcmwl driver (bcmwl-kernel-source)

---

### Post by ub2011 on 2012-08-06
> **ub2011 said:**
> I too have a new 15R 5520 that i just installed 11.10 on.   Wireless does not work.  dmesg reports

 iwlagn 0000:02:00.0: request for firmware file 'iwlwifi-2030-5.ucode' failed.

There is a  *2030-6.ucode in /lib/firmware but no  -5   .... sigh

I had hoped since 15R was Ubuntu certified that Ubuntu would work, but I guess a model still has lots of different hardware options, so the certification only applies if you can match the config of the certified model.  ugh
 
I also have a horizontal flicker line at the top of the display  (3 or 4 pixles in height)

I'm running updated 11.10   3.0.0-23-generic-pae 
hardwired ethernet works


installing 12.04 solved my problem

---

### Post by Vladiator on 2012-08-14
Ndiswraper doesn't help or I installed not right driver (Network_Broadcom_W7_A01_Setup-WTD28_ZPE.exe).
Some information:
```
:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl6 : driver installed
	device (14E4:4365) present

:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:056a]
	Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
	Subsystem: Dell Device [1028:0016]
```

Ubuntu 12.04
---'
Also I've found this: [http://askubuntu.com/a/175115](http://askubuntu.com/a/175115) (Broadcom Corporation Device [14e4:4365] too). I've tried to install it - all is OK, this driver is shown in 'Additional drivers' as currently in use... but it doesn't help too! Why? Maybe laptop model doesn't matter so I can't understand why.

---

### Post by Bucky Ball on 2012-08-14
> **Vladiator said:**
> Ndiswraper doesn't help or I installed not right driver (Network_Broadcom_W7_A01_Setup-WTD28_ZPE.exe).
Some information:
```
:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl6 : driver installed
    device (14E4:4365) present

:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:056a]
    Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
    Subsystem: Dell Device [1028:0016]
```Ubuntu 12.04
---'
Also I've found this: [http://askubuntu.com/a/175115](http://askubuntu.com/a/175115) (Broadcom Corporation Device [14e4:4365] too). I've tried to install it - all is OK, this driver is shown in 'Additional drivers' as currently in use... but it doesn't help too! Why? Maybe laptop model doesn't matter so I can't understand why.

Please create another thread with a descriptive title and as much info as you can provide about your issue. Gets confusing when you hijack another thread and helpers are attempting to fix two issues from two separate posters. (And confusing for the original poster.) ;)

Also, this is a pretty old thread now, and you will have more chance of getting help, and more specific help, with a new thread.

---

### Post by Vladiator on 2012-08-15
> **Bucky Ball said:**
> Please create another thread with a descriptive title and as much info as you can provide about your issue. Gets confusing when you hijack another thread and helpers are attempting to fix two issues from two separate posters. (And confusing for the original poster.) ;)

Also, this is a pretty old thread now, and you will have more chance of getting help, and more specific help, with a new thread.

My problem is the same - do I realy need to create new thread?

---

### Post by Bucky Ball on 2012-08-15
Your problem involves ndiswrapper and is therefore not the same in any way I can see. As mentioned, the thread is old and reasonably dead so don't like your chances of getting help (as your issue doesn't match the thread title and is 30 posts deep).

But I'll leave it up to you. Good luck with it. ;)

PS: Have you plugged in a cable, updated, and checked additional drivers? Ndiswrapper is nowadays a last resort and largely superseded.

---

### Post by Frosch09 on 2012-08-16
Hi, 

I just found a reported solution to the wireless problem. I could not test it however, because I am working on a 32 bit system right now. 

Please see post #18 in the following link: [https://answers.launchpad.net/ubuntu-certification/+question/200767](https://answers.launchpad.net/ubuntu-certification/+question/200767)

Maybe someone working on 12.04 64 bit might like to test ist.

---

### Post by Slvtmong00se on 2012-08-19
I had the same problem. Luckily, It's now been finally fixed. 

The .deb package for the drivers has been made available here:

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

Please make sure to undo any changes you have made to your drivers- i.e uninstall ndiswrapper, undo any blacklisting, etc, .... I.e return to a clean-install type state and then run the .deb file appropriate to your system and reboot.

Try it out and let us know. This solution worked for my Inspiron 5520

---

### Post by Vladiator on 2012-08-20
**Slvtmong00se**, It doesn't work for me. I removed all ndiswrapper's folders and files and cleaned /etc/modprobe.d/blacklist... I don't know what drivers I installed more (except ATI/AMD graphics driver).

---

### Post by Saurabh2816 on 2012-08-20
Hey I have the same laptop and I'm facing the same problem.
Do tell me if you have solved it now.

---

### Post by wildmanne39 on 2012-08-20
Hi Saurabh2816, please do not post your email address for your own safety.

---

### Post by xxsmarty on 2012-08-21
I also have the same problem it shows that the braodcom driver is in use but it didn't help.

---

### Post by grc01 on 2012-09-07
If you have a wired connection, go to the tutorial, there is a solution for that problem. Search the tutorial with the word Broadcom.
Good luck

---

### Post by jasmineaura on 2012-09-10
> **Slvtmong00se said:**
> I had the same problem. Luckily, It's now been finally fixed. 

The .deb package for the drivers has been made available here:

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

Please make sure to undo any changes you have made to your drivers- i.e uninstall ndiswrapper, undo any blacklisting, etc, .... I.e return to a clean-install type state and then run the .deb file appropriate to your system and reboot.

Try it out and let us know. This solution worked for my Inspiron 5520

Confirmed, also on Dell Inspiron 15R 5520. Installed like a charm on LMDE (Linux Mint Debian Edition) x64 release 201204 w/ Update Pack 3.

I should add, there were more custom deb packages installed by Dell on the 15R 5520, because I looked in "Additional drivers" on the Dell-installed Ubuntu before formatting and installing LMDE.

There were at least four driver-related proprietary packages in Dell's factory installed Ubuntu:
1. Broadcom 802.11 Linux STA Wireless driver source (the one you already linked to)
2. Broadcom BCM434142 Bluetooth Firmware Install
3. Fix Bluetooth not working after resume
4. dell-laptop-oneiric driver in DKMS format

[Someone (**legalnycyklista**) on archlinux forum]("https://bbs.archlinux.org/viewtopic.php?pid=1140595#p1140595") was nice enough to upload [all the custom debs they found on the Dell-installed Ubuntu]("http://wielki.tk/vostro/")

You don't need all of them, obviously some don't even apply here, like the alps-touchpad-* , bt-dw1703-* , ethernet-alx-* etc, because the aforementioned hardware only applies to the vostro, not the Inspiron 15R/5520 (unless yours came with DellWireless bluetooth instead of broadcom)

Besides the wifi driver, you really only need:
1. Two packages for bluetooth, and bluetooth proper operation after resume from suspend
[http://wielki.tk/vostro/debs/bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb](http://wielki.tk/vostro/debs/bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb)
[http://wielki.tk/vostro/debs/bt-reload-module-after-resume-oneiric_0.1_all.deb](http://wielki.tk/vostro/debs/bt-reload-module-after-resume-oneiric_0.1_all.deb)
After installing these two, and if you want to test if your bluetooth works without having to reboot, just: `modprobe btusb`

2. The customized dell-laptop kernel module package
[http://wielki.tk/vostro/debs/dell-laptop-oneiric-dkms_1.7_all.deb](http://wielki.tk/vostro/debs/dell-laptop-oneiric-dkms_1.7_all.deb)
**Someone should really look into this to see what dell have changed and why, since this is already included in 3.x LINUX KERNEL)**

> **Vladiator said:**
> **Slvtmong00se**, It doesn't work for me. I removed all ndiswrapper's folders and files and cleaned /etc/modprobe.d/blacklist... I don't know what drivers I installed more (except ATI/AMD graphics driver).

You obviously need to `modprobe wl` after installing the deb package, as DKMS wouldn't automagically load it once installed. Still, it should work if you had rebooted (with the module still there).

So make sure the module is loaded: `lsmod | grep wl`

---

### Post by jasmineaura on 2012-09-10
After installing liquorix kernel (**3.4**.0-10.dmz.1-liquorix-amd64), DKMS failed to compile the bcm43142 module driver (wl), with error in the dkms build log about **missing asm/system.h**

**_Workaround_**

> $ sudo nano /usr/src/wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400/src/wl/sys/wl_linux.c
replace line 50:
```
#include <asm/system.h>
```with:
```
#if LINUX_VERSION_CODE < KERNEL_VERSION(3, 4, 0)
#include <asm/system.h>
#endif

```Rebuild/install:
> $ sudo dkms install wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400
and finally `modprobe wl`. Enjoy your new 3.4 kernel w/ working wifi :)

_**UPDATE 13-Sep**_ 

I have updated the bcm43142 driver package, with the following changes:
1. One-line change of the call *ndo_set_multicast_list *to *ndo_set_rx_mode *as described [here]("https://bbs.archlinux.org/viewtopic.php?pid=1141276#p1141276") , so that it compiles on Kernels 3.2.x. This seems more proper than [commenting out the line that uses the said call as others have done]("http://wielki.tk/vostro/")!
2. Incorporated my changes outlined above so that it compiles on kernels 3.4.x  (Might need a few more changes to compile on 3.5.x?)
3. Updated md5sum of the modified wl_linux.c file (per 1 & 2 above)
4. Removed "oneiric" (which is reference to Ubuntu 11.10) from package name, and all directory & path-names everywhere in the package contents, as it is no longer ubuntu/oneiric -specific.

Get the updated deb package here: [http://jas.gemnetworks.com/debian/wireless-bcm43142-dkms-6.20.55.19_amd64.deb](http://jas.gemnetworks.com/debian/wireless-bcm43142-dkms-6.20.55.19_amd64.deb)

---

### Post by dogbiscui on 2012-09-15
I am a complete beginner when it comes to this, but this is what I tried:
1. I copied the .deb files (all of them) to the /home/user/ directory
2. I tried installing them with
```
sudo dpkg -i pkg.deb
```3. This worked for the two Bluetooth ones, but the "wireless-bcm43142-dkms-6.20.55.19_amd64.deb" and the "wlan_amd64.deb" packages failed to install, giving the following output:
```
user@ubuntu:~$ sudo dpkg -i wireless-bcm43142-dkms-6.20.55.19_amd64.deb
[sudo] password for user: 
Selecting previously unselected package wireless-bcm43142-dkms.
(Reading database ... 137798 files and directories currently installed.)
Unpacking wireless-bcm43142-dkms (from wireless-bcm43142-dkms-6.20.55.19_amd64.deb) ...
dpkg: dependency problems prevent configuration of wireless-bcm43142-dkms:
 wireless-bcm43142-dkms depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing wireless-bcm43142-dkms (--install):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
Warning: No support for locale: en_GB.utf8
Errors were encountered while processing:
 wireless-bcm43142-dkms
```I am running a fresh install of 64-bit en-GB Ubuntu 12.04 on a Dell Inspiron 5420 (the 14" sister of the 5520) using the Wubi installer. I have no access to non-wireless internet.

Edit: System specs
Intel Core i5-2500k @ 2.5 GHz
4 GB RAM
nVidia GeForce GT630M
488 GB Seagate ST9500325AS (SATA) HDD (Ubuntu installed to an otherwise empty 100 GB partition)

---

### Post by jawadjee on 2012-09-24
Hi,

I have tested this on Fedora 17 Kernel 3.5.4. The driver is working. 

There is a small problem. This driver does not support Wireless N.

Did I miss something?

---

### Post by jawadjee on 2012-09-24
Hi dogbiscui,

First run The following command

> 
sudo apt-get install dkms


Then try again.

---

### Post by dogbiscui on 2012-09-25
Hi jawadjee,

I tried the command you posted to no avail. I then downloaded the dkms package for Dell from [http://linux.dell.com/dkms/permalink/](http://linux.dell.com/dkms/permalink/) and installed the .deb file, then installed both the wireless .deb files. I restarted, and lo! my laptop started picking up wi-fi signals.

Thanks a million.

---

### Post by jasmineaura on 2012-09-26
If anyone manages to get it working (actually associating to an AP) on linux >= 3.6-rc7 please follow-up on this:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809)

---

### Post by jasmineaura on 2012-10-19
Reposting updated link, as I'm getting emails about it. it's also
mentioned at the bottom of the homepage [jas.gemnetworks.com]("http://jas.gemnetworks.com") :)
[http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142-dkms_6.20.55.19_amd64.deb]("http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142-dkms/wireless-bcm43142-dkms_6.20.55.19%7Ebdcom0602.0400.1000.0400-0somerville1_amd64.deb")

P.S. It works just fine with 3.5.x, but for 3.6.x, you need to spam broadcom for support,
[http://marc.info/?l=linux-wireless&m=134909572204130&w=2](http://marc.info/?l=linux-wireless&m=134909572204130&w=2)

.. especially since they haven't updated their linux drivers page in over a year, and this (6.x) driver isn't even listed on their site: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Better yet, spam them to open source their drivers, or at least release specs for their PHY's so people can start developing opensource drivers for these cards, because broadcom fails to maintain their own linux drivers
[EMAIL="linux-wlan-client-support-list@broadcom.com"]linux-wlan-client-support-list@broadcom.com[/EMAIL].

> **jasmineaura said:**
> After installing liquorix kernel (**3.4**.0-10.dmz.1-liquorix-amd64), DKMS failed to compile the bcm43142 module driver (wl), with error in the dkms build log about **missing asm/system.h**

**_Workaround_**

replace line 50:
```
#include <asm/system.h>
```with:
```
#if LINUX_VERSION_CODE < KERNEL_VERSION(3, 4, 0)
#include <asm/system.h>
#endif

```Rebuild/install:
and finally `modprobe wl`. Enjoy your new 3.4 kernel w/ working wifi :)

_**UPDATE 13-Sep**_ 

I have updated the bcm43142 driver package, with the following changes:
1. One-line change of the call *ndo_set_multicast_list *to *ndo_set_rx_mode *as described [here]("https://bbs.archlinux.org/viewtopic.php?pid=1141276#p1141276") , so that it compiles on Kernels 3.2.x. This seems more proper than [commenting out the line that uses the said call as others have done]("http://wielki.tk/vostro/")!
2. Incorporated my changes outlined above so that it compiles on kernels 3.4.x  (Might need a few more changes to compile on 3.5.x?)
3. Updated md5sum of the modified wl_linux.c file (per 1 & 2 above)
4. Removed "oneiric" (which is reference to Ubuntu 11.10) from package name, and all directory & path-names everywhere in the package contents, as it is no longer ubuntu/oneiric -specific.

Get the updated deb package here: [http://jas.gemnetworks.com/debian/wireless-bcm43142-dkms-6.20.55.19_amd64.deb](http://jas.gemnetworks.com/debian/wireless-bcm43142-dkms-6.20.55.19_amd64.deb)

---

### Post by befana on 2012-10-24
> **Frosch09 said:**
> Hi, 

I just found a reported solution to the wireless problem. I could not test it however, because I am working on a 32 bit system right now. 

Please see post #18 in the following link: [https://answers.launchpad.net/ubuntu-certification/+question/200767](https://answers.launchpad.net/ubuntu-certification/+question/200767)

Maybe someone working on 12.04 64 bit might like to test ist.

It works for me - on Dell Inspiron 5520 with Ubuntu 12.04 64 bit. Thanks for the link!

---

### Post by uluroki on 2012-10-26
Hi all, 
I got the wireless working on Xubuntu 12.10 64-bit with 3.5 kernel.

```

uluroki@nayan5520:~$ uname -r
3.5.0-17-generic

```

```

uluroki@nayan5520:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:056a]
    Kernel driver in use: r8169
--
08:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
    Kernel driver in use: wl

```

First I started with solutions in this tread, but it did not help. 

Then I tried [https://answers.launchpad.net/ubuntu-certification/+question/200767](https://answers.launchpad.net/ubuntu-certification/+question/200767)
but there was some sort of a problem with the kernel, as mentioned in
[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

Finally, [http://askubuntu.com/questions/178352/broadcom-4365-wireless-driver-with-3-4-3-5-kernel/](http://askubuntu.com/questions/178352/broadcom-4365-wireless-driver-with-3-4-3-5-kernel/) worked for me. 

Oh, and don't forget to
```

uluroki@nayan5520:~$ sudo modprobe wl

```

---

