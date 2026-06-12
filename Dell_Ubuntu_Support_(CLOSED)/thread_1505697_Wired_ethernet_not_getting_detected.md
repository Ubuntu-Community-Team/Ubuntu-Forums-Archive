---
title: "Wired ethernet not getting detected"
date: 2010-06-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rbisawa on 2010-06-09
Hello Everyone,

I have installed Ubuntu 10.04-64 bit ( Lucid Lynx ) on my Dell Inspiron N4010 laptop.

**I'm unable to detect my wired ethernet.**
I tried searching for it extensively but I think I was unable to make sense out of the posts already present.

I know this has something to do with the need to install the correct drivers.

Also posting the output of few popular commands which I'm sure I would be asked to execute.

[B]==========================================
sudo ifconfig -a[/B]
_Output :_
lo      Link encap:Local Loopback
         inet addr:127.0.0.1 Mask:255.0.0.0
         UP LOOPBACK RUNNING MTU:16436 Metric:1
         ...........
         ...........

No other interfaces were detected apart from loopback.         
================================================
**lspci**
_Output :_
...........
...........
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Ethernet controller: Atheros Communication AR8152 v1.1 Fast Ethernet (rev c1)
=================================================
**ifup eth0**
_Output :_
Ignoring unknown interface eth0=eth0
=================================================
Please let me know if you need any more information.

Looking forward to some pointers on this issue.

Cheers!

---

### Post by pytheas22 on 2010-06-09
Please also post the output of these commands:
```

cat /etc/network/interfaces
cat /etc/NetworkManager/nm-system-settings.conf
dmesg | grep -e eth0 -e bcm
ifconfig -a
```

They should help straighten things out.

---

### Post by rbisawa on 2010-06-10
@[pytheas22]("http://ubuntuforums.org/member.php?u=358340")

Sorry was at office since morning.

Here you are with all the outputs.

[B]===============================================
cat /etc/network/interfaces[/B]
_Output :_
auto lo
iface lo inet loopback
=====================================================
**cat /etc/NetworkManager/nm-system-settings.conf**
_Output :_
# ...some comments...
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
=====================================================
**dmesg | grep -e eth0 -e bcm**
_Output :_
<No output>
=====================================================
**ifconfig -a**
_Output :_
Same as given in my 1st post...only loopback interface is being displayed.
=====================================================

Do let me know if you want any more info.

Anticipating a quick reply. Thanks.

Cheers!

---

### Post by pytheas22 on 2010-06-10
hmmm, it seems like the system is not trying to initialize the hardware at all, even though it doesn't recognize that it's present, according to the "lspci" output from your first post.

I'll have to ask for a little more information so we can figure out if any driver is even trying to claim the ethernet device.  Could you please post the output of:
```

lshw -C Network
lspci -nn
```

---

### Post by rbisawa on 2010-06-11
[B]Here you are with the outputs :
[/B]
=======================================================
[B]lshw -C Network
[/B]_Output :_
WARNING: you should run this program as super-user.
*-network UNCLAIMED 
description: Network controller
product: Broadcom Corporation
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: memory:f0500000-f0503fff
*-network UNCLAIMED
description: Ethernet controller
product: AR8152 v1.1 Fast Ethernet
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:04:00.0
version: c1
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: memory:f0400000-f043ffff ioport:2000(size=128)
======================================================
**lspci -nn**
_Output :_
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03] Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
=======================================================

Hope the above outputs can give us some lead.

Cheers!

---

### Post by pytheas22 on 2010-06-11
Your ethernet hardware seems to be quite new and doesn't have a driver built into Ubuntu as of yet.  However, there's a driver included in the compat-wireless stack that you can use (I have no idea why they included an ethernet driver in compat-wireless, but according to [these emails]("http://omgili.com/mailinglist/kernel-team/lists/ubuntu/com/43e72e891002020915x572a11fcg57f0b9caf7ed08eamailgmailcom.html"), someone did).

To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking).  Save it to your desktop. Then run these commands (the first two commands require that you either have an Internet connection, or have your [Ubuntu installation CD enabled as a software repository]("https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD")):
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```

Then reboot.  Hopefully your ethernet will work automatically after reboot; if not, run:
```

sudo modprobe atl1c
```

to insert the driver.  Let me know how it goes.

We can probably make your wireless work too, if you're interested.

---

### Post by rbisawa on 2010-06-12
[B]Yo !!

Wired ethernet is now up n running !!
[/B]
I performed all the steps suggested in the previous post and rebooted.

**_@pytheas22 :_ Thanks a lot dude. Keep up the good work.**

Can you also post the commands to enable wireless networking and bluetooth if possible.
Although I don't have a wireless router to test the connection still it would be nice
if I could get it up n ready to use anytime.


Cheers n keep Ubunting !!

---

### Post by pytheas22 on 2010-06-12
Glad to hear the ethernet is sorted out :)  The only caveat is that whenever you get a new kernel from Ubuntu Updates (usually updated kernel packages are pushed out once a month or so), you will have to recompile the ethernet driver by repeating the steps in my previous post in order to make the driver work with the new kernel.  Hopefully the next release of Ubuntu (in October) will include support for your card out-of-the-box and this will no longer be an issue.

As for the wireless, that shouldn't be too hard to get up and running.  Your device needs a closed-source driver that Ubuntu doesn't ship by default, but you can install it easily by running:
```

sudo apt-get install bcmwl-kernel-source
echo wl | sudo tee -a /etc/modules
```

After that, you should be able to connect to wireless networks (when there's one around to connect to) using the NetworkManager applet in the upper-right corner of your screen.  The wireless driver should be  updated automatically whenever the kernel is, so in this case you don't have to worry about recompiling manually.

I've never owned a bluetooth device so I don't have experience dealing with one in Linux, unfortunately.  I assume, though, that you've gone to System>Preferences>Bluetooth and was told that no bluetooth devices were present?  If that's the case, I'll do my best to set you on the right path if you could plug the bluetooth device in and then post the output of:
```

lsusb
```

---

### Post by rbisawa on 2010-06-13
Yes, as soon as I got my ethernet working I went for an upgrade using the update manager. In the process it also upgraded the kernel which resulted in losing the driver again. But I reinstalled the driver using the steps mentioned previously and it was up again.

Regarding the wireless network, I read in one of the posts that it could be installed using the Hardware Manager which was a cake walk and I guess the above commands given by you would do the same.

Also bluetooth is now enabled after switching on the Bluetooth adapter in Windows.

Will get back if need any more help in this regard.

Cheers!

---

### Post by banskt on 2010-06-18
I am also having the same problems.

I will try this solution today and post it here.

---

### Post by gibu_ on 2010-07-02
I too have the same problem as the original poster. i.e I can't connect to the internet and do not have an interface other than loopback.

However I am not sure how we can upgrade using  pytheas22 commands 


sudo apt-get update
sudo apt-get install build-essential

if I do not have a network connection itself on the machine where I need to fix the "original network problem".  I do have another windows laptop. I downloaded build-essential but that has some dependency and then that has other dependency. I was wondering if there is any other way or some way to download via http (a browser) from packages.ubuntu.com all dependencies and packages for build-essential ? 

Any comments would be helpful.

Thanks

---

### Post by pytheas22 on 2010-07-02
**gibu_**: first off, keep in mind that the solution for the original poster only applies to specific hardware.  If you don't have the same exact ethernet card, your problem is likely different.

That said, assuming your problem is the same, the Ubuntu installation CD has the build-essential package on it and all dependencies.  So you can put your CD in the drive, then go to System>Administration>Software Sources and under the "Ubuntu Software" tab, make sure the box for using your CD or DVD as a repository is checked.  Then close the window, agree to update your sources list when prompted, and try running again:
```

sudo apt-get update
sudo apt-get install build-essential
```

If this works, you can proceed with compiling the ethernet driver and hopefully this will get you online.

If you don't have the same hardware as the original poster (or aren't sure which hardware you have), please post the output of these commands so we can try to figure out how to solve your problem:

```
lspci -nn
dmesg | grep -e eth -e atl
cat /etc/issue
uname -rm
```

---

### Post by gibu_ on 2010-07-02
pytheas22 : You have been a great help. 

Thanks for the original steps. I did not know the easiest approach to updating build-essential was using the original cd itself. I took a long route to reaching that by using my windows laptop + [keryx]("http://keryxproject.org/tutorial/#on_windows") to get all dependencies for build-essential and then followed the rest of your steps. 

Wired networking is working for me. 

I bought a new laptop a few days back Dell N4010 i3, without an OS. So getting Ubuntu to run was mandatory. Without a network running, i was disappointed. Thanks a ton for your post.


For the record my hardware details as per your request. 

```
drince@drince-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

drince@drince-laptop:~$ dmesg | grep -e  eth -e at1
[   17.434315] atl1c 0000:04:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   19.817303] atl1c 0000:04:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   28.156600] eth0: no IPv6 routers present
drince@drince-laptop:~$ cat /etc/issue 
Ubuntu 10.04 LTS \n \l

drince@drince-laptop:~$ uname -rm
2.6.32-21-generic x86_64


```Next I will try to get the wireless running as per your suggestion and  revert back (need to head back to bed right now though). Do you think your previous comments about the wireless holds good ? 

```

Find below the output of lshw -C network

drince@drince-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: b8:ac:6f:67:27:68
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A ip=192.168.2.3 latency=0 multicast=yes
       resources: irq:33 memory:f0400000-f043ffff ioport:2000(size=128)
drince@drince-laptop:~$
```

---

### Post by pytheas22 on 2010-07-02
**gibu_**: glad to hear that worked.  It looks like your ethernet hardware is the same as the original poster's.

The same procedure should probably also work for your wireless.  You just need the proprietary 'wl' module installed, which you can accomplish using the steps earlier in the thread.  Let me know if you have any trouble.

Keep in mind that you will need to recompile the ethernet driver whenever you update your Ubuntu kernel; you may want to keep a clean copy of the source code on hand for that purpose.

Out of curiosity, did you buy your computer from Dell directly without any operating system installed?  I've never been able to find them like that here in the United States, but I'd sure like to in order to be able to avoid paying for Windows.  Dell also offers a few laptops with Ubuntu preinstalled, but the selection is much smaller than the Windows offerings, so being able to choose any laptop and not have Windows preinstalled would be great.

---

### Post by gibu_ on 2010-07-04
pytheas22:

I was not able to setup wireless on the laptop.  Output of the steps you suggested. (I executed a second time). It had executed with no errors.

I have never setup wireless on Ubuntu so was not sure where to look for it. The Network Manager also  does not give a hint that you should ideally find it there. I guess it should have shown something there. 

```
drince@drince-laptop:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for drince: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 212 not upgraded.
drince@drince-laptop:~$ echo wl | sudo tee -a /etc/modules
wl
```For me in the Network Manager, the rows are as follows "
```
Wired Network
Auto eth0
Disconnect
VPN Connections 

```Is there some other output i should post ? BTW I have seen some posts about enabling wireless, but was not sure if i should try and disturb the default settings on this new installation. So waiting for any comments you have. 

I got this laptop from an authorized Dell outlet (not  direct Dell). It came with only a  FreeDOS CD. So without Windows I got it at approx. $80 cheaper.

Thanks in advance.

Gibu

---

### Post by pytheas22 on 2010-07-04
**gibu_**: sorry that didn't work.  Please post the output of these commands so we can try to figure out what went wrong:
```

sudo modprobe wl
ls /lib/firmware
dmesg | grep -e wl -ie firmware -e wlan -ie radio
lshw -C Network
```

The first command may have no output; that's alright.

---

### Post by gibu_ on 2010-07-05
Hi pytheas22:

Output for the commands.  

```

** sudo modprobe wl**
FATAL: Error inserting wl (/lib/modules/2.6.32-21-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
[B]
ls /lib/firmware[/B]
2.6.32-21-generic         dabusb                    libertas       sxg
3com                      dsp56k                    matrox         tehuti
acenic                    dvb-fe-xc5000-1.6.114.fw  mts_cdma.fw    ti_3410.fw
adaptec                   dvb-usb-dib0700-1.20.fw   mts_edge.fw    ti_5052.fw
advansys                  e100                      mts_gsm.fw     tigon
agere_ap_fw.bin           ea                        mwl8k          tr_smctr.bin
agere_sta_fw.bin          edgeport                  myricom        ttusb-budget
aic94xx-seq.fw            emi26                     NPE-B          usbdux
ar9170-1.fw               emi62                     NPE-C          usbduxfast_firmware.bin
ar9170-2.fw               ess                       ositech        usbdux_firmware.bin
ar9170.fw                 i2400m-fw-usb-1.3.sbcf    ql2100_fw.bin  v4l-cx231xx-avcore-01.fw
ath3k-1.fw                i2400m-fw-usb-1.4.sbcf    ql2200_fw.bin  v4l-cx23418-apu.fw
atmel_at76c502_3com.bin   intelliport2.bin          ql2300_fw.bin  v4l-cx23418-cpu.fw
atmel_at76c502.bin        ipw2100-1.3.fw            ql2322_fw.bin  v4l-cx23418-dig.fw
atmel_at76c502d.bin       ipw2100-1.3-i.fw          ql2400_fw.bin  v4l-cx2341x-dec.fw
atmel_at76c502e.bin       ipw2100-1.3-p.fw          ql2500_fw.bin  v4l-cx2341x-enc.fw
atmel_at76c504_2958.bin   ipw2200-bss.fw            qlogic         v4l-cx2341x-init.mpg
atmel_at76c504a_2958.bin  ipw2200-ibss.fw           r128           v4l-cx23885-avcore-01.fw
atmel_at76c504.bin        ipw2200-sniffer.fw        radeon         v4l-cx23885-enc.fw
atmel_at76c506.bin        iwlwifi-1000-3.ucode      rt2561.bin     v4l-cx25840.fw
atmsar11.fw               iwlwifi-3945-2.ucode      rt2561s.bin    v4l-pvrusb2-24xxx-01.fw
av7110                    iwlwifi-4965-2.ucode      rt2661.bin     v4l-pvrusb2-29xxx-01.fw
bnx2                      iwlwifi-5000-1.ucode      rt2860.bin     vicam
bnx2x-e1-4.8.53.0.fw      iwlwifi-5000-2.ucode      rt2870.bin     whiteheat.fw
bnx2x-e1-5.2.7.0.fw       iwlwifi-5150-2.ucode      rt73.bin       whiteheat_loader.fw
bnx2x-e1h-4.8.53.0.fw     iwlwifi-6000-4.ucode      RTL8192SE      yam
bnx2x-e1h-5.2.7.0.fw      kaweth                    sb16           yamaha
cis                       keyspan                   scripts        zd1201-ap.fw
cpia2                     keyspan_pda               slicoss        zd1201.fw
cxgb3                     korg                      sun            zd1211


[B]dmesg | grep -e wl -ie firmware -e wlan -ie radio

[/B] [   16.032845] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.033594] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   16.033595] wl: Unknown symbol lib80211_get_crypto_ops
[   16.037820] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   16.037824] wl: Unknown symbol lib80211_get_crypto_ops
[   16.045915] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   16.045919] wl: Unknown symbol lib80211_get_crypto_ops
[   16.053361] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   16.053365] wl: Unknown symbol lib80211_get_crypto_ops
[   16.059630] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   16.059634] wl: Unknown symbol lib80211_get_crypto_ops
[  501.119832] wl: disagrees about version of symbol lib80211_get_crypto_ops
[  501.119840] wl: Unknown symbol lib80211_get_crypto_ops
[  507.391666] wl: disagrees about version of symbol lib80211_get_crypto_ops
[  507.391675] wl: Unknown symbol lib80211_get_crypto_ops
[  559.166387] wl: disagrees about version of symbol lib80211_get_crypto_ops
[  559.166395] wl: Unknown symbol lib80211_get_crypto_ops
[  577.657950] wl: disagrees about version of symbol lib80211_get_crypto_ops
[  577.657959] wl: Unknown symbol lib80211_get_crypto_ops


[B]lshw -C Network
[/B]WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: b8:ac:6f:67:27:68
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A ip=192.168.2.2 latency=0 multicast=yes
       resources: irq:33 memory:f0400000-f043ffff ioport:2000(size=128)



```thanks for your help.

---

### Post by pytheas22 on 2010-07-05
**gibu_**: thanks for the output.  From your dmesg output, it looks like the system doesn't like the version of the 'wl' module (the driver for your wireless card) that was installed before.  I'm not sure exactly why, but I think it would be worth removing it by typing:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get remove --purge bcmwl-modaliases
```

(If it says either of these packages is not installed, just ignore the message and continue.)

Then reboot.  After the reboot, reinstall the package with:
```

sudo apt-get install bcmwl-kernel-source
```

This should give you a fresh build of the module, which will hopefully work better.  After it finishes installing, please reboot.  If after that point it still doesn't work, please let me know the output of:
```

dmesg | grep -e wl
modinfo wl
```

If this process won't work on the second try, we can install the driver manually...

---

### Post by gibu_ on 2010-07-05
**pytheas22:**


Thanks for the steps. However it still does not work.  I don't know if i should have said this earlier, but i had added a "Wireless connection"  via that Network Manager Applet under the wireless tab. However as mentioned previously it does not show up under the "NM Applet Menu". 


```

**dmesg | grep -e wl**
[   15.833827] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.835009] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.835012] wl: Unknown symbol lib80211_get_crypto_ops
[   15.840662] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.840668] wl: Unknown symbol lib80211_get_crypto_ops
[   15.845757] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.845761] wl: Unknown symbol lib80211_get_crypto_ops
[   15.853172] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.853176] wl: Unknown symbol lib80211_get_crypto_ops
[   15.859018] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.859022] wl: Unknown symbol lib80211_get_crypto_ops


** modinfo wl**
filename:       /lib/modules/2.6.32-21-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     74F8D9437CF7F1FCB427C79
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string
prince@prince-laptop:~$ 


```Thanks for your help.

---

### Post by pytheas22 on 2010-07-06
**gibu_**: I did some googling and found this [bug report]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630"), which I think is related.  The fix is supposed to be to remove the linux-backports-modules-wireless package.  So please run:
```

sudo apt-get remove linux-backports-modules-wireless-`uname -r`-generic
```

Then please reboot and see if wireless works.  If it still fails, please try:

```
sudo insmod /lib/modules/`uname -r`/kernel/net/wireless/lib80211.ko
sudo insmod /lib/modules/`uname -r`/kernel/net/wireless/lib80211_crypt_ccmp.ko
sudo insmod /lib/modules/`uname -r`/kernel/net/wireless/lib80211_crypt_tkip.ko
sudo insmod /lib/modules/`uname -r`/kernel/net/wireless/lib80211_crypt_wep.ko
sudo modprobe wl
```

---

### Post by gibu_ on 2010-07-06
pytheas22: it gave some errors and did not work. 

I will google around more and update here if i find a solution.
The wireless card i have is kind of not yet supported. I can see its not listed even in the list of [ndiswrapper]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:Dell"). I guess i have to wait.

```
Dell Wireless 1501 802.11b/g/n Half Mini Card
Network controller: Broadcom Corporation Device 4727 (rev 01)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)

``````

[B]sudo apt-get remove linux-backports-modules-wireless-`uname -r`-generic
[/B]some message not removed as its not installed......

[B]sudo insmod /lib/modules/`uname -r`/kernel/net/wireless/lib80211.ko
[/B]insmod: error inserting '/lib/modules/2.6.32-21-generic/kernel/net/wireless/lib80211.ko': -1 File exists

[B]sudo insmod /lib/modules/`uname -r`/kernel/net/wireless/lib80211_crypt_ccmp.ko
[/B]insmod: error inserting '/lib/modules/2.6.32-21-generic/kernel/net/wireless/lib80211_crypt_ccmp.ko': -1 Unknown symbol in module


[B]sudo insmod /lib/modules/`uname -r`/kernel/net/wireless/lib80211_crypt_tkip.ko
[/B]insmod: error inserting '/lib/modules/2.6.32-21-generic/kernel/net/wireless/lib80211_crypt_tkip.ko': -1 Unknown symbol in module


[B]sudo insmod /lib/modules/`uname -r`/kernel/net/wireless/lib80211_crypt_wep.ko
[/B]insmod: error inserting '/lib/modules/2.6.32-21-generic/kernel/net/wireless/lib80211_crypt_wep.ko': -1 Unknown symbol in module

[B]sudo modprobe wl
[/B]FATAL: Error inserting wl (/lib/modules/2.6.32-21-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)


dmesg | grep wl
[   15.975041] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.975803] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.975805] wl: Unknown symbol lib80211_get_crypto_ops
[   15.980961] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.980967] wl: Unknown symbol lib80211_get_crypto_ops
[   15.985940] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.985945] wl: Unknown symbol lib80211_get_crypto_ops
[   15.991639] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.991643] wl: Unknown symbol lib80211_get_crypto_ops
[   15.997513] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.997518] wl: Unknown symbol lib80211_get_crypto_ops
[  102.223975] wl: disagrees about version of symbol lib80211_get_crypto_ops
[  102.223984] wl: Unknown symbol lib80211_get_crypto_ops

```

---

### Post by pytheas22 on 2010-07-07
Your device really should be supported.  The ndiswrapper list is not necessarily up-to-date, so I wouldn't put much stock in it; more importantly, there is a native Linux driver for your card available from Broadcom (which manufactures the device) at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).  That driver is the one that should have been installed earlier when you ran the command "sudo apt-get install bcmwl-kernel-source", but apparently that version of the driver didn't work for you.

I think it might be worth a try to install the driver directly from Broadcom's site, instead of using the Ubuntu package that you tried earlier.  To install from Broadcom, first go to [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and download the appropriate driver for your kernel architecture (32 or 64-bit).  Save the file to your desktop.  Then run these commands to compile and install it:
```

sudo apt-get remove bcmwl-kernel-source
sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
mv hybrid-portsrc*gz /tmp
cd /tmp
tar -xzvf hybrid-portsrc*gz
make
sudo make install
```

Then try rebooting, and see if it works.  If this also fails, we can try the ndiswrapper approach, which would get your card running using Windows drivers.

---

### Post by gibu_ on 2010-07-07
pytheas22:  I tried the steps you suggested. It `still does not work.

From the [broadcom site]("http://www.broadcom.com/docs/linux_sta/README.txt") they mention loading 
lib80211     or  ieee80211_crypt_tkip. The first one loaded without errors, but there is no wireless enabled. 

I tried loading ieee80211_crypt_tkip but was not able to do so as the module does not exist. However if you look at the dmesg (as seen previously), all the while the errors seem to be related to this module.

BTW one note, after downloading from the broadcom site, I am not able to enable the driver via the "Hardware Drivers" applet. When i used your earlier approaches, atleast  over there it was shown as enabled.  

On another note, do you think by any chance using Ubuntu 8.10 or 9.10 would solve this problem ? or if i shift to the 32 bit version ? I am open to downgrading  to sort this problem. Earlier I was just fine using 8.10. 

```
drince@drince-laptop:~/Downloads/hyb$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /home/drince/Downloads/hyb/built-in.o
  CC [M]  /home/drince/Downloads/hyb/src/shared/linux_osl.o
  CC [M]  /home/drince/Downloads/hyb/src/wl/sys/wl_linux.o
  CC [M]  /home/drince/Downloads/hyb/src/wl/sys/wl_iw.o
  LD [M]  /home/drince/Downloads/hyb/wl.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/drince/Downloads/hyb/wl.o
see include/linux/module.h for more information
  CC      /home/drince/Downloads/hyb/wl.mod.o
  LD [M]  /home/drince/Downloads/hyb/wl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
  
Thanks for all your effort. 

dmesg | grep -e wl -ie firmware -e wlan -ie wl -ie hybrid  -ie x86_64-v5 -ie 4727 
[   15.613275] wl: module license 'unspecified' taints kernel.
[   15.614128] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.614131] wl: Unknown symbol lib80211_get_crypto_ops
[   15.618793] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.618798] wl: Unknown symbol lib80211_get_crypto_ops
[   15.625928] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.625932] wl: Unknown symbol lib80211_get_crypto_ops
[   15.631682] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.631687] wl: Unknown symbol lib80211_get_crypto_ops
[   15.637417] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   15.637421] wl: Unknown symbol lib80211_get_crypto_ops
drince@drince-laptop:~/Downloads/hybdir$ sudo insmod wl.ko
insmod: error inserting 'wl.ko': -1 Unknown symbol in module
```

---

### Post by pytheas22 on 2010-07-08
A different version of Ubuntu may well solve the problem.  It seems that something weird is going on with your wireless stack (the bits of code in your computer that include the wireless device drivers and other modules on which they depend, such as drivers for doing WPA decryption), and the 'wl' driver is "disagreeing" with some of the other modules in the wireless stack.  I've seen this type of stuff before and simply rebooting always solves it, but apparently that's not working in your case.

Thinking about it more, the problem might be related to when you compiled the ethernet driver, because that could potentially have modified some of the modules in the wireless stack (since in your particular case the ethernet driver source code was part of the [compat-wireless]("http://wireless.kernel.org/en/users/Download") package, for bizarre reasons) and caused these module "disagreements."  I suspect that the wireless would work if you simply ran "sudo apt-get install bcmwl-kernel-source" on a clean system, before compiling the ethernet driver.

So it might certainly be worth trying this on an earlier version of Ubuntu, or reinstalling 10.04 and seeing if installing the wireless driver before the ethernet works better.  I'm pretty sure that the bcmwl-kernel-source package is on the Ubuntu installation CD, so if you enable your CD as a repository using the tool at System>Administration>Software Sources, you should then be able to install the wireless driver even without having an Internet connection available.

---

### Post by gibu_ on 2010-07-09
pytheas22:

Thanks for your suggestions. I will try both options and get back. First with 10.04 and then with 8.10.

Gibu
ps : I may take sometime to get back

---

### Post by gibu_ on 2010-07-13
**pytheas22**:

I had to try both options  to get it to work ! 

First tried to get it working with **Ubuntu 10.04 - 64 bit**, i did  not succeed. 

Here are a few observations : 
a) The  bcmwl-kernel-source in the CD has a version that does not  support 
broadcom 4313 device. So we will have to download the latest version  directly from the [broadcom  site]("http://www.broadcom.com/docs/linux_sta/README.txt").

b) Broadcom site says kernel 2.6.32 is not tested though some users have  reported it to work for them.  Ubuntu 10.04 comes with kernel 2.6.32,  so there is some reason I could not get it to work.

As per your suggestion, I tried a fresh install of 10.04, and tried  installing bcmwl form CD, then removed it, then downloaded and compiled  the drivers from broadcom site. It did not work for me. Strangely there  were no errors (dmesg) on startup this time unlike what i used to see  before. The only problem was there was no indication that wireless  loaded / was enabled.

I was in a hurry to get the wireless working so went to option 2 you  mentioned, use an older Version of Ubuntu. 
I had the Ubuntu 8.10 CD and installed 8.10.

**It Works in Ubuntu 8.10 - 32 bit : ** 
For the record my  hardware : Dell 14R (N4010) with broadcom 4313 (equivalent Dell name is  Dell 1501) device and it works well with Ubuntu 8.10. 

I first got wired to work and then wireless.  I followed the same  steps mentioned in the [readme  in broadcom site]("http://www.broadcom.com/docs/linux_sta/README.txt") (32 bit). 

> 

Follow Build Instructions from [here]("http://www.broadcom.com/docs/linux_sta/README.txt"). Then  make sure you are in the same folder where "wl.ko" is present. 
sudo  modprobe ieee80211_crypt_tkip
sudo insmod ./wl.ko
**Thank you very much for your help.** Maybe in a weeks time i will  reinstall 10.04 and give it another try, now that I know it works with  8.10. Now all i have to do is put the last 2 lines in some startup script so that wireless loads everytime i boot.

> [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
WHAT'S NEW IN THIS RELEASE
----------------------------
+ Supports up to linux kernel 2.6.31. 2.6.32 support is there also but 

not tested (although reports from users suggests it works fine.)

---

### Post by pytheas22 on 2010-07-13
**gibu_**: thanks for reporting back and glad to hear you were at least able to get it work in Ubuntu 8.10.

I'm wondering if perhaps the module was simply not loaded when you installed in under Ubuntu 10.04.  Usually the system loads it automatically at boot time, but if it's not, try running:
```

sudo modprobe wl
```

and see if you then find information in dmesg about the driver being present.

If you want to play around with 10.04 and need more help, let me know.  But I completely understand if you want to stick with 8.10 since you know it works.

---

### Post by gibu_ on 2010-07-14
[B]pytheas22:
[/B]
In 10.04, I did not try loading the driver explicitly, I hope to re-try it over the weekend and get back to you.

---

### Post by Rajeshtl on 2010-07-15
> **pytheas22 said:**
> Your ethernet hardware seems to be quite new and doesn't have a driver built into Ubuntu as of yet. However, there's a driver included in the compat-wireless stack that you can use (I have no idea why they included an ethernet driver in compat-wireless, but according to [these emails]("http://omgili.com/mailinglist/kernel-team/lists/ubuntu/com/43e72e891002020915x572a11fcg57f0b9caf7ed08eamailgmailcom.html"), someone did).
 
To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking). Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```
 
Then reboot. Hopefully your ethernet will work automatically after reboot; if not, run:
```

sudo modprobe atl1c
```
 
to insert the driver. Let me know how it goes.
 
We can probably make your wireless work too, if you're interested.
 
 
This didnt help I still have the same problem...
for sudo Modprobe command :: it does nothing...

---

### Post by Rajeshtl on 2010-07-15
> **pytheas22 said:**
> **gibu_**: first off, keep in mind that the solution for the original poster only applies to specific hardware. If you don't have the same exact ethernet card, your problem is likely different.
 
That said, assuming your problem is the same, the Ubuntu installation CD has the build-essential package on it and all dependencies. So you can put your CD in the drive, then go to System>Administration>Software Sources and under the "Ubuntu Software" tab, make sure the box for using your CD or DVD as a repository is checked. Then close the window, agree to update your sources list when prompted, and try running again:
```

sudo apt-get update
sudo apt-get install build-essential
```
 
If this works, you can proceed with compiling the ethernet driver and hopefully this will get you online.
 
If you don't have the same hardware as the original poster (or aren't sure which hardware you have), please post the output of these commands so we can try to figure out how to solve your problem:
 
```
lspci -nn
dmesg | grep -e eth -e atl
cat /etc/issue
uname -rm
```
 
Here are the results of the above commands.. 
 
lspsci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
02:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
02:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
02:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

dmesg | grep -e eth -e atl
[    1.081890] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:70:71:20
[   11.415935] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.816271] b44: eth0: Link is up at 100 Mbps, full duplex.
[   14.816277] b44: eth0: Flow control is off for TX and off for RX.
[   14.816589] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   25.212022] eth0: no IPv6 routers present
cat /etc/issue
Ubuntu 10.04 LTS \n \l
unmae -rm
2.6.32-21-generic i686

---

### Post by gibu_ on 2010-07-15
[B]pytheas22:
[/B]
I reinstalled 10.04, had the wireless driver from broadcom site installed first. It worked :oops: :-) 
Not sure what I missed the first time. I did not have to load the wl module either. However I followed the instructions mentioned from the  broadcom site. 

After a reboot, i then tried getting the wired network to work. I compiled and restarted. The wired works.  However after that I can't get the wireless to work again. Since it is not   auto loaded, i tried doing it manually again as below. 
> 

sudo insmod wl.ko  
**insmod: error inserting 'wl.ko': -1 Unknown symbol in module**
drince10@drince10-laptop:~/Desktop/forums2/hy64$ sudo insmod ./wl.ko  
insmod: error inserting './wl.ko': -1 Unknown symbol in module
drince10@drince10-laptop:~/Desktop/forums2/hy64$  sudo modprobe wl
FATAL: Module wl not found.It looks like with a Dell 1501 wireless card  (broadcom 4313) on Ubuntu 10.04, we can't get wired and wireless to work (without some developer help) due to some compatibility errors. 

One additional observation i would like to make is with 10.04, the access to Internet is slow every time you visit a page. In Firefox, it looks like a dns lookup of the website is done every time, so it says looking up site and after a minimum of 3-7 seconds, it starts the page download.   I observed this on **both wired and wireless**, even in  the second installation. Note, this occurs every time we access the website in the same session. I tried multiple sites too. The first time too I had observed it on the wired , but i thought something was wrong with my connection. However with Ubuntu 8.10, both wired and wireless worked smoothly. The reinstallation of 10.04 confirms it.

I guess I am better off staying with 8.10 (because it has a lower supported kernel version). When I get a 9.10 cd, i could even try that :-) or whenever broadcom site supports the 2.6.32 kernel, i could retry.

---

### Post by pytheas22 on 2010-07-16
**gibu**: that makes sense and confirms what I had come to suspect.  It seems that compiling the ethernet driver for your device modifies the wireless stack in such a way that it makes the Broadcom wireless driver incompatible.  Unfortunately Broadcom's driver can be picky about what it needs to work, and since it's maintained by Broadcom rather than open-source developers, it's hard to fix these problems.

I'm thinking it may still be possible for you to get your wireless and ethernet working at the same time by using ndiswrapper for the wireless.  ndiswrapper would drive your card using Windows drivers rather than Broadcom's driver, and it should work even with your modified wireless stack.  If you want to give this a try, I'll try to write up instructions if you can point me to a Windows driver for your wireless card, and tell me whether you're using a 32 or 64-bit Linux kernel (if you aren't sure, post the output of "uname -m").

Of course, if you'd prefer simply to stick with 8.10 at this point, that's completely fine, so don't feel any pressure to try ndiswrapper unless you want to.

**Rajeshtl**: the commands you ran installed an ethernet driver for a device that you don't have.  I assume you want to get your wireless working; to do that, it should be sufficient to do:
```

sudo apt-get update
sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
echo wl | sudo tee -a /etc/modules
```

You may also need to run this command to undo the changes you made before:
```

cd ~/Desktop/compat-wireless*
sudo make uninstall
```

If this still doesn't make your wireless work after a reboot, please post the output of:
```

dmesg | grep -e wl -e eth1 -e disagree
lshw -C Network
```

---

### Post by Rajeshtl on 2010-07-16
> **pytheas22 said:**
> **gibu**: that makes sense and confirms what I had come to suspect. It seems that compiling the ethernet driver for your device modifies the wireless stack in such a way that it makes the Broadcom wireless driver incompatible. Unfortunately Broadcom's driver can be picky about what it needs to work, and since it's maintained by Broadcom rather than open-source developers, it's hard to fix these problems.
 
I'm thinking it may still be possible for you to get your wireless and ethernet working at the same time by using ndiswrapper for the wireless. ndiswrapper would drive your card using Windows drivers rather than Broadcom's driver, and it should work even with your modified wireless stack. If you want to give this a try, I'll try to write up instructions if you can point me to a Windows driver for your wireless card, and tell me whether you're using a 32 or 64-bit Linux kernel (if you aren't sure, post the output of "uname -m").
 
Of course, if you'd prefer simply to stick with 8.10 at this point, that's completely fine, so don't feel any pressure to try ndiswrapper unless you want to.
 
**Rajeshtl**: the commands you ran installed an ethernet driver for a device that you don't have. I assume you want to get your wireless working; to do that, it should be sufficient to do:
```

sudo apt-get update
sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
echo wl | sudo tee -a /etc/modules
```
 
You may also need to run this command to undo the changes you made before:
```

cd ~/Desktop/compat-wireless*
sudo make uninstall
```
 
If this still doesn't make your wireless work after a reboot, please post the output of:
```

dmesg | grep -e wl -e eth1 -e disagree
lshw -C Network
```
 
 
@pytheas22
First of all I appreciate your reply and Yes I want to make my wireless work..
 
first set of commands didnt work.
here is the output of 
 
dmesg | grep -e wl -e eth1 -e disagree
 
this gave me nothing.
 
lshw -C Network

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:0c:00.0"]pci@0000:0c:00.0[/EMAIL]
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       logical name: eth0
       version: 02
       serial: 00:15:c5:70:71:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:17 memory:ef9fe000-ef9fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:d8:2f:2a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by pytheas22 on 2010-07-16
**Rajeshtl**: what do you mean when you say the first set of commands didn't work?  It would be useful to see the output to know exactly what failed.

Another approach is to run these commands, then reboot:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

At one point you will be asked whether you want to download firmware; make sure to say yes.

Note that for this to work, you will need to be plugged into the Internet because you need to download files required by the wireless driver.  If you have no way to plug into the Internet, let me know and we can try a different approach (but plugging in is much less complicated).

---

### Post by Rajeshtl on 2010-07-16
> **pytheas22 said:**
> **gibu**: that makes sense and confirms what I had come to suspect. It seems that compiling the ethernet driver for your device modifies the wireless stack in such a way that it makes the Broadcom wireless driver incompatible. Unfortunately Broadcom's driver can be picky about what it needs to work, and since it's maintained by Broadcom rather than open-source developers, it's hard to fix these problems.
 
I'm thinking it may still be possible for you to get your wireless and ethernet working at the same time by using ndiswrapper for the wireless. ndiswrapper would drive your card using Windows drivers rather than Broadcom's driver, and it should work even with your modified wireless stack. If you want to give this a try, I'll try to write up instructions if you can point me to a Windows driver for your wireless card, and tell me whether you're using a 32 or 64-bit Linux kernel (if you aren't sure, post the output of "uname -m").
 
Of course, if you'd prefer simply to stick with 8.10 at this point, that's completely fine, so don't feel any pressure to try ndiswrapper unless you want to.
 
**Rajeshtl**: the commands you ran installed an ethernet driver for a device that you don't have. I assume you want to get your wireless working; to do that, it should be sufficient to do:
```

sudo apt-get update
sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
echo wl | sudo tee -a /etc/modules
```
 
You may also need to run this command to undo the changes you made before:
```

cd ~/Desktop/compat-wireless*
sudo make uninstall
```
 
If this still doesn't make your wireless work after a reboot, please post the output of:
```

dmesg | grep -e wl -e eth1 -e disagree
lshw -C Network
```
 
 
**Sudo apt-get update**
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
W: Some index files failed to download, they have been ignored, or old ones used instead.
 
 
**sudo apt-get install bcmwl-kernel-source bcmwl-modaliases**

eading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-modaliases is already the newest version.
The following extra packages will be installed:
  dkms fakeroot patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,205kB of archives.
After this operation, 3,764kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3
  File not found
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main fakeroot 1.14.4-1ubuntu1
  File not found
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main patch 2.6-2ubuntu1
  File not found
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

** echo wl | sudo tee -a /etc/modules**
wl

---

### Post by Rajeshtl on 2010-07-16
> **pytheas22 said:**
> **Rajeshtl**: what do you mean when you say the first set of commands didn't work? It would be useful to see the output to know exactly what failed.
 
Another approach is to run these commands, then reboot:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```
 
At one point you will be asked whether you want to download firmware; make sure to say yes.
 
Note that for this to work, you will need to be plugged into the Internet because you need to download files required by the wireless driver. If you have no way to plug into the Internet, let me know and we can try a different approach (but plugging in is much less complicated).
 
 
output of the command:
**sudo apt-get install b43-fwcutter**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up b43-fwcutter (1:012-1build1) ...
--2010-07-16 16:41:05--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by pytheas22 on 2010-07-16
**Rajeshtl**: it looks like you were not connected to the Internet when you ran those commands.  You need to have an Internet connection to download the files you need.

If it's totally impossible for you to get an Internet connection on this computer, you can do this:

1. on another computer with Internet access, download the file [http://burnthesorbonne.com/files/b43_firmware.tar.gz](http://burnthesorbonne.com/files/b43_firmware.tar.gz)
2. use a USB stick or CD to transfer that file to your Ubuntu computer.  Save it on your desktop there.
3. run these commands on the Ubuntu computer:
```

cd ~/Desktop
tar -xzvf b43_firmware.tar.gz
sudo mv b43 /lib/firmware
sudo mv b43legacy /lib/firmware
```

Now try rebooting and hopefully the wireless will work.  If it still does not work, please post the output of these commands (some commands may have no output):
```

sudo rmmod wl
sudo rmmod ssb
sudo rmmod b43
sudo modprobe b43
sudo iwlist scan
dmesg | grep -e b43 -e wlan -e firmware
ls /lib/firmware
```

---

### Post by Rajeshtl on 2010-07-17
> **pytheas22 said:**
> **Rajeshtl**: it looks like you were not connected to the Internet when you ran those commands. You need to have an Internet connection to download the files you need.
 
If it's totally impossible for you to get an Internet connection on this computer, you can do this:
 
1. on another computer with Internet access, download the file [http://burnthesorbonne.com/files/b43_firmware.tar.gz](http://burnthesorbonne.com/files/b43_firmware.tar.gz)
2. use a USB stick or CD to transfer that file to your Ubuntu computer. Save it on your desktop there.
3. run these commands on the Ubuntu computer:
```

cd ~/Desktop
tar -xzvf b43_firmware.tar.gz
sudo mv b43 /lib/firmware
sudo mv b43legacy /lib/firmware
```
 
Now try rebooting and hopefully the wireless will work. If it still does not work, please post the output of these commands (some commands may have no output):
```

sudo rmmod wl
sudo rmmod ssb
sudo rmmod b43
sudo modprobe b43
sudo iwlist scan
dmesg | grep -e b43 -e wlan -e firmware
ls /lib/firmware
```
 
My laptop was connected to internet when I was executing the commands in the above post....Anyways I tried downloading and executing the commands,restarting it after that but it didnt work....Hence I ran the commands as specified:

**sudo rmmod wl**
ERROR: Module wl does not exist in /proc/modules
**sudo rmmod ssb**
ERROR: Module ssb is in use by b43,b44
[B]Sudo iwlist scan
[/B]lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     Interface doesn't support scanning : Network is down
**dmesg | grep -e b43 -e wlan -e firmware**
[    1.422897] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.422919] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   11.325212] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   11.425146] Registered led device: b43-phy0::tx
[   11.425167] Registered led device: b43-phy0::rx
[   11.425187] Registered led device: b43-phy0::radio
[  434.696850] b43-phy1: Broadcom 4311 WLAN found (core revision 10)
[  434.768748] Registered led device: b43-phy1::tx
[  434.768789] Registered led device: b43-phy1::rx
[  434.768826] Registered led device: b43-phy1::radio
 
**ls /lib/firmware**
2.6.32-21-generic         ess                     rt2561s.bin
3com                      i2400m-fw-usb-1.3.sbcf  rt2661.bin
acenic                    i2400m-fw-usb-1.4.sbcf  rt2860.bin
adaptec                   intelliport2.bin        rt2870.bin
advansys                  ipw2100-1.3.fw          rt73.bin
agere_ap_fw.bin           ipw2100-1.3-i.fw        RTL8192SE
agere_sta_fw.bin          ipw2100-1.3-p.fw        sb16
aic94xx-seq.fw            ipw2200-bss.fw          scripts
ar9170-1.fw               ipw2200-ibss.fw         slicoss
ar9170-2.fw               ipw2200-sniffer.fw      sun
ar9170.fw                 iwlwifi-1000-3.ucode    sxg
ath3k-1.fw                iwlwifi-3945-2.ucode    tehuti
atmel_at76c502_3com.bin   iwlwifi-4965-2.ucode    ti_3410.fw
atmel_at76c502.bin        iwlwifi-5000-1.ucode    ti_5052.fw
atmel_at76c502d.bin       iwlwifi-5000-2.ucode    tigon
atmel_at76c502e.bin       iwlwifi-5150-2.ucode    tr_smctr.bin
atmel_at76c504_2958.bin   iwlwifi-6000-4.ucode    ttusb-budget
atmel_at76c504a_2958.bin  kaweth                  usbdux
atmel_at76c504.bin        keyspan                 usbduxfast_firmware.bin
atmel_at76c506.bin        keyspan_pda             usbdux_firmware.bin
atmsar11.fw               korg                    v4l-cx231xx-avcore-01.fw
av7110                    libertas                v4l-cx23418-apu.fw
b43                       matrox                  v4l-cx23418-cpu.fw
b43legacy                 mts_cdma.fw             v4l-cx23418-dig.fw
bnx2                      mts_edge.fw             v4l-cx2341x-dec.fw
bnx2x-e1-4.8.53.0.fw      mts_gsm.fw              v4l-cx2341x-enc.fw
bnx2x-e1-5.2.7.0.fw       mwl8k                   v4l-cx2341x-init.mpg
bnx2x-e1h-4.8.53.0.fw     myricom                 v4l-cx23885-avcore-01.fw
bnx2x-e1h-5.2.7.0.fw      NPE-B                   v4l-cx23885-enc.fw
cis                       NPE-C                   v4l-cx25840.fw
cpia2                     ositech                 v4l-pvrusb2-24xxx-01.fw
cxgb3                     ql2100_fw.bin           v4l-pvrusb2-29xxx-01.fw
dabusb                    ql2200_fw.bin           vicam
dsp56k                    ql2300_fw.bin           whiteheat.fw
dvb-fe-xc5000-1.6.114.fw  ql2322_fw.bin           whiteheat_loader.fw
dvb-usb-dib0700-1.20.fw   ql2400_fw.bin           yam
e100                      ql2500_fw.bin           yamaha
ea                        qlogic                  zd1201-ap.fw
edgeport                  r128                    zd1201.fw
emi26                     radeon                  zd1211
emi62                     rt2561.bin

---

### Post by pytheas22 on 2010-07-17
The firmware looks like it's installed now, so that's good.  In order to connect to networks, you may simply need to type:
```

sudo ifconfig wlan0 up
```

If that doesn't produce any errors, type:
```

sudo iwlist scan
```

You should see a list of wireless networks in range.  If you do, try connecting to yours.

---

### Post by Rajeshtl on 2010-07-17
> **pytheas22 said:**
> The firmware looks like it's installed now, so that's good. In order to connect to networks, you may simply need to type:
```

sudo ifconfig wlan0 up
```
 
If that doesn't produce any errors, type:
```

sudo iwlist scan
```
 
You should see a list of wireless networks in range. If you do, try connecting to yours.
 
 
first time when I ran 'sudo ifconfig wlan0 up' it asked for my password and when I typed in it did nothing,then I entered the second one and it gave me this results
 
lo Interface doesnt support Scanning
eth0 interface doesnt support scanning
wlan0 interface doesnt support scanning: network is down...
 
Network is not down...I have a desktop which is working fine.
 
THen I typed in the same commands again
for the first one this time I got SIOCSIFFLAGS: Unknown error 132
second one gave the same results...
 
Appreciate your help...

---

### Post by Rajeshtl on 2010-07-17
> **Rajeshtl said:**
> first time when I ran 'sudo ifconfig wlan0 up' it asked for my password and when I typed in it did nothing,then I entered the second one and it gave me this results
 
lo Interface doesnt support Scanning
eth0 interface doesnt support scanning
wlan0 interface doesnt support scanning: network is down...
 
Network is not down...I have a desktop which is working fine.
 
THen I typed in the same commands again
for the first one this time I got SIOCSIFFLAGS: Unknown error 132
second one gave the same results...
 
Appreciate your help...
 
 
I just did 'rfkill list'
these are the results:
dell-wifi:Wireless LAN
   Soft Blocked : no
   Hard Blocked : no
Phy0:wireless LAN
   Soft Blocked : no
   hArd blocked : no

---

### Post by pytheas22 on 2010-07-17
That's strange.  We may need to try a different driver.  The one you were using was called 'b43'; let's try the STA driver instead, which is called 'wl'.  To install the STA driver, type:
```

sudo apt-get update
sudo apt-get install --fix-missing bcmwl-kernel-source bcmwl-modaliases
```

Alternatively, you should be able to install the driver graphically using the utility at System>Administration>Hardware Drivers.

You will need to be connected to the Internet for this to work, so please make sure you can browse websites before trying to install the STA driver.

Once the driver is installed, reboot.  If the wireless still doesn't work, try typing "sudo ifconfig eth1 up".  If it still doesn't work even after that, please post:
```

ifconfig
iwconfig
lshw -C Network
dmesg | grep -e b43 -e wl -e eth
```

Sorry this is turning out to be difficult, but thanks for your patience.

---

### Post by Rajeshtl on 2010-07-18
> **pytheas22 said:**
> That's strange. We may need to try a different driver. The one you were using was called 'b43'; let's try the STA driver instead, which is called 'wl'. To install the STA driver, type:
```

sudo apt-get update
sudo apt-get install --fix-missing bcmwl-kernel-source bcmwl-modaliases
```
 
Alternatively, you should be able to install the driver graphically using the utility at System>Administration>Hardware Drivers.
 
You will need to be connected to the Internet for this to work, so please make sure you can browse websites before trying to install the STA driver.
 
Once the driver is installed, reboot. If the wireless still doesn't work, try typing "sudo ifconfig eth1 up". If it still doesn't work even after that, please post:
```

ifconfig
iwconfig
lshw -C Network
dmesg | grep -e b43 -e wl -e eth
```
 
Sorry this is turning out to be difficult, but thanks for your patience.
 
**** My Wired Network is not working.
**iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

**ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
**lshw -C Network**
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:0c:00.0"]pci@0000:0c:00.0[/EMAIL]
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       logical name: eth0
       version: 02
       serial: 00:15:c5:70:71:20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:17 memory:ef9fe000-ef9fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:d8:2f:2a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
[B]dmesg | grep -e b43 wl -e eth
[/B]grep: wl: No such file or directory

---

### Post by pytheas22 on 2010-07-18
Do you have an Ubuntu installation CD?  If so, you can install the driver from there.  First you need to put your CD in the drive, then go to System>Administration>Software Sources and, under the "Ubuntu Software" tab, enable the use of your CD as a repository.  After that, try running again:
```

sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
```

If this doesn't work, you may also be able to get your wired Internet working by typing:
```

sudo ifconfig eth0 up
sudo dhclient eth0
```

After typing those commands, try opening Web pages.  If that works, you can download the STA driver using:

```

sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
```

---

### Post by Rajeshtl on 2010-07-18
> **pytheas22 said:**
> Do you have an Ubuntu installation CD? If so, you can install the driver from there. First you need to put your CD in the drive, then go to System>Administration>Software Sources and, under the "Ubuntu Software" tab, enable the use of your CD as a repository. After that, try running again:
```

sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
```
 
If this doesn't work, you may also be able to get your wired Internet working by typing:
```

sudo ifconfig eth0 up
sudo dhclient eth0
```
 
After typing those commands, try opening Web pages. If that works, you can download the STA driver using:
 
```

sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
```
 
 
selected CD ROM as repository,this is what I got...
**sudo apt-get install bcmwl-kernel-source bcmwl-modaliases**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
bcmwl-modaliases is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...
------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-21-generic
Building for architecture i686
Building initial module for 2.6.32-21-generic
/usr/sbin/dkms: line 35: patch: command not found
Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Rajeshtl on 2010-07-18
> **Rajeshtl said:**
> selected CD ROM as repository,this is what I got...
**sudo apt-get install bcmwl-kernel-source bcmwl-modaliases**
Reading package lists... Done
Building dependency tree 
Reading state information... Done
bcmwl-kernel-source is already the newest version.
bcmwl-modaliases is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...
------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-21-generic
Building for architecture i686
Building initial module for 2.6.32-21-generic
/usr/sbin/dkms: line 35: patch: command not found
Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
 
**SUDO IFCONFIG ETH0 UP**
 
**sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Listening on LPF/eth0/00:15:c5:70:71:20
Sending on   LPF/eth0/00:15:c5:70:71:20
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by pytheas22 on 2010-07-18
It looks like it didn't work on the first try because the package 'patch' was not installed, which it apparently needs.  Please make sure your Ubuntu CD is still enabled to be used as a repository, then try:
```

sudo apt-get install build-essential patch
sudo apt-get install --reinstall bcmwl-kernel-source bcmwl-modaliases
```

---

### Post by Rajeshtl on 2010-07-18
> **pytheas22 said:**
> It looks like it didn't work on the first try because the package 'patch' was not installed, which it apparently needs. Please make sure your Ubuntu CD is still enabled to be used as a repository, then try:
```

sudo apt-get install build-essential patch
sudo apt-get install --reinstall bcmwl-kernel-source bcmwl-modaliases
```
 
Sure I will try it tommorow and let u know..

---

### Post by julio prada on 2010-07-23
Hi rbisawa, on Pytheas post hes asked to enter:

sudo apt-get update

My problem is that I dont have access to any network since my wired and wireless cards are not recognized.

How did you do?

---

### Post by pytheas22 on 2010-07-23
**julio prada**: we can find a way to activate your wireless even if you don't have wired Internet access, but first let's make sure your situation is actually the same as that of the other posters in this thread.  Please post the output of these commands so we know which hardware you have, etc.:
```

lspci -nn
lshw -C Network
dmesg | grep wlan
```

If you have different hardware and a different problem, I'll ask you please to start a new thread so that this one doesn't become too convoluted, and I'll help you in your new thread.

Also, keep in mind that you can save the output of the commands to a text file, then use a USB disk or CD to transfer the file to a computer with Internet access, so that you can copy the output to this forum.

---

### Post by crabiorc on 2010-07-25
Hi Pytheas..First a very BIG bow for your help here. I am having the new inspiron N4010 - 14R from Dell and in the same page as Gilo__.

Tried:
Everything from the above posts and confirmed that wireless DO work without wired being configured (we are with the same system configuration).

Current scene:
My Wired connection works - thru your tip of enabling eth0 from compat-wireless.
Wireless not enabled. Hardware drivers-No restricted driver modules installed, as i tried installed from the broadcomm site.
But with the above workarounds i can confirm that its because of the wired driver, my wireless modules are not able to launch.

Now as you suggested please please please help me run the wireless up-ndiswrapper way. Thanks a ton in advance.

---

### Post by crabiorc on 2010-07-25
To add..I am using Ubuntu 10.04 ultimate 64 Bit- with tons of apps. This was pre-installed with a menu Windows wireless Drivers (i believe thats ndiswrapper).
I downloaded the Broadcomm 1501 Wireless card-64 Bit for Windows 7.
In this program i selected the .inf for the driver. Now it shows as
bcmwl6 - Hardware present:yes
What should i do next?

---

### Post by pytheas22 on 2010-07-26
**crabiorc**: it looks like you're most of the way there if you have the Windows driver loaded into ndiswrapper and ndisgtk (the graphical "Windows Wireless Drivers" utility you're using--it's just a graphical frontend to ndiswrapper) says the hardware is present.  This means you installed the right Windows driver for your device.

I'm guessing that either the ndiswrapper module is simply not loaded, or it can't claim the card because another driver is trying to.  Please run these commands and post the output; hopefully these will put ndiswrapper in control:
```

sudo rmmod wl
sudo rmmod ssb
sudo rmmod b43
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
dmesg | grep -e ndis -e wlan
ndiswrapper -l
lshw -C Network
```

By this point, hopefully your wireless card will be working.  If it's not, the command output should help figure out why.

Also, note that some of the commands above may have no output, and that some of them may produce errors.  That's alright; just proceed to the next command.

---

### Post by crabiorc on 2010-07-26
Thanks again.. doing it right away. I believe that the previous tried-out Broadcomm driver for linux is blocking access to ndis.
I am sorry that i am not pasting the exact terminal output here.
**sudo rmmod wl**
No mod found in /proc/modules
**sudo rmmod ssb**
No mod found in /proc/modules
**sudo rmmod b43**
No mod found in /proc/modules
**sudo rmmod ndiswrapper**
Nothing
**sudo modprobe ndiswrapper**
A warning on .conf
**sudo iwlist scan**
lists the names of my network devices
lo device cannot scan
eth0 device cannot scan
pan0 device cannot scan
**dmesg | grep -e ndis -e wlan**
Listed lots of lines with the same message 'Unknown symbol:filename'
Last 2 lines states that
Couldnt prepare driver bsmwl6
Couldnt load driver bsmwl6
**ndiswrapper -l**
bcmwl6:driver installed
device (14E4:4727) present
**lshw -C Network**
Listed all my network devices (lo, eth0, pan0) except eth1

And in Windows wireless drivers it still says that bcmwl6 Hardware present:Yes

---

### Post by crabiorc on 2010-07-27
Can i try updating the new lucid kernel 2.6.34 stable or 2.6.35rc1 ? I have lot other issues like Headphone/Mic jack not working, brightness increase/decrease keys not working,touchpad disable key not working.

---

### Post by pytheas22 on 2010-07-27
From the output you posted, it actually doesn't look like the problem is another driver claiming your wireless card.  Rather, it appears that ndiswrapper doesn't like the Windows driver that you loaded into it, as indicated by this output from dmesg:

> dmesg | grep -e ndis -e wlan
Listed lots of lines with the same message 'Unknown symbol:filename'
Last 2 lines states that
Couldnt prepare driver bsmwl6
Couldnt load driver bsmwl6

Sometimes this just happens.  When ndiswrapper says that the hardware is present, it's not actually checking to see whether the given driver will *work*; it's just telling you that the driver says it *should* work for your particular device (it figures this out by looking at PCI IDs).

My advice would be to uninstall the Windows driver that you currently have loaded into ndiswrapper, and try installing a different version of that driver.  ndiswrapper tends to work better with older Windows drivers, so if you can find one for XP or earlier, that would probably be better than Vista or 7.  You can search the [ndiswrapper database]("http://www.burnthesorbonne.com/?page_id=32") to see if there are any links to Windows drivers known to work for your device.

As for upgrading your kernel, you can give it a try if you like--it's not too risky as long as you keep your old kernel installed as well and know how to boot to it in case the newer one doesn't work for some reason.  I don't see any way that a newer kernel would solve your problem with ndiswrapper, because the solution there is going to be to find a Windows driver that ndiswrapper likes better.  But a newer kernel might solve your other issues.

---

### Post by rugito on 2010-08-05
Hi all,
 
I have been trying to use the solution of the compat-wireless driver, as suggested. I am running Ubuntu 10.04 amd64 on a new Toshiba L635-S3015, and I have exactly the same wired ethernet card as rbisawa. However, when I run ```
scripts/driver-select at11c
``` I obtain ```
Unsupported driver
``` What am I doing wrong?
 
Thanks very much.

---

### Post by PaulD475 on 2010-08-05
Hi.
I too have connection issues similer to the original thread starter.
Both my wired and wireless connections are not detected.
Thanks in advance for any help.

---

### Post by rugito on 2010-08-05
Solved! The problem was that I didn't realize that it was not AT11C but ATL1C! the "l" and the "1" look very similar...

---

### Post by djschlotte on 2010-08-06
So I am having a similar, if not the same, problem on my Asus G1s. I have Ubuntu 10.04 and my attempts to connect to the internet via a brand new Cat-5 cable have all failed. My wireless is working fine, and has been from the get go. I attempted the steps laid out on the first page before reading that those were hardware specific, so I hope I didn't screw things up worse than they were. Here is the information previously asked of others.

sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:54:46:07  
          inet6 addr: fe80::21f:c6ff:fe54:4607/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120 (120.0 B)  TX bytes:4572 (4.5 KB)
          Interrupt:31 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:5f:8b:69  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fe5f:8b69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:224300557 (224.3 MB)  TX bytes:11260784 (11.2 MB
==========================================================================
lspci

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
==========================================================================
ifup eth0

ifup: failed to open statefile /var/run/network/ifstate: Permission denied
==========================================================================
cat /etc/network/interfaces

auto lo
iface lo inet loopback
==========================================================================
cat /etc/NetworkManager/nm-system-settings.conf

[main]
plugins=ifupdown,keyfile

no-auto-default=00:1f:c6:54:46:07,

[ifupdown]
managed=false
==========================================================================
dmesg | grep -e eth0 -e bcm

[    2.211513] eth0: RTL8168b/8111b at 0xffffc90000672000, 00:1f:c6:54:46:07, XID 18000000 IRQ 31
[   16.233960] r8169: eth0: link up
[   16.233964] r8169: eth0: link up
[   26.670030] eth0: no IPv6 routers present
==========================================================================
lshw -C Network

       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:c6:54:46:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:31 ioport:a800(size=256) memory:fdfff000-fdffffff memory:fdfc0000-fdfdffff(prefetchable)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:5f:8b:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.114 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:fe0fe000-fe0fffff
============================================================================
lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 9500M GS] [10de:0405] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
07:00.0 SATA controller [0106]: JMicron Technology Corp. JMB360 AHCI Controller [197b:2360] (rev 02)
08:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
08:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
08:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
08:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
===========================================================================

I don't really have a need for being connected via wires, but sometimes I would like to have the faster speeds. Thanks in advance for your time.

---

### Post by pytheas22 on 2010-08-10
Sorry for not responding sooner--I was traveling and without an Internet connection.

**PaulD475**: even though your symptoms are the same as the original poster's, the causes may be different.  Please post the output of these commands so we can have a better idea:
```

ifconfig
ifconfig -a
lshw -C Network
dmesg | grep eth
lspci -nn
```
[B]
djschlotte[/B]: I'm not sure exactly what's wrong in your case, because from all of the output you posted, it looks like your wired interface should work.  Maybe it's a dumb question, but are you positive that the network you're plugging into grants addresses via dhcp and that you don't need to configure it statically?  You could try to request an address manually with:
```

sudo dhclient eth0
```

If that works, it will tell you that your interface has received an IP address from your router; otherwise it will time out with a message like "no leases received, sleeping."

It could also hep to see if the output of:

```
dmesg | grep eth0
lshw -C Network
```

says anything useful.

---

### Post by sls54 on 2010-08-13
I have an Acer AOD260 with the same network hardware as the original poster.   I have a dual boot with windows7 & no CD drive.  I installed Kubuntu 10.04-netbook from a USB stick that I set up from my desktop computer.
 
Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
Network controller: Broadcom Corporation Device 4727 (rev 01)
 
As a newbie, I am not sure how this works. I did get the file compat-wireless-2.6.tar.bz2 onto my netbook's desktop file.
I have Kubuntu 10.04 - netbook installed. Do I type this code into Konsole & execute one line at a time? I did the first two lines & got what seem to be errors. Does the netbook version have all the required files?
 
Can I update the Ubuntu 10.04 - netbook that I have on a USB stick the same way as well?
 
Or is there a way to just install the newest kernel 2.6.34 that has this new driver already?
 
(From post #6)
```

[COLOR=blue]sudo apt-get update[/COLOR]
[COLOR=#0000ff]     [COLOR=black]I got[/COLOR]    [/COLOR][COLOR=black]... some index files failed to download ...:[/COLOR]
[COLOR=blue]sudo apt-get install build-essential[/COLOR]
[COLOR=black]I got   ... couldn't find package build-essential:[/COLOR]
[COLOR=blue]cd ~/Desktop[/COLOR]
[COLOR=blue]tar -xjvf compat-wireless-2.6.tar.bz2[/COLOR]
[COLOR=blue]cd compat-wireless*[/COLOR]
[COLOR=blue]scripts/driver-select atl1c[/COLOR]
[COLOR=blue]make[/COLOR]
[COLOR=blue]sudo make install[/COLOR]
```
 
[COLOR=blue]Then reboot. Hopefully your ethernet will work automatically after reboot; if not, run:[/COLOR]
```

[COLOR=blue]sudo modprobe atl1c[/COLOR]
```
 
[COLOR=blue]to insert the driver. Let me know how it goes.[/COLOR]
 
[COLOR=blue]We can probably make your wireless work too, if you're interested.[/QUOTE][/COLOR]
 
[COLOR=black]I'll worry about the wireless after I get the wired network functioning.[/COLOR]

---

### Post by pytheas22 on 2010-08-13
**sls54**: the "sudo apt-get" commands aren't working because they expect you to have an Internet connection, and you obviously don't at this time because neither wireless nor wired Internet works.  However, if you have an Ubuntu installation CD and a CD drive, you should be able to grab the files you need from there.  Put the CD in your drive, then go to System>Administration>Software Sources.  Under the "Ubuntu Software" tab, check the box for using your CD as a repository, then press OK.  You'll be asked if you want to update your sources list; say yes.  It may complain about being unable to download some files; that's alright.

Once the CD has been registered as a repository, type again:
```

sudo apt-get install build-essential
```

and it should work this time.  With build-essential installed, you can compile the atl1c module from the compat-wireless package using the instructions that you copied below.

If you don't have a CD drive, you can try using the USB stick as a repository but I'm not positive that will work; you may need to have an actual CD.  If it doesn't, let me know and we can try another solution.

> 
Or is there a way to just install the newest kernel 2.6.34 that has this new driver already?

I'm not positive which version of the kernel has the module you need, but if you want to try installing a more recent kernel, you can download packages from the [Ubuntu kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").  Just download the linux-headers, linux-image and linux-source package for the kernel version you want, transfer them to your Ubuntu computer and double-click them to install (you may need to install them in a certain order; try linux-image first).  You'll need to run "sudo update-grub2" after installing the kernel to create an entry for it in your boot menu.

---

### Post by djschlotte on 2010-08-13
@pytheas22 - Doh! I forgot to delete my post. I figured out after finally tracking down a manual online that I had the Cat5 cable plugged into the wrong spot. Who would have though that a port labeled "Broadband" wouldn't have anything to do with broadband. Thanks for your help and time.

---

### Post by pytheas22 on 2010-08-13
> **djschlotte said:**
> @pytheas22 - Doh! I forgot to delete my post. I figured out after finally tracking down a manual online that I had the Cat5 cable plugged into the wrong spot. Who would have though that a port labeled "Broadband" wouldn't have anything to do with broadband. Thanks for your help and time.

Haha, well, glad you figured it out!

---

### Post by altonbr on 2010-08-21
> **pytheas22 said:**
> Your ethernet hardware seems to be quite new and doesn't have a driver built into Ubuntu as of yet.  However, there's a driver included in the compat-wireless stack that you can use (I have no idea why they included an ethernet driver in compat-wireless, but according to [these emails]("http://omgili.com/mailinglist/kernel-team/lists/ubuntu/com/43e72e891002020915x572a11fcg57f0b9caf7ed08eamailgmailcom.html"), someone did).

To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking).  Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```Then reboot.  Hopefully your ethernet will work automatically after reboot; if not, run:
```

sudo modprobe atl1c
```to insert the driver.  Let me know how it goes.

We can probably make your wireless work too, if you're interested.

I just wanted to confirm this works on my friend's Dell Inspiron with the following lspci
```
$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

This is what I ran: 
```
sudo aptitude update
sudo aptitude install build-essential
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2010-08-21.tar.bz2
tar -xjvf compat-wireless-*.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
sudo modprobe atl1c
```

And then it worked without rebooting.
[B]
THANK YOU![/B]

---

### Post by pytheas22 on 2010-08-22
altonbr: thanks for letting us know it worked :)  Hopefully in Ubuntu 10.10 this will all be sorted out out-of-the-box and no manual installation will be necessary.

(If any of you who own this hardware have tested Ubuntu 10.10 yet, please let us know your experience.)

---

### Post by homebound on 2010-08-24
I have **Toshiba Satellite L655-S5061** laptop. Both wired and wireless adapters don't work; wired adapter doesn't even show up on ifconfig.

I followed the steps mentioned here but still not working. This is what I did, as suggested in various parts in this thread:

[LIST=1]
[*]hookup a (netgear) wifi usb adapter
[*]perform a full system upgrade
[*]ifconfig only shows two interfaces: loopback and wifi
[*]ran through the steps outlined earlier and shown below:
[/LIST]

[LIST]
[*] sudo apt-get update
[*] sudo apt-get install build-essential
[*] cd ~/Desktop
[*] tar -xjvf compat-wireless-2.6.tar.bz2
[*] cd compat-wireless*
[*] scripts/driver-select atl1c
[*] make
[*] sudo make install
[/LIST]

[LIST=1]
[*]reboot
[*]"lshw -c Network" shows
[*] *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
[*]ifconfig shows
[*]vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[*]So I enabled it ifconfig vboxnet0 up
[*]i rebooted and the adapter became DISABLED again
[*]I re-enabled it but the wired link still not work.
[/LIST]

Any help is appreciated.

Btw, how do you insert textboxes???? I tried to put the output in one of them but couldn't figure it out.

Thank you
Michael

---

### Post by pytheas22 on 2010-08-24
> I have Toshiba Satellite L655-S5061 laptop. Both wired and wireless adapters don't work; wired adapter doesn't even show up on ifconfig.

Could you please post the output of:
```

lspci -nn
```

so we can see exactly which type of ethernet chipset you have?  I'm guessing yours is different than the ones dealt with earlier in this thread.

The vobxnet0 interface is for VMware or VirtualBox, not your actual ethernet hardware.  That will most likely come up as eth0.

As for creating the text boxes for code, you just insert the code, highlight it and press the button with a # symbol on it in the list of tools directly above the box where you enter text.  Alternatively, you can manually apply the code tags as below:

[html]```
code here
```[/html]

---

### Post by homebound on 2010-08-24
Hi pytheas22,

Thank you for the help.

```

user@bibi:~$ lsb_release -d
Description:    Ubuntu 10.04.1 LTS
user@bibi:~$ uname -mr
2.6.32-24-generic i686
user@bibi:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]
00:01.0 PCI bridge [0604]: Toshiba America Info Systems Device [1179:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 41)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:15.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a0]
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
user@bibi:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2464 (2.4 KB)  TX bytes:2464 (2.4 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 20:7c:8f:0d:ad:3f  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::227c:8fff:fe0d:ad3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2308 (2.3 KB)
          Interrupt:16 Memory:f8768000-f8768100 

wlan1     Link encap:Ethernet  HWaddr c0:3f:0e:3f:a7:5a  
          inet addr:10.50.202.29  Bcast:10.50.203.255  Mask:255.255.254.0
          inet6 addr: fe80::c23f:eff:fe3f:a75a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:235016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:330877098 (330.8 MB)  TX bytes:12628963 (12.6 MB)

user@bibi:~$ iwconfig
lo        no wireless extensions.

wlan0     802.11bg  ESSID:"eaglerising"  Nickname:"rtl8191SEVA2"
          Mode:Ad-Hoc  Frequency=2.457 GHz  Cell: 22:87:52:BF:42:57   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID:"SFHQ"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:6C:AE:71:61   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

user@bibi:~$ lsmod
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          2271  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46926  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4413  1 nf_nat_pptp
nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             4414  1 
nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_conntrack           61583  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  2 iptable_filter,iptable_nat
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
michael_mic             1732  4 
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6326  0 
vboxnetflt             15280  0 
vboxdrv               190594  2 vboxnetadp,vboxnetflt
snd_hda_intel          21941  2 
snd_hda_codec          74201  1 snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
arc4                    1153  4 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
fbcon                  35102  71 
tileblit                2031  1 fbcon
joydev                  8708  0 
rtl8187                50680  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
font                    7557  1 fbcon
fglrx                2092908  31 
bitblit                 4707  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
softcursor              1189  1 bitblit
agpgart                31724  1 fglrx
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205146  1 rtl8187
vga16fb                11385  1 
snd                    54148  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               56990  0 
soundcore               6620  1 snd
led_class               2864  1 rtl8187
videodev               34361  1 uvcvideo
vgastate                8961  1 vga16fb
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63245  0 
cfg80211              126517  2 rtl8187,mac80211
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
shpchp                 28820  0 
r8192se_pci           447966  0 
eeprom_93cx6            1333  1 rtl8187
i2c_piix4               8335  0 
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39425  0 
ahci                   32200  2 
user@bibi:~$ lshw -c Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 20:7c:8f:0d:ad:3f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=10.42.43.1 latency=0 multicast=yes wireless=802.11bg
       resources: irq:16 ioport:6000(size=256) memory:f3000000-f3003fff
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: c0:3f:0e:3f:a7:5a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.50.202.29 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
user@bibi:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

wlan1     Scan completed :
          Cell 01 - Address: 00:24:6C:AE:71:61
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"SFHQ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013e02b1057
                    Extra: Last beacon: 4996ms ago
                    IE: Unknown: 000453464851
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B000000FF000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B000000FF000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A00037F04010000000000

vboxnet0  Interface doesn't support scanning.

user@bibi:~$ 



```

---

### Post by hungh3 on 2010-08-24
Just wanna say thank you to [pytheas22]("http://ubuntuforums.org/member.php?u=358340") for the very valuable help in your first page. With your instructions to *rbisawa*, I was also able to get both my Ethernet and wireless up and working. 

I believe some time soon, manufacturers (such as Dell, in my case) would feel a need to put a label like "Ubuntu lucid lynx ready" in the sense that all necessary drivers for the hardware, if not already supported by Ubuntu, must be provided out-of-the-box by that manufacturer :D. 

Again, appreciate your kind help, pytheas22.

---

### Post by pytheas22 on 2010-08-24
**homebound**: strangely, your lspci -nn output doesn't mention any devices that look like ethernet cards.  These should always be listed by lspci, even if the operating system has no driver available to control them.  In your case, however, the only network device described in a Realtek wireless card.

If lspci fails to detect a device, it usually indicates a hardware problem.  Is your ethernet card disabled in your BIOS?  If you have any other operating systems installed on this computer, do they detect the ethernet?

It looks like you now have your internal wireless is now working, correct?
[B]
hungh3[/B]: glad it helped you out, and thanks for the feedback :)

---

### Post by Rodog on 2010-08-25
Hi,

I have a problem too with my internet connection, im using the USB Live mode. I have a Dell Laptop N4010.

Using the lastest version of Ubuntu, it doesn't recognize the Wireless networks, also if I connect the ethernet cable just nothing happers, Ubuntu don't recognize it neither, I have a notificacion in the bar that says that I can install a new driver but it ask for download, but I can't, no internet.

It's the driver

Broadcom STA wireless driver

I just have followed the steps of the first page without luck.



Output

```

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

```Can someone help me please? :(

---

### Post by homebound on 2010-08-25
From Pytheas22

>  If lspci fails to detect a device, it usually indicates a hardware  problem.  Is your ethernet card disabled in your BIOS?  If you have any  other operating systems installed on this computer, do they detect the  ethernet?You are amazing. That was the problem. I had asked someone to help me troubleshoot the problem before finding this thread and he apparently disabled the adapter. 

Now, both wire and wireless adapters are working. **You are terrific.**

Thank you
Michael

---

### Post by pytheas22 on 2010-08-25
**Rodog**: your situation is a bit tricky, but I think we should be able to solve it if you can provide just a bit more information.  Can you tell me what the output is if you open a terminal on your Ubuntu computer and type:
```

uname -a
lshw -C Network
```

You can save this output to a text file and transfer that file to a computer where you have Internet access.

With this information, we should be able to get the STA driver working, so you'll have wireless.  We can fix the ethernet after that if you want wired as well (but I assume wireless is most useful to you).

**Michael**: glad to hear that solved it :)  Enjoy Ubuntu!

---

### Post by mike909 on 2010-08-26
Rodog,
Same thing here. I have the same Dell N4010 and Hardware drivers reports "Broadcom STA wireless driver" available. Here's what I did to get it to work:
*try to activate driver, and then selectively install each .deb it complains about not being able to find using "gdebi", the visual package installer. I did this by just manually browsing the ubuntu install CD for the files it complains about not finding. (I couldn't get the CD repository to be used.) After about the third file, you select "activate", and the button goes green (driver in use) and wireless works.
*then sudo apt-get update, and sudo apt-get upgrade. Everything works fine on latest kernal with all updates.
*then I followed the steps on page one to get wired working, and it borked my wireless, but it did get my wired working. (now I have wired, but no wireless). 
*Tried to "sudo modprobe wl" but get error inserting wl. dmesg shows: "wl: disagrees about version of symbol lib80211_get_crypto_ops wl: Unknown symbol lib80211_get_crypto_ops"
Also the "hardware drivers" page shows the STA driver as "this driver is activated but not currently in use". I tried removing/re-adding but that didn't change anything.
lshw -C Network before the compat wireless driver install showed "driver=wl0" but not after.
So I started with neither wired or wireless, then got wireless, then got wired, but lost wireless. Going to try and poke at it again tomorrow.

---

### Post by mike909 on 2010-08-26
*tried sudo apt-get --reinstall install bcmwl-kernel-source to reinstall the bcmwl driver but that didn't work
tried to follow the broadcom readme (after downloading latest broadcom driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) ) and followed the readme at [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) which specifically mentions the error messages I get when I try to "insmod wl.ko", but their solution of:
# modprobe   lib80211 
    or 
# modprobe ieee80211_crypt_tkip
    and then re-try to insmod the wl driver.
  # insmod wl.ko
Doesn't work. 
*So now I'm thinking of re-installing ubuntu, and getting wireless working with the STA driver, and then trying to get wired working in a different manner (not using the compat-wireless package).
Open to ideas.

---

### Post by pytheas22 on 2010-08-26
> *So now I'm thinking of re-installing ubuntu, and getting wireless working with the STA driver, and then trying to get wired working in a different manner (not using the compat-wireless package).

That's what I'd do.

I don't have any of this hardware myself, but my suggestion would be to get the wireless working using the STA driver, then try driving the ethernet using ndiswrapper (usually ndiswrapper is used for wireless cards but it should work equally well for ethernet devices).

I'm pretty sure the overall issue is that when you compile compat-wireless, it rebuilds your lib80211.ko module, among others.  The version of lib80211.ko that compat-wireless wants to use is incompatible with the STA driver for some reason.  So the STA driver and compat-wireless simply can't coexist happily.

In contrast, the STA driver and ndiswrapper should get along, because neither of them modifies the stock lib80211.ko modules that ships with your system.  By using ndiswrapper instead of compat-wireless, you will ensure that all of the modules on which the STA driver depends are left intact.  As a bonus, you will not have to worry about recompiling compat-wireless each time you upgrade your kernel.

You seem to know what you're doing but if you need more specific instructions on how to get ndiswrapper set up for your ethernet card, let me know.

---

### Post by marconbr on 2010-08-27
Hi,

I've been facing problems with my wired internet connection. I have a dell 1318 laptop with broadcom internet card and an Ubuntu 10.04 64 bit installed with a Windows Vista boot. My wireless internet connection works fine, but the auto eth0 connection in Ubuntu isn't working - in the connection tab it is shown as not managed. It can be discarded any bios issues (I guess) since both wired and wireless connections work in the windows boot.
Here goes the uname -a and the lshw -class network

```

#uname -a
Linux ******* 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux

#lshw -class network
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 03
       serial: 00:24:2b:bb:8c:0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.104 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f6cfc000-f6cfffff memory:f0000000-f00fffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:23:ae:28:1e:b5
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=sb v3.04 latency=0 link=yes multicast=yes port=twisted pair
       resources: irq:17 memory:f69f0000-f69fffff

```

Even after using the "ifconfig eth0 up", so changing the above wired network status to enabled, still I don't have any wired connection.

Thanks in advance and I hope anybody can help me.

---

### Post by mike909 on 2010-08-27
> **pytheas22 said:**
> my suggestion would be to get the wireless working using the STA driver, then try driving the ethernet using ndiswrapper (usually ndiswrapper is used for wireless cards but it should work equally well for ethernet devices).

Pytheas,
I'm thinking of ndiswrapper as a "last resort". What I'd like to try first is the following official driver from atheros:
[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)
also, not exactly sure how to use the following, but looks like someone did some work already to get this working:
[http://www.at.kernel.org/pub/linux/kernel/people/mcgrof/ethernet/](http://www.at.kernel.org/pub/linux/kernel/people/mcgrof/ethernet/)

Will post back with my results.

---

### Post by pytheas22 on 2010-08-27
**marconbr**: if you type:

sudo ifconfig eth0 up
sudo dhclient eth0

with the ethernet plugged in, do you get a connection?  If you do, the second command ("sudo dhclient eth0" will tell you you have been granted an IP address).  This assumes your wired network uses dhcp to assign address dynamically.

If dhclient doesn't get you an address, what is the output of:
```

dmesg | grep -e tg3 -e ssb -e eth0
```
[B]
mike909[/B]: I agree that a native driver would be preferable to ndiswrapper--I didn't realize any existed for this device that didn't require installing the whole compat-wireless stack.

I imagine either the driver from Atheros or the one from [http://www.at.kernel.org/pub/linux/kernel/people/mcgrof/ethernet/](http://www.at.kernel.org/pub/linux/kernel/people/mcgrof/ethernet/) would work.  I just did a quick installation of the latter (just wanted to see if it would compile) and it built and installed fine by running:
```

wget http://www.at.kernel.org/pub/linux/kernel/people/mcgrof/ethernet/AR81Family-linux-v1.0.1.6.tar.bz2
tar -xjvf AR81*
make
sudo make install
```

I now have a module named atl1e that says it supports your ethernet device, according to "modinfo atl1e".

---

### Post by mike909 on 2010-08-27
> **pytheas22 said:**
> 
I now have a module named atl1e that says it supports your ethernet device, according to "modino atl1e".
Cool, definitely going to try it as soon as possible and report back. Hopefully this will be tonight. Thanks for looking at that for me.

---

### Post by JamieWrites on 2010-08-27
Just a quick question before I go back to where the solutions were posted and I try those out - my problem is that my ethernet worked at first, but then when I used the USB connection to my router (I've only got one ethernet connection and it usually goes into my desktop PC) the next time I tried the ethernet connection it didn't work.

Is that the same problem or a different problem? I couldn't find a solution on the search forums for that specific issue, and no-one responded to the thread I started - so apologies if I'm hijacking with an unrelated issue.

Cheers,

Jamie

---

### Post by marconbr on 2010-08-27
Thanks for the reply, pytheas22.

Well, after typing

sudo ifconfig eth0 up

It doesn't apear to happen anything, and still no signal of the wired connection. Even if turn off the wireless connection I won't get the wired connection.

So, when I type
 
sudo dhclient eth0

I get:
```

There is already a pid file /var/run/dhclient.pid with pid 2147
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:23:ae:28:1e:b5
Sending on   LPF/eth0/00:23:ae:28:1e:b5
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.170 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.170 from 192.168.0.1
bound to 192.168.0.170 -- renewal in 472060 seconds.

```

and when I type:

dmesg | grep -e tg3 -e ssb -e eth0

I get
```

[    0.848346] tg3.c:v3.102 (September 1, 2009)
[    0.848381] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.848396] tg3 0000:09:00.0: setting latency timer to 64
[    1.671847] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:23:ae:28:1e:b5
[    1.671851] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
[    1.671854] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.671856] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[  703.356945] tg3 0000:09:00.0: irq 30 for MSI/MSI-X
[  703.389949] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  705.254779] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  705.254785] tg3: eth0: Flow control is on for TX and on for RX.
[  705.255657] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  715.880120] eth0: no IPv6 routers present
[  725.560293] bridge-eth0: up
[  725.560299] bridge-eth0: attached
[  793.173902] tg3: eth0: Link is down.
[  793.223570] bridge-eth0: disabling the bridge
[  793.260133] bridge-eth0: down
[  793.260144] bridge-eth0: detached
[  871.623448] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  871.623453] tg3: eth0: Flow control is on for TX and on for RX.
[  871.650350] bridge-eth0: up
[  871.650357] bridge-eth0: attached
[ 1135.088199] bridge-eth0: disabling the bridge
[ 1135.100064] bridge-eth0: down
[ 1135.100075] bridge-eth0: detached
[ 1246.112804] bridge-eth0: up
[ 1246.112810] bridge-eth0: attached

```

---

### Post by pytheas22 on 2010-08-27
> Just a quick question before I go back to where the solutions were posted and I try those out - my problem is that my ethernet worked at first, but then when I used the USB connection to my router (I've only got one ethernet connection and it usually goes into my desktop PC) the next time I tried the ethernet connection it didn't work.

Is that the same problem or a different problem? I couldn't find a solution on the search forums for that specific issue, and no-one responded to the thread I started - so apologies if I'm hijacking with an unrelated issue.

That sounds like a different problem.  Please start a new thread, let me know the URL and I'll reply there.
[B]
marconbr[/B]: the command "sudo dhclient eth0" got you an IP address, which is good--this means your driver and interface are working.

Your dmesg mentions an ethernet bridge.  I have no idea where that came from, but I'm wondering if you accidentally created a bridge which is causing routing problems and preventing you from accessing the Internet, even though you're connected.  What is the output of:
```

ifconfig
ifconfig -a
route
```

---

### Post by marconbr on 2010-08-28
Well, I remember I couldn't use the wireless connection when I did the upgrade to Lucid, so this bridge may habe been created when I did some fix - but I'm not so sure now.

Here goes the outputs :

ifconfig
```

eth1      Link encap:Ethernet  HWaddr 00:24:2b:bb:8c:0c  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:febb:8c0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4082 errors:0 dropped:0 overruns:0 frame:3409
          TX packets:3697 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4129377 (4.1 MB)  TX bytes:612169 (612.1 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1610687 (1.6 MB)  TX bytes:1610687 (1.6 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.13.1  Bcast:172.16.13.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.37.1  Bcast:192.168.37.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:23:ae:28:1e:b5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:bb:8c:0c  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:febb:8c0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4156 errors:0 dropped:0 overruns:0 frame:3527
          TX packets:3773 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4186277 (4.1 MB)  TX bytes:625453 (625.4 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1718608 (1.7 MB)  TX bytes:1718608 (1.7 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.13.1  Bcast:172.16.13.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.37.1  Bcast:192.168.37.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

route
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.37.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.0.0     *               255.255.255.0   U     2      0        0 eth1
172.16.13.0     *               255.255.255.0   U     0      0        0 vmnet1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

```

---

### Post by mike909 on 2010-08-28
Ok, well in regard to the N4010 network adapter issues:
The good: The official atheros drivers work great for the wired lan connection (AR8152). Note, the modified ones do not work (I can provide more detail on why those ones fail on request).
The Bad: fresh install of Ubuntu 10.04.1 I can't get wireless (bcm 4727) to work. I've tried the STA driver that comes w/ ubuntu, and I've also tried the broadcom ones from: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
Both have the same result, the install completes and it appears to function (lshw shows it working with wl1 for STA, or wl0 with broadcom drivers) but I can't actually connect to any wireless networks. Network manager doesn't show any available, and manually trying to onnect doesn't work. iwlist <int> scan doesn't work either (eth0 failed to read scan data : invalid argument )
So, in conclusion I can get wired working with official Atheros driver, no problem, but can't get wireless working. 
Worst part about this, I had wireless working fine before, no idea what's changed (maybe going to install 10.04?)

EDIT: ok, you need to disable the toggle switch for wlan in the BIOS. Going to try and make a new post detailing exactly what to do for everyone owning one of these laptops or a laptop with one of these NIC's.

---

### Post by mike909 on 2010-08-28
Ok, so for all owners of this N4010 here's how to get both wired & wireless working:
lspci showing: broadcom corporation device 4727 (rev 01)
		Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
---Wireless-------: 
1. Disable the wlan toggle switch in BIOS
2. Enable the STA drivers via ubuntu "restricted drivers" (system-->administration-->Hardware Drivers)
Note: if you don't do the Wired NIC first, you'll need to browse the ubuntu cd manually for the packages that it complains about not finding. You can just double click them and let GDebi install them for you (there are just 3 of them)
3.restart
-----Wired------:
1. Download official Atheros driver, from their website: [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (file: AR81Family-linux-v1.0.1.9.tar.gz)
2. tar -xvf AR*
3. make
4. sudo make install
5. restart

Done.
NOTE: you will not need to re-install wireless drivers with each kernel update, but you WILL need to do that for the wired nic (just make/make install again).

---

### Post by pytheas22 on 2010-08-28
**mike909**: glad you figured it out and thanks for explaining what you did.  Being able to install just the Atheros driver, without compat-wireless, should make this a lot easier for everyone affected.  Hopefully in the next release of Ubuntu this ethernet chip will be supported out-of-the-box.

**marconbr**: I'm not positive what's wrong, as it doesn't actually look like you have any bridged interfaces.  Would you mind please disabling your wireless, then running the following commands (in this order) and posting the output:
```

ifconfig
sudo dhclient eth0
ping -c 3 192.168.0.1
ping -c 3 google.com
dmseg | grep -e eth
lshw -C Network
sudo ethtool eth0
```

Before running these commands, you should also install the package ethtool by running:

```
sudo apt-get install ethtool
```

Hopefully these commands will provide a better clue as to what's wrong.  It's possible something strange is going on with your virtual interfaces, vmnet1 and vmnet8, or that something's wrong with your ethernet driver.

---

### Post by JamieWrites on 2010-08-28
> **pytheas22 said:**
> That sounds like a different problem.  Please start a new thread, let me know the URL and I'll reply there.

Thanks, the thread I began was [http://ubuntuforums.org/showthread.php?p=9513085#post9513085](http://ubuntuforums.org/showthread.php?p=9513085#post9513085)

Cheers,

Jamie

---

### Post by marconbr on 2010-08-28
Thanks for all the efforts, pytheas22. After typing the sequence of commands you asked me the wired connection was apparently reestablished. Anyway, I'm posting down the outputs you asked me, as they might be useful: 

ifconfig
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19811 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3504343 (3.5 MB)  TX bytes:3504343 (3.5 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.13.1  Bcast:172.16.13.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.37.1  Bcast:192.168.37.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

sudo dhclient eth0
```

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:23:ae:28:1e:b5
Sending on   LPF/eth0/00:23:ae:28:1e:b5
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.170 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.170 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.170 from 192.168.0.1
bound to 192.168.0.170 -- renewal in 502363 seconds.

```

ping -c 3 192.168.0.1
```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.391 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.402 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.398 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.391/0.397/0.402/0.004 ms

```

ping -c 3 google.com
```

PING google.com (64.233.163.104) 56(84) bytes of data.
64 bytes from bs-in-f104.1e100.net (64.233.163.104): icmp_seq=1 ttl=57 time=13.4 ms
64 bytes from bs-in-f104.1e100.net (64.233.163.104): icmp_seq=2 ttl=57 time=10.9 ms
64 bytes from bs-in-f104.1e100.net (64.233.163.104): icmp_seq=3 ttl=57 time=10.1 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 10.162/11.515/13.468/1.419 ms

```

dmesg | grep -e eth
```

[    1.661835] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:23:ae:28:1e:b5
[    1.661839] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
[    1.661842] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.661844] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   13.732407] eth1: Broadcom BCM4328 802.11 Hybrid Wireless Controller 5.60.48.36 
[   56.260224] eth1: no IPv6 routers present
[  177.354040] bridge-eth1: is a Wireless Adapter
[  177.354046] bridge-eth1: up
[  177.354051] bridge-eth1: attached
[ 6227.341127] bridge-eth1: disabling the bridge
[ 6227.380099] bridge-eth1: down
[ 6227.380112] bridge-eth1: detached
[ 6377.722945] bridge-eth0: up
[ 6377.724003] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6377.753671] bridge-eth0: attached
[ 6377.753765] bridge-eth0: disabling the bridge
[ 6377.782673] bridge-eth0: down
[ 6377.782682] bridge-eth0: detached
[ 6379.354599] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 6379.354604] tg3: eth0: Flow control is on for TX and on for RX.
[ 6379.355425] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 6379.355684] bridge-eth0: up
[ 6379.355689] bridge-eth0: attached
[ 6389.360052] eth0: no IPv6 routers present

```

lshw -C Network
```

WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 03
       serial: 00:24:2b:bb:8c:0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f6cfc000-f6cfffff memory:f0000000-f00fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:23:ae:28:1e:b5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v3.04 ip=192.168.0.170 latency=0 multicast=yes
       resources: irq:30 memory:f69f0000-f69fffff

```

sudo ethtool eth0
```

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: g
    Wake-on: d
    Current message level: 0x000000ff (255)
    Link detected: yes

```

Thanks again!!

---

### Post by vampcheah on 2010-08-29
hi all, 
i just bought a new laptop (toshiba satellite L655).
but i found that the wifi and wired connection totally can't work.


cat /etc/network/interfaces 
```

auto lo
iface lo inet loopback

```

cat /etc/NetworkManager/nm-system-settings.conf 
```

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```


dmesg | grep -e eth0 -e bcm
```

[   10.878522] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   69.554158] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr c8:0a:a9:b7:8e:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:35 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36816 (36.8 KB)  TX bytes:36816 (36.8 KB)

```

---

### Post by pytheas22 on 2010-08-29
**marconbr**: I'm glad that helped, although I'm not positive why :)  None of the output you posted indicates anything strange or problematic.

If you reboot now, disable the wireless card and plug in the ethernet, does it still not work automatically?  If not, does it work if you type:

```
sudo ifconfig eth0 up
sudo dhclient eth0
```

Also, what is the output of:
```

cat /etc/NetworkManager/nm-system-settings.conf
```

**vampcheah**: your problem is probably different than that of the other posters here, because you at least have an ethernet interface detected.  This thread has also already become pretty long and convoluted, so would you mind please starting a new thread and letting me help you there?

In your new thread, please include the output of these commands, while your ethernet device is plugged in:
```

lspci -nn
lsusb
lshw -C Network
sudo dhclient eth0
```

Also, are you sure your network uses dhcp to assign address dynamically?  The fact that you have an ethernet interface detected but that it has no IP address makes me suspect that you may need to set the IP address statically.

---

### Post by vampcheah on 2010-08-29
thanks for reply, i creating a thread here.
[http://ubuntuforums.org/showthread.php?p=9780759#post9780759](http://ubuntuforums.org/showthread.php?p=9780759#post9780759)

i got another 2 pc and 1 laptop were connected to same network (router), all of them using dhcp to get ip.

---

### Post by marconbr on 2010-08-31
Hey pytheas22, you've anticipated me! :) After rebooting my laptop the wired connection went down - fortunately the two commands you suggested worked and I could reconnect again.

Here is the output you asked:
cat /etc/NetworkManager/nm-system-settings.conf
```

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

---

### Post by pytheas22 on 2010-08-31
> Hey pytheas22, you've anticipated me!  After rebooting my laptop the wired connection went down - fortunately the two commands you suggested worked and I could reconnect again.

Hmmm, that's a bit strange, but at least you know how to make it work.  Just one last question: if you type just:
```

sudo ifconfig eth0 up
```

are you then able to connect using the NetworkManager applet in the upper-right part of your screen?  (You may need to right-click on the applet and select "Enable Networking.")

If you let me know how this goes, I'll tell you how to write a script to bring up the interface automatically when you turn on the computer, so it should "just work."

---

### Post by mgastelum on 2010-08-31
> **pytheas22 said:**
> Your ethernet hardware seems to be quite new and doesn't have a driver built into Ubuntu as of yet.  However, there's a driver included in the compat-wireless stack that you can use (I have no idea why they included an ethernet driver in compat-wireless, but according to [these emails]("http://omgili.com/mailinglist/kernel-team/lists/ubuntu/com/43e72e891002020915x572a11fcg57f0b9caf7ed08eamailgmailcom.html"), someone did).

To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking).  Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```

Then reboot.  Hopefully your ethernet will work automatically after reboot; if not, run:
```

sudo modprobe atl1c
```

to insert the driver.  Let me know how it goes.

We can probably make your wireless work too, if you're interested.


Hi, i have the same problem whit Atheros, i follow this steps, but when i type make the terminal show me this:


make -C /lib/modules/2.6.32-24-generic/build M=/home/chisus/Descargas/compat-wireless-2010-08-31 modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/chisus/Descargas/compat-wireless-2010-08-31/compat/main.o
In file included from /home/chisus/Descargas/compat-wireless-2010-08-31/include/linux/compat-2.6.h:10,
                 from <command-line>:0:
/home/chisus/Descargas/compat-wireless-2010-08-31/include/linux/compat_autoconf.h:1:1: error: unterminated #ifndef
make[3]: *** [/home/chisus/Descargas/compat-wireless-2010-08-31/compat/main.o] Error 1
make[2]: *** [/home/chisus/Descargas/compat-wireless-2010-08-31/compat] Error 2
make[1]: *** [_module_/home/chisus/Descargas/compat-wireless-2010-08-31] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [modules] Error 2


thanks for yours answers.

---

### Post by pytheas22 on 2010-09-01
> 

make -C /lib/modules/2.6.32-24-generic/build M=/home/chisus/Descargas/compat-wireless-2010-08-31 modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.32-24-generic'
CC [M] /home/chisus/Descargas/compat-wireless-2010-08-31/compat/main.o
In file included from /home/chisus/Descargas/compat-wireless-2010-08-31/include/linux/compat-2.6.h:10,
from <command-line>:0:
/home/chisus/Descargas/compat-wireless-2010-08-31/include/linux/compat_autoconf.h:1:1: error: unterminated #ifndef
make[3]: *** [/home/chisus/Descargas/compat-wireless-2010-08-31/compat/main.o] Error 1
make[2]: *** [/home/chisus/Descargas/compat-wireless-2010-08-31/compat] Error 2
make[1]: *** [_module_/home/chisus/Descargas/compat-wireless-2010-08-31] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.32-24-generic'

This looks like a problem with the compat-wireless source code.  You probably work around it by downloading an earlier version of the code from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

Another, probably better solution is to install the ethernet driver using the instructions in post 88 of this thread, namely:
> 
1. Download official Atheros driver, from their website: [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)  (file: AR81Family-linux-v1.0.1.9.tar.gz).  Save it to your desktop
2. cd ~/Desktop; tar -xvf AR*
3. make
4. sudo make install
5. restart

---

### Post by mike909 on 2010-09-01
> **mgastelum said:**
> Hi, i have the same problem whit Atheros, 
I havn't been keeping up with this thread (trying to hash out all other hardware issues with the Dell N4010 --almost there--), but as Pytheas suggested, if you have the same Atheros NIC, then follow post 88, then post your output of "lshw -C Network" here.

---

### Post by marconbr on 2010-09-02
> **pytheas22 said:**
> Hmmm, that's a bit strange, but at least you know how to make it work.  Just one last question: if you type just:
```

sudo ifconfig eth0 up
```are you then able to connect using the NetworkManager applet in the upper-right part of your screen?  (You may need to right-click on the applet and select "Enable Networking.")

If you let me know how this goes, I'll tell you how to write a script to bring up the interface automatically when you turn on the computer, so it should "just work."

No, just typing ```
 sudo ifconfig eth0 up 
``` didn't worked with the Network Manager applet - I still had to type ```
 sudo dhclient eth0 
``` to get the wired connection.

---

### Post by pytheas22 on 2010-09-02
> No, just typing
Code:

 sudo ifconfig eth0 up

didn't worked with the Network Manager applet - I still had to type
Code:

 sudo dhclient eth0

to get the wired connection.

Thanks for that information.  To create a script that will run those two commands automatically whenever your computer boots, type these commands:
```

sudo -s
gedit /etc/init.d/eth0-up.sh
```

A file will open.  Paste these lines into it:

```
#!/bin/bash

ifconfig eth0 up
dhclient eth0
```

Then save and close the file, and finish by typing:
```

chmod +x eth0-up.sh
update-rc.d eth0-up.sh defaults
```

Now the commands that you need to get the ethernet working should be run automatically each time your computer boots.  Let me know if you have trouble.

---

### Post by NetGeir on 2010-09-03
Hello,

Yesterday I installed Ubuntu on my Acer Aspire 4820TG and that completed without errors. Then I was checking my wireless, and it did not find any. I have looked in this thread, and that helped a little. 

Like I said, I don't have wireless-connection, and therefor I need to install my wireless driver offline. I have placed b43-fwcutter in the right map, and in "Admin -> Synaptic Package Manager -> Settings -> Repositories" I have checked the "Restricted copyright" on the bottom og that site. 

Then I can go into "Hardware Drivers" and there I find one driver: "Broadcom STA wireles driver". Thats probably the one I have to install. When I click "Activate" I got an error:
```
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS_Lucid 
Lynx_ - Release amd64  (20100816)]/pool/main/p/
patch/patch_2.6-2ubuntu1_amd64.deb File not found.
```

How can I fix this?

Thanks for answers!

---

### Post by pytheas22 on 2010-09-03
**NetGeir**: the driver you need should be on the Ubuntu installation CD (assuming you used a CD to install).  You first need to [enable your CD as a software repository]("https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD"), then try installing the driver again by clicking "Activate" in Hardware Drivers.  If you have trouble, please let me know.

---

### Post by Srikant.M on 2010-09-04
Thanks to all,
With this Forum i resolved my Ethernet problem with "Etheros Communications AR8152 v1.1 Ethernet(rev c1)"  in Ubuntu
With the help a mobile broadband connection we got all the dependencies by following this process.

:DThanks a lot again.:D):P


> **pytheas22 said:**
> Your ethernet hardware seems to be quite new and doesn't have a driver built into Ubuntu as of yet.  However, there's a driver included in the compat-wireless stack that you can use (I have no idea why they included an ethernet driver in compat-wireless, but according to [these emails]("http://omgili.com/mailinglist/kernel-team/lists/ubuntu/com/43e72e891002020915x572a11fcg57f0b9caf7ed08eamailgmailcom.html"), someone did).

To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking).  Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```Then reboot.  Hopefully your ethernet will work automatically after reboot; if not, run:
```

sudo modprobe atl1c
```to insert the driver.  Let me know how it goes.

We can probably make your wireless work too, if you're interested.



HI all

---

### Post by NetGeir on 2010-09-04
pytheas22: That's what I did, maybe I didn't explane it god enought. And when I do that, I get the error like i sayd:

```
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS_Lucid 
Lynx_ - Release amd64  (20100816)]/pool/main/p/
patch/patch_2.6-2ubuntu1_amd64.deb File not found.
```

The installations CD is in, but the files can't be found.

If you want me to check some code in terminal, just let me know.

---

### Post by pytheas22 on 2010-09-04
**NetGeir**: ah, I understand now.  That is a bit strange.  If you open up your CD to browse the files, can you navigate to the folder ...pool/main/p/patch/?  Do you see a file there named patch_2.6-2ubuntu1_amd64.deb and if so can you install it by double-clicking?

If that works, try also going to ...pool/main/g and installing the gcc package, and ...pool/main/m and installing make.  Then, go to ...pool/restricted/b and look for packages whose names begin with "bcmwl" and install them.

If this all works, it will get the wireless driver installed for you automatically.  If it fails, however, let me know and we'll see about installing it a different way.  In that case, it would be helpful to know the output of:
```

uname -a
lshw -C Network
lspci -nn
```

---

### Post by NetGeir on 2010-09-04
Hi again,

patch_2.6-2ubuntu1_amd64.deb was finish without errors:
[IMG]http://i55.tinypic.com/a2xctu.png[/IMG]

I find every file in the folders exept the "make". 

When I try to install the gcc package it say that it could not install booth of the files. I guess thats because Ubuntu is looking for the second file on the internet, and not in the folder the other file are in:
[IMG]http://i56.tinypic.com/fdaijm.png[/IMG]
[IMG]http://i56.tinypic.com/2afbh92.png[/IMG]

Here is the output of the code:
```
sondre@sondre-laptop:~$ uname -a
Linux sondre-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

sondre@sondre-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:db400000-db43ffff ioport:2000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:da400000-da403fff

sondre@sondre-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 18)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
02:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)
7f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
7f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
7f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
7f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
7f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
7f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
```

---

### Post by pytheas22 on 2010-09-05
**NetGeir**: can you find the packages 'fakeroot' or 'dkms' on your CD as well?  They should be there, I think.  If you install them, you should then be able to install 'gcc' without it having to download packages from the Internet.

If this doesn't work, let me know and we can try to get the driver installed another way, but it will be tricky.

---

### Post by NetGeir on 2010-09-05
Fakeroot and dkms has been installed, but when I try to install gcc, I get the same error. It will not install the second file from the folder, but it will try to install it from the network:

[IMG]http://i52.tinypic.com/eq4ktd.png[/IMG]

I will try anything to get the network, 'cause I really like Ubuntu. Thank you for helping me.

---

### Post by pytheas22 on 2010-09-05
**NetGeir**: I'm not sure why that's happening when you try to install gcc, but let's try a different strategy.  I compiled an ethernet driver that should work on your system, using the source code from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx).  To install it, first download the file [http://burnthesorbonne.com/files/AR81.tar.gz](http://burnthesorbonne.com/files/AR81.tar.gz) and transfer it to your Ubuntu computer.  Save it on the desktop there.  Then run these commands (if this doesn't work as expected, please post all output so I can see what might have gone wrong):

```
cd ~/Desktop
tar -xzvf AR81.tar.gz
cd AR81
sudo cp src/atl1e.ko /lib/modules/2.6.32-24-generic/kernel/drivers/net/atl1e/
sudo insmod /lib/modules/2.6.32-24-generic/kernel/drivers/net/atl1e/atl1e.ko
sudo ifconfig eth0 up
```

At this point, your ethernet should work and you should be able to connect if you plug it in.  If you get this far, you should then be able to get the wireless to work by running:
```

sudo apt-get update
sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
```

It will be able to download the files it needs from the Internet, since wacky things seem to be happening with the CD.

Let me know how this goes.  If the ethernet doesn't work, please post the output of all of the commands from the first set above, along with:
```

dmesg | grep -e atl -e eth
lshw -C Network
lsmod | grep atl
```

---

### Post by NetGeir on 2010-09-06
Okei, this is strange. I did what you say, and then I was finish with "sudo ifconfig eth0 up", I could use the internet. Then I installed the wireless-driver, and had to reboot the computer.

When I then again came in to the "Ubuntu-startup-screen", and after that it all is black. I can't to anything! 

It seemed to work, but now it wouldn't startup.

Here is the output that I copied when I was finish install the driver. I don't think you need that though:
```
sondre@sondre-laptop:~$ cd ~/Skrivebord
sondre@sondre-laptop:~/Skrivebord$ cd AR81
sondre@sondre-laptop:~/Skrivebord/AR81$ sudo cp src/atl1e.ko /lib/modules/2.6.32-24-generic/kernel/drivers/net/atl1e/
[sudo] password for sondre: 
sondre@sondre-laptop:~/Skrivebord/AR81$ sudo insmod /lib/modules/2.6.32-24-generic/kernel/drivers/net/atl1e/atl1e.ko
sondre@sondre-laptop:~/Skrivebord/AR81$ sudo ifconfig eth0 up
sondre@sondre-laptop:~/Skrivebord/AR81$ sudo apt-get update
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/ lucid/main Translation-nb
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/ lucid/restricted Translation-nb
Funnet http://no.archive.ubuntu.com lucid Release.gpg                          
Funnet http://no.archive.ubuntu.com/ubuntu/ lucid/main Translation-nb          
Funnet http://no.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-nb
Ign http://no.archive.ubuntu.com/ubuntu/ lucid/universe Translation-nb         
Funnet http://no.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-nb    
Funnet http://no.archive.ubuntu.com lucid-updates Release.gpg                  
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-nb 
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-nb
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-nb 
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-nb
Funnet http://no.archive.ubuntu.com lucid Release                              
Funnet http://no.archive.ubuntu.com lucid-updates Release                      
Funnet http://no.archive.ubuntu.com lucid/main Packages                        
Funnet http://no.archive.ubuntu.com lucid/restricted Packages          
Funnet http://no.archive.ubuntu.com lucid/main Sources                 
Funnet http://no.archive.ubuntu.com lucid/restricted Sources           
Funnet http://no.archive.ubuntu.com lucid/universe Packages            
Funnet http://no.archive.ubuntu.com lucid/universe Sources
Funnet http://no.archive.ubuntu.com lucid/multiverse Packages          
Funnet http://no.archive.ubuntu.com lucid/multiverse Sources           
Funnet http://no.archive.ubuntu.com lucid-updates/main Packages
Funnet http://no.archive.ubuntu.com lucid-updates/restricted Packages  
Funnet http://no.archive.ubuntu.com lucid-updates/main Sources         
Funnet http://no.archive.ubuntu.com lucid-updates/restricted Sources   
Funnet http://no.archive.ubuntu.com lucid-updates/universe Packages    
Funnet http://no.archive.ubuntu.com lucid-updates/universe Sources     
Funnet http://no.archive.ubuntu.com lucid-updates/multiverse Packages  
Funnet http://no.archive.ubuntu.com lucid-updates/multiverse Sources   
Funnet http://security.ubuntu.com lucid-security Release.gpg           
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-nb
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-nb
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-nb
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-nb
Funnet http://security.ubuntu.com lucid-security Release
Funnet http://security.ubuntu.com lucid-security/main Packages
Funnet http://security.ubuntu.com lucid-security/restricted Packages
Funnet http://security.ubuntu.com lucid-security/main Sources
Funnet http://security.ubuntu.com lucid-security/restricted Sources
Funnet http://security.ubuntu.com lucid-security/universe Packages
Funnet http://security.ubuntu.com lucid-security/universe Sources
Funnet http://security.ubuntu.com lucid-security/multiverse Packages
Funnet http://security.ubuntu.com lucid-security/multiverse Sources
Leser pakkelister ... Ferdig
sondre@sondre-laptop:~/Skrivebord/AR81$ sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Leser tilstandsinformasjon ... Ferdig   
bcmwl-modaliases er allerede nyeste versjon.
Følgende NYE pakker vil bli installert:
  bcmwl-kernel-source
0 oppgraderte, 1 nylig installerte, 0 å fjerne og 32 ikke oppgradert.
1 pakker ikke fullt installert eller fjernet.
Må hente 0B/896kB med arkiver.
Etter denne operasjonen vil 2*867kB ekstra diskplass bli brukt.
Velger den tidligere fravalgte pakken bcmwl-kernel-source.
(Leser database ... 120715 filer og kataloger er installerte.)
Pakker ut bcmwl-kernel-source (fra .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb) ...
Setter opp b43-fwcutter (1:012-1build1) ...

Setter opp bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture x86_64
Building initial module for 2.6.32-24-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-24-generic/updates/dkms/

depmod......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Behandler utløsere for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
sondre@sondre-laptop:~/Skrivebord/AR81$ 
```

---

### Post by pytheas22 on 2010-09-06
**NetGeir**: there are a lot of reasons that may have happened and it's hard to know what's at fault without being able to boot the system and see some output.

Did you do anything else (such as apply updates) besides downloading the wireless driver, once you got an Internet connection?

Can you boot to a "recovery mode" prompt (on your Ubuntu boot menu, the second line should be a recovery mode)?  If you can get that far, we might be able to try to fix your system.

Otherwise, your only option might be to try reinstalling Ubuntu from scratch, then installing the Internet driver as you did before but without installing the wireless, and rebooting after that to make sure it's not the ethernet driver that's causing problems (it's unlikely that it is).

---

### Post by venkidwaraka on 2010-09-09
Hello,

I tried the method you specified in the first reply of this thread. Where I got stuck up was the selection of at11c driver. It said unsupported driver. Please help. I am ready with the results of all the commands you asked to execute in the previous replies

Here are they:


**[B]1)sudo ifconfig -a**[/B]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16080 (16.0 KB)  TX bytes:16080 (16.0 KB)

pan0      Link encap:Ethernet  HWaddr 72:e4:6a:a1:64:63  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
=================================================================
**2)lspci**
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
===========================================================================

**3)sudo ifup eth0**
Ignoring unknown interface eth0=eth0.

=================================================================

**4)cat /etc/network/interfaces**
auto lo
iface lo inet loopback

===========================================================================

**5)cat /etc/NetworkManager/nm-system-settings.conf **
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

=================================================================

**6)dmesg | grep -e eth0 -e bcm**
Output: Nothing

==========================================================================

**7)lshw -C Network**
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)

=====================================================================

**8)lspci -nn**
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)


Thanks..

---

### Post by venkidwaraka on 2010-09-09
Hello,

Please visit the link

[https://lists.ubuntu.com/archives/kernel-team/2010-February/008808.html]("https://lists.ubuntu.com/archives/kernel-team/2010-February/008808.html")
Hope that will fix the issue

Thanks

---

### Post by mike909 on 2010-09-09
venkidwaraka,
Have you tried the following steps? (also outlined in this thread)
[http://ubuntuforums.org/showthread.php?t=1569966](http://ubuntuforums.org/showthread.php?t=1569966)

---

### Post by pytheas22 on 2010-09-09
**venkidwaraka**: as mike909 points out, you can get both your wired and wireless interfaces working using that link.

Another solution is simply to reinstall Ubuntu using the 10.10 version, which you can download from [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/).  Ubuntu 10.10 is still in beta but should work reasonably well at this point.  It comes with a driver for your ethernet card preinstalled, so that will at least work--and once you have ethernet you can easily install the wireless driver by enabling wireless in the System>Administration>Hardware Drivers utility.

I didn't recommend Ubuntu 10.10 earlier in this thread because I wasn't sure if it would work, but I just checked and it definitely will support the AR81 ethernet chips.

---

### Post by Overloaded on 2010-09-10
Hello, have tried the steps described on the first page on this thread with no luck. Its a Acer Aspire One 533 and the network card are Atheros AR8152, I have run the commands listed earlier and are posting the outputs below, any suggestions?

  	 	 	 	 	 	  service@service-laptop:~$ **sudo ifconfig -a **
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 
  
 wlan0     Link encap:Ethernet  HWaddr 78:e4:00:92:68:88   
           inet addr:192.168.2.103  Bcast:192.168.2.255  Mask:255.255.255.0 
           inet6 addr: fe80::7ae4:ff:fe92:6888/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:3240 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:2539 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:3945169 (3.9 MB)  TX bytes:372409 (372.4 KB) 
 

 service@service-laptop:~$ **lspci **
 00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge 
 00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller 
 00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller 
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) 
 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) 
 00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02) 
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) 
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) 
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) 
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
 00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02) 
 00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) 
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02) 
 01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1) 
 02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01) 
 

 service@service-laptop:~$ **sudo ifup eth0 **
 Ignoring unknown interface eth0=eth0. 
 

 service@service-laptop:~$ **cat /etc/network/interfaces **
 auto lo 
 iface lo inet loopback 
 

 service@service-laptop:~$ **cat /etc/NetworkManager/nm-system-settings.conf **
 # This file is installed into /etc/NetworkManager, and is loaded by  
 # NetworkManager by default.  To override, specify: '--config file'  
 # during NM startup.  This can be done by appending to DAEMON_OPTS in  
 # the file: 
 # 
 # /etc/default/NetworkManager 
 # 
  
 [main] 
 plugins=ifupdown,keyfile 
  
 [ifupdown] 
 managed=false 
 

 service@service-laptop:~$ **dmesg | grep -e eth0 -e bcm **
 service@service-laptop:~$  
 

 service@service-laptop:~$ **ifconfig -a **
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 
  
 wlan0     Link encap:Ethernet  HWaddr 78:e4:00:92:68:88   
           inet addr:192.168.2.103  Bcast:192.168.2.255  Mask:255.255.255.0 
           inet6 addr: fe80::7ae4:ff:fe92:6888/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:3254 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:2554 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:3947138 (3.9 MB)  TX bytes:374186 (374.1 KB) 
 

 service@service-laptop:~$ **lshw -C Network **
 WARNING: you should run this program as super-user. 
   *-network UNCLAIMED      
        description: Ethernet controller 
        product: AR8152 v1.1 Fast Ethernet 
        vendor: Atheros Communications 
        physical id: 0 
        bus info: pci@0000:01:00.0 
        version: c1 
        width: 64 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list 
        configuration: latency=0 
        resources: memory:57000000-5703ffff ioport:5000(size=128) 
   *-network 
        description: Wireless interface 
        product: AR9285 Wireless Network Adapter (PCI-Express) 
        vendor: Atheros Communications Inc. 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: wlan0 
        version: 01 
        serial: 78:e4:00:92:68:88 
        width: 64 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=ath9k ip=192.168.2.103 latency=0 multicast=yes wireless=IEEE 802.11bgn 
        resources: irq:17 memory:56000000-5600ffff 
 

 service@service-laptop:~$ **lspci -nn **
 00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010] 
 00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] 
 00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012] 
 00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02) 
 00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) 
 00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) 
 00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) 
 00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) 
 00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) 
 00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) 
 00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) 
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) 
 00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02) 
 00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02) 
 00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02) 
 01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1) 
 02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

---

### Post by mike909 on 2010-09-10
overloaded, see post 115. That will work for your wired NIC.

---

### Post by Overloaded on 2010-09-10
FANTASTIC, it worked like a charm, you are a real lifesaver!!

---

### Post by krishnik on 2010-10-23
Hi

 Ihave the same problem i'm using a dell n4010 laptop got following result when i run sudo lshw -C network
```

*-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)

```I have followed your steps but its showing some errors
```

make -C /lib/modules/2.6.32-21-generic/build M=/home/nikhil/Desktop/compat-wireless-2010-10-22 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/nikhil/Desktop/compat-wireless-2010-10-22/compat/main.o
In file included from /home/nikhil/Desktop/compat-wireless-2010-10-22/include/linux/compat-2.6.h:29,
                 from <command-line>:0:
/home/nikhil/Desktop/compat-wireless-2010-10-22/include/linux/compat-2.6.34.h: In function â€˜device_lockâ€™:
/home/nikhil/Desktop/compat-wireless-2010-10-22/include/linux/compat-2.6.34.h:147: error: â€˜struct deviceâ€™ has no member named â€˜mutexâ€™
/home/nikhil/Desktop/compat-wireless-2010-10-22/include/linux/compat-2.6.34.h: In function â€˜device_trylockâ€™:
/home/nikhil/Desktop/compat-wireless-2010-10-22/include/linux/compat-2.6.34.h:157: error: â€˜struct deviceâ€™ has no member named â€˜mutexâ€™
/home/nikhil/Desktop/compat-wireless-2010-10-22/include/linux/compat-2.6.34.h: In function â€˜device_unlockâ€™:
/home/nikhil/Desktop/compat-wireless-2010-10-22/include/linux/compat-2.6.34.h:167: error: â€˜struct deviceâ€™ has no member named â€˜mutexâ€™
make[3]: *** [/home/nikhil/Desktop/compat-wireless-2010-10-22/compat/main.o] Error 1
make[2]: *** [/home/nikhil/Desktop/compat-wireless-2010-10-22/compat] Error 2
make[1]: *** [_module_/home/nikhil/Desktop/compat-wireless-2010-10-22] Error 2

```

---

### Post by pytheas22 on 2010-10-23
**krishnik**: that's strange.  It looks like it could be an issue with the source code.  It might help to choose an older version of the code to download from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/).  You have the snapshot from October 22, which may have happened to have errors.  The code gets updated every day and some days introduce bugs that prevent it from compiling.  It looks like the snapshots from early September worked for others, so I would give those a try.

If that doesn't help, let me know

---

### Post by Lucasbananas on 2010-10-24
Hi guy,

I just bought a new netbook (Acer Aspire one 521) and Installed Ubuntu 10.04 netbook edition. The thing is that I don't have acces to internet since my wired network isn't working and my wireless isn't either. I tried a bunch of things as I have been trying to fix this problem for a few days now. I think the recommendations on post 6 would work, but when I try to install build-essential, it asks me to insert the ubuntu netbook install disk into /cdrom/ in order to install. Since I don't actually have a cdrom on my netbook, I was wondering how I could install build-essential in order to get acces to my ethernet driver.

Any help would be greatly appreciated!

---

### Post by pytheas22 on 2010-10-25
**Lucasbananas**: I think you can also use a USB installation stick (which I presume you used to install Ubuntu on your netbook) as a repository, but I'm not sure how.  You might be able to find instructions via Google.

What you definitely can do, however, is download what you need from [http://packages.ubuntu.com/lucid/build-essential](http://packages.ubuntu.com/lucid/build-essential)  At the bottom of the page there are links to the actual downloads; you need to select the appropriate one depending on whether you have installed 32-bit Ubuntu (i386) or 64-bit (amd64).  It will then send you to a list of mirrors; click the link for a mirror close to you and you'll be able to download the file you need.

You also need to do the same for each of the packages listed as dependencies of build-essential, i.e. dpkg-dev, g++, etc.

Once you have all of these files, which should add up to about a half-dozen .deb packages, transfer them to your Ubuntu computer and save them on your desktop there.  Then open a terminal and run the commands:
```

cd ~/Desktop
sudo dpkg -i *deb
```

This will install all of the packages.  After that, you should be able to compile the driver using the instructions in post #6.

Alternatively, you could also just upgrade to Ubuntu 10.10, which should support your hardware out-of-the-box.

---

### Post by Lucasbananas on 2010-10-26
Thanks alot for the link and the info, I didn't know that it could be done that way!

---

### Post by pytheas22 on 2010-10-26
Yes, it can get tedious having to download all those individual packages and then transport them to your Ubuntu computer, but it can be done :)

---

### Post by Clodzilla on 2010-10-27
I have run the steps from the first post and have now gotten the OS to detect my Ethernet card, but I cannot figure out the scripts to make and install the driver. I will post information as necessary for the help.

Thanks!

---

### Post by Clodzilla on 2010-10-27
Well, I am officially a tard! I had the wrong compat file. My wired network works now and will attempt to get the wireless working as well once I download all the updates. THANKS for the help!!!!

---

### Post by pytheas22 on 2010-10-28
**Clodzilla**: good to hear.  Let me know if you have any more trouble.

---

### Post by ktechman on 2010-10-29
When the kernel gets updated will these changes hold or will I have to reinstall the patch?

---

### Post by pytheas22 on 2010-10-29
> When the kernel gets updated will these changes hold or will I have to reinstall the patch?

You would have to reinstall the driver from source.  It's good to keep a clean copy of the source code on hand for this purpose.

Also note that if you upgrade to Ubuntu 10.10, your wired ethernet should work out-of-the-box (assuming you have the same hardware and suffer from the same issue as the others in this thread).

---

### Post by ktechman on 2010-10-31
Are there plans to include the wired part of the patch in any of the kernel updates?  And if I use this method (from the compat wireless team) what are the drawbacks?

> Getting compat-wireless on Ubuntu

With Ubuntu you have the option of either installing compat-wireless yourself or of installing the package that provides it built by the Ubuntu kernel team. The Ubuntu package that carries compat-wireless is called linux-backport-modules and it has more backported modules than just your wireless subsystem. Its updated whenever major updates are pushed out into the wireless-testing git tree.

# For Ubuntu 8.10 Intrepid users:
sudo apt-get install linux-backports-modules-intrepid

# For Ubuntu 9.04 Jaunty users:
sudo apt-get install linux-backports-modules-jaunty

# For Ubuntu 9.10 Karmic users:
sudo apt-get install linux-backports-modules-karmic

# For Ubuntu 10.04 Lucid users (one of the following depending on the installed kernel. Most user should choose generic):
sudo apt-get install linux-backports-modules-wireless-lucid-generic
sudo apt-get install linux-backports-modules-wireless-lucid-generic-pae
sudo apt-get install linux-backports-modules-wireless-lucid-preempt
sudo apt-get install linux-backports-modules-wireless-lucid-server

Ktechman

---

### Post by pytheas22 on 2010-10-31
> Are there plans to include the wired part of the patch in any of the kernel updates? And if I use this method (from the compat wireless team) what are the drawbacks?

I'm not sure whether the backports-modules packages would provide the ethernet driver you need.  You can always install it, reboot and test; it's easy to uninstall later if it doesn't help.

I can't really think of any drawbacks to installing the backports-modules packages, other than that I'm not positive whether they would contain the driver you need.

Also keep in mind that if you upgrade to 10.10, your ethernet should work out-of-the-box there, because the 10.10 kernel has the right driver built in.

---

### Post by ktechman on 2010-10-31
The reason for staying with 10.04 is keeping all of my customers on the same page, in the past they were spread out over many different releases which meant that I had to keep several different releases on my laptop. As a matter of fact the 8.04 release has the same problem with the ath9k driver, which is present on my laptop, I believe I will try the backports module on it to see if it holds my wireless driver in place without having to reinstall. 

Ktechman

---

### Post by ktechman on 2010-10-31
If I reinstall the present kernel will that be sufficient to test whether or not the driver will hold in the future?

Ktechman

---

### Post by pytheas22 on 2010-11-01
> If I reinstall the present kernel will that be sufficient to test whether or not the driver will hold in the future?

Sorry, I'm not positive what you mean.  Are you referring to the non-backports kernel, or the Ubuntu 10.10 kernel that you would install on Ubuntu 10.04, or something else?

I agree that staying on Ubuntu 10.04 makes sense if you've got a broad range of machines to support.  It's LTS anyway.

---

### Post by jopeto on 2010-11-12
Hello, I'm running into trouble with my wired internet connection and I thought I would post to this thread, as I think my problem is more or less related.

I'm using Ubutu 10.4 LTS 64 bit edition and recently after a restart my wired internet connection stopped working. I am connected to the internet via LAN and when I am in Ubuntu, the orange light in the back where the ethernet cable is plugged in is blinking even though I don't have internet connectivity. I have a dual boot machine and I can access the internet via Windows XP. Furthermore I have used this computer and connection for over 3 years now and have never had this problem before. Also, I'm not using wireless and never have, just the wired LAN connection.

When in GNOME I go to System -> Preferences -> Network Connections in the Wired tab I see Auto eth0 and in the column 'last used' it says 'never', which is strange since I have used it pretty much every day for over three years.

I looked at various forums online and it seems that other people have the same problem, however I could not find the solution. Here are various posts on the matter:

[http://ubuntuforums.org/showthread.php?t=1613055](http://ubuntuforums.org/showthread.php?t=1613055)
[http://ubuntuforums.org/showthread.php?t=1573496](http://ubuntuforums.org/showthread.php?t=1573496)
[http://ubuntuforums.org/showthread.php?t=1539746](http://ubuntuforums.org/showthread.php?t=1539746)
[http://ubuntuforums.org/showthread.php?t=1487820](http://ubuntuforums.org/showthread.php?t=1487820)
[http://ubuntuforums.org/archive/index.php/t-1073970.html](http://ubuntuforums.org/archive/index.php/t-1073970.html)

I also tried booting from previous versions of the kernel from the list when Ubuntu starts up, however to no avail.

Below I provide the outputs for the commands which were asked in previous posts in this thread:

----------------------------------------------
Command:
**ifconfig eth0 up**
Output:
(no output)

Command:
**route -n**
Output:
(returns empty list)

Command:
**host [www.google.com](www.google.com)**
Output:
;;connection timed out; no servers could be reached

Command:
**ping [www.google.com](www.google.com)**
Output:
ping: unknown host [www.google.com](www.google.com)

Command:
**ifconfig -a**
Output:
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:65:a8:97
          inet6 addr: fe80::21a:a0ff:fe65:a897/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:981493 (981.4 KB)  TX bytes:1876 (1.8 KB)
          Interrupt:16

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10104 (10.1 KB)  TX bytes:10104 (10.1 KB)

Command:
**cat /etc/network/interfaces**
Output:
auto lo
iface lo inet loopback

Command:
**cat /etc/NetworkManager/nm-system-settings.conf**
Output:
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:1a:a0:65:a8:97,

[ifupdown]
managed=false

Command:
**dmesg | grep -e eth0 -e bcm**
Output:
[    3.327753] eth0: Tigon3 [partno(BCM95754) rev b002] (PCI Express) MAC address 00:1a:a0:65:a8:97
[    3.327757] eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    3.327760] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.327762] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   29.691277] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.438141] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   31.438144] tg3: eth0: Flow control is off for TX and off for RX.
[   31.476586] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   41.970981] eth0: no IPv6 routers present

Command:
**sudo dhclient eth0**
Output:
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:1a:a0:65:a8:97
Sending on   LPF/eth0/00:1a:a0:65:a8:97
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Command:
**sudo lshw -C Network**
Output:
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:65:a8:97
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5754-v3.15 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:dfbf0000-dfbfffff

Command:
**lspci -nn**
Output:
00:00.0 Host bridge [0600]: Intel Corporation 82Q963/Q965 Memory Controller Hub [8086:2990] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82Q963/Q965 Integrated Graphics Controller [8086:2992] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82Q963/Q965 Integrated Graphics Controller [8086:2993] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller [8086:2810] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller [8086:2820] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller [8086:2825] (rev 02)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)

----------------------------------------------

When I read this thread, I followed the advice given in post #6, however my internet is still not working. That's why I ran followed post #32 and ran sudo make uninstall.

I guess the reason why it the proposed solution didn't work is that my problem is slightly different. My internet connection was working fine for 3 years (I started with ubuntu 7.10 and upgraded to every single new version) and suddenly it stopped working now. In addition my hardware is different, if I read the commands correctly my internet interface is "NetXtreme BCM5754 Gigabit Ethernet PCI Express". If anyone has any suggestions what I should do to fix my problem, it would be greatly appreciated.

If all else fails and I decide to reinstall Ubuntu, is there a way to do that without reformatting my harddrive? In other words would I lose all my documents, such as my old emails stored in local folders in Thunderbird as well as bookmarks in firefox?

Thanks a lot for your help!

PS. If my problem is different than the one discussed in this thread, I'll be happy to repost a new one.

---

### Post by pytheas22 on 2010-11-12
**jopeto**: yes, I think your problem is different than the others in this thread.  The problem of other posters had to do with Ubuntu not having a driver available for their ethernet hardware (which was different from the hardware you have), so they had to compile a driver manually.  In your case, the device is being brought up and it doesn't appear like the driver is the issue.

The one thing in the output you posted that looks out-of-place to me is the line in the nm-system-settings.conf file that reads "no-auto-default=00:1a:a0:65:a8:97,"  As I understand it, that line would normally tell the system not to manage your ethernet connection, which could certainly be the problem.

So, I'd suggest opening up the configuration file by typing:
```

sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

Then put a hash (#) in front of the line in question so it looks like:
```

#no-auto-default=00:1a:a0:65:a8:97,
```

This will comment it out so the system will ignore that line, but leave it there so you can always uncomment it later if you need to.

After this, save the file, then reboot your computer.  Do you have better luck now?  If not, we can try some other things.

By the way, you're positive you use dynamic IP addresses served via DHCP and not static ones, correct?  If you don't know what this means, you probably use DHCP.

---

### Post by jopeto on 2010-11-13
Hi pytheas22, thanks a lot for your quick reply!

I just tried your suggestion by commenting the above line, however unfortunately that didn't solve my problem. I still cannot connect to the internet.

Yes, I am quite sure that I am using a dynamically assigned IP address via DHCP. I can double check that on Monday and will get back to you in case I'm wrong.

One additional piece of information - I just tried booting from the Ubuntu 10.4 LTS 64 bit live CD and I could not connect to the internet even in that case. Then I booted from the same live CD from a different computer connected via the same ethernet cable and I could connect to the internet without a problem. I'm wondering if there is some problem with the hardware address of my computer on the network, but I cannot check that before Monday as well.

If in the meantime you have any suggestions please let me know.

Thanks a lot once again for your help!

---

### Post by pytheas22 on 2010-11-13
**jopeto**: hmmm, that is very bizarre that it doesn't work under a live CD either.  I wonder if you could connect if you spoofed your MAC address, so that the hardware address of your computer would appear different on the network.

You could change the MAC by typing:
```

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:26:b9:06:2a:e2
sudo ifconfig eth0 up
```

This should change the MAC address to 00:26:b9:06:2a:e2 (which is just a random one I made up).  You can verify that it's changed correctly by typing "ifconfig eth0".

With the address changed, try connecting (using either NetworkManager or "sudo dhclient eth0" from the command line).  Any luck?

---

### Post by jopeto on 2010-11-14
Hi pytheas22,

Thanks once again for your suggestion. I tried it but unfortunately spoofing my MAC address didn't work either (neither when I booted from the hard drive nor when I booted from the live CD). Tomorrow I'll check with the network guys whether there is some problem on their side and will also take my computer home to check whether I can connect to the internet there. I'll let you know.

Thanks once again for your help!

---

### Post by pytheas22 on 2010-11-14
**jopeto**: hmmm, strange.  Please let me know what the network guys say, and if you're able to connect using ethernet in a different location.

---

### Post by Scuzzbuntu on 2010-11-15
@ pytheas22 perhaps you could help me too.  I have the same problem with the same results from all commands until #3 where on inputting 
 
**cat /etc/NetworkManager/nm-system-settings.conf **
 
mine has **no-auto-default=00:26:b9:e7:e0:57** (my physical address obviously)
 
any helpful hints??

---

### Post by pytheas22 on 2010-11-15
**Scuzzbuntu**: were things also working fine for you, but then stopped for some reason?  Does spoofing a MAC address make any difference?  And just to confirm that you have the same exact hardware, your "lspci -nn" output includes this exact line:
```

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
```

correct?

If all of the above is true, then I would assume this is a hardware (and/or driver)-specific problem, though that still doesn't explain why the connection apparently worked fine at one point, but then stopped, and still fails under an older live CD.

If this is indeed a hardware/driver problem, then it might help to try driving the card with ndiswrapper instead of the native Linux driver.  You'd need to blacklist the tg3 module, which is the native Linux driver for your ethernet card, and then install ndiswrapper and load Windows drivers for your ethernet device into it.  You should be able to find instructions to do all this elsewhere on the Internet, but let me know if you're unable.

Also note that you'll probably find ndiswrapper discussed in most contexts involving wireless cards, but it should work for ethernet devices just as well.

---

### Post by bmeacham on 2010-11-23
> **mike909 said:**
> 
-----Wired------:
1. Download official Atheros driver, from their website: [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (file: AR81Family-linux-v1.0.1.9.tar.gz)
2. tar -xvf AR*
3. make
4. sudo make install
5. restartI had a similar problem with a new Acer Aspire One D255.  Atheros ethernet adapter was not recognized.  When I upgraded from Ubuntu 10.04 to 10.10, it was fixed.  Thanks, Ubuntu team!

---

### Post by jopeto on 2010-12-01
Dear pytheas22,

Thanks a lot for all your help. Sorry I didn't get back to you but I was away for some time due to an illness. Hope it didn't come off as rude.

I spent quite a bit of time on my computer - the network guys said that on their side they don't see any blocks or anything else that might prevent me from connecting. Then I took my computer home and the strangest thing was that I was able to connect to the internet from home. Everything just worked automatically. I was really puzzled and finally decided that it would take less time if I reinstall everything as opposed to try and find out a solution. So I did a backup, wiped up my harddrive and reinstalled the 32 bit version of Ubuntu 10.4 LTS. Now it's working fine and I even have the feeling that it might be a bit faster than the 64 bit version.

Anyway, I'm all set now, although I didn't really understand what was the problem. Thanks a lot once again for all your prompt and thorough help!

---

### Post by pytheas22 on 2010-12-01
**jopeto**: no worries at all, but thanks for letting me know how you made out.  Sometimes it just makes more sense to deploy the wipe-it-all-out-and-start-from-scratch approach.  In any case, I'm glad you got it working and if you run into any more trouble, let me know.

---

### Post by wijit on 2011-01-15
hi pytheas22.
i followed your suggestion that you gave to rbisawa. it put my new dell n4030 on the wired network. you are great. keep going.:D

---

### Post by wijit on 2011-01-15
hi pytheas22.
i followed your suggestion that you gave to rbisawa. it put my new dell n4030 on the wired network. you are great. keep going.:D

---

### Post by wijit on 2011-01-15
hi pytheas22.
i followed your suggestion that you gave to rbisawa. it put my new dell n4030 on the wired network. you are great. keep going.:D

---

### Post by wijit on 2011-01-15
hi pytheas22.
i followed your suggestion that you gave to rbisawa. it put my new dell n4030 on the wired network. you are great. keep going.:D

---

### Post by iykrichie on 2011-01-31
thanks man u also solved my atheros ethernet issue.. i am very grateful

---

### Post by Omegus on 2011-02-02
Hey hey, I was reading about how to downgrade the kernel and did every thing the first guy on the thread did so here is my info. I'm still stuck .

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 6c:62:6d:81:95:de  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)



lspci


00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [RAID5 mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Cypress [Radeon HD 5800 Series]
01:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
05:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller


ifup eth0

ifup: failed to open statefile /var/run/network/ifstate: Permission denied


cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.12
netmask 255.255.255.0
gateway 192.168.2.255


cat /etc/networkManager/nm-system-setting.conf

cat: /etc/networkManager/nm-system-setting.conf: No such file or directory


lshw -c network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 6c:62:6d:81:95:de
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.12 latency=0 multicast=yes
       resources: irq:45 ioport:c800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:fe8e0000-fe8fffff




and thats all I got so far.

---

### Post by pytheas22 on 2011-02-02
**Omegus**: your problem looks different.  Your ethernet card is being brought up without a problem, but I guess you can't connect?  If you could please post the output of the following commands, that should help figure out how to resolve your situation:
```

dmesg | grep -e rt8 -e rtl -e eth0
sudo dhclient eth0
uname -a
cat /etc/NetworkManager/nm-system-settings.conf
```

Also, were you able to connect in the past on this system (with Ubuntu installed) and the problem just started occurring recently, or did ethernet never work for you under Ubuntu on this computer?

Finally, you have your /etc/network/interfaces file configured to use a static IP address.  Are you sure you need a static IP?  In most situations these days everyone uses dynamic IPs; if your router is not configured to serve static IP addresses but you're trying to use one, that's probably what's wrong.

---

### Post by Omegus on 2011-02-02
Hey thanks for the help. To answer your questions . No I recently bought this computer online at Ibuypower.com and I Installed Maverick . I noticed that I had no connection with the wired and the network card isnt wireless so I used my laptop to figure out the problem on the net using the ubuntu search engine. Found like 14 different solutions to the problem one being that i need to set up a Static IP. I am not sure if my router is a requires one. It is a 2wire gateway wireless router with 4 ethernet ports model Number 2701HG-G . 

As for the output you wanted me to grab here it is.

dmesg | grep -e rt8 -e rtl -e eth0
```
[    2.964288] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc900117e0000, 6c:62:6d:81:95:de, XID 081000c0 IRQ 45
[    7.510208] r8169 0000:02:00.0: eth0: link down
[    7.510943] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

sudo dhclient eth0
```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/6c:62:6d:81:95:de
Sending on   LPF/eth0/6c:62:6d:81:95:de
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

uname -a
```
Linux ultimoore-MS-7642 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
```

cat /etc/NetworkManager/nm-system-settings.conf
```
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=6c:62:6d:81:95:de,

[ifupdown]
managed=false
```

I really hope this helps I have racking my brain for 2 weeks trying to figure it out on my own.

---

### Post by pytheas22 on 2011-02-03
**Omegus**: thanks for the information.  At least part of the problem is probably that NetworkManager is configured to ignore your ethernet card.  To fix that, type:
```

sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

to open the configuration file in a text editor.  Then put a # in front of the line that reads "no-auto-default=6c:62:6d:81:95:de," so it looks like:
```

#no-auto-default=6c:62:6d:81:95:de,
```

This comments out that line.  Now save the file and close the text editor.

Next, I would also comment out the static IP settings in your /etc/network/interfaces file.  So open that file in a text editor with:

```
sudo gedit /etc/network/interfaces
```

and put a # in front of all of the non-blank lines *except* these two:

```
auto lo
iface lo inet loopback

```

Save that file and close the program.

Finally, right-click on the NetworkManager applet in the system tray (which by default would be in the upper-right part of your screen) and select "Edit Connections."  Under the "Wired" tab, if there is an entry called "Auto eth0," select it and click edit; otherwise click the button to add a new entry.  In the box that pops up, go to the "IPv4 Settings" tab, switch the method to manual and enter your static IP settings there: address 192.168.2.12, netmask 255.255.255.0 and gateway 192.168.2.255.  You should also set your DNS server appropriately (probably it's 192.168.2.255).

With the changes above, NetworkManager will manage your connection using a static IP, which should work better.  Previously you had the static IP configured differently, and although it should have worked, sometimes NetworkManager doesn't play nicely with configurations like that; I suspect it might work better if you just let NetworkManager run the show.

After all this, reboot your computer and see if you can connect to websites after the reboot.  If it still doesn't work, please post the output of:
```

route
ifconfig
ping -c 3 209.85.146.105
```

It would also be useful to know what happens if you type these commands:
```

sudo /etc/init.d/network-manager stop
sudo ifconfig eth0 up
sudo dhclient eth0
```

If you're able to connect to websites after running these commands, let me know.  If these commands break your connectivity (assuming you have any to begin with), just reboot and you'll be pushed back to the default settings.

---

### Post by Omegus on 2011-02-03
Ok It seems to be progressing well it now shows me that my ethernet is not connected now....lol but still not connected. Here are the results:

route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:81:95:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
```

ping -c 3 209.85.146.105
```
connect: Network is unreachable
```

sudo /etc/init.d/network-manager stop
```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
network-manager stop/waiting

```

sudo dhclient eth0
```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/6c:62:6d:81:95:de
Sending on   LPF/eth0/6c:62:6d:81:95:de
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```




Ok I have a quick question my address for my ethernet card is 6c:62:6d:81:95:de the address for my router is 00:25:3c:34:30:c8. which one am I spose to use for the connection?

---

### Post by pytheas22 on 2011-02-03
Thanks again for the output.  It helps to narrow down the possibilities of what could be wrong.

If you left-click on the NetworkManager applet, you should now see an entry under the "Wired Connection" section that you can select by left-clicking.  If you do that, does it then tell you you're connected?  With a static IP, I think it should at least say you're connected at that point (whether or not you can actually connect to external websites would be a different question).

I'd also be interested to know the output of these commands (in this order):

```
sudo /etc/init.d/network-manager stop
sudo ifconfig eth0 192.168.2.12
ping 192.168.2.155
```

You should reboot after running these so that the system will forget the changes they make.

---

### Post by Omegus on 2011-02-03
to answer the question about network manager it does show a wired network but it said that its not connected. or wait a second......its says disconnected . 

sudo /etc/init.d/network-manager stop
 	Code:
 	Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
network-manager stop/waiting 

sudo ifconfig eth0 192.168.2.12

```
nothing happened
```


ping 192.168.2.155

now i wasnt sure if you ment .255 or .155 so I did both and both got to 
the 254th ping and it said no response. ill recopy it in a min .

but this is what I have so far.

---

### Post by pytheas22 on 2011-02-04
> now i wasnt sure if you ment .255 or .155 so I did both and both got to
the 254th ping and it said no response. ill recopy it in a min .

Sorry, you're right--I mean 255.  I also should have told you that you only had to let it try to ping a few times.  Sorry if you waited 254 times!

It's strange that you don't get a ping response from the router even after setting the address manually using ifconfig.  When you set the address manually, you should always be able at least to ping the router (you can't access external sites without also setting the gateway and netmask, but those aren't necessary for talking just to the router).

Based on the absence of a ping response, there are only three possible conclusions to draw:

1. there's a hardware problem somewhere in the connection between the router and the computer--probably either because you're using a bad ethernet cable, or you have the cable plugged into a port on the router that's dead.  You can try swapping cables or ports to check for this, if you haven't already.  Also, do you see lights flashing on the ethernet port in the back of your Ubuntu computer, and on the router?  If not, it's probably a hardware issue involving the cable or the router port
2. the IP address you set (192.168.2.12) is not valid from the router's point of view.  Are you sure that's the right address that your router wants you to set statically?
3. the router's IP address is not actually the one you pinged (192.168.2.255).  Are you sure that's the right address?  If it is, you should be able to type that address into a Web browser from a computer connected to the router and the router configuration page would show up

If you can rule out (1) and think (2) or (3) might be the problem, we could probably figure out the right IP settings for your network if you posted the output of the command "ipconfig /all" from the terminal of a Windows computer connected to your router, or of "/sbin/ifconfig" from a Linux or OS X computer.  If you have any other computers on your network from which you could run those commands, please post the output and hopefully we can get to the bottom of this.

---

### Post by Omegus on 2011-02-05
the biggest problem is that every computer in the house runs on Ubuntu. All the laptops are obviously wireless. so they automaticly connect after i put in the WEP key . What  ill do is download windows most likely xp or something dual boot and ill do the Ip ping/all. if that fails Ill go through all the steps that ill take. If it is a hardware problem ill switch the ports if nothing happens ill switch the cables. If that fails ill keep the new cable in and do a manual reset. after that ill try and see if it is the IP and then ill get back to you.

---

### Post by pytheas22 on 2011-02-06
> the biggest problem is that every computer in the house runs on Ubuntu. All the laptops are obviously wireless. so they automaticly connect after i put in the WEP key . What ill do is download windows most likely xp or something dual boot and ill do the Ip ping/all. if that fails Ill go through all the steps that ill take. If it is a hardware problem ill switch the ports if nothing happens ill switch the cables. If that fails ill keep the new cable in and do a manual reset. after that ill try and see if it is the IP and then ill get back to you.

Actually don't worry about downloading Windows, unless you already have.  You could get the same information from Ubuntu with the commands:
```

ifconfig
route
```

I basically just want to know which gateway, netmask and subnet the other computers in your house are using.  It's possible those values are different for the wireless clients than for the wired ones, but in most cases I'd expect them to be the same.

If you've already gotten the information from Windows, that's fine as well, but I hope you didn't have to go to all that trouble.  Sorry I wasn't able to respond sooner than today...

---

### Post by Omegus on 2011-02-06
cool I tried windows and it was an epic fail on their part...curropt file. Anyways This is the info from My laptop that I am communicating from for the past while.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:03:0d:76:48:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:62:d3:2e  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe62:d32e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5581267 (5.5 MB)  TX bytes:365480 (365.4 KB)

```

route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         mymodem         0.0.0.0         UG    0      0        0 wlan0

```

---

### Post by pytheas22 on 2011-02-06
Thanks for the information.  At least part of the problem you were having is probably that your laptop (the one you've been posting from) looks like it has the IP address 192.168.2.12, which is the same one you were trying to assign to the desktop.  They can't both have the same address and be turned on at the same time.  Unless you always had the laptop off when the desktop was up, that explains part of the problem.

I'm not sure it's the whole problem, however, because probably you should still have been able to ping the router even if there was an IP conflict for the 192.168.2.12 address.  The output of the "route" command should have told me the address of your gateway, except I screwed up and forgot that to get the actual IP address of the gateway (rather than just the name), you have to add the -n flag.

In other words, would you mind please posting the output from your laptop of the command:
```

gateway -n
```

Also, just to be safe, what do you get from:
```

cat /etc/resolv.conf
cat /etc/hosts
host mymodem
```

This should provide the definitive answer on where your router is, numerically speaking.

---

### Post by Omegus on 2011-02-06
[FONT=monospace]That does make alot of sense . Here are my results.

gateway -n
[/FONT]```
gateway: command not found 
```

cat /etc/resolv.conf
```
# Generated by NetworkManager
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.2.1

```

cat /etc/hosts

```
192.168.2.12    sandy-ODM    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    sandy-ODM    localhost6.localdomain6    localhost6
127.0.1.1    sandy-ODM

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

host mymodem
```
mymodem.gateway.2wire.net has address 192.168.2.1
mymodem.gateway.2wire.net has address 192.168.2.1
Host mymodem.gateway.2wire.net not found: 4(NOTIMP)
```

---

### Post by pytheas22 on 2011-02-06
Aha, according to that output, your gateway looks like it's 192.168.2.1, not 192.168.2.255.  So that definitely seems like the core part of the problem.

I'd try editing your network configuration settings in NetworkManager (by right-clicking on the applet).  Set it to Manual, and set the gateway to 192.168.2.12, the netmask to 255.255.255.0 and the gateway to 192.168.2.1.  Then try turning off or disconnecting your laptop (to free up the 192.168.2.12 IP address) and see if you can get connected on the desktop.

If this doesn't work, are you at least now able to get a ping response from the router if you do:
```

sudo ifconfig eth0 192.168.2.12
ping -c 3 192.168.2.1
```

---

### Post by Omegus on 2011-02-06
Hey hey guess what...sorry still didnt work. I shut down my laptop after i got your message and tried what you said . When I ping the router it sent the 3 packages but never received anything back. here are the results of the ping.

```
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.12 icmp_seq=1 Destination Host Unreachable
From 192.168.2.12 icmp_seq=2 Destination Host Unreachable
From 192.168.2.12 icmp_seq=3 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2004ms
pipe 3
```

so here I think 1 of 2 things or both need to happen.
 1. its a cable thing and I need to switch the ports on the router.
 2. I will need to change my ip address on my desktop.
I am just guessing here but I am going off of the info we have been send each other.. Because of you I have learned so much about teminal commands.

---

### Post by pytheas22 on 2011-02-07
hmmm, that's very strange.  I'd definitely check on the cable and router port.

It might also be worth paying attention to the lights on the ethernet ports on both ends of the connection.  When you try to ping the router from the desktop, you should see flashes on both your desktop's ethernet port and on the router's.

If you don't see any flashes on the desktop's end, then that's weird and it could be that there's something strangely wrong with your ethernet card itself.

If you see flashes on the desktop port but not on the router's, it probably means there's a problem with the cable and the packets are not reaching the router.

If you see flashes on both ports but get no ping response from the router, the issue most likely has to do with the configuration of your router.  That could mean several different things, the most likely of which is problem (2) noted in your last post: that your desktop needs to use a different IP than 192.168.2.12.  If you have your router configured to accept traffic on that IP address only from a certain MAC address, then it would see that your desktop's MAC address is not the same as your laptop's, and would reject the traffic.

The router may also simply not be configured to respond to pings, but that seems unlikely unless you changed the default configuration.

So, to recap, I'd definitely check on the possibility of the port or cable being bad, and if neither of those seems to be the problem, pay attention to the lights on the ethernet ports and see if you can figure out exactly how far the ping packets are getting before they vanish.  If it seems like a router configuration issue, let me know which model it is and any information you have about how it's set up, and I'll see if anything stands out.

---

### Post by Omegus on 2011-02-07
I just finished checking both ports and yes they are both blinking. the model number of the router is the 2wire 2701G-G . The software is is a service advisor . when I manually reset the router I need to go into this software to finish th reset. Its bells way of controlling and seeing what you do. the site is  [http://internet.bell.ca/index.cfm?language=en&method=content.view&content_id=17435   ]("http://internet.bell.ca/index.cfm?language=en&method=content.view&content_id=17435")

problem is that the software is windows based and wont work in wine. How would go about changing my desktops ip?

---

### Post by pytheas22 on 2011-02-07
That seems silly, but I guess it makes sense.  God forbid you should be able to exercise control over your own property without checking in first with Bell.

Anyway, I did some googling and unless I am misundersanding something, it seems that you should be able to access the configuration page for this router through a Web browser, without needing Windows.  In your case, the URL to put into the address bar should be this

```
192.168.2.1/xslt?PAGE=C06
```

That should bring up the page where you can configure network settings.  The easiest thing to do would be to check the box to enable dhcp, in which case you should be able to get an IP address just by plugging in your computer and typing the command "dhclient eth0" (of course, you can configure Ubuntu to do that automatically whenever it gets plugged into the router, but for the moment your desktop is not set up that way because of the changes I had you make in NetworkManager).

If you can't get dhcp to work, you'll need to find a page where you can set static IP addresses.  The URL above doesn't seem to be the right one, but I'd try experimenting with different values in the URL; for example, see what you get at 192.168.2.1/xslt?PAGE=C07

Let me know if this gets you anywhere.

---

### Post by Omegus on 2011-02-07
how does ths look?
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:81:95:de  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6e62:6dff:fe81:95de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:661501 (661.5 KB)  TX bytes:111155 (111.1 KB)
          Interrupt:45 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


well I thought I would update DHCP so I put in  
sudo dhclient eth0
and BAM worked.
Thank you bro you hve helped me so much and I have learned so much from you. you have inspired me to take the Ubuntu Classes.

---

### Post by pytheas22 on 2011-02-08
Great to hear it finally worked!  We can conclude it was a configuration problem on the router's end all along.  At least it finally makes sense now...

You should be able to tell Ubuntu to use dhcp for the connection from now on automatically, without requiring you to run dhclient yourself, by editing your connections in NetworkManager and making sure the IPv4 settings for your eth0 connection are set to "Automatic (DHCP)."

Let me know if you have any problems with this, and otherwise, keep on enjoying Ubuntu.  Thanks for all of your patience through trying different things until we were finally able to hit the root of the problem.

---

### Post by arch0njw on 2011-02-17
> **pytheas22 said:**
> To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking).  Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```Then reboot.  Hopefully your ethernet will work automatically after reboot; if not, run:
```

sudo modprobe atl1c
```to insert the driver. 

Freaking AWESOME.

This worked for me on an Acer AspireONE D255.  "sudo make install" took *a very long time* (10 minutes+) to complete.  But patience paid off.

THANK YOU!!!

---

### Post by pytheas22 on 2011-02-17
> Freaking AWESOME.

This worked for me on an Acer AspireONE D255. "sudo make install" took a very long time (10 minutes+) to complete. But patience paid off.

THANK YOU!!!

Glad to hear it worked :)  And yes, compiling these drivers can take a long time (actually "sudo make install" should not have been the step where you compile them, but if you didn't do "make" first, it may have compiled them before installing), but that's part of the fun.

---

### Post by avi95 on 2011-02-18
> **pytheas22 said:**
> Your ethernet hardware seems to be quite new and doesn't have a driver built into Ubuntu as of yet.  However, there's a driver included in the compat-wireless stack that you can use (I have no idea why they included an ethernet driver in compat-wireless, but according to [these emails]("http://omgili.com/mailinglist/kernel-team/lists/ubuntu/com/43e72e891002020915x572a11fcg57f0b9caf7ed08eamailgmailcom.html"), someone did).

To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking).  Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```

Then reboot.  Hopefully your ethernet will work automatically after reboot; if not, run:
```

sudo modprobe atl1c
```

to insert the driver.  Let me know how it goes.

We can probably make your wireless work too, if you're interested.
I have the same problem with the same laptop, but these steps are not being able to fix it.
What should I do ?
Plz help...

---

### Post by avi95 on 2011-02-18
Also, look at these pics which I get on my system...
[https://www.facebook.com/album.php?aid=28422&id=100001565634032&l=9452c06d45]("https://www.facebook.com/album.php?aid=28422&id=100001565634032&l=9452c06d45")

---

### Post by pytheas22 on 2011-02-18
**avi95**: please open a terminal and post the output of these commands:
```

ifconfig
ifconfig -a
lspci -nn
lshw -C Network
sudo dhclient eth0
```

I'm not sure what's going on in your case--in your screenshots it looks like your ethernet card is being detected, but NetworkManager is ignoring it for some reason--and the command output should help pinpoint the problem.

---

### Post by avi95 on 2011-02-19
Here are the outputs of the commands you gave me :


```
ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


ifconfig -a

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12064 (12.0 KB)  TX bytes:12064 (12.0 KB)


lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)


lshw -C Network

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)


sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

---

### Post by dollarside on 2011-02-19
Oh my word! I have an Eeepc 1001x with 10.04, Ethernet wasn't working, but after I tried pytheas22's method, reboot, connected the wire, it worked like it does on my desktop.

Thanks so much pytheas22!:popcorn:

---

### Post by pytheas22 on 2011-02-19
**dollarside**: glad it worked for you :)  Just keep in mind that you may need to recompile the driver again (repeating the steps that got it working the first time) whenever you install a new kernel via Ubuntu Updates.

**avi95**: it looks like your card is actually not being recognized, which is strange because in one of the screenshots you posted NetworkManager has an entry for "eth0."  Maybe at one time the card was brought up successfully, and now for some reason it no longer is.

In any case, I'm afraid I'll have to ask for more output to figure out why the driver doesn't want to claim the card.  Could you please post the output of these commands (the first one may have no output):
```

sudo modprobe atl1c
dmesg | grep -e eth -e atl1
modinfo atl1c
```

Also, when you ran the commands to compile the driver, I presume you didn't get any error messages?  If you have time, it would not hurt to run those commands again and post all the output, just so I can make sure they're proceeding as expected.  According to everything I'm reading, rebuilding the atl1c module using the most recent compat-wireless source code (which is what those commands do for you) should get your hardware (with PCI ID 1969:2060) working in Ubuntu 10.10, so it's strange that it's not doing the trick for you.

---

### Post by MountainX on 2011-02-20
> **pytheas22 said:**
> Your ethernet hardware seems to be quite new and doesn't have a driver built into Ubuntu as of yet.  However, there's a driver included in the compat-wireless stack that you can use (I have no idea why they included an ethernet driver in compat-wireless, but according to [these emails]("http://omgili.com/mailinglist/kernel-team/lists/ubuntu/com/43e72e891002020915x572a11fcg57f0b9caf7ed08eamailgmailcom.html"), someone did).

To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking).  Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```

Then reboot.  Hopefully your ethernet will work automatically after reboot; if not, run:
```

sudo modprobe atl1c
```

to insert the driver.  Let me know how it goes.

We can probably make your wireless work too, if you're interested.

That fixed my Acer AO D255E running Linux Mint 9. (And I did not have to do the last modprobe.) Thanks!

---

### Post by Saju007 on 2011-02-20
Hi....
 I just installed UBUNTU 10.04 and unable to connect with internet.
My LAN card is not detected so i can't install or update wine from internet. I have wine-1.3.13.tar which is downloaded to my hard disc. 
1.How can i install wine from that?
2.Where i can find Driver for " intex IT-584" 10/100 Mbps ETHERNET CARD?

---

### Post by pytheas22 on 2011-02-20
**Saju007**: the .tar.gz file you have for wine is probably source code.  Although you could use this file to install wine (by uncompressing the file and then compiling the source code), that's probably not what you want.  Instead, wait until you have Internet access and you will then be able to install wine very easily using the Ubuntu Software Center.  You can read more about this [here]("https://help.ubuntu.com/community/InstallingSoftware") if you want the exhaustive details.

As for finding the driver for your ethernet card so that you can connect, please open a terminal from the Applications>Accessories menu, run the following commands and post the output here:
```

lspci -nn
lshw -C Network
uname -a
ifconfig
ifconfig -a
```

That will tell me exactly what hardware you have, so that we can find the right driver.

---

### Post by avi95 on 2011-02-21
Hey pytheas22,
Did you get to know what is wrong with my network connection ?
Pls respond quickly...

---

### Post by avi95 on 2011-02-21
Oh hi,
I completely missed this post of yours...
Here is the output of the original commands :


```
sudo apt-get update
Err http://security.ubuntu.com maverick-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://archive.canonical.com maverick Release.gpg
  Could not resolve 'archive.canonical.com'
Err http://archive.canonical.com/ maverick/partner Translation-en
  Could not resolve 'archive.canonical.com'
Err http://archive.canonical.com/ maverick/partner Translation-en_US
  Could not resolve 'archive.canonical.com'
Err http://us.archive.ubuntu.com maverick Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com maverick-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://dl.google.com stable Release.gpg
  Could not resolve 'dl.google.com'
Err http://dl.google.com/linux/chrome/deb/ stable/main Translation-en
  Could not resolve 'dl.google.com'
Err http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US
  Could not resolve 'dl.google.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done           
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://archive.canonical.com/dists/maverick/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Could not resolve 'dl.google.com'

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en.bz2  Could not resolve 'dl.google.com'

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2  Could not resolve 'dl.google.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.


sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essential



cd compat-wireless*
yash@ubuntu:~/Desktop/compat-wireless-2011-02-16$ scripts/driver-select atl1c
Backup exists: Makefile.bk
Old build found, going to clean this up first...
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CLEAN   /home/yash/Desktop/compat-wireless-2011-02-16
  CLEAN   /home/yash/Desktop/compat-wireless-2011-02-16/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
Restoring Makefiles...
Restored makefile: ./drivers/net/Makefile (and removed backup)
Restored makefile: ./Makefile (and removed backup)
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk


make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
smake -C /lib/modules/2.6.35-22-generic/build M=/home/yash/Desktop/compat-wireless-2011-02-16 modules
udmake[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  LD      /home/yash/Desktop/compat-wireless-2011-02-16/compat/built-in.o
  CC [M]  /home/yash/Desktop/compat-wireless-2011-02-16/compat/main.o
  CC [M]  /home/yash/Desktop/compat-wireless-2011-02-16/compat/compat-2.6.36.o
  CC [M]  /home/yash/Desktop/compat-wireless-2011-02-16/compat/compat-2.6.37.o
  CC [M]  /home/yash/Desktop/compat-wireless-2011-02-16/compat/compat-2.6.38.o
  LD [M]  /home/yash/Desktop/compat-wireless-2011-02-16/compat/compat.o
  CC [M]  /home/yash/Desktop/compat-wireless-2011-02-16/compat/kfifo.o
  LD      /home/yash/Desktop/compat-wireless-2011-02-16/drivers/net/built-in.o
  LD      /home/yash/Desktop/compat-wireless-2011-02-16/drivers/net/atl1c/built-in.o
  CC [M]  /home/yash/Desktop/compat-wireless-2011-02-16/drivers/net/atl1c/atl1c_main.o
o  CC [M]  /home/yash/Desktop/compat-wireless-2011-02-16/drivers/net/atl1c/atl1c_hw.o
  CC [M]  /home/yash/Desktop/compat-wireless-2011-02-16/drivers/net/atl1c/atl1c_ethtool.o
   LD [M]  /home/yash/Desktop/compat-wireless-2011-02-16/drivers/net/atl1c/atl1c.o
  LD      /home/yash/Desktop/compat-wireless-2011-02-16/built-in.o
m  Building modules, stage 2.
  MODPOST 3 modules
a  CC      /home/yash/Desktop/compat-wireless-2011-02-16/compat/compat.mod.o
  LD [M]  /home/yash/Desktop/compat-wireless-2011-02-16/compat/compat.ko
  CC      /home/yash/Desktop/compat-wireless-2011-02-16/compat/kfifo.mod.o
ke  LD [M]  /home/yash/Desktop/compat-wireless-2011-02-16/compat/kfifo.ko
  CC      /home/yash/Desktop/compat-wireless-2011-02-16/drivers/net/atl1c/atl1c.mod.o
   LD [M]  /home/yash/Desktop/compat-wireless-2011-02-16/drivers/net/atl1c/atl1c.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'


sudo make install

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko
kernel/drivers/net/wireless/orinoco/orinoco_plx.ko
kernel/drivers/net/wireless/orinoco/orinoco_usb.ko
kernel/drivers/net/wireless/orinoco/orinoco.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/net/wireless/orinoco/spectrum_cs.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/wl12xx/wl1251.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

Your old ethernet subsystem modules are left intact:

kernel/drivers/net/atlx/atl1.ko
kernel/drivers/net/atlx/atl2.ko
kernel/drivers/net/atl1e/atl1e.ko
kernel/drivers/net/atl1c/atl1c.ko

Your old bluetooth subsystem modules were left intact:

kernel/drivers/bluetooth/ath3k.ko
kernel/drivers/bluetooth/bcm203x.ko
kernel/drivers/bluetooth/bluecard_cs.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/drivers/bluetooth/bpa10x.ko
kernel/drivers/bluetooth/bt3c_cs.ko
kernel/drivers/bluetooth/btmrvl.ko
kernel/drivers/bluetooth/btmrvl_sdio.ko
kernel/drivers/bluetooth/btsdio.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/bluetooth/btuart_cs.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/drivers/bluetooth/dtl1_cs.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/net/bluetooth/l2cap.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/sco.ko

make -C /lib/modules/2.6.35-22-generic/build M=/home/yash/Desktop/compat-wireless-2011-02-16 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  Building modules, stage 2.
  MODPOST 3 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make -C /lib/modules/2.6.35-22-generic/build M=/home/yash/Desktop/compat-wireless-2011-02-16 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  INSTALL /home/yash/Desktop/compat-wireless-2011-02-16/compat/compat.ko
  INSTALL /home/yash/Desktop/compat-wireless-2011-02-16/compat/kfifo.ko
  INSTALL /home/yash/Desktop/compat-wireless-2011-02-16/drivers/net/atl1c/atl1c.ko
  DEPMOD  2.6.35-22-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
Updating Ubuntu's initramfs for 2.6.35-22-generic under /boot/ ...
Warning: No support for locale: en_US.utf8
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
cat: /boot/grub/video.lst: No such file or directory
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found Windows 7 (loader) on /dev/sda2
done
depmod will prefer updates/ over kernel/ -- OK!

Currently detected wireless subsystem modules:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko
kernel/drivers/net/wireless/orinoco/orinoco_plx.ko
kernel/drivers/net/wireless/orinoco/orinoco_usb.ko
kernel/drivers/net/wireless/orinoco/orinoco.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/net/wireless/orinoco/spectrum_cs.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/wl12xx/wl1251.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

Currently detected ethernet subsystem modules:

kernel/drivers/net/atlx/atl1.ko
kernel/drivers/net/atlx/atl2.ko
kernel/drivers/net/atl1e/atl1e.ko
updates/drivers/net/atl1c/atl1c.ko

Currently detected bluetooth subsystem modules:

kernel/drivers/bluetooth/ath3k.ko
kernel/drivers/bluetooth/bcm203x.ko
kernel/drivers/bluetooth/bluecard_cs.ko
kernel/net/bluetooth/bluetooth.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/drivers/bluetooth/bpa10x.ko
kernel/drivers/bluetooth/bt3c_cs.ko
kernel/drivers/bluetooth/btmrvl.ko
kernel/drivers/bluetooth/btmrvl_sdio.ko
kernel/drivers/bluetooth/btsdio.ko
kernel/drivers/bluetooth/btusb.ko
kernel/drivers/bluetooth/btuart_cs.ko
kernel/net/bluetooth/cmtp/cmtp.ko
kernel/drivers/bluetooth/dtl1_cs.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko
kernel/net/bluetooth/l2cap.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/sco.ko

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.


yash@ubuntu:~$ sudo modprobe atl1c
yash@ubuntu:~$ 
```

The last command gave absolutely no output.
Now I'd like to mention that out of sheer boredom & irritation I had deleted the "eth0" connection...
That's probably why it's not being detected(sorry)...

And these are the outputs of the commands you just gave :

```
dmesg | grep -e eth -e atl1
[    1.137014] atl1c 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.137039] atl1c 0000:04:00.0: setting latency timer to 64
[    1.659361] atl1c 0000:04:00.0: PCI INT A disabled
[    1.659375] atl1c: probe of 0000:04:00.0 failed with error -5



modinfo atl1c
filename:       /lib/modules/2.6.35-22-generic/updates/drivers/net/atl1c/atl1c.ko
version:        1.0.1.0-NAPI
license:        GPL
description:    Atheros 1000M Ethernet Network Driver
author:         Jie Yang <jie.yang@atheros.com>
srcversion:     CAF56BEA4220368C023ED8B
alias:          pci:v00001969d00001083sv*sd*bc*sc*i*
alias:          pci:v00001969d00001073sv*sd*bc*sc*i*
alias:          pci:v00001969d00002062sv*sd*bc*sc*i*
alias:          pci:v00001969d00002060sv*sd*bc*sc*i*
alias:          pci:v00001969d00001062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001063sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.35-22-generic SMP mod_unload modversions
``` 

The command "sudo modprobe" didn't give anything...
And, seeing as that "eth0" connection is kind of important, I've created another connection with same name.

This IS a real mess.
Now, only you can work your magic...

---

### Post by pytheas22 on 2011-02-21
**avi95**: it looks like you successfully compiled the updated ethernet driver and it now "recognizes" your hardware, but the problem is the line in your dmesg that says:
```

[    1.659375] atl1c: probe of 0000:04:00.0 failed with error -5
```

Googling around, it sounds like this may be an issue related to ACPI.  So let's try disabling ACPI and see if that solves the problem.  First, type this command:

sudo gedit /etc/default/grub

A file will open.  Look for the line that says:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and add the string **acpi=off** (inside the quotes), so that the line reads:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

Then save and close the file, and run this command to apply the change:
```

sudo update-grub
```

Now reboot and hopefully the ethernet will work.  If it still doesn't, please let me know the output of:
```

lsmod | grep atl
dmesg | grep -e atl -e eth0
```

If disabling ACPI doesn't solve the problem, it may also help to disconnect the power cord from your machine, remove the battery if it's a laptop and then hold the power button in for about fifteen seconds.  This will cut off all electricity to the machine and force all the hardware to default back to its original state, which can sometimes solve strange ACPI-related issues (I don't know if this will help you specifically, but it won't hurt to try if the instructions above don't achieve anything).

---

### Post by avi95 on 2011-02-22
Well, my Ethernet didn't start working but, there was an improvement - It is now detecting 2 connections, but is unable to connect to the internet using either of those.

Here are some of the screenshots :
(Ignore the first 5, you've already seen those)


[https://www.facebook.com/album.php?aid=28422&id=100001565634032&l=9452c06d45](https://www.facebook.com/album.php?aid=28422&id=100001565634032&l=9452c06d45)


I'll just give you the output of those commands & try that method that you told me...

---

### Post by pytheas22 on 2011-02-22
**avi95**: that looks better.  It looks like your ethernet card is being detected now.  But to be sure, please post the output of these (some may have no output):
```

lsmod | grep atl
dmesg | grep -e atl -e eth0
sudo /etc/init.d/network-manager stop
sudo ifconfig eth0 up
sudo dhclient eth0
```

And please also let me know if disconnecting the power to your computer changes anything.

---

### Post by avi95 on 2011-02-23
I have some very good news  !!!
My wired internet is now working !!!
I installed Ubuntu by burning the contents of the ISO file to a disc.
Then, I created a partition along with Windows 7.
Automatically, my Ethernet began to work...
I'm posting this from Ubuntu only !!!

I'd really like to thank pytheas22 for all the hardwork and effort he put into helping me.
Thanks a lot !!!:D

But, I still need your help to get my wifi working...
It is now detecting my wifi network, I've installed the Broadcom STA Wireless Driver, put in the password for my connection.
The network icon shows those bars flashing as a sign of connecting but, after a few minutes of trying to connect it gives a message saying "Wireless not connected".

Although this seems to be quite an ordinary problem, I'd really appreciate your help.
Thanks anyway :D

---

### Post by pytheas22 on 2011-02-24
**avi95**: glad to hear you got the ethernet working.  That's good news.  I'm not sure why it works for you now, but perhaps the bug that causes your hardware not to be recognized in Ubuntu 10.10 has been fixed and you got the update in the ISO of Ubuntu that you downloaded recently.

As for the wireless, that's strange that it won't connect.  Normally I'd suggest trying a different driver, but the STA driver that you already installed is the only one that will support your hardware (with PCI ID 14e4:4727).  (There's ndiswrapper, but that's a last-ditch solution.)  Are you able to connect if you change the settings on your router?  For example, you could try changing the channel or the encryption scheme (e.g., switch from WPA1 to WPA2, or vice-versa).

If you still can't get the wireless to connect, it would be useful to see the output of:
```

grep -ie wl -ie eth1 /var/log/syslog
sudo iwlist scan
iwconfig
```

---

### Post by fliksr on 2011-02-25
I installed 10.04 LTS a few days ago and was having the occasional freezing issue (like many it seems).  I found a workaround until I had time to actually fix it (video driver?) but now I have a more annoying problem.  It all of a sudden does not detect the wired connection.

I had to go back to the Vista partition just to post here!

I would very much appreciate some help and guidance!

---

### Post by avi95 on 2011-02-26
Okay, I tried everything you said, but it didn't work.
Those bars in the wireless network connection icon flash & blink for a while & then a message is displayed saying "Wireless not connected"...

So, here are the outputs of the commands you asked for :


```
grep -ie wl -ie eth1 /var/log/syslog

Feb 26 10:27:28 BaddyMaster kernel: [   16.318649] wl: module license 'MIXED/Proprietary' taints kernel.
Feb 26 10:27:28 BaddyMaster kernel: [   16.322586] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 26 10:27:28 BaddyMaster kernel: [   16.322597] wl 0000:03:00.0: setting latency timer to 64
Feb 26 10:27:28 BaddyMaster kernel: [   16.456832] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
Feb 26 10:27:28 BaddyMaster NetworkManager[970]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1)
Feb 26 10:27:28 BaddyMaster NetworkManager[970]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <error> [1298696248.496072] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): driver supports SSID scans (scan_capa 0x01).
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): now managed
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): bringing up device.
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): preparing device.
Feb 26 10:27:28 BaddyMaster avahi-daemon[968]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fe6e:e8e4.
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): deactivating device (reason: 2).
Feb 26 10:27:28 BaddyMaster avahi-daemon[968]: New relevant interface eth1.IPv6 for mDNS.
Feb 26 10:27:28 BaddyMaster avahi-daemon[968]: Registering new address record for fe80::72f1:a1ff:fe6e:e8e4 on eth1.*.
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant manager state:  down -> idle
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): device state change: 2 -> 3 (reason 0)
Feb 26 10:27:28 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant interface state:  starting -> ready
Feb 26 10:27:37 BaddyMaster dhclient: Listening on LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:27:37 BaddyMaster dhclient: Sending on   LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:27:37 BaddyMaster dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Feb 26 10:27:37 BaddyMaster avahi-daemon[968]: Interface eth1.IPv6 no longer relevant for mDNS.
Feb 26 10:27:37 BaddyMaster avahi-daemon[968]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fe6e:e8e4.
Feb 26 10:27:37 BaddyMaster avahi-daemon[968]: Withdrawing address record for fe80::72f1:a1ff:fe6e:e8e4 on eth1.
Feb 26 10:27:37 BaddyMaster dhclient: Listening on LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:27:37 BaddyMaster dhclient: Sending on   LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:27:38 BaddyMaster dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Feb 26 10:27:39 BaddyMaster avahi-daemon[968]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fe6e:e8e4.
Feb 26 10:27:39 BaddyMaster avahi-daemon[968]: New relevant interface eth1.IPv6 for mDNS.
Feb 26 10:27:39 BaddyMaster avahi-daemon[968]: Registering new address record for fe80::72f1:a1ff:fe6e:e8e4 on eth1.*.
Feb 26 10:27:48 BaddyMaster kernel: [   38.224525] eth1: no IPv6 routers present
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) starting connection 'Auto SiddSharma'
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1/wireless): access point 'Auto SiddSharma' has security, but secrets are required.
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): device state change: 5 -> 6 (reason 0)
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): device state change: 6 -> 4 (reason 0)
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1/wireless): connection 'Auto SiddSharma' has security, and secrets exist.  No new secrets needed.
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  scanning -> disconnected
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  scanning -> associated
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  4-way handshake -> disconnected
Feb 26 10:27:52 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Feb 26 10:27:55 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  scanning -> associated
Feb 26 10:27:55 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Feb 26 10:27:55 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  4-way handshake -> disconnected
Feb 26 10:27:55 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Feb 26 10:27:59 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  scanning -> associated
Feb 26 10:27:59 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Feb 26 10:27:59 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  4-way handshake -> disconnected
Feb 26 10:27:59 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Feb 26 10:28:07 BaddyMaster NetworkManager[970]: <warn> (eth1): link timed out.
Feb 26 10:28:09 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  scanning -> disconnected
Feb 26 10:28:09 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Feb 26 10:28:19 BaddyMaster dhclient: Listening on LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:28:19 BaddyMaster dhclient: Sending on   LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:28:20 BaddyMaster dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Feb 26 10:28:20 BaddyMaster avahi-daemon[968]: Interface eth1.IPv6 no longer relevant for mDNS.
Feb 26 10:28:20 BaddyMaster avahi-daemon[968]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fe6e:e8e4.
Feb 26 10:28:20 BaddyMaster avahi-daemon[968]: Withdrawing address record for fe80::72f1:a1ff:fe6e:e8e4 on eth1.
Feb 26 10:28:20 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  scanning -> disconnected
Feb 26 10:28:20 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  disconnected -> associating
Feb 26 10:28:20 BaddyMaster dhclient: Listening on LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:28:20 BaddyMaster dhclient: Sending on   LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:28:20 BaddyMaster dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Feb 26 10:28:21 BaddyMaster dhclient: Listening on LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:28:21 BaddyMaster dhclient: Sending on   LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:28:21 BaddyMaster dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Feb 26 10:28:23 BaddyMaster avahi-daemon[968]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fe6e:e8e4.
Feb 26 10:28:23 BaddyMaster avahi-daemon[968]: New relevant interface eth1.IPv6 for mDNS.
Feb 26 10:28:23 BaddyMaster avahi-daemon[968]: Registering new address record for fe80::72f1:a1ff:fe6e:e8e4 on eth1.*.
Feb 26 10:28:25 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  associating -> disconnected
Feb 26 10:28:25 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Feb 26 10:28:28 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  scanning -> associated
Feb 26 10:28:28 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Feb 26 10:28:29 BaddyMaster avahi-daemon[968]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.1.
Feb 26 10:28:29 BaddyMaster avahi-daemon[968]: New relevant interface eth1.IPv4 for mDNS.
Feb 26 10:28:29 BaddyMaster avahi-daemon[968]: Registering new address record for 192.168.1.1 on eth1.IPv4.
Feb 26 10:28:30 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  4-way handshake -> associating
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  associating -> associated
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  4-way handshake -> group handshake
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  group handshake -> completed
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'SiddSharma'.
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> (eth1): device state change: 5 -> 7 (reason 0)
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Beginning IP6 addrconf.
Feb 26 10:28:31 BaddyMaster avahi-daemon[968]: Withdrawing address record for fe80::72f1:a1ff:fe6e:e8e4 on eth1.
Feb 26 10:28:31 BaddyMaster avahi-daemon[968]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fe6e:e8e4.
Feb 26 10:28:31 BaddyMaster avahi-daemon[968]: Interface eth1.IPv6 no longer relevant for mDNS.
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Feb 26 10:28:31 BaddyMaster NetworkManager[970]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Feb 26 10:28:31 BaddyMaster dhclient: Listening on LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:28:31 BaddyMaster dhclient: Sending on   LPF/eth1/70:f1:a1:6e:e8:e4
Feb 26 10:28:31 BaddyMaster dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Feb 26 10:28:32 BaddyMaster avahi-daemon[968]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::72f1:a1ff:fe6e:e8e4.
Feb 26 10:28:32 BaddyMaster avahi-daemon[968]: New relevant interface eth1.IPv6 for mDNS.
Feb 26 10:28:32 BaddyMaster avahi-daemon[968]: Registering new address record for fe80::72f1:a1ff:fe6e:e8e4 on eth1.*.
Feb 26 10:28:33 BaddyMaster dhclient: DHCPREQUEST of 192.168.1.3 on eth1 to 255.255.255.255 port 67
Feb 26 10:28:33 BaddyMaster NetworkManager[970]: <info> (eth1): DHCPv4 state changed preinit -> bound
Feb 26 10:28:33 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb 26 10:28:33 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Feb 26 10:28:33 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Feb 26 10:28:41 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  completed -> disconnected
Feb 26 10:28:41 BaddyMaster NetworkManager[970]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Feb 26 10:28:41 BaddyMaster kernel: [   91.158454] eth1: no IPv6 routers present
Feb 26 10:28:51 BaddyMaster NetworkManager[970]: <info> (eth1): IP6 addrconf timed out or failed.
Feb 26 10:28:51 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Feb 26 10:28:51 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 4 of 5 (IP6 Configure Timeout) started...
Feb 26 10:28:51 BaddyMaster NetworkManager[970]: <info> (eth1): device state change: 7 -> 9 (reason 5)
Feb 26 10:28:51 BaddyMaster NetworkManager[970]: <warn> Activation (eth1) failed for access point (SiddSharma)
Feb 26 10:28:51 BaddyMaster NetworkManager[970]: <warn> Activation (eth1) failed.
Feb 26 10:28:51 BaddyMaster NetworkManager[970]: <info> Activation (eth1) Stage 4 of 5 (IP6 Configure Timeout) complete.
Feb 26 10:28:51 BaddyMaster NetworkManager[970]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Feb 26 10:28:51 BaddyMaster NetworkManager[970]: <info> (eth1): deactivating device (reason: 0).
Feb 26 10:28:51 BaddyMaster NetworkManager[970]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1949
Feb 26 10:28:51 BaddyMaster avahi-daemon[968]: Withdrawing address record for 192.168.1.1 on eth1.
Feb 26 10:28:51 BaddyMaster avahi-daemon[968]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.1.
Feb 26 10:28:51 BaddyMaster avahi-daemon[968]: Interface eth1.IPv4 no longer relevant for mDNS.




sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument




iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0



```

Hope this helps....

---

### Post by fliksr on 2011-02-26
Hopefully this is useful:

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10127 (10.1 KB)  TX bytes:10127 (10.1 KB)

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:b9:5a:7d:c5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10127 (10.1 KB)  TX bytes:10127 (10.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:92:9b:12:ce  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)

lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5a:7d:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:9b:12:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:19:b9:5a:7d:c5
Sending on   LPF/eth0/00:19:b9:5a:7d:c5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPOFFER of 76.23.128.214 from 73.157.232.1
DHCPREQUEST of 76.23.128.214 on eth0 to 255.255.255.255 port 67
DHCPACK of 76.23.128.214 from 73.157.232.1
bound to 76.23.128.214 -- renewal in 104418 seconds.

Disabled?? WTF?!

---

### Post by pytheas22 on 2011-02-26
**fliksr**: you were able to get a connection manually using dhclient, so it is probably not a problem with your driver.  Most likely the issue is that NetworkManager is not starting automatically for some reason.  Do you get connected if you type these commands:
```

sudo ifconfig eth0 up
sudo /etc/init.d/network-manager start
```

If that works I can tell you how to make those commands run automatically whenever you boot your computer.

**avi95**: I'm not sure, but it looks for your syslog like your machine is trying to use IPv6, which I suspect might be the problem.  Is your router configured to use IPv6?  Do you have your connection configured to use IPv6 in NetworkManager?

In most cases IPv6 should not be necessary, so you should probably disable it.  Let me know if you're able to connect then.

---

### Post by fliksr on 2011-02-26
No such luck.  All I get is this message:

Rather than invoking init scripts through /etc/init.d, use the service(8 )
utility, e.g. service network-manager start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8 ) utility, e.g. start network-manager

---

### Post by avi95 on 2011-02-27
Dude, you ROCK !!!!
The minute I disabled IPv6, my wireless got connected !!!

Believe me,if there was a Nobel Prize for helping others, I would have given it to you...
It's amazing.
Today, you have gained a new fan :D

---

### Post by pytheas22 on 2011-02-27
**avi95**: glad it worked and you're finally all set :)  Just for the sake of anyone else who reads this thread, was it on your router that you had to disable IPv6, or in NetworkManager in Ubuntu?

**fliksr**: strange.  The only other possibility that stands out to me as potentially being the cause of your problem is that you simply have the interface disabled in NetworkManager for some reason, or not set to connect automatically.  If you right-click on the NetworkManager applet (which by default is in the upper-right corner of your screen) and select "Edit Connections," you should see an entry called "Auto eth0" under the "Wired" tab.  And if you click the "Edit" button for that connection, you should see that the interface is configured to connect automatically, is available to all users and (under the "IPv6 Settings" tab) is set to use "Automatic (DHCP)" as its connection method.  These should all be the default settings, but if they're not, that could be the problem.

It could also be helpful to check your syslog output for any bits about the ethernet interface.  What is the output of:
```

grep -i -e eth0 -e b44 /var/log/syslog
```

By the way, the bit in your "lshw -C Network" output about the interface being "DISABLED" usually just means that it's "down"--i.e., not activated--but the "sudo ifconfig eth0 up" command should put it "up."  After you run that command, does lshw still say the interface is DISABLED?

If none of the above helps and we can't figure out the root cause of your issue, a second-best solution would be just to write a script that use dhclient to get you an IP address, and would run automatically each time you boot your computer.  That's easy to set up, but let's see if we can figure out the real problem first.

---

### Post by avi95 on 2011-02-28
Yeah, I'm all set now :D

I disabled IPv6 in the Network Manager Applet in Ubuntu.
It worked beautifully :)

---

### Post by Anil hegde on 2011-03-11
Hi i hav recently bought Dell inspiron N4010 and i am unable to detect wired connection in it.....

The below are few outputs i am getting

**cat /etc/network/interfaces**
_Output :_
auto lo
iface lo inet loopback

**cat /etc/NetworkManager/nm-system-settings.conf**
_Output :_
# ...some comments...
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

**dmesg | grep -e eth0 -e bcm**
_Output :_
<No output>

After seein previous posts i tried installin 
compat-wireless-2.6.tar.bz2

But then i got the following error
anil@anil-laptop:~/Desktop/compat-wireless-2011-03-10$ sh scripts/driver-select atl1c
scripts/driver-select: 47: function: not found
-e Usage: scripts/driver-select [ <driver-name> | <driver-group-name> | restore ]
-e Supported 802.11 drivers:
-e 	ath5k
-e 	ath9k
-e 	ath9k_htc
-e 	carl9170
-e 	b43
-e 	zd1211rw
-e 	rt2x00
-e 	wl1251
-e 	wl12xx
-e 	ath6kl
-e 	brcm80211
-e 
Supported group drivers:
-e 	atheros <  ath5k ath9k carl9170 zd1211rw >
-e 	ath <  ath5k ath9k carl9170 >
-e 	iwlagn <  iwlagn >
-e 	rtl818x <  rtl8180 rtl8187 >
-e 	rtlwifi <  rtl8192ce >
-e 	wl12xx <  wl1251 wl12xx (SPI and SDIO)>
-e 
Supported group drivers: Bluetooth & Ethernet:
-e 	atlxx <  atl1 atl2 atl1e atl1c >
-e 	bt <  Linux bluetooth drivers >
-e Restoring compat-wireless:
-e 	restore: you can use this option to restore compat-wireless to the original state
scripts/driver-select: 71: Syntax error: "}" unexpected


 Any help is appreciated

---

### Post by pytheas22 on 2011-03-11
**Anil hegde**: thanks for the output you posted, but I'm afraid it doesn't indicate which hardware you have.  I'll need to know that before I can figure out what's probably going wrong for you.  Please post the output of these commands when you are able:
```

lspci -nn
lshw -C Network
uname -a
```

---

### Post by Anil hegde on 2011-03-12
Tis is the output of cmds u specified

anil@anil-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
03:00.0 Network controller [0280]: Intel Corporation WiFi Link 1000 Series [8086:0083]
04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
anil@anil-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:17:8c:04
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=10.158.240.55 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:33 memory:f0500000-f0501fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)
anil@anil-laptop:~$ uname -a
Linux anil-laptop 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux

---

### Post by pytheas22 on 2011-03-12
**Anil hegde**: thanks for the output. Your ethernet hardware should be supported by the compat-wireless code, so compiling that should solve your problem.  When you tried to compile it before and ran into an error, it was probably because you tried calling one of the scripts with "sh" instead of "bash."  Please try compiling compat-wireless using the exact commands specified in post #6 of this thread, and it should work for you (you may need to reboot for the new driver to take effect).  If not, please post all the output you get, along with:
```

dmesg | grep -e atl1c
ifconfig
lshw -C Network
```

---

### Post by Anil hegde on 2011-03-12
Sir i tried it using bash but same error


tis is the o/p of other cmds


anil@anil-laptop:~/Desktop$ dmesg | grep -e atl1c
anil@anil-laptop:~/Desktop$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69740 (69.7 KB)  TX bytes:69740 (69.7 KB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:17:8c:04  
          inet addr:172.16.41.53  Bcast:172.16.47.255  Mask:255.255.248.0
          inet6 addr: fe80::8ea9:82ff:fe17:8c04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3648877 (3.6 MB)  TX bytes:40703 (40.7 KB)

anil@anil-laptop:~/Desktop$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:17:8c:04
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=172.16.41.53 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:32 memory:f0500000-f0501fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)

---

### Post by pytheas22 on 2011-03-12
hmmm, I just ran those commands using the latest version of compat-wireless and they worked without an issue.  Could you post the exact commands you're entering when you try to compile compat-wireless, along with the exact output you get?

In case it wasn't clear, I think the reason you're getting an error when try to run the driver-select script is because you were running it with the command:
```

sh scripts/driver-select atl1c
```

It should work if you call it with just
```

scripts/driver-select atl1c
```

---

### Post by Anil hegde on 2011-03-13
when i run without sh i.e scrits/driver-select i get the following error


must run scripts/driver-select from the compat-wireless top level directory

???????????? wat to do next?:confused:

---

### Post by Anil hegde on 2011-03-13
@[[COLOR=#D40000]**pytheas22**[/COLOR]]("http://ubuntuforums.org/member.php?u=358340") Problem solved..... Thanks for all your support....Truly grateful to you sir.

Wat i did was to redownload the compat-wireless file and then followed the same commands in thread #6 and to my surprise it worked..

Thanks a lot:lolflag:

Cheers:popcorn:

---

### Post by pytheas22 on 2011-03-13
**Anil hegde**: good to hear.  Maybe you got a bad copy of the compat-wireless code the first time you downloaded it, for some reason.  In any case, enjoy Ubuntu :)

---

### Post by knighteyres on 2011-04-20
I'm having a problem with my wired ethernet. wireless works great, but I would still like to have wired in case I need it
I ran these commands. I am using ubuntu10.4     Thanks

cat /etc/network/interfaces
cat /etc/NetworkManager/nm-system-settings.conf
dmesg | grep -e eth0 -e bcm
ifconfig -a




 cat /etc/network/interfaces
auto lo
iface lo inet loopback

 cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


 dmesg | grep -e eth0 -e bcm
[   13.167290] eth0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
[   23.896534] eth0: no IPv6 routers present


 ifconfig -a
eth0      Link encap:Ethernet  HWaddr ec:55:f9:24:5c:08  
          inet addr:192.168.120.36  Bcast:192.168.120.255  Mask:255.255.255.0
          inet6 addr: fe80::ee55:f9ff:fe24:5c08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4031 errors:0 dropped:0 overruns:0 frame:1744
          TX packets:3747 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3381153 (3.3 MB)  TX bytes:606196 (606.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

---

### Post by arch0njw on 2011-04-20
knighteyres,

run this and post the output: lspci

---

### Post by knighteyres on 2011-04-21
jody@jody-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

---

### Post by arch0njw on 2011-04-21
knighteyres,

You're having exactly the same problem I had with exactly the same hardware.  I blogged about my solution here:

[http://arch0njw.wordpress.com/2011/02/18/acer-aspireone-d255-wireless-network-and-kubuntu/](http://arch0njw.wordpress.com/2011/02/18/acer-aspireone-d255-wireless-network-and-kubuntu/)

Those steps worked for me.  Let me know if that helps.

---

### Post by pytheas22 on 2011-04-21
arch0njw: thanks for the tip.  Hopefully that will solve it.  If not, knighteyres, please post back and we can try some other things.

---

### Post by Brouham on 2011-04-21
I had problems with the Atheros AR8151 ethernet port on my new motherboard. I couldn't find a clean, working copy of the driver pack talked about in this forum. However, it doesn't matter because I upgraded to Ubuntu 11.04 beta and the correct driver is embedded in that release and the Atheros ethernet port worked automatically after upgrading. I know that the final release is next week but I couldn't wait and it is running great as a beta release.

---

### Post by arch0njw on 2011-04-21
Brouham,

Thanks for the update on that.  It's good to know there are updated drivers to look forward to.

---

### Post by vanyat77 on 2011-08-24
Hi, Thanks to you I too have now an working wired ethernet. What I already had expected is that after an update it doesn work anymore. I`ll need to install the driver again. Nevertheless with the working wired connection I couldn't get the wireless to work even after these commands:
sudo apt-get install bcmwl-kernel-source
echo wl | sudo tee -a /etc/modules

---

### Post by vanyat77 on 2011-08-24
@pytheas22
Hi, I've got my wired end wireless connection working thanks to you. Keep up the good work!

---

### Post by smith.mincha on 2011-09-26
So i finally get everything working on my toshiba satellite c650d-007! Only one thing left, the Ethernet, which is a[COLOR=black] Atheros AR8152/8158 PCI-E.

When i run theses commands (given on the first page of this thread):

[/COLOR]tar -xjvf compat-wireless-2.6.tar.bz2 
cd compat-wireless* 
scripts/driver-select atl1c 
make 
sudo make install

All seems to have gone well, it installs fine, and when i reboot i can even use the Ethernet for a while!

Except after about 1-2 mins everything freezes and stays frozen, I reboot again and i get the same issue.

Luckily i made a backup of my system in a .tar so i start-up in command line mode and reset my system. Everything works again (save the Ethernet).

I have done this many times and always my system freezes after reboot from installing the Ethernet drivers.

Any ideas??? I would love to have completely everything working on my laptop.:mad:
[COLOR=black]
[/COLOR]

---

### Post by pytheas22 on 2011-09-26
**smith.mincha**: first of all, which version of Ubuntu are you using?  In Ubuntu 11.04 and later, the ethernet driver for the device dealt with earlier in this thread is already built-in, so the wired connection should "just work" (assuming your device is indeed the same as that of others in this thread).  If you are on Ubuntu 11.04 or later, I wonder if your dmesg provides any clues on why it's not working out-of-the-box.  What output do you get from:
```

lspci -nn
dmesg | grep -e eth -e atl
```

Otherwise, if you do need to compile the driver from source, my first suggestion would be to try using an older version of the compat-wireless code.  It's possible that the code you compiled from happened to be a bad snapshot, where there was some bug present that causes your system to freeze after a few minutes.  At [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) you can download snapshots from particular dates.  (If you just download the file "compat-wireless-2.6.tar.bz2" it will give you the most recent snapshot.)  I'd try an older one to see if that makes a difference.

---

### Post by mbpram on 2011-09-29
Hi

I am using ubuntu 10.04 LTS OS. Re-installed it recently coz i had to clean up my harddisk. Thought of reinstalling the whole OS n did it... But my wired and wireless network are not working. I tried the steps given in the first page of this thread but with no success. I think my ethernet card is not getting detected because the mac address shows 00:00:00:00:00:00  
I am posting the output of the commands....

1. **ifconfig -a**

eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

pan0      Link encap:Ethernet  HWaddr 2a:a2:7c:82:e7:2e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:00:a2:5d:e9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


2. [B]dmesg | grep -e eth0 -e bcn
[/B]
[    0.990441] eth0: RTL8102e at 0xf8442000, 00:00:00:00:00:00, XID 14a00000 IRQ 30


3. **cat /etc/network/interfaces**

auto lo
iface lo inet loopback


4. **cat /etc/NetworkManager/nm-systems-settings.conf**

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

5. **ifup eth0**

Ignoring unknown interface eth0=eth0.

6. **lspci**

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


Please help me solve this problem....

---

### Post by pytheas22 on 2011-09-29
**mbpram**: please post the output of:
```

lspci -nn
```

The "-nn" part is important.  You didn't include it when you ran the command before.

Also, with your Ubuntu CD inserted in the drive, run the Hardware Drivers program (you can find it in the menu, or launch it from a terminal by typing "sudo jocket-gtk") and follow the instructions.  You may be able to get the driver for your wireless card installed that way (but to know for sure how to make your wireless work, I need to see your "lspci -nn" output).

---

### Post by mbpram on 2011-09-29
Hi 
I tried the sudo jockey-gtk command but it asks for internet to activate the sta n another driver. I am posting the result of lspci -nn command

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

Waiting for the reply as well as solution...!!! 
Thank u

---

### Post by jamesisin on 2011-09-29
> **pytheas22 said:**
> To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking).  Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```

Those first two commands won't work without a network connection.  Everything else seems to do the job.  Please confirm there is no reason to bother with those first two commands.

---

### Post by andriansah on 2011-09-30
> **jamesisin said:**
> Those first two commands won't work without a network connection.  Everything else seems to do the job.  Please confirm there is no reason to bother with those first two commands.


It's okay, just skip the first 2 line and start on ./scripts/driver-select


Now is how can I make the wireless up

---

### Post by pytheas22 on 2011-09-30
**jamesisin**: you only need the first two commands if you don't have a compiler and other build dependencies installed.  Apparently you already had a compiler installed on your system, since the rest of the commands worked without issue.  So you're all set.

**mbpram**: what output do you get from these commands (run them in this order, with your ethernet cable plugged into your router):
```

dmesg | grep -ie realtek -ie rtl -ie r8 -re 8136
lshw -C Network
sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:1a:2b:56:78:09
sudo ifconfig eth0 up
sudo dhclient eth0
```

Some commands may have no output.

---

### Post by jamesisin on 2011-09-30
That that's all well and good, but keep in mind that anyone attempting to get this nic working won't have Internet access either.  You may want to put a note on the original post where you added these instructions for less tech-savy users.

---

### Post by pytheas22 on 2011-09-30
> **jamesisin said:**
> That that's all well and good, but keep in mind that anyone attempting to get this nic working won't have Internet access either.  You may want to put a note on the original post where you added these instructions for less tech-savy users.

Yes, I agree that would be helpful--although I originally wrote those instructions for one user and had no idea so many others were going to latch onto this thread (though I'm glad it's proved to be helpful).  It was never supposed to be a tutorial or how-to for the masses.  So please don't be too harsh with the criticism; I'm doing the best I can here :)

---

### Post by jamesisin on 2011-10-02
Hahaha.  You're just gonna have to learn how to live with your sudden fame and success.

---

### Post by mbpram on 2011-10-04
Hi sorry for late reply.... Had my term exams.
I did run the commands in the given order with my ethernet cable plugged... I m puttin the o/p

**1.dmesg | grep -ie realtek -ie rtl -ie r8 -re 8136**

[    1.008869] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.008887] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.008927] r8169 0000:03:00.0: setting latency timer to 64
[    1.008995] r8169 0000:03:00.0: irq 31 for MSI/MSI-X
[    1.009666] eth0: RTL8102e at 0xf8572000, 00:00:00:00:00:00, XID 14a00000 IRQ 31

**2.lshw -C Network**

  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:db600000-db603fff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:31 ioport:6000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:00:a2:5d:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

[B]3.sudo ifconfig eth0 down
4.sudo ifconfig eth0 hw ether 00:1a:2b:56:78:09
5.sudo ifconfig eth0 up[/B]
After executing these commands i was able to connect with the internet using the wired network...:p. Still my wireless does not work. So i installed the wireless drivers, then the wireless network got detected but wen tried to connect it showed connecting for may be 20 min or so n finally did not connect. Also wen i rebooted, the wired network was again down. If i execute those three commands again i was able to get the wired network. 

**6.sudo dhclient eth0**

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:1a:2b:56:78:09
Sending on   LPF/eth0/00:1a:2b:56:78:09
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.7 from 192.168.1.1
DHCPREQUEST of 192.168.1.7 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.7 from 192.168.1.1
bound to 192.168.1.7 -- renewal in 19390 seconds.

---

### Post by pytheas22 on 2011-10-04
**mbpram**: those commands had you set a MAC address manually for the ethernet.  It seems that it works once you do this.  You could write a boot script to set the MAC address automatically when your computer boots, so that it should connect on its own.  To write the appropriate boot script, type these commands:
```

sudo -s
cd /etc/init.d
echo -e "ifconfig eth0 down\nifconfig eth0 hw ether 00:1a:2b:56:78:09\nifconfig eth0 up" > ethernet-fix.sh
chmod +x ethernet-fix.sh
update-rc.d ethernet-fix defaults
```

After this the ethernet should just work whenever you boot your computer.  As for the wireless, please try connecting, then post the output of:
```

lshw -C Network
dmesg | grep -e wl
sudo iwlist scan
```

---

### Post by mbpram on 2011-10-05
HI i got my wired networking... Thank u very much... I executed the three commands but first two commands(ie **lshw -C Networks** n **dmesg | grep -e w1**) did not yield any result... Simply nothing... I tried aft disconnectin my wired network but stil no output... I m putting up the result for third command
3. **sudo iwlist scan**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:E9:00:00:02
                    ESSID:"Saismaran"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:4/5  Signal level:-59 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

Saismaran is my wireless network SSID and user name. I use a WAP and WAP2 key for security... I dont know why i didnt get o/p for first two commands...:(

---

### Post by pytheas22 on 2011-10-05
**mbpram**: when you type "lshw -C Network" you need to wait a second and it should show output.  It should definitely show you something so please give it another try.

As for the other command, it should be "dmesg | grep -e wl" with a lowercase L as the last character, not the number 1.  Please try that again as well.

---

### Post by mbpram on 2011-10-05
Hi sorry... I did not wait previously... The o/p is
1.[B]lshw -C Network
[/B]

*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:a2:5d:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:db600000-db603fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:2b:56:78:09
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.7 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:6000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


2.**mesg | grep -e wl**


[   16.638361] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.650107] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.650120] wl 0000:02:00.0: setting latency timer to 64


3.**sudo iwlist scan**

lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

eth1 Scan completed :
Cell 01 - Address: 00:15:E9:00:00:02
ESSID:"Saismaran"
Mode:Managed
Frequency:2.422 GHz (Channel 3)
Quality:4/5 Signal level:-59 dBm Noise level:-92 dBm
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : TKIP CCMP
Authentication Suites (1) : PSK
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s

---

### Post by pytheas22 on 2011-10-06
**mbpram**: please give the instructions in [this blog post]("http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx") a try.  I think they apply to your situation.

---

### Post by mbpram on 2011-10-16
Hi I checked the link you gave and then tried out both the solutions given there. But the problem still exists. The wireless network gets detected n everything is fine. When i try to connect it takes forever to connect n ultimately I wont be able to connect... Please help me out...!!

---

### Post by pytheas22 on 2011-10-19
**mbpram**: sorry not to respond sooner.  I am in the middle of traveling.

You might have better luck connecting if you use wicd instead of NetworkManager.  You can find wicd in the Ubuntu Software Center.  Please give that a try.

---

### Post by arshiya on 2011-12-05
i do the same steps above  i got the same problem but when i run sudo modprobe atl1c         the output is like this FATAL : atl1c module not found .....anyone  knows how to fix this ......please help

---

### Post by arshiya on 2011-12-05
guys i got the same problem and i have done all the steps above when i run this command sudo modprobe atl1c the output is like this  FATAL: atl1c module not found .....anyone knows how to fix this please help me

---

### Post by pytheas22 on 2011-12-06
**arshiya**: please post all the commands you are trying to run to solve the problem, along with the output.  We will need that information to know why the particular command you mentioned produces a fatal error.

---

### Post by ianlone81 on 2011-12-12
I have problems also similar with that. heres the info;

 [FONT=Calibri]1.       [/FONT]Machine Name brand and model :Laptop Acer Aspire 4743Z Windows7 64-bit Home Basic Edition


  Im using backtrack5 in my VMware Player version 3.1.3 build-324285
   
  [FONT=Calibri]2.       [/FONT]Wireless Brand,Model & wireless chipset : 
  Atheros ARB5B97 wireless network adapter
   
  Im using Realtek  RTL8191su adapter in which it cannot detect wireless in the VMware player.
   
  Code I entered:
  $lsusb  -     Bus: 001
                    Device :002
                    ID Obda: 8172u
   
  [FONT=Calibri]3.       [/FONT]Check interface – 
  $iwconfig wlan1 
  unassociated nickname : “rtl_wifi”
  Mode: auto Access point: not associated  sensitivity:0/0
  Retry: off RTS thr: off   fragment thr: off
  Encryption key: of
  Link quality:0 signal level:0 noise level:0
  Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
  Tx excessive retries:0 invalid misc: 0 missed beacon
   
  $if wconfig
  Eth0 link encap: Ethernet
           Int addr:  I see ip add here
          Up broadcast running multicast
          Some packets & zero’s down & errors. Etc.
   
  L0 link encap: local loopback
       Net addr: Ip add again
       Up loopback running


  [FONT=Calibri]4.       [/FONT]$Lshw –C network
  *network disabled
  Description: wireless interface
  Physical ID:2
  Bus info: usb@1:1
  Logical name: wlan1
  Configuration:broadcast:yes,driver:r8172u,multicast:yes,wireless:unassociated
  [FONT=Calibri]5.       [/FONT]Scan for network;
  $iwlist scan
  Lo : interface doesn’t support scanning
  Eth0:interface doesn’t support scanning
  Wlan1: no scan result
   
  [FONT=Calibri]6.       [/FONT]Ubunto version.
  Ubunto 10.04.2 LTS


  [FONT=Calibri]7.       [/FONT]Kernel architecture
  2.6.38.i686
   
  Hope you can help me solve this problem.Please state any more code and result  to be posted if any.

---

### Post by pytheas22 on 2011-12-12
ianlone81: I'm a little confused as to what exactly you're trying to do.  Do you have your wireless card working correctly on your Ubuntu 10.04 system, but it is not being detected inside the backtrack5 system that you're running inside a virtual machine hosted on Ubuntu 10.04?  If that's the case, it's probably an issue with the "passthrough" feature of VMware (I'm not even sure whether VMware Player supports this), which I don't know much about.  You'd be better off starting a thread in the virtualization section of this forum.

If your wireless card isn't working on Ubuntu 10.04, then that's a different problem, but in that case I'm not sure what VMware has to do with it.

Please clarify a bit and I'd be happy to help if I can.

---

### Post by ianlone81 on 2011-12-13
ok sorry. when i start open vmware and start bt5, in the virtual machine and removable device section i can see in the lower right  that the wireless adpater was connected so i guess it was detected. what im trying to do is to detect nearby wireless signal. here's the thread i started. [http://ubuntuforums.org/showthread.php?p=11535895#post11535895](http://ubuntuforums.org/showthread.php?p=11535895#post11535895)

---

### Post by andreazana on 2012-01-31
Hello, I'm begging for some help here. I've got an HP Pavilion dv4, intel i5. I've installed Ubuntu 10.04 and at first I couldn't make a connection, not wired nor wireless. Following the instructions of the first page of this thread, I managed to achieve a wired connection, but after reading almost every post I still can't connect wiressly. I have an Atheros card. I've already done apt-get update and tried with every winXP 32-bits driver listed here: [http://www.atheros.cz/atheros-wireless-drivers.php](http://www.atheros.cz/atheros-wireless-drivers.php) and ndiswrapper. Here is some info to save time:

**ifconfig**
eth0      Link encap:Ethernet  direcciónHW 78:e3:b5:60:ee:66  
          Direc. inet:192.168.1.7  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::7ae3:b5ff:fe60:ee66/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:91750 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:70552 errores:0 perdidos:0 overruns:0 carrier:3
          colisiones:0 long.colaTX:1000 
          Bytes RX:129819312 (129.8 MB)  TX bytes:6754352 (6.7 MB)
          Interrupción:33 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:292 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:292 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:22088 (22.0 KB)  TX bytes:22088 (22.0 KB)


**ifconfig -a**

eth0      Link encap:Ethernet  direcciónHW 78:e3:b5:60:ee:66  
          Direc. inet:192.168.1.7  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::7ae3:b5ff:fe60:ee66/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:91754 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:70557 errores:0 perdidos:0 overruns:0 carrier:3
          colisiones:0 long.colaTX:1000 
          Bytes RX:129819623 (129.8 MB)  TX bytes:6754703 (6.7 MB)
          Interrupción:33 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:292 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:292 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:22088 (22.0 KB)  TX bytes:22088 (22.0 KB)

pan0      Link encap:Ethernet  direcciónHW 96:f8:ef:ea:65:83  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)


[B]lshw -C network

[/B]eth0      Link encap:Ethernet  direcciónHW 78:e3:b5:60:ee:66  
          Direc. inet:192.168.1.7  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::7ae3:b5ff:fe60:ee66/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:91754 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:70557 errores:0 perdidos:0 overruns:0 carrier:3
          colisiones:0 long.colaTX:1000 
          Bytes RX:129819623 (129.8 MB)  TX bytes:6754703 (6.7 MB)
          Interrupción:33 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:292 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:292 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:22088 (22.0 KB)  TX bytes:22088 (22.0 KB)

pan0      Link encap:Ethernet  direcciónHW 96:f8:ef:ea:65:83  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
[B]
dmesg | grep eth

[/B][   17.725411] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.219637] atl1c 0000:08:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   19.219743] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  252.267003] atl1c 0000:08:00.0: atl1c: eth0 NIC Link is Down
[  366.408595] atl1c 0000:08:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  371.852146] NETDEV WATCHDOG: eth0 (atl1c): transmit queue 0 timed out
[  371.877185] atl1c 0000:08:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>


**lspci -nn**

00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1c.4 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 5 [8086:1c18] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
01:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)
02:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)
02:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 30)
08:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)

Sorry if the post is long, but I'm desperate and I would really appreciate some help.

Thanks already!

---

### Post by pytheas22 on 2012-02-02
**andreazana**: it looks like you actually have an Intel wireless card, with PCI ID 8086:008b.  Only your ethernet card is Atheros.

Your wireless device should be supported by the iwlagn driver, which is built into Ubuntu, so I'm not sure why it's not working.  I'm afraid I have to ask for more output to know what could be wrong.  Please post the results of:
```

dmesg | grep -ie iwl -ie wlan
lshw -C Network
sudo iwlist scan
uname -a
```

---

### Post by andreazana on 2012-02-02
**pytheas22: **

Hello and thank you very much for answering. Here are the results:
[B]
dmesg | grep -ie iwl -ie wlan[/B]

(no output)

**lshw -C Network**

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c2500000-c2501fff
  *-network
       description: Ethernet interface
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: 78:e3:b5:60:ee:66
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI ip=192.168.1.7 latency=0 multicast=yes
       resources: irq:33 memory:c1400000-c143ffff ioport:2000(size=128)

**sudo iwlist scan**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


**uname -a**

Linux flaca 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux


Only one more thing. Today some one gave me a CD with a Debian ISO (
[debian-live-6.0.3-i386-gnome-desktop.iso]("http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.3-i386-gnome-desktop.iso")). Do you think that installing 
Debian could solve my problem? It's just that I already have some school 
projects to develop and I'm kind of desperate... Thanks again and have a wonderful evening!

---

### Post by pytheas22 on 2012-02-03
**andreazana**: it looks like you're using a somewhat old kernel, version 2.6.32.  I'm not positive but that version might not have the iwlagn driver that you need built-in.  You could compile and install it yourself, but an easier solution might be just to try installing a more up-to-date release of Ubuntu.  Ubuntu 11.10 should definitely have the driver you need.

If you do want to compile the driver from source, you can get the code from [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) and follow the instructions there for building it.  If you need more specific help than what's there I can give it.

As for Debian, I'm not sure whether it will work any better.  It depends on whether or not it has the iwlagn driver built-in and I'm not sure.  (It's been a while since I've used Debian myself.)

Also, just in case it's simply a problem with the iwlagn driver not loading, try typing:
```

sudo modprobe iwlagn
```

and then see whether the command "dmesg | grep -ie iwl -ie wlan" produces any output.  If so, please post the output here.  I doubt this is the issue, though -- most likely the iwlagn driver simply doesn't exist on your system (or the version of iwlagn that you have is too old to support your hardware).

If you are really desperate to get Linux running so you can do work, you could also always just install it inside a virtual machine on Windows using VirtualBox or VMware.  It won't be the same as a bare-metal installation but it would be the quick-and-easy route.

---

### Post by flightrisk on 2012-02-04
Greetings.  This is an excellent forum and I apologize if I'm going about this the wrong way.....I'm not real familiar with the ins and outs here.  I have the same problem as above in that I cannot get wired ethernet going on a fresh install of Lucid on an Acer Aspire One with Atheros 8152 controller.  I can't get past the whole "build-essential" thing, though.  I keep getting a "please insert the disk labeled: Ubuntu 10.04....".  I installed the OS via iso image on a USB which I still have available and am apparently not smart enough to figure out how to use.

I have managed to install fakeroot, patch, xz-utils, and dpkg-dev.
As I understand it I still need libstdc++6-4.4-dev, g++, g++-4.4, and build-essential.

Any help would be greatly appreciated and keep up the good work.

---

### Post by pytheas22 on 2012-02-05
**flightrisk**: first of all, on Lucid I don't think you should have to compile the driver from source.  It should be built in.  It would be good to see the output of these commands on your system to get a better idea of what might be wrong:
```

lspci -nn
sudo modprobe atl1c
dmesg | grep -e eth -e ath
ifconfig
```

If you don't want to compile the driver, though, you should be able to solve the issue with being asked for the CD by opening the Ubuntu Software Center, going to Edit>Software Sources, unchecking any and all boxes related to CDs and DVDs, then reloading the software sources list.  (The sources list should be reloaded automatically but in case it is not you can do it manually by typing "sudo apt-get update")

---

### Post by flightrisk on 2012-02-05
PYTHEAS22....you're a diamond.  You actually solved most of this problem about 25 pages and a year ago if I'd have been smart enough to read all the words correctly.  I went back and went through it for about the 10th time and finally got the wired connection to work.  I was superimposing some words over each other and wasn't getting the right outcome.  

It's embarrassing but I'm not real sure how to post the results of command line outputs here like everyone has done so I'm gonna search on that for a bit and I'll attempt to post those for you real soon.  

Again, thanks for the help.

---

### Post by pytheas22 on 2012-02-05
> PYTHEAS22....you're a diamond. You actually solved most of this problem about 25 pages and a year ago if I'd have been smart enough to read all the words correctly. I went back and went through it for about the 10th time and finally got the wired connection to work. I was superimposing some words over each other and wasn't getting the right outcome.

It's embarrassing but I'm not real sure how to post the results of command line outputs here like everyone has done so I'm gonna search on that for a bit and I'll attempt to post those for you real soon.

Again, thanks for the help. 

Glad it helped.  This thread has become so large I no longer remember what it contains :)

You can copy output from the terminal by highlighting it with your mouse cursor, right-clicking and selecting "Copy."  Then just paste into your Web browser as normal to get it here.

Alternatively, just highlight the text and (with the text still highlighted) switch to the Web browser window and press your mouse's middle button (the scroll wheel).  That's an abbreviated way of copying and pasting in Linux.

---

### Post by flightrisk on 2012-02-05
OK, I'm gonna give this a shot
klaw@klaw-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1510]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9807]
00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1314]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:15.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a0]
00:15.2 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a2]
00:15.3 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a3]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1719]
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
07:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0032] (rev 01)
klaw@klaw-laptop:~$ 
klaw@klaw-laptop:~$ sudo modprobe atl1c
klaw@klaw-laptop:~$
klaw@klaw-laptop:~$ dmesg | grep -e -wl -e ath
[    1.031642] device-mapper: multipath: version 1.1.0 loaded
[    1.031647] device-mapper: multipath round-robin: version 1.0.0 loaded
klaw@klaw-laptop:~$ 
klaw@klaw-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr dc:0e:a1:4f:db:6d  
          inet addr:192.168.1.146  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::de0e:a1ff:fe4f:db6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2098 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2802861 (2.8 MB)  TX bytes:240602 (240.6 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

I may have dislocated this whole thing.  Let me know if you can make heads and tails of this.

---

### Post by pytheas22 on 2012-02-06
Your ethernet card seems to be up and working without a problem.  You even have an IP address on it.  So everything looks alright there.

For the wireless, it should work using the ath9k driver, which is built into more recent versions of Ubuntu but may not exist in Ubuntu 10.04 (I don't remember whether it was there).  To solve this problem you have two options: either upgrade to a more recent version of Ubuntu, or compile the ath9k driver manually from source.  For specific instructions on the latter option, see post 63 of [this thread]("http://ubuntuforums.org/showthread.php?t=1857808&page=7").

---

### Post by flightrisk on 2012-02-06
PYTHEAS22....ya, it's looking like I'll probably move over to 11.10 here pretty soon.  I was a huge fan of Lucid as it worked on a old,  pretty much worthless netbook of mine for over a year with zero problems.  I finally scrounge up enough cash to get this new Aspire One and it turns out 10.04 doesn't seem to work too well on it.  Oh well......whatch gonna do.  

I want to thank you, again, for the help.  No way I would have gotten as far along as I did without it.  

Cheers

---

### Post by satish_j on 2012-02-17
@pytheas22,can you pls tell me the significance of tag
```

[ifupdown]
managed=false

```
in file /etc/NetworkManager/nm-system-settings.conf.
I have this set to true and i have been facing frequent Network crashes for Lucid.I have raised a separate thread for my issue,but that has not been of much help.I was wondering whether this tag may be the source of the problem..

---

### Post by pytheas22 on 2012-02-17
**satish_j**: I didn't know what that meant exactly, but according to the man page for NetworkManager.conf (type "man NetworkManager.conf"; if that doesn't work try "man nm-system-settings.conf" as the name of the file seems to be different on Lucid):

> [ifupdown]

This section contains ifupdown-specific options and thus only has effect when using ifupdown plugin.

managed=false | true

Controls whether interfaces listed in the 'interfaces' file are managed by NetworkManager.  If  set to true, then interfaces listed in /etc/network/interfaces are managed by NetworkManager.  If set to false, then any interface listed in  /etc/network/interfaces  will  be  ignored  by  NetworkManager.  Remember  that  NetworkManager controls the default route, so because the interface is ignored, NetworkManager may assign the default route to some other interface.  When the option is missing, false value is taken as default.

I gather from that that this is a way to tell NetworkManager not to try to control a particular device.  However, it seems that it only takes effect if you add a device name to the configuration file -- by default my file just looks like this:

```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

and so even though the managed=false flag is set, it's not doing anything because no devices are mentioned anywhere in the file.

I guess this is a bit convulted, but hopefully it clears it up.  If you still need help with your issue feel free to ask.

---

### Post by satish_j on 2012-02-18
> **pytheas22 said:**
> **satish_j**: I didn't know what that meant exactly, but according to the man page for NetworkManager.conf (type "man NetworkManager.conf"; if that doesn't work try "man nm-system-settings.conf" as the name of the file seems to be different on Lucid):



I gather from that that this is a way to tell NetworkManager not to try to control a particular device.  However, it seems that it only takes effect if you add a device name to the configuration file -- by default my file just looks like this:

```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

and so even though the managed=false flag is set, it's not doing anything because no devices are mentioned anywhere in the file.

I guess this is a bit convulted, but hopefully it clears it up.  If you still need help with your issue feel free to ask.


Thanks for the revert,i will try keeping this tag to false and monitor the crash issue on my system for some time.Also,came to know from other threads about NetworkManager.state file which should have enabled=true for networking.
BTW,can you suggest what logs should be checked immediately after network crashes to check whether anything of relevance be found in them.Ichecked kern.log but it does not capture anything.

---

### Post by pytheas22 on 2012-02-18
> BTW,can you suggest what logs should be checked immediately after network crashes to check whether anything of relevance be found in them.Ichecked kern.log but it does not capture anything.

Did you try /var/log/syslog?

---

### Post by tedmar on 2012-03-14
> **pytheas22 said:**
> Your ethernet hardware seems to be quite new and doesn't have a driver built into Ubuntu as of yet.  However, there's a driver included in the compat-wireless stack that you can use (I have no idea why they included an ethernet driver in compat-wireless, but according to [these emails]("http://omgili.com/mailinglist/kernel-team/lists/ubuntu/com/43e72e891002020915x572a11fcg57f0b9caf7ed08eamailgmailcom.html"), someone did).

To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking).  Save it to your desktop. Then run these commands (the first two commands require that you either have an Internet connection, or have your [Ubuntu installation CD enabled as a software repository]("https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD")):
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```

Then reboot.  Hopefully your ethernet will work automatically after reboot; if not, run:
```

sudo modprobe atl1c
```

to insert the driver.  Let me know how it goes.

We can probably make your wireless work too, if you're interested.
I have a Lenovo G470 notebook recently acquired which has an Atheros AR8152 v 2.0 Fast Ethernet (rev c1); the result is that ethernet wired card is not visible (only the wireless card as eth0); operating system is Ubuntu 10.04 32 bits
I tried to do the steps that you recommended but in the make step I obtain a compilation error:

make -C /lib/modules/2.6.32-39-generic/build M=/home/lautaro/Desktop/compat-wireless-2012-03-12 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-39-generic'
CC [M] /home/lautaro/Desktop/compat-wireless-2012-03-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.o
/home/lautaro/Desktop/compat-wireless-2012-03-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.c: In function ‘atl1c_set_mac_addr’:
/home/lautaro/Desktop/compat-wireless-2012-03-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.c:475: error: ‘struct net_device’ has no member named ‘addr_assign_type’
/home/lautaro/Desktop/compat-wireless-2012-03-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.c: In function ‘atl1c_probe’:
/home/lautaro/Desktop/compat-wireless-2012-03-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.c:2775: error: ‘struct net_device’ has no member named ‘addr_assign_type’
make[4]: *** [/home/lautaro/Desktop/compat-wireless-2012-03-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.o] Error 1
make[3]: *** [/home/lautaro/Desktop/compat-wireless-2012-03-12/drivers/net/ethernet/atheros/atl1c] Error 2
make[2]: *** [/home/lautaro/Desktop/compat-wireless-2012-03-12/drivers/net/ethernet/atheros] Error 2
make[1]: *** [_module_/home/lautaro/Desktop/compat-wireless-2012-03-12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-39-generic'
make: *** [modules] Error 2

Please, let me know where is my error

Thanks and regards

Tedmar

---

### Post by pytheas22 on 2012-03-15
**tedmar**: it's a compilation error, so you might have better luck if you downloaded a different snapshot of the source code (especially an older one).  The copy you got could just happen to have a bug in it.  At [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) you can grab copies from a wide range of different dates.

If that doesn't help, please post the output of:
```

lspci -nn
```

so I know exactly which chipset you have.

Also, chances are the device would "just work" if you upgraded to a more recent version of Ubuntu, if that is a possibility.  10.04 is not getting a bit old.

---

### Post by busols on 2012-04-14
hello every one!
first post here and thank you ubuntuforums.
this is a bit long, sorry.

Issues: not recognized by Ubuntu 2.6.38-14
1. AR8152 v2.0 Fast Ethernet
2. AR9485 Wireless Network

I have a laptop Acer aspire 5349-2899 [http://us.acer.com/ac/en/US/content/model/LX.RR902.132](http://us.acer.com/ac/en/US/content/model/LX.RR902.132)
this laptop runs on windows 7 home premium, can connect to the internet both wired and wireless, after a few hours of used and since I already have windows on the other laptop I decided to format the hard drive and give linux a shot ubuntu 2.6.38-14-generic, gnome 2.32.1 was installed, not too happy with unity, I played with the OS a bit, then I tried to connect to router but no wired and wireless card detected tried every possible ways to get online with no luck, I just blew up windows 7. so to be able to get online I used a realtek wireless n usb adapter which was recognized by ubuntu and connected to the internet and I was able to pull the existing wireless card driver to work using the instructions below.


acer@acer-Aspire-5349:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Acer Incorporated [ALI] Device [1025:0623]
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e047]
	Kernel driver in use: ath9k


acer@acer-Aspire-5349:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5344 (5.3 KB)  TX bytes:5344 (5.3 KB)

***this is when the wireless lan detected and operating***

wlan1     Link encap:Ethernet  HWaddr 64:27:37:33:91:25  
          inet addr:192.168.1.41  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:fe33:9125/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129755274 (129.7 MB)  TX bytes:3220428 (3.2 MB)


for the wireless card to be detected I followed the instructions provided praseodym here:
***[http://ubuntuforums.org/showthread.php?t=1857808&page=7***](http://ubuntuforums.org/showthread.php?t=1857808&page=7***)
from terminal:
1. sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
2. wget [http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)  
3. tar jxvf compat-wireless-2.6.tar.bz2
4. cd compat-wireless-20*
5. ./scripts/driver-select atheros 
6. make
7. sudo make install
8. sudo make unload
9. sudo make wlunload
10. sudo make btunload
11. reboot the laptop
these steps worked, laptop connects to router linksys WRT54G (tomato firmware) with wireless security WPA on, also connected to internet.

and for the wired ethernet I used the instructions provided by pytheas22 here:
***[http://ubuntuforums.org/showthread.php?t=1505697***](http://ubuntuforums.org/showthread.php?t=1505697***)
***first go to [http://linuxwireless.org/download/compat-wireless-2.6***](http://linuxwireless.org/download/compat-wireless-2.6***)
from terminal:
1. sudo apt-get update
2. sudo apt-get install build-essential
3. cd ~/Desktop
4. tar -xjvf compat-wireless-2.6.tar.bz2
5. cd compat-wireless-20*
6. scripts/driver-select atl1c
7. make
8. sudo make install
9. sudo make unload
10. sudo make wlunload
11. sudo make btunload
12. reboot the laptop
***these steps worked, wired ethernet detected and can connect to router and to the internet***.

the issue I'm having is I can't have both wired ethernet and wireless to be detected at the same time after startup. when I install the wired ethernet driver and is detected I lose the wireless connection then the wireless card disappear in the applet panel. It would be nice to have both wired and wireless LAN. please help me get the lan and wlan to be recognized by ubuntu at the same time I'm not going to use both at the same time but it would be nice. if you need more info on the hardware please let me know.
thank you.

acer@acer-Aspire-5349:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c3400000-c343ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan1
       version: 01
       serial: 64:27:37:33:91:25
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-14-generic firmware=N/A ip=192.168.1.41 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c2400000-c247ffff memory:c1400000-c140ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

acer@acer-Aspire-5349:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
02:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
acer@acer-Aspire-5349:~$

---

### Post by pytheas22 on 2012-04-15
**busols**: please post the output of these commands, in this order (some commands may have no output):
```

lsmod | grep -e atl -e ath
sudo rmmod atl1c
sudo rmmod ath9k
sudo modprobe atl1c
sudo modprobe ath9k
lshw -C Network
dmesg | grep -e atl -e ath
cat /etc/lsb-release
```

---

### Post by busols on 2012-04-15
hello Pytheas22;
thanks for the quick reply especially your precious time.
as instructed here's the results please let me know if i need me to repeat some commands.

acer@acer-Aspire-5349:~$ lsmod | grep -e atl -e ath
ath9k                 115574  0 
mac80211              451568  1 ath9k
ath9k_common           13780  1 ath9k
ath9k_hw              379900  2 ath9k,ath9k_common
ath                    19182  3 ath9k,ath9k_common,ath9k_hw
cfg80211              173697  3 ath9k,mac80211,ath
compat                 16044  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211

acer@acer-Aspire-5349:~$ sudo rmmod atl1c
[sudo] password for acer: 
ERROR: Module atl1c does not exist in /proc/modules

acer@acer-Aspire-5349:~$ sudo modprobe atl1c
FATAL: Module atl1c not found.

acer@acer-Aspire-5349:~$ sudo modprobe ath9k

acer@acer-Aspire-5349:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c3400000-c343ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan1
       version: 01
       serial: 64:27:37:33:91:25
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-14-generic firmware=N/A ip=192.168.1.41 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c2400000-c247ffff memory:c1400000-c140ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

acer@acer-Aspire-5349:~$ dmesg | grep -e atl -e ath
[    1.169030] device-mapper: multipath: version 1.2.0 loaded
[    1.169033] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.090018] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.090035] ath9k 0000:07:00.0: setting latency timer to 64
[   15.103378] ath: EEPROM regdomain: 0x6c
[   15.103381] ath: EEPROM indicates we should expect a direct regpair map
[   15.103385] ath: Country alpha2 being used: 00
[   15.103387] ath: Regpair used: 0x6c
[   15.121333] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.123795] Registered led device: ath9k-phy0

acer@acer-Aspire-5349:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Zorin OS 5.2"
acer@acer-Aspire-5349:~$

---

### Post by pytheas22 on 2012-04-15
**busols**: thanks for the output.  It seems that the atl1c module, which you need to drive your ethernet card, is not installed, which doesn't make much sense if you ran the script to compile it.  But let's see if it exists on your system anywhere.  What is the output of:
```

locate atl1c
```

---

### Post by busols on 2012-04-15
Hi Pytheas22;
thank you.

yes I managed to install the driver for the lan card AR8152 v2.0 Fast Ethernet via lan, can connect to router and internet but as soon as the lan card recognized by the system the wlan connection dropped and wireless applet dissappear from the panel. meaning the lan take over the network connection. loosing the wlan driver, this is what I'm not understanding why. I'm very new to linux so please bear with me.

here's the results:

acer@acer-Aspire-5349:~$ locate atl1c
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/.tmp_versions/atl1c.mod
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c.ko.cmd
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c.mod.o.cmd
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c.o.cmd
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c_ethtool.o.cmd
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c_hw.o.cmd
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c_main.o.cmd
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/Makefile
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.h
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.mod.c
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.mod.o
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.o
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.c
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.o
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.c
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.h
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.o
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.c
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.o
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/modules.order
/home/acer/Documents/linux/tools/wireless driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c
/home/acer/Documents/linux/tools/wireless driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/Makefile
/home/acer/Documents/linux/tools/wireless driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.h
/home/acer/Documents/linux/tools/wireless driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.c
/home/acer/Documents/linux/tools/wireless driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.c
/home/acer/Documents/linux/tools/wireless driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.h
/home/acer/Documents/linux/tools/wireless driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.c
/home/acer/Downloads/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c
/home/acer/Downloads/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/Makefile
/home/acer/Downloads/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.h
/home/acer/Downloads/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.c
/home/acer/Downloads/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.c
/home/acer/Downloads/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.h
/home/acer/Downloads/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.c
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c.ko.cmd
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c.mod.o.cmd
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c.o.cmd
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c_ethtool.o.cmd
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c_hw.o.cmd
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c_main.o.cmd
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/Makefile
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.h
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.mod.c
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.mod.o
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.o
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.c
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.o
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.c
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.h
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.o
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.c
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.o
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/modules.order
/lib/modules/2.6.38-12-generic/kernel/drivers/net/atl1c
/lib/modules/2.6.38-12-generic/kernel/drivers/net/atl1c/atl1c.ko
/lib/modules/2.6.38-14-generic/kernel/drivers/net/atl1c
/lib/modules/2.6.38-14-generic/kernel/drivers/net/atl1c/atl1c.ko.ignore
/lib/modules/2.6.38-14-generic/updates/drivers/net/ethernet/atheros/atl1c
/lib/modules/2.6.38-14-generic/updates/drivers/net/ethernet/atheros/atl1c/atl1c.ko.ignore
/usr/src/linux-headers-2.6.38-12/drivers/net/atl1c
/usr/src/linux-headers-2.6.38-12/drivers/net/atl1c/Makefile
/usr/src/linux-headers-2.6.38-12-generic/include/config/atl1c.h
/usr/src/linux-headers-2.6.38-14/drivers/net/atl1c
/usr/src/linux-headers-2.6.38-14/drivers/net/atl1c/Makefile
/usr/src/linux-headers-2.6.38-14-generic/include/config/atl1c.h
acer@acer-Aspire-5349:~$

---

### Post by busols on 2012-04-15
to add to that same scenario, when I install the driver for the wlan, the lan card is no longer active in the system, I might be doing something wrong besides compatibility issue, not designed to work with linux?? meaning both hardware can't be installed at the same time.

---

### Post by pytheas22 on 2012-04-16
You do have the atl1c driver installed but only for the 2.6.38-12 kernel.  My guess is that you upgraded your kernel but did not compile the driver again for the new kernel.  Try running these commands once more:
> 
***[http://ubuntuforums.org/showthread.php?t=1505697***](http://ubuntuforums.org/showthread.php?t=1505697***)
***first go to [http://linuxwireless.org/download/co...ireless-2.6***](http://linuxwireless.org/download/co...ireless-2.6***)
from terminal:
1. sudo apt-get update
2. sudo apt-get install build-essential
3. cd ~/Desktop
4. tar -xjvf compat-wireless-2.6.tar.bz2
5. cd compat-wireless-20*
6. scripts/driver-select atl1c
7. make
8. sudo make install
9. sudo make unload
10. sudo make wlunload
11. sudo make btunload
12. reboot the laptop
***these steps worked, wired ethernet detected and can connect to router and to the internet***.

Then reboot and the wired should probably work.  If it still doesn't, let me know the output at this point of:
```

uname -a
sudo modprobe atl1c
locate atl1c.ko
```

---

### Post by busols on 2012-04-16
Hi Pytheas22;
***thank you for your patience.
***please note: wlan ath9k is active at this point, internet is working.
***to avoid confusion. also note that the drivers used both lan and wlan (ath9k & atl1c) were in the same folder I downloaded.
***before installing the lan driver I ran the following commands:
uname -a
sudo modprobe atl1c
locate atl1c.ko
***results below***

acer@acer-Aspire-5349:~$ uname -a
Linux acer-Aspire-5349 2.6.38-14-generic #58-Ubuntu SMP Tue Mar 27 18:48:46 UTC 2012 i686 i686 i386 GNU/Linux
acer@acer-Aspire-5349:~$ sudo modprobe atl1c
[sudo] password for acer: 
FATAL: Module atl1c not found.
acer@acer-Aspire-5349:~$ locate atl1c.ko
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c.ko.cmd
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c.ko.cmd
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/lib/modules/2.6.38-12-generic/kernel/drivers/net/atl1c/atl1c.ko
/lib/modules/2.6.38-14-generic/kernel/drivers/net/atl1c/atl1c.ko.ignore
/lib/modules/2.6.38-14-generic/updates/drivers/net/ethernet/atheros/atl1c/atl1c.ko.ignore
acer@acer-Aspire-5349:~$ 


***lan driver installation commands intro*** steps 1 and 2 not triggered.
3. cd ~/Desktop
4. tar -xjvf compat-wireless-2.6.tar.bz2
5. cd compat-wireless-20*
6. scripts/driver-select atl1c
7. make
8. sudo make install

acer@acer-Aspire-5349:~$ cd ~/Desktop
acer@acer-Aspire-5349:~/Desktop$ tar -xjvf compat-wireless-2.6.tar.bz2
compat-wireless-2012-04-12/
compat-wireless-2012-04-12/compat_base_tree_version
compat-wireless-2012-04-12/compat_base_tree
compat-wireless-2012-04-12/.gitignore
compat-wireless-2012-04-12/pending-stable/
compat-wireless-2012-04-12/pending-stable/README
compat-wireless-2012-04-12/pending-stable/.ignore
compat-wireless-2012-04-12/Makefile
compat-wireless-2012-04-12/README
compat-wireless-2012-04-12/net/
compat-wireless-2012-04-12/net/mac80211/
compat-wireless-2012-04-12/net/mac80211/wpa.h
compat-wireless-2012-04-12/net/mac80211/debugfs_sta.h
compat-wireless-2012-04-12/net/mac80211/sta_info.c
compat-wireless-2012-04-12/net/mac80211/aes_ccm.c
compat-wireless-2012-04-12/net/mac80211/iface.c.orig
compat-wireless-2012-04-12/net/mac80211/ibss.c
compat-wireless-2012-04-12/net/mac80211/rc80211_minstrel_ht.h
compat-wireless-2012-04-12/net/mac80211/rc80211_pid_algo.c
compat-wireless-2012-04-12/net/mac80211/agg-rx.c
compat-wireless-2012-04-12/net/mac80211/driver-trace.h
compat-wireless-2012-04-12/net/mac80211/pm.c
compat-wireless-2012-04-12/net/mac80211/driver-ops.h
compat-wireless-2012-04-12/net/mac80211/status.c
compat-wireless-2012-04-12/net/mac80211/michael.c
compat-wireless-2012-04-12/net/mac80211/mesh_hwmp.c
compat-wireless-2012-04-12/net/mac80211/rc80211_minstrel_ht_debugfs.c
compat-wireless-2012-04-12/net/mac80211/key.h
compat-wireless-2012-04-12/net/mac80211/led.h
compat-wireless-2012-04-12/net/mac80211/cfg.h
compat-wireless-2012-04-12/net/mac80211/Makefile
compat-wireless-2012-04-12/net/mac80211/rc80211_pid.h
compat-wireless-2012-04-12/net/mac80211/debugfs_key.h
compat-wireless-2012-04-12/net/mac80211/agg-tx.c
compat-wireless-2012-04-12/net/mac80211/driver-ops.h.orig
compat-wireless-2012-04-12/net/mac80211/debugfs_sta.c
compat-wireless-2012-04-12/net/mac80211/mlme.c
compat-wireless-2012-04-12/net/mac80211/wep.h
compat-wireless-2012-04-12/net/mac80211/scan.c
compat-wireless-2012-04-12/net/mac80211/wme.c
compat-wireless-2012-04-12/net/mac80211/work.c
compat-wireless-2012-04-12/net/mac80211/offchannel.c
compat-wireless-2012-04-12/net/mac80211/cfg.c
compat-wireless-2012-04-12/net/mac80211/sta_info.h
compat-wireless-2012-04-12/net/mac80211/iface.c
compat-wireless-2012-04-12/net/mac80211/wme.h
compat-wireless-2012-04-12/net/mac80211/rate.c
compat-wireless-2012-04-12/net/mac80211/key.c
compat-wireless-2012-04-12/net/mac80211/tkip.h
compat-wireless-2012-04-12/net/mac80211/rx.c.orig
compat-wireless-2012-04-12/net/mac80211/aes_cmac.h
compat-wireless-2012-04-12/net/mac80211/mesh_plink.c
compat-wireless-2012-04-12/net/mac80211/rc80211_minstrel_ht.c
compat-wireless-2012-04-12/net/mac80211/tx.c
compat-wireless-2012-04-12/net/mac80211/aes_ccm.h
compat-wireless-2012-04-12/net/mac80211/mesh_sync.c
compat-wireless-2012-04-12/net/mac80211/led.c
compat-wireless-2012-04-12/net/mac80211/debugfs_key.c
compat-wireless-2012-04-12/net/mac80211/debugfs.h
compat-wireless-2012-04-12/net/mac80211/driver-trace.c
compat-wireless-2012-04-12/net/mac80211/wpa.c
compat-wireless-2012-04-12/net/mac80211/wep.c
compat-wireless-2012-04-12/net/mac80211/tkip.c
compat-wireless-2012-04-12/net/mac80211/spectmgmt.c
compat-wireless-2012-04-12/net/mac80211/debugfs_netdev.c
compat-wireless-2012-04-12/net/mac80211/michael.h
compat-wireless-2012-04-12/net/mac80211/chan.c
compat-wireless-2012-04-12/net/mac80211/util.c
compat-wireless-2012-04-12/net/mac80211/mesh.c
compat-wireless-2012-04-12/net/mac80211/rc80211_minstrel.h
compat-wireless-2012-04-12/net/mac80211/ieee80211_i.h
compat-wireless-2012-04-12/net/mac80211/debugfs_netdev.h
compat-wireless-2012-04-12/net/mac80211/main.c
compat-wireless-2012-04-12/net/mac80211/ht.c
compat-wireless-2012-04-12/net/mac80211/event.c
compat-wireless-2012-04-12/net/mac80211/tx.c.orig
compat-wireless-2012-04-12/net/mac80211/rate.h
compat-wireless-2012-04-12/net/mac80211/aes_cmac.c
compat-wireless-2012-04-12/net/mac80211/main.c.orig
compat-wireless-2012-04-12/net/mac80211/ieee80211_i.h.orig
compat-wireless-2012-04-12/net/mac80211/rc80211_minstrel.c
compat-wireless-2012-04-12/net/mac80211/rc80211_minstrel_debugfs.c
compat-wireless-2012-04-12/net/mac80211/rc80211_pid_debugfs.c
compat-wireless-2012-04-12/net/mac80211/rx.c
compat-wireless-2012-04-12/net/mac80211/debugfs.c
compat-wireless-2012-04-12/net/mac80211/mesh.h
compat-wireless-2012-04-12/net/mac80211/mesh_pathtbl.c
compat-wireless-2012-04-12/net/wireless/
compat-wireless-2012-04-12/net/wireless/nl80211.h
compat-wireless-2012-04-12/net/wireless/ibss.c
compat-wireless-2012-04-12/net/wireless/core.c
compat-wireless-2012-04-12/net/wireless/db.txt
compat-wireless-2012-04-12/net/wireless/core.c.orig
compat-wireless-2012-04-12/net/wireless/lib80211_crypt_wep.c
compat-wireless-2012-04-12/net/wireless/sme.c
compat-wireless-2012-04-12/net/wireless/Makefile
compat-wireless-2012-04-12/net/wireless/lib80211.c
compat-wireless-2012-04-12/net/wireless/sysfs.h
compat-wireless-2012-04-12/net/wireless/ethtool.c
compat-wireless-2012-04-12/net/wireless/mlme.c
compat-wireless-2012-04-12/net/wireless/scan.c
compat-wireless-2012-04-12/net/wireless/nl80211.c.orig
compat-wireless-2012-04-12/net/wireless/wext-priv.c
compat-wireless-2012-04-12/net/wireless/wext-sme.c
compat-wireless-2012-04-12/net/wireless/core.h
compat-wireless-2012-04-12/net/wireless/ethtool.h
compat-wireless-2012-04-12/net/wireless/wext-proc.c
compat-wireless-2012-04-12/net/wireless/lib80211_crypt_ccmp.c
compat-wireless-2012-04-12/net/wireless/debugfs.h
compat-wireless-2012-04-12/net/wireless/wext-compat.h
compat-wireless-2012-04-12/net/wireless/chan.c
compat-wireless-2012-04-12/net/wireless/util.c
compat-wireless-2012-04-12/net/wireless/mesh.c
compat-wireless-2012-04-12/net/wireless/nl80211.c
compat-wireless-2012-04-12/net/wireless/wext-compat.c
compat-wireless-2012-04-12/net/wireless/wext-core.c
compat-wireless-2012-04-12/net/wireless/radiotap.c
compat-wireless-2012-04-12/net/wireless/wext-spy.c
compat-wireless-2012-04-12/net/wireless/sysfs.c
compat-wireless-2012-04-12/net/wireless/lib80211_crypt_tkip.c
compat-wireless-2012-04-12/net/wireless/reg.h
compat-wireless-2012-04-12/net/wireless/regdb.h
compat-wireless-2012-04-12/net/wireless/debugfs.c
compat-wireless-2012-04-12/net/wireless/reg.c
compat-wireless-2012-04-12/net/wireless/genregdb.awk
compat-wireless-2012-04-12/net/bluetooth/
compat-wireless-2012-04-12/net/bluetooth/hci_sock.c
compat-wireless-2012-04-12/net/bluetooth/af_bluetooth.c
compat-wireless-2012-04-12/net/bluetooth/hci_core.c
compat-wireless-2012-04-12/net/bluetooth/hci_conn.c
compat-wireless-2012-04-12/net/bluetooth/Makefile
compat-wireless-2012-04-12/net/bluetooth/smp.c
compat-wireless-2012-04-12/net/bluetooth/bnep/
compat-wireless-2012-04-12/net/bluetooth/bnep/bnep.h
compat-wireless-2012-04-12/net/bluetooth/bnep/netdev.c
compat-wireless-2012-04-12/net/bluetooth/bnep/core.c
compat-wireless-2012-04-12/net/bluetooth/bnep/Makefile
compat-wireless-2012-04-12/net/bluetooth/bnep/sock.c
compat-wireless-2012-04-12/net/bluetooth/lib.c
compat-wireless-2012-04-12/net/bluetooth/cmtp/
compat-wireless-2012-04-12/net/bluetooth/cmtp/core.c
compat-wireless-2012-04-12/net/bluetooth/cmtp/cmtp.h
compat-wireless-2012-04-12/net/bluetooth/cmtp/Makefile
compat-wireless-2012-04-12/net/bluetooth/cmtp/capi.c
compat-wireless-2012-04-12/net/bluetooth/cmtp/sock.c
compat-wireless-2012-04-12/net/bluetooth/hidp/
compat-wireless-2012-04-12/net/bluetooth/hidp/core.c
compat-wireless-2012-04-12/net/bluetooth/hidp/Makefile
compat-wireless-2012-04-12/net/bluetooth/hidp/hidp.h
compat-wireless-2012-04-12/net/bluetooth/hidp/sock.c
compat-wireless-2012-04-12/net/bluetooth/sco.c
compat-wireless-2012-04-12/net/bluetooth/hci_event.c
compat-wireless-2012-04-12/net/bluetooth/rfcomm/
compat-wireless-2012-04-12/net/bluetooth/rfcomm/core.c
compat-wireless-2012-04-12/net/bluetooth/rfcomm/Makefile
compat-wireless-2012-04-12/net/bluetooth/rfcomm/tty.c
compat-wireless-2012-04-12/net/bluetooth/rfcomm/tty.c.orig
compat-wireless-2012-04-12/net/bluetooth/rfcomm/sock.c
compat-wireless-2012-04-12/net/bluetooth/hci_sysfs.c
compat-wireless-2012-04-12/net/bluetooth/l2cap_core.c
compat-wireless-2012-04-12/net/bluetooth/l2cap_sock.c
compat-wireless-2012-04-12/net/bluetooth/mgmt.c
compat-wireless-2012-04-12/net/rfkill/
compat-wireless-2012-04-12/net/rfkill/core.c
compat-wireless-2012-04-12/net/rfkill/Makefile
compat-wireless-2012-04-12/net/rfkill/rfkill-gpio.c
compat-wireless-2012-04-12/net/rfkill/rfkill-regulator.c
compat-wireless-2012-04-12/net/rfkill/rfkill.h
compat-wireless-2012-04-12/net/rfkill/input.c
compat-wireless-2012-04-12/scripts/
compat-wireless-2012-04-12/scripts/driver-select
compat-wireless-2012-04-12/scripts/compress_modules
compat-wireless-2012-04-12/scripts/gen-stable-release.sh
compat-wireless-2012-04-12/scripts/btunload.sh
compat-wireless-2012-04-12/scripts/admin-clean.sh
compat-wireless-2012-04-12/scripts/iwl-enable
compat-wireless-2012-04-12/scripts/athenable
compat-wireless-2012-04-12/scripts/check_depmod
compat-wireless-2012-04-12/scripts/athload
compat-wireless-2012-04-12/scripts/iwl-load
compat-wireless-2012-04-12/scripts/wlunload.sh
compat-wireless-2012-04-12/scripts/unload.sh
compat-wireless-2012-04-12/scripts/madwifi-unload
compat-wireless-2012-04-12/scripts/admin-update.sh
compat-wireless-2012-04-12/scripts/check_config.sh
compat-wireless-2012-04-12/scripts/update-initramfs
compat-wireless-2012-04-12/scripts/admin-refresh.sh
compat-wireless-2012-04-12/scripts/b43enable
compat-wireless-2012-04-12/scripts/skip-colors
compat-wireless-2012-04-12/scripts/modlib.sh
compat-wireless-2012-04-12/scripts/b43load
compat-wireless-2012-04-12/scripts/alx-enable
compat-wireless-2012-04-12/scripts/gen-compat-autoconf.sh
compat-wireless-2012-04-12/drivers/
compat-wireless-2012-04-12/drivers/ssb/
compat-wireless-2012-04-12/drivers/ssb/ssb_private.h
compat-wireless-2012-04-12/drivers/ssb/driver_gige.c
compat-wireless-2012-04-12/drivers/ssb/b43_pci_bridge.c
compat-wireless-2012-04-12/drivers/ssb/embedded.c
compat-wireless-2012-04-12/drivers/ssb/Makefile
compat-wireless-2012-04-12/drivers/ssb/driver_extif.c
compat-wireless-2012-04-12/drivers/ssb/pcmcia.c
compat-wireless-2012-04-12/drivers/ssb/Kconfig
compat-wireless-2012-04-12/drivers/ssb/sdio.c
compat-wireless-2012-04-12/drivers/ssb/pcihost_wrapper.c
compat-wireless-2012-04-12/drivers/ssb/scan.c
compat-wireless-2012-04-12/drivers/ssb/sprom.c
compat-wireless-2012-04-12/drivers/ssb/driver_pcicore.c
compat-wireless-2012-04-12/drivers/ssb/pci.c
compat-wireless-2012-04-12/drivers/ssb/main.c
compat-wireless-2012-04-12/drivers/ssb/driver_chipcommon_pmu.c
compat-wireless-2012-04-12/drivers/ssb/driver_chipcommon.c
compat-wireless-2012-04-12/drivers/ssb/driver_mipscore.c
compat-wireless-2012-04-12/drivers/bcma/
compat-wireless-2012-04-12/drivers/bcma/driver_mips.c
compat-wireless-2012-04-12/drivers/bcma/core.c
compat-wireless-2012-04-12/drivers/bcma/Makefile
compat-wireless-2012-04-12/drivers/bcma/Kconfig
compat-wireless-2012-04-12/drivers/bcma/scan.c
compat-wireless-2012-04-12/drivers/bcma/driver_pci.c
compat-wireless-2012-04-12/drivers/bcma/scan.h
compat-wireless-2012-04-12/drivers/bcma/sprom.c
compat-wireless-2012-04-12/drivers/bcma/host_pci.c
compat-wireless-2012-04-12/drivers/bcma/main.c
compat-wireless-2012-04-12/drivers/bcma/bcma_private.h
compat-wireless-2012-04-12/drivers/bcma/driver_pci_host.c
compat-wireless-2012-04-12/drivers/bcma/driver_chipcommon_pmu.c
compat-wireless-2012-04-12/drivers/bcma/driver_chipcommon.c
compat-wireless-2012-04-12/drivers/bcma/host_soc.c
compat-wireless-2012-04-12/drivers/net/
compat-wireless-2012-04-12/drivers/net/ethernet/
compat-wireless-2012-04-12/drivers/net/ethernet/broadcom/
compat-wireless-2012-04-12/drivers/net/ethernet/broadcom/b44.c
compat-wireless-2012-04-12/drivers/net/ethernet/broadcom/Makefile
compat-wireless-2012-04-12/drivers/net/ethernet/broadcom/b44.h
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/Makefile
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/Kconfig
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/alx/
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atlx/
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atlx/Makefile
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atlx/atl1.h
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atlx/atl2.c
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atlx/atlx.c
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atlx/atl2.h
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atlx/atl1.c
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atlx/atlx.h
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1e/
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1e/atl1e_hw.h
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1e/atl1e_ethtool.c
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1e/Makefile
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1e/atl1e_hw.c
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1e/atl1e_param.c
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1e/atl1e.h
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1e/atl1e_main.c
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.c
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/Makefile
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.c
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.h
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.h
compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.c
compat-wireless-2012-04-12/drivers/net/usb/
compat-wireless-2012-04-12/drivers/net/usb/rndis_host.c
compat-wireless-2012-04-12/drivers/net/usb/Makefile
compat-wireless-2012-04-12/drivers/net/usb/cdc_ether.c
compat-wireless-2012-04-12/drivers/net/usb/usbnet.c
compat-wireless-2012-04-12/drivers/net/wireless/
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_rf_uw2453.c
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_rf_rf2959.c
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_rf_al7230b.c
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_chip.h
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_rf.h
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_mac.c
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_chip.c
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_rf.c
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_usb.h
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_usb.c
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_rf_al2230.c
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_mac.h
compat-wireless-2012-04-12/drivers/net/wireless/zd1211rw/zd_def.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas_tf/
compat-wireless-2012-04-12/drivers/net/wireless/libertas_tf/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/libertas_tf/libertas_tf.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas_tf/cmd.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas_tf/if_usb.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas_tf/main.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas_tf/if_usb.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas_tf/deb_defs.h
compat-wireless-2012-04-12/drivers/net/wireless/mac80211_hwsim.h
compat-wireless-2012-04-12/drivers/net/wireless/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/init.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/testmode.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/boot.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/sdio.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/boot.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/scan.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/acx.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/rx.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/cmd.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/tx.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/event.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/wl12xx.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/debugfs.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/scan.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/tx.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/acx.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/io.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/cmd.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/ps.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/testmode.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/io.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/ps.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/spi.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/main.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/ini.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/event.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/debug.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/wl12xx_80211.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/conf.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/main.c.orig
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/init.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/reg.h
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/wl12xx_platform_data.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/rx.c
compat-wireless-2012-04-12/drivers/net/wireless/wl12xx/debugfs.c
compat-wireless-2012-04-12/drivers/net/wireless/mwl8k.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/phy.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/sysfs.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/radio.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/rfkill.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/leds.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/xmit.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/leds.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/dma.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/dma.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/debugfs.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/pio.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/b43legacy.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/main.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/ilt.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/main.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/rfkill.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/phy.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/sysfs.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/radio.h
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/debugfs.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/xmit.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/ilt.c
compat-wireless-2012-04-12/drivers/net/wireless/b43legacy/pio.h
compat-wireless-2012-04-12/drivers/net/wireless/at76c50x-usb.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/netdev.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/eeprom.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/sdio.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/rx.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/bus.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/fw.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/sdio.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/tx.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/eeprom.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/hal.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/fw.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/trace.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/commands.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/iwm.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/lmac.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/main.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/hal.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/trace.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/debug.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/umac.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/cfg80211.h
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/cfg80211.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/rx.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/debugfs.c
compat-wireless-2012-04-12/drivers/net/wireless/iwmc3200wifi/commands.h
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/ipw2100.c
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/libipw_geo.c
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/ipw2100.h
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/libipw.h
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/ipw2200.c
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/libipw_wx.c
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/libipw_tx.c
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/libipw_rx.c
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/ipw2200.h
compat-wireless-2012-04-12/drivers/net/wireless/ipw2x00/libipw_module.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/
compat-wireless-2012-04-12/drivers/net/wireless/b43/radio_2055.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_g.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_g.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/radio_2056.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/radio_2055.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/b43/pcmcia.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/tables_lpphy.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/b43/sdio.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/sysfs.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_ht.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_a.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/rfkill.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/tables_phy_ht.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/leds.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/xmit.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/tables_nphy.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/leds.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/bus.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/sdio.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/dma.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/dma.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/tables.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/lo.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_ht.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/tables_phy_lcn.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/radio_2059.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/radio_2056.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/tables_phy_ht.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/tables_lpphy.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/tables_nphy.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/debugfs.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/tables.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/wa.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/pio.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/radio_2059.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/b43.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/wa.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_n.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_lcn.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_n.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_lp.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/tables_phy_lcn.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/main.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_common.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_lp.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/main.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/rfkill.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/bus.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/main.c.orig
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_common.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/sysfs.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/pcmcia.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_a.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/debugfs.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/lo.h
compat-wireless-2012-04-12/drivers/net/wireless/b43/phy_lcn.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/xmit.c
compat-wireless-2012-04-12/drivers/net/wireless/b43/pio.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00pci.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2800pci.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00usb.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2800lib.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00pci.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2500pci.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2800usb.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00queue.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2400pci.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00leds.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00debug.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt73usb.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00reg.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00config.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2800pci.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt73usb.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2500pci.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00soc.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2800.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00dump.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt61pci.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00firmware.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2400pci.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00mac.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00queue.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00debug.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2500usb.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt61pci.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00crypto.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2800usb.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00usb.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00lib.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00link.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00soc.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00leds.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2800lib.h
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2x00dev.c
compat-wireless-2012-04-12/drivers/net/wireless/rt2x00/rt2500usb.h
compat-wireless-2012-04-12/drivers/net/wireless/rndis_wlan.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/orinoco_tmd.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/cfg.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/hermes_dld.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/scan.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/wext.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/hermes_dld.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/cfg.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/orinoco_pci.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/hw.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/fw.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/mic.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/airport.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/orinoco_pci.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/hermes.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/scan.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/hermes_rid.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/orinoco_cs.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/fw.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/spectrum_cs.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/mic.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/main.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/hermes.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/orinoco_plx.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/main.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/wext.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/orinoco.h
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/hw.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/orinoco_usb.c
compat-wireless-2012-04-12/drivers/net/wireless/orinoco/orinoco_nortel.c
compat-wireless-2012-04-12/drivers/net/wireless/adm8211.h
compat-wireless-2012-04-12/drivers/net/wireless/p54/
compat-wireless-2012-04-12/drivers/net/wireless/p54/p54.h
compat-wireless-2012-04-12/drivers/net/wireless/p54/eeprom.h
compat-wireless-2012-04-12/drivers/net/wireless/p54/net2280.h
compat-wireless-2012-04-12/drivers/net/wireless/p54/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/p54/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/p54/fwio.c
compat-wireless-2012-04-12/drivers/net/wireless/p54/p54usb.h
compat-wireless-2012-04-12/drivers/net/wireless/p54/p54spi.h
compat-wireless-2012-04-12/drivers/net/wireless/p54/led.c
compat-wireless-2012-04-12/drivers/net/wireless/p54/eeprom.c
compat-wireless-2012-04-12/drivers/net/wireless/p54/p54pci.h
compat-wireless-2012-04-12/drivers/net/wireless/p54/p54pci.c
compat-wireless-2012-04-12/drivers/net/wireless/p54/txrx.c
compat-wireless-2012-04-12/drivers/net/wireless/p54/p54spi_eeprom.h
compat-wireless-2012-04-12/drivers/net/wireless/p54/p54usb.c
compat-wireless-2012-04-12/drivers/net/wireless/p54/lmac.h
compat-wireless-2012-04-12/drivers/net/wireless/p54/main.c
compat-wireless-2012-04-12/drivers/net/wireless/p54/p54spi.c
compat-wireless-2012-04-12/drivers/net/wireless/adm8211.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/core.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/debug.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/testmode.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/sdio.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/target.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/core.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/bmi.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/bmi.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/hif-ops.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/wmi.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/wmi.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/hif.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/usb.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/testmode.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/txrx.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/common.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/hif.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/main.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/htc.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/debug.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/cfg80211.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/main.c.orig
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/cfg80211.c.orig
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/init.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/cfg80211.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath6kl/htc.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/regd.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/ath/debug.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9001_initvals.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9330_1p1_initvals.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9002_calib.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_paprd.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/btcoex.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/htc_drv_main.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/htc_drv_debug.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/eeprom.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/calib.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9002_initvals.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9485_initvals.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_rtt.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/dfs_pattern_detector.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9330_1p2_initvals.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_eeprom.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/mac.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/hif_usb.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_mci.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/dfs_pattern_detector.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/calib.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/btcoex.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9002_phy.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/debug.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_calib.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/phy.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/rc.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/init.c.orig
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9580_1p0_initvals.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/recv.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/mci.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/htc_drv_gpio.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/pci.c.orig
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_mci.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9002_hw.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/hw.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar5008_initvals.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_2p2_initvals.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9002_mac.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_rtt.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ani.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/dfs_pri_detector.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/hif_usb.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_hw.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar5008_phy.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/dfs_debug.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/dfs_pri_detector.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/htc_hst.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_phy.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/dfs.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/eeprom.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ani.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9462_2p0_initvals.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/beacon.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/wmi.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/wmi.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/eeprom_9287.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ath9k.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_mac.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/dfs.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/common.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/mac.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/pci.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/rc.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9340_initvals.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/htc_drv_txrx.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/main.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/hw-ops.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/htc.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9002_phy.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/eeprom_4k.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/htc_drv_init.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_mac.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/debug.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_phy.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/common.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ar9003_eeprom.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ahb.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/gpio.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/mci.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/dfs_debug.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/init.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/reg.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/htc_drv_beacon.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/hw.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/eeprom_def.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/xmit.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/htc_hst.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/key.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/wlan.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/eeprom.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/carl9170.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/fwdesc.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/debug.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/phy.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/version.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/hw.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/cmd.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/fw.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/tx.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/led.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/usb.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/cmd.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/fwcmd.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/mac.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/main.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/debug.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/phy.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/carl9170/rx.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/rfgain.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/eeprom.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/rfbuffer.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/desc.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/reset.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/debug.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/caps.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/pcu.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/base.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/pci.c.orig
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/rfkill.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/ath5k.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/ani.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/dma.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/base.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/mac80211-ops.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/mac80211-ops.c.orig
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/led.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/eeprom.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/ani.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/initvals.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/attach.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/qcu.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/pci.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/trace.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/debug.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/phy.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/ahb.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/gpio.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/desc.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/sysfs.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath5k/reg.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/ath.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/main.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/regd_common.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/main.c.orig
compat-wireless-2012-04-12/drivers/net/wireless/ath/regd.c
compat-wireless-2012-04-12/drivers/net/wireless/ath/reg.h
compat-wireless-2012-04-12/drivers/net/wireless/ath/hw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/usb.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/core.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/led.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/phy.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/hw.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/fw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/rf.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/table.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/led.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/def.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/table.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/sw.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/trx.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/dm.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/trx.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/fw.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/rf.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/dm.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/sw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/phy.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/reg.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192de/hw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/mac.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/led.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/phy.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/hw.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/rf.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/table.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/led.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/def.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/table.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/sw.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/trx.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/dm.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/trx.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/rf.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/mac.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/dm.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/sw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/phy.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/reg.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192cu/hw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/cam.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/regd.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/pci.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/debug.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rc.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/wifi.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/base.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/cam.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/core.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/efuse.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/led.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/phy.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/hw.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/fw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/rf.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/table.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/led.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/def.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/table.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/sw.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/trx.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/dm.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/trx.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/fw.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/rf.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/dm.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/sw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/phy.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/reg.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192se/hw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/base.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/efuse.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/usb.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/ps.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/pci.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/ps.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rc.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/led.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/phy.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/hw.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/rf.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/table.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/led.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/def.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/table.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/sw.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/trx.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/dm.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/trx.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/rf.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/dm.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/sw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/phy.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/reg.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192ce/hw.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/debug.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/regd.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192c/
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.h
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192c/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192c/main.c
compat-wireless-2012-04-12/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/4965.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/debug.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/prph.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/4965.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/3945-rs.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/4965-rs.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/3945-mac.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/4965-mac.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/4965-debug.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/iwl-spectrum.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/4965-calib.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/csr.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/common.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/3945.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/3945-debug.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/common.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/3945.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlegacy/commands.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-led.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-calib.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-led.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-rxon.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-op-mode.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-trans-pcie-int.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-io.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-5000.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-tt.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-commands.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-fw-file.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-devtrace.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-calib.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-power.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-lib.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-phy-db.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-rx.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-trans-pcie-rx.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-notif-wait.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-6000.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-notif-wait.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-ucode.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-io.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-phy-db.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-eeprom.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-sta.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-1000.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-debugfs.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-devtrace.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-trans-pcie-tx.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-hw.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-rs.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-trans.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-prph.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-eeprom.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-fh.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-pci.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-mac80211.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-power.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-debug.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-fw.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-pci.c.orig
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-drv.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-shared.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-core.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-testmode.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-dev.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-scan.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-rs.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-2000.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-csr.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-debug.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-cfg.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-tx.c
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-core.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-drv.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-testmode.h
compat-wireless-2012-04-12/drivers/net/wireless/iwlwifi/iwl-agn-tt.h
compat-wireless-2012-04-12/drivers/net/wireless/mac80211_hwsim.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/usb.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/bcmsdh.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/dhd_sdio.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/bcmsdh_sdmmc.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/wl_cfg80211.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/usb_rdl.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/sdio_host.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/dhd_common.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/wl_cfg80211.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/usb.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/sdio_chip.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/dhd_dbg.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/dhd_proto.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/dhd_bus.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/sdio_chip.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/dhd_cdc.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/dhd_linux.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmfmac/dhd.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmutil/
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmutil/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmutil/utils.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/brcms_trace_events.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/otp.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/ucode_loader.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/mac80211_if.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/antsel.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/mac80211_if.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/srom.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/ampdu.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/types.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/rate.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/aiutils.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/dma.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/ucode_loader.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/dma.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/pmu.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/ampdu.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/scb.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/stf.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/channel.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/antsel.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/nicpci.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/d11.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy_shim.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/aiutils.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/pmu.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/main.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy_shim.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/main.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/channel.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/stf.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/brcms_trace_events.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/srom.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/nicpci.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/rate.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/pub.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/otp.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_int.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phytbl_lcn.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phytbl_n.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phyreg_n.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_lcn.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_n.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phytbl_lcn.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_hal.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_cmn.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_qmath.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_qmath.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phytbl_n.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_radio.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_lcn.c
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/include/
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/include/chipcommon.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/include/brcmu_wifi.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/include/soc.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/include/brcmu_utils.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/include/brcm_hw_ids.h
compat-wireless-2012-04-12/drivers/net/wireless/brcm80211/include/defs.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/init.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/boot.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/sdio.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/boot.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/acx.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/rx.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/cmd.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/tx.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/event.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/debugfs.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/tx.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/acx.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/io.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/cmd.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/ps.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/io.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/ps.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/spi.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/main.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/event.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/wl12xx_80211.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/init.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/wl1251.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/spi.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/reg.h
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/rx.c
compat-wireless-2012-04-12/drivers/net/wireless/wl1251/debugfs.c
compat-wireless-2012-04-12/drivers/net/wireless/at76c50x-usb.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/join.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/11n_rxreorder.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/wmm.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/sdio.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/util.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/scan.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/decl.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/wmm.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/sdio.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/cmdevt.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/11n.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/sta_ioctl.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/fw.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/util.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/pcie.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/sta_tx.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/txrx.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/11n.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/11n_aggr.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/main.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/11n_rxreorder.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/ioctl.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/cfp.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/sta_event.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/main.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/sta_cmd.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/sta_cmdresp.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/cfg80211.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/11n_aggr.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/init.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/cfg80211.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/pcie.h
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/sta_rx.c
compat-wireless-2012-04-12/drivers/net/wireless/mwifiex/debugfs.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/
compat-wireless-2012-04-12/drivers/net/wireless/libertas/cfg.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/libertas/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/libertas/ethtool.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/if_cs.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/decl.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/host.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/cfg.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/cmd.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/types.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/radiotap.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/tx.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/dev.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/cmdresp.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/debugfs.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/cmd.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/if_sdio.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/mesh.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/if_usb.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/main.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/if_usb.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/if_spi.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/defs.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/if_spi.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/rx.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/debugfs.c
compat-wireless-2012-04-12/drivers/net/wireless/libertas/mesh.h
compat-wireless-2012-04-12/drivers/net/wireless/libertas/if_sdio.c
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/Kconfig
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl818x.h
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8187/
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8187/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8187/rtl8187.h
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8187/dev.c
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8187/rfkill.c
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8187/rtl8225.c
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8187/leds.c
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8187/leds.h
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8187/rfkill.h
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8187/rtl8225.h
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/max2820.c
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/Makefile
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/dev.c
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/grf5101.h
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/rtl8225.c
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/sa2400.c
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/grf5101.c
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/max2820.h
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/sa2400.h
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/rtl8225.h
compat-wireless-2012-04-12/drivers/net/wireless/rtl818x/rtl8180/rtl8180.h
compat-wireless-2012-04-12/drivers/bluetooth/
compat-wireless-2012-04-12/drivers/bluetooth/btmrvl_sdio.h
compat-wireless-2012-04-12/drivers/bluetooth/hci_ath.c
compat-wireless-2012-04-12/drivers/bluetooth/dtl1_cs.c
compat-wireless-2012-04-12/drivers/bluetooth/Makefile
compat-wireless-2012-04-12/drivers/bluetooth/bpa10x.c
compat-wireless-2012-04-12/drivers/bluetooth/ath3k.c
compat-wireless-2012-04-12/drivers/bluetooth/btwilink.c
compat-wireless-2012-04-12/drivers/bluetooth/hci_bcsp.c
compat-wireless-2012-04-12/drivers/bluetooth/bfusb.c
compat-wireless-2012-04-12/drivers/bluetooth/btusb.c
compat-wireless-2012-04-12/drivers/bluetooth/btmrvl_sdio.c
compat-wireless-2012-04-12/drivers/bluetooth/btmrvl_main.c
compat-wireless-2012-04-12/drivers/bluetooth/hci_h4.c
compat-wireless-2012-04-12/drivers/bluetooth/bluecard_cs.c
compat-wireless-2012-04-12/drivers/bluetooth/hci_vhci.c
compat-wireless-2012-04-12/drivers/bluetooth/btmrvl_debugfs.c
compat-wireless-2012-04-12/drivers/bluetooth/hci_ldisc.c
compat-wireless-2012-04-12/drivers/bluetooth/bcm203x.c
compat-wireless-2012-04-12/drivers/bluetooth/hci_ll.c
compat-wireless-2012-04-12/drivers/bluetooth/btsdio.c
compat-wireless-2012-04-12/drivers/bluetooth/hci_uart.h
compat-wireless-2012-04-12/drivers/bluetooth/btmrvl_drv.h
compat-wireless-2012-04-12/drivers/bluetooth/bt3c_cs.c
compat-wireless-2012-04-12/drivers/bluetooth/btuart_cs.c
compat-wireless-2012-04-12/drivers/staging/
compat-wireless-2012-04-12/drivers/misc/
compat-wireless-2012-04-12/drivers/misc/eeprom/
compat-wireless-2012-04-12/drivers/misc/eeprom/Makefile
compat-wireless-2012-04-12/drivers/misc/eeprom/eeprom_93cx6.c
compat-wireless-2012-04-12/linux-next-pending/
compat-wireless-2012-04-12/linux-next-pending/0001-alx-add-new-QCA-ethernet-driver-which-supercedes-atl.patch
compat-wireless-2012-04-12/linux-next-pending/README
compat-wireless-2012-04-12/linux-next-pending/0002-backport-alx.patch
compat-wireless-2012-04-12/defconfigs/
compat-wireless-2012-04-12/defconfigs/README
compat-wireless-2012-04-12/defconfigs/atheros-debug.mk
compat-wireless-2012-04-12/compat/
compat-wireless-2012-04-12/compat/compat-2.6.21.c
compat-wireless-2012-04-12/compat/cordic.c
compat-wireless-2012-04-12/compat/compat-3.0.c
compat-wireless-2012-04-12/compat/compat-2.6.25.c
compat-wireless-2012-04-12/compat/Makefile
compat-wireless-2012-04-12/compat/compat-3.2.c
compat-wireless-2012-04-12/compat/compat-2.6.39.c
compat-wireless-2012-04-12/compat/compat-3.5.c
compat-wireless-2012-04-12/compat/compat-2.6.35.c
compat-wireless-2012-04-12/compat/compat-2.6.33.c
compat-wireless-2012-04-12/compat/compat-2.6.37.c
compat-wireless-2012-04-12/compat/compat-2.6.26.c
compat-wireless-2012-04-12/compat/compat-3.3.c
compat-wireless-2012-04-12/compat/scripts/
compat-wireless-2012-04-12/compat/scripts/compat_firmware_install
compat-wireless-2012-04-12/compat/scripts/gen-compat-config.sh
compat-wireless-2012-04-12/compat/scripts/skip-colors
compat-wireless-2012-04-12/compat/scripts/gen-compat-autoconf.sh
compat-wireless-2012-04-12/compat/compat_atomic.c
compat-wireless-2012-04-12/compat/compat-2.6.19.c
compat-wireless-2012-04-12/compat/kfifo.c
compat-wireless-2012-04-12/compat/compat-2.6.28.c
compat-wireless-2012-04-12/compat/compat-2.6.22.c
compat-wireless-2012-04-12/compat/compat-2.6.24.c
compat-wireless-2012-04-12/compat/compat-2.6.29.c
compat-wireless-2012-04-12/compat/compat-2.6.23.c
compat-wireless-2012-04-12/compat/compat-2.6.38.c
compat-wireless-2012-04-12/compat/pm_qos_params.c
compat-wireless-2012-04-12/compat/compat-2.6.14.c
compat-wireless-2012-04-12/compat/kstrtox.c
compat-wireless-2012-04-12/compat/compat-2.6.32.c
compat-wireless-2012-04-12/compat/main.c
compat-wireless-2012-04-12/compat/compat-2.6.36.c
compat-wireless-2012-04-12/compat/crc8.c
compat-wireless-2012-04-12/compat/compat-2.6.18.c
compat-wireless-2012-04-12/compat/compat_firmware_class.c
compat-wireless-2012-04-12/compat/compat-2.6.27.c
compat-wireless-2012-04-12/udev/
compat-wireless-2012-04-12/udev/50-compat_firmware.rules
compat-wireless-2012-04-12/udev/ubuntu/
compat-wireless-2012-04-12/udev/ubuntu/50-compat_firmware.rules
compat-wireless-2012-04-12/udev/ubuntu/compat_firmware.sh
compat-wireless-2012-04-12/udev/compat_firmware.sh
compat-wireless-2012-04-12/patches/
compat-wireless-2012-04-12/patches/22-multiqueue.patch
compat-wireless-2012-04-12/patches/46-use_other_workqueue.patch
compat-wireless-2012-04-12/patches/61-netdev-addr_assign_type.patch
compat-wireless-2012-04-12/patches/14-device-type.patch
compat-wireless-2012-04-12/patches/38-led-max-brightness.patch
compat-wireless-2012-04-12/patches/11-dev-pm-ops.patch
compat-wireless-2012-04-12/patches/49-rename_path_lookup.patch
compat-wireless-2012-04-12/patches/39-remove_blink_set.patch
compat-wireless-2012-04-12/patches/17-netdev-queue.patch
compat-wireless-2012-04-12/patches/43-rename_pm_qos_request.patch
compat-wireless-2012-04-12/patches/48-use_skb_get_queue_mapping.patch
compat-wireless-2012-04-12/patches/09-threaded-irq.patch
compat-wireless-2012-04-12/patches/32-remove-ns-type.patch
compat-wireless-2012-04-12/patches/51-in-header.patch
compat-wireless-2012-04-12/patches/03-rfkill.patch
compat-wireless-2012-04-12/patches/52-tty-dev.patch
compat-wireless-2012-04-12/patches/15-symbol-export-conflicts.patch
compat-wireless-2012-04-12/patches/02-ksize.patch
compat-wireless-2012-04-12/patches/README
compat-wireless-2012-04-12/patches/21-capi-proc_fops.patch
compat-wireless-2012-04-12/patches/0003-netdev-needed_headroom_tailroom.patch
compat-wireless-2012-04-12/patches/10-add-wext-handlers-to-netdev.patch
compat-wireless-2012-04-12/patches/07-change-default-rate-alg.patch
compat-wireless-2012-04-12/patches/30-bridge-port.patch
compat-wireless-2012-04-12/patches/27-hermes-read-pda-conflict.patch
compat-wireless-2012-04-12/patches/50-libertas-olpc-ec-wakeup.patch
compat-wireless-2012-04-12/patches/53-pr_fmt.patch
compat-wireless-2012-04-12/patches/12-mac80211-disable-tx-status.patch
compat-wireless-2012-04-12/patches/09-cfg80211-wext-padding.patch
compat-wireless-2012-04-12/patches/18-rename-usb-net-symbols.patch
compat-wireless-2012-04-12/patches/40-netdev-hw-features.patch
compat-wireless-2012-04-12/patches/29-sdio_no_suspend.patch
compat-wireless-2012-04-12/patches/08-rename-config-options.patch
compat-wireless-2012-04-12/patches/47-no_trans_start_on_netdev_queue.patch
compat-wireless-2012-04-12/patches/99-change-makefiles.patch
compat-wireless-2012-04-12/patches/12-iw_handler-changes.patch
compat-wireless-2012-04-12/patches/05-usb.patch
compat-wireless-2012-04-12/patches/04-netns.patch
compat-wireless-2012-04-12/patches/45-remove-platform-id-table.patch
compat-wireless-2012-04-12/patches/24-pcmcia.patch
compat-wireless-2012-04-12/patches/0002-net-misc.patch
compat-wireless-2012-04-12/patches/44-deactivate-mac80211-tracing.patch
compat-wireless-2012-04-12/patches/36-workqueue.patch
compat-wireless-2012-04-12/patches/16-bluetooth.patch
compat-wireless-2012-04-12/patches/0004-wext-namespace.patch
compat-wireless-2012-04-12/patches/25-multicast-list_head.patch
compat-wireless-2012-04-12/patches/06-header-changes.patch
compat-wireless-2012-04-12/patches/37-vsnprintk.patch
compat-wireless-2012-04-12/patches/0001-netdev_ops.patch
compat-wireless-2012-04-12/patches/54-get_ts_info.patch
compat-wireless-2012-04-12/patches/26-sdio-quirks.patch
compat-wireless-2012-04-12/patches/42-netlink_seq.patch
compat-wireless-2012-04-12/patches/35-fix-makefile-includes.patch
compat-wireless-2012-04-12/MAINTAINERS
compat-wireless-2012-04-12/COPYRIGHT
compat-wireless-2012-04-12/crap/
compat-wireless-2012-04-12/crap/README
compat-wireless-2012-04-12/include/
compat-wireless-2012-04-12/include/pcmcia/
compat-wireless-2012-04-12/include/pcmcia/cistpl.h
compat-wireless-2012-04-12/include/crypto/
compat-wireless-2012-04-12/include/crypto/aes.h
compat-wireless-2012-04-12/include/net/
compat-wireless-2012-04-12/include/net/cfg80211.h.orig
compat-wireless-2012-04-12/include/net/cfg80211-wext.h
compat-wireless-2012-04-12/include/net/ieee80211_radiotap.h
compat-wireless-2012-04-12/include/net/lib80211.h
compat-wireless-2012-04-12/include/net/mac80211.h
compat-wireless-2012-04-12/include/net/bluetooth/
compat-wireless-2012-04-12/include/net/bluetooth/smp.h
compat-wireless-2012-04-12/include/net/bluetooth/hci_core.h
compat-wireless-2012-04-12/include/net/bluetooth/rfcomm.h
compat-wireless-2012-04-12/include/net/bluetooth/hci.h
compat-wireless-2012-04-12/include/net/bluetooth/l2cap.h
compat-wireless-2012-04-12/include/net/bluetooth/bluetooth.h
compat-wireless-2012-04-12/include/net/bluetooth/hci_mon.h
compat-wireless-2012-04-12/include/net/bluetooth/mgmt.h
compat-wireless-2012-04-12/include/net/regulatory.h
compat-wireless-2012-04-12/include/net/net_namespace.h
compat-wireless-2012-04-12/include/net/cfg80211.h
compat-wireless-2012-04-12/include/net/mac80211.h.orig
compat-wireless-2012-04-12/include/trace/
compat-wireless-2012-04-12/include/trace/define_trace.h
compat-wireless-2012-04-12/include/linux/
compat-wireless-2012-04-12/include/linux/pm_qos.h
compat-wireless-2012-04-12/include/linux/atomic.h
compat-wireless-2012-04-12/include/linux/nl80211.h
compat-wireless-2012-04-12/include/linux/spi/
compat-wireless-2012-04-12/include/linux/spi/libertas_spi.h
compat-wireless-2012-04-12/include/linux/ssb/
compat-wireless-2012-04-12/include/linux/ssb/ssb_driver_gige.h
compat-wireless-2012-04-12/include/linux/ssb/ssb_driver_chipcommon.h
compat-wireless-2012-04-12/include/linux/ssb/ssb_driver_mips.h
compat-wireless-2012-04-12/include/linux/ssb/ssb_driver_pci.h
compat-wireless-2012-04-12/include/linux/ssb/ssb.h
compat-wireless-2012-04-12/include/linux/ssb/ssb_embedded.h
compat-wireless-2012-04-12/include/linux/ssb/ssb_regs.h
compat-wireless-2012-04-12/include/linux/ssb/ssb_driver_extif.h
compat-wireless-2012-04-12/include/linux/compat-3.5.h
compat-wireless-2012-04-12/include/linux/rfkill_backport.h
compat-wireless-2012-04-12/include/linux/compat-3.0.h
compat-wireless-2012-04-12/include/linux/compat-3.3.h
compat-wireless-2012-04-12/include/linux/compat-2.6.30.h
compat-wireless-2012-04-12/include/linux/export.h
compat-wireless-2012-04-12/include/linux/unaligned/
compat-wireless-2012-04-12/include/linux/unaligned/packed_struct.h
compat-wireless-2012-04-12/include/linux/unaligned/memmove.h
compat-wireless-2012-04-12/include/linux/unaligned/be_memmove.h
compat-wireless-2012-04-12/include/linux/unaligned/le_memmove.h
compat-wireless-2012-04-12/include/linux/unaligned/be_byteshift.h
compat-wireless-2012-04-12/include/linux/unaligned/generic.h
compat-wireless-2012-04-12/include/linux/unaligned/be_struct.h
compat-wireless-2012-04-12/include/linux/unaligned/access_ok.h
compat-wireless-2012-04-12/include/linux/unaligned/le_byteshift.h
compat-wireless-2012-04-12/include/linux/unaligned/le_struct.h
compat-wireless-2012-04-12/include/linux/compat-2.6.27.h
compat-wireless-2012-04-12/include/linux/compat-2.6.33.h
compat-wireless-2012-04-12/include/linux/pm_qos_params.h
compat-wireless-2012-04-12/include/linux/compat-2.6.25.h
compat-wireless-2012-04-12/include/linux/average.h
compat-wireless-2012-04-12/include/linux/of.h
compat-wireless-2012-04-12/include/linux/compat-2.6.22.h
compat-wireless-2012-04-12/include/linux/compat-2.6.39.h
compat-wireless-2012-04-12/include/linux/usb/
compat-wireless-2012-04-12/include/linux/usb/rndis_host.h
compat-wireless-2012-04-12/include/linux/usb/usbnet.h
compat-wireless-2012-04-12/include/linux/printk.h
compat-wireless-2012-04-12/include/linux/bcma/
compat-wireless-2012-04-12/include/linux/bcma/bcma_regs.h
compat-wireless-2012-04-12/include/linux/bcma/bcma_soc.h
compat-wireless-2012-04-12/include/linux/bcma/bcma_driver_chipcommon.h
compat-wireless-2012-04-12/include/linux/bcma/bcma.h
compat-wireless-2012-04-12/include/linux/bcma/bcma_driver_mips.h
compat-wireless-2012-04-12/include/linux/bcma/bcma_driver_pci.h
compat-wireless-2012-04-12/include/linux/math64.h
compat-wireless-2012-04-12/include/linux/compat-2.6.14.h
compat-wireless-2012-04-12/include/linux/kfifo.h
compat-wireless-2012-04-12/include/linux/compat-2.6.35.h
compat-wireless-2012-04-12/include/linux/compat-2.6.31.h
compat-wireless-2012-04-12/include/linux/bitops.h
compat-wireless-2012-04-12/include/linux/compat-2.6.38.h
compat-wireless-2012-04-12/include/linux/compat-2.6.20.h
compat-wireless-2012-04-12/include/linux/compat-3.2.h
compat-wireless-2012-04-12/include/linux/compat-2.6.21.h
compat-wireless-2012-04-12/include/linux/compat-2.6.26.h
compat-wireless-2012-04-12/include/linux/compat-2.6.18.h
compat-wireless-2012-04-12/include/linux/wl12xx.h
compat-wireless-2012-04-12/include/linux/pci_ids.h
compat-wireless-2012-04-12/include/linux/pm_runtime.h
compat-wireless-2012-04-12/include/linux/compat-2.6.32.h
compat-wireless-2012-04-12/include/linux/compat-2.6.23.h
compat-wireless-2012-04-12/include/linux/crc8.h
compat-wireless-2012-04-12/include/linux/tracepoint.h
compat-wireless-2012-04-12/include/linux/compat-3.4.h
compat-wireless-2012-04-12/include/linux/compat-2.6.36.h
compat-wireless-2012-04-12/include/linux/compat-2.6.29.h
compat-wireless-2012-04-12/include/linux/cordic.h
compat-wireless-2012-04-12/include/linux/compat-2.6.19.h
compat-wireless-2012-04-12/include/linux/ieee80211.h
compat-wireless-2012-04-12/include/linux/compat-3.1.h
compat-wireless-2012-04-12/include/linux/compat-2.6.28.h
compat-wireless-2012-04-12/include/linux/compat-2.6.37.h
compat-wireless-2012-04-12/include/linux/wireless.h
compat-wireless-2012-04-12/include/linux/rfkill.h
compat-wireless-2012-04-12/include/linux/compat-2.6.24.h
compat-wireless-2012-04-12/include/linux/semaphore.h
compat-wireless-2012-04-12/include/linux/pci-aspm.h
compat-wireless-2012-04-12/include/linux/eeprom_93cx6.h
compat-wireless-2012-04-12/include/linux/compat-2.6.34.h
compat-wireless-2012-04-12/include/linux/compat-2.6.h
compat-wireless-2012-04-12/include/linux/ath9k_platform.h
compat-wireless-2012-04-12/code-metrics.txt
compat-wireless-2012-04-12/linux-next-cherry-picks/
compat-wireless-2012-04-12/linux-next-cherry-picks/README
compat-wireless-2012-04-12/enable-older-kernels/
compat-wireless-2012-04-12/enable-older-kernels/enable-2.6.22.patch
compat-wireless-2012-04-12/enable-older-kernels/README
compat-wireless-2012-04-12/enable-older-kernels/enable-2.6.21.patch
compat-wireless-2012-04-12/enable-older-kernels/enable-2.6.23.patch
compat-wireless-2012-04-12/config.mk
compat-wireless-2012-04-12/master-tag
compat-wireless-2012-04-12/compat_version
acer@acer-Aspire-5349:~/Desktop$ cd compat-wireless-20*
acer@acer-Aspire-5349:~/Desktop/compat-wireless-2012-04-12$ scripts/driver-select atl1c
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/ethernet/broadcom/Makefile.bk
Backing up makefile: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
acer@acer-Aspire-5349:~/Desktop/compat-wireless-2012-04-12$ make
./scripts/gen-compat-autoconf.sh /home/acer/Desktop/compat-wireless-2012-04-12/.config /home/acer/Desktop/compat-wireless-2012-04-12/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.38-14-generic/build M=/home/acer/Desktop/compat-wireless-2012-04-12 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-14-generic'
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/main.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/compat-2.6.39.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/kstrtox.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/compat-3.0.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/compat-3.2.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/compat-3.3.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/compat-3.5.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/cordic.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/crc8.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/compat_atomic.o
  LD [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/compat.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_main.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_hw.o
  CC [M]  /home/acer/Desktop/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.o
  LD [M]  /home/acer/Desktop/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.o
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /home/acer/Desktop/compat-wireless-2012-04-12/compat/compat.mod.o
  LD [M]  /home/acer/Desktop/compat-wireless-2012-04-12/compat/compat.ko
  CC      /home/acer/Desktop/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.mod.o
  LD [M]  /home/acer/Desktop/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-14-generic'
acer@acer-Aspire-5349:~/Desktop/compat-wireless-2012-04-12$ sudo make install
[sudo] password for acer: 

make -C /lib/modules/2.6.38-14-generic/build M=/home/acer/Desktop/compat-wireless-2012-04-12 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-14-generic'
  Building modules, stage 2.
  MODPOST 2 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-14-generic'
make -C /lib/modules/2.6.38-14-generic/build M=/home/acer/Desktop/compat-wireless-2012-04-12 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-14-generic'
  INSTALL /home/acer/Desktop/compat-wireless-2012-04-12/compat/compat.ko
  INSTALL /home/acer/Desktop/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.ko
  DEPMOD  2.6.38-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-14-generic'
Updating Ubuntu's initramfs for 2.6.38-14-generic under /boot/ ...
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done
depmod will prefer updates/ over kernel/ -- OK!

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

acer@acer-Aspire-5349:~/Desktop/compat-wireless-2012-04-12$ exit
***reboot!

***laptop rebooted
***after reboot the lan is recognized and working
***wlan is no longer active

***code
uname -a
sudo modprobe atl1c
locate atl1c.ko

acer@acer-Aspire-5349:~$ uname -a
Linux acer-Aspire-5349 2.6.38-14-generic #58-Ubuntu SMP Tue Mar 27 18:48:46 UTC 2012 i686 i686 i386 GNU/Linux
acer@acer-Aspire-5349:~$ sudo modprobe atl1c
[sudo] password for acer: 
acer@acer-Aspire-5349:~$ locate atl1c.ko
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c.ko.cmd
/home/acer/Documents/linux/tools/ethernet driver/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/.atl1c.ko.cmd
/home/acer/compat-wireless-2012-04-12/drivers/net/ethernet/atheros/atl1c/atl1c.ko
/lib/modules/2.6.38-12-generic/kernel/drivers/net/atl1c/atl1c.ko
/lib/modules/2.6.38-14-generic/kernel/drivers/net/atl1c/atl1c.ko.ignore
/lib/modules/2.6.38-14-generic/updates/drivers/net/ethernet/atheros/atl1c/atl1c.ko.ignore
acer@acer-Aspire-5349:~$ 


acer@acer-Aspire-5349:~$ uname -a
Linux acer-Aspire-5349 2.6.38-14-generic #58-Ubuntu SMP Tue Mar 27 18:48:46 UTC 2012 i686 i686 i386 GNU/Linux
acer@acer-Aspire-5349:~$ sudo modprobe ath9k
acer@acer-Aspire-5349:~$ locate ath9k.ko
/home/acer/Documents/linux/tools/wireless driver/compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/.ath9k.ko.cmd
/home/acer/Documents/linux/tools/wireless driver/compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ath9k.ko
/home/acer/Downloads/compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/.ath9k.ko.cmd
/home/acer/Downloads/compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ath9k.ko
/home/acer/compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/.ath9k.ko.cmd
/home/acer/compat-wireless-2012-04-12/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/2.6.38-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/2.6.38-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
acer@acer-Aspire-5349:~$ 

***at this point laptop is using wired connection connected to an AP client (no wlan active on the laptop).

thank you!

---

### Post by pytheas22 on 2012-04-16
**busols**: does the wireless come on if you type:
```

sudo modprobe ath9k
```

If that doesn't work, try:
```

sudo insmod /lib/modules/2.6.38-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
```

If you get error messages from either of these commands please post them.

If none of the above helps, please try compiling the ethernet driver (atl1c) again using the same commands you followed before, but make sure first to delete any folders on your desktop whose names being with "compat-wireless"  (You do not have to delete the compat-wireless tarball fall, which is not a folder.)  Also, skip step 6 of the commands ("scripts/driver-select atl1c").  When you are done, reboot.  If both the wireless and wired connections are still not working at that point, please post the output of:
```

lsmod | grep -e ath -e atl1c
sudo modprobe ath9k
sudo modprobe atl1c
dmesg | grep -e ath -e atl1c
lshw -C Network
```

---

### Post by busols on 2012-04-16
Hi Pytheas22;
thanks again and I am so sorry to bother you. I see that you have a very good linux experience I know that your are capable of writing commands and I am now educated by you in this forum.

okay, using the code here's what it gives:

acer@acer-Aspire-5349:~$ sudo modprobe ath9k
[sudo] password for acer: 
acer@acer-Aspire-5349:~$ sudo insmod /lib/modules/2.6.38-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
insmod: error inserting '/lib/modules/2.6.38-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko': -1 File exists
acer@acer-Aspire-5349:~$

if I type code:
sudo modprobe ath9k wlan won't come on.


please review before I move forward as I have to do it one at a time and I know you are busy. I might have to do it all over. also I want to post a screen shot showing both eth0 and wlan1 before I reboot the laptop but I don't know where to attach.

---

### Post by busols on 2012-04-16
Hi Pytheas22;

code:
lsmod | grep -e ath -e atl1c
sudo modprobe ath9k
sudo modprobe atl1c
dmesg | grep -e ath -e atl1c
lshw -C Network

acer@acer-Aspire-5349:~$ lsmod | grep -e ath -e atl1c
ath9k                 115574  0 
mac80211              451568  1 ath9k
ath9k_common           13780  1 ath9k
ath9k_hw              379900  2 ath9k,ath9k_common
ath                    19182  3 ath9k,ath9k_common,ath9k_hw
cfg80211              173697  3 ath9k,mac80211,ath
compat                 16044  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
acer@acer-Aspire-5349:~$ sudo modprobe ath9k
[sudo] password for acer: 
acer@acer-Aspire-5349:~$ sudo modprobe atl1c
FATAL: Module atl1c not found.
acer@acer-Aspire-5349:~$ dmesg | grep -e ath -e atl1c
[    0.969181] device-mapper: multipath: version 1.2.0 loaded
[    0.969184] device-mapper: multipath round-robin: version 1.0.0 loaded
[   14.930739] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.930756] ath9k 0000:07:00.0: setting latency timer to 64
[   14.939024] ath: EEPROM regdomain: 0x6c
[   14.939027] ath: EEPROM indicates we should expect a direct regpair map
[   14.939031] ath: Country alpha2 being used: 00
[   14.939032] ath: Regpair used: 0x6c
[   14.950687] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.951799] Registered led device: ath9k-phy0
acer@acer-Aspire-5349:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c3400000-c343ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan1
       version: 01
       serial: 64:27:37:33:91:25
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-14-generic firmware=N/A ip=192.168.1.41 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c2400000-c247ffff memory:c1400000-c140ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
acer@acer-Aspire-5349:~$ 

***If none of the above helps, please try compiling the ethernet driver (atl1c) again using the same commands you followed before, but make sure first to delete any folders on your desktop whose names being with "compat-wireless" (You do not have to delete the compat-wireless tarball fall, which is not a folder.) Also, skip step 6 of the commands ("scripts/driver-select atl1c"). When you are done, reboot. If both the wireless and wired connections are still not working at that point, please post the output of:***

***I followed the instructions above this is what it gives***
Note: atl1c detected, we're going to disable it. If you would like to enable it later you can run:
    sudo alx-load atl1c

Running alx-enable alx...
Disabling atl1c ...	[OK]	Module disabled:
updates/drivers/net/ethernet/atheros/atl1c/atl1c.ko
depmod will prefer updates/ over kernel/ -- OK!

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

acer@acer-Aspire-5349:~/Desktop/compat-wireless-2012-04-12$ exit

---

### Post by busols on 2012-04-16
Hi Pytheas22;
I had posts above this.
***Thank you for sharing to me the knowledge and patience!!!*** 
After spending some time.
It worked and hoping to stay this way. I can now connect to router and the internet using the eth0 or wlan1. DHCP/static ip's worked perfect. I'm loving linux.
maybe I can use some of the commands I learned from you to troubleshoot Cisco MWR2941 routers out in the field due to connectivity issues.
thanks.
Busols
[email]busols@yahoo.com[/email]

acer@acer-Aspire-5349:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:ee:16:2a  
          inet addr:192.168.1.32  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea9a:8fff:feee:162a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:956 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:1132236 (1.1 MB)  TX bytes:94564 (94.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan1     Link encap:Ethernet  HWaddr 64:27:37:33:91:25  
          inet addr:192.168.1.41  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6627:37ff:fe33:9125/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3427201 (3.4 MB)  TX bytes:591529 (591.5 KB)

acer@acer-Aspire-5349:~$ 


Laptop Acer aspire 5349-2899 running Ubuntu 11.04 Kernel 2.6.38-14 gnome 2.32.1
***Issues:***
1. no lan card atheros(atl1c)
2. no wlan card atheros(ath9k) wireless n capable recognized by the OS.

***here's exactly what I did to share with others***
***please note step #6 can skip, driver will detect hardware automatically if installed correctly but will take longer to process***
***download the appropriate kernel driver for your distro here [http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.38_stable_releases](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.38_stable_releases)
and save on the desktop***
***the downloaded driver worked for both lan card atl1c and wlan card ath9k***
***this will take some time so be patient.***
***for the lan***
from terminal:
1. sudo apt-get update
2. sudo apt-get install build-essential
3. cd ~/Desktop
4. tar -xjvf compat-wireless-2.6.tar.bz2
5. cd compat-wireless-20*
6. scripts/driver-select atl1c (atl1c for lan card)(optional per pytheas22)
7. make
8. sudo make install
9. sudo make unload
10. sudo make wlunload
11. sudo make btunload
12. reboot the laptop

***for the wlan***
from terminal:
3. cd ~/Desktop
4. tar -xjvf compat-wireless-2.6.tar.bz2
5. cd compat-wireless-20*
6. scripts/driver-select ath9k (ath9k for wlan)(optional per pytheas22)
7. make
8. sudo make install
9. sudo make unload
10. sudo make wlunload
11. sudo make btunload
12. reboot the laptop
***these steps worked, ethernet detected and can connect to router and to the internet***.
***thank you ubuntuforums***

---

### Post by pytheas22 on 2012-04-16
Glad it worked.  It seems like you just needed to compile both the ath9k and atl1c drivers at the same time.  In the future, you will probably need to repeat the process that made things work whenever you update your kernel.  Usually Ubuntu updates pushes out a new kernel package every month or so.

I would also give Ubuntu 12.04 a try when it appears later this month.  With any luck both your wired and wireless cards will both "just work" in that latest version of the operating system.

---

### Post by busols on 2012-04-16
> **pytheas22 said:**
> Glad it worked.  It seems like you just needed to compile both the ath9k and atl1c drivers at the same time.  In the future, you will probably need to repeat the process that made things work whenever you update your kernel.  Usually Ubuntu updates pushes out a new kernel package every month or so.

I would also give Ubuntu 12.04 a try when it appears later this month.  With any luck both your wired and wireless cards will both "just work" in that latest version of the operating system.

Hi Pytheas22;
thanks a million to you.
I guess its time for me to create a back up of the working system, is there any guide? my system is working and I'm loving it as we speak.
When I plugged the lan cable the lan connection takes over the wlan automatically which is nice.
***I have a question***
1. is there a way to turn off kernel auto update?
2. my compiz yes the desktop cube is not working is there a way to make it work? I have compiz and compiz-fusion-plugins-extras installed but no worky.

***I need another system for the Ubuntu 12.04 coz it took me some time (27 hours to be exact) to make this system work the way I wanted***.
thank you.
busols

---

### Post by pytheas22 on 2012-04-17
**busols**: you can disable updates in general using the Software Sources tool.  I don't know of a way to turn off kernel updates specifically, however.  Also, it is not generally a good idea to disable kernel updates because they include security patches.

Your compiz issues are most likely related to your graphics driver, but I'm afraid I don't know as much about that stuff.  You should start a new thread for this issue in the appropriate part of the forums.

On backing up the system, refer to the [wiki]("https://help.ubuntu.com/community/BackupYourSystem") or google.

---

### Post by adamant715 on 2012-05-11
I'm actually having a similar problem in Ubuntu 12.04.. The internet barely works at boot until I run "sudo dhclient eth0" in a terminal. My network card is a Marvell Yukon 88E8053 PCI-E Gigabit Ethernet Controller.

---

### Post by pytheas22 on 2012-05-11
**adamant715**: a simple solution would be to [write a boot script]("http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") so that command runs automatically each time you turn on your computer.  If you need further instructions let me know.

---

### Post by mauro66404 on 2012-09-18
Salve Pytheas22,sono un nuovo utente mi chiamo mauro66404 e mi sono appena registrato proprio perchè sono interessato alla vostra discussione perchè anche io ho problemi di connessione e specialmente con ubuntu10.04.4LTS 32bit.Sono sicuro che la soluzione del mio problema è nel link riportato nel tuo messaggio#6 e sarebbe il file 2.6tar.bz2.Ho rpovato ad andare dove ti dirotta il tuo link ma una volta arrivato nel sito linuxwireless provo a cliccare su download ma non accade nulla.Come si dovrebbe procedere per poter scaricare questo benedettissimo file?Attendo tue notizie e ti ringrazio anticipatamente per questo!MAURO66404

---

### Post by mauro66404 on 2012-09-22
Salve ragazzi!
Mi scuso se non parlo inglese,cercherò di rimediare.
Per PITHEAS22.
Sono riuscito a scaricare il file compact-wireless2.6.tar.bz2,come avevi consigliato all'altro utente.
 dopo installazione su pendrive il sistema rifiuta il CD 10.04.4LTS i386 non consentendomi di procedere con installazione driver.
Cosa posso fare?

---

### Post by pytheas22 on 2012-09-22
**mauro66404**: I can't read Italian.  Sorry.  You might have better luck at [http://forum.ubuntu-it.org/](http://forum.ubuntu-it.org/)

---

### Post by Repgahroll on 2012-10-09
Hello there.
I'm experiencing intermittent connection with an AR8151, on another thread the guys were having this problem and it seems the solution pytheas22 posted here actualy solved the issue for them.
I already rebooted and am testing right now with fingers crossed. Until now the thing is working, I'll let you know if it's actually working properly after some hours of torrent downloading.
Thank you.

---

### Post by Repgahroll on 2012-10-10
Unfortunately the problem is still happening here. Maybe it has something to do with my router. Thank you anyway.

---

### Post by jherrick42 on 2013-02-07
> **pytheas22 said:**
> **tedmar**: it's a compilation error, so you might have better luck if you downloaded a different snapshot of the source code (especially an older one).  The copy you got could just happen to have a bug in it.  At [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) you can grab copies from a wide range of different dates.

If that doesn't help, please post the output of:
```

lspci -nn
```so I know exactly which chipset you have.

Also, chances are the device would "just work" if you upgraded to a more recent version of Ubuntu, if that is a possibility.  10.04 is not getting a bit old.

I just installed 12.10 on a brand new desktop I put together.  I'm thinking the driver issue is my problem as well.  I got the same compilation error so I went to [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and grabbed the file named [compat-wireless.tar.bz2]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless.tar.bz2") dated Feb 6 2013 that is 6.1MB.  Is this going to be the same as the one you called out on the first page?   Apologies, but I haven't been able to read the whole thread yet...  Thanks!

---

### Post by pytheas22 on 2013-02-09
**jherrick42**: this thread is now very old, and I would not assume that your problem is the same as the one that the thread originally addressed.  Could you tell us more about what exactly is not working for you?  If it's your ethernet card not working, it would be helpful to see the output of:
```

lspci -nn
lshw -C Network
ifconfig
uname -a
dmesg | grep -e eth
```

---

### Post by BertrandL4 on 2013-03-16
> **pytheas22 said:**
> Your ethernet hardware seems to be quite new and doesn't have a driver built into Ubuntu as of yet.  However, there's a driver included in the compat-wireless stack that you can use (I have no idea why they included an ethernet driver in compat-wireless, but according to [these emails]("http://omgili.com/mailinglist/kernel-team/lists/ubuntu/com/43e72e891002020915x572a11fcg57f0b9caf7ed08eamailgmailcom.html"), someone did).

To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (you can't download it in the terminal because of anti-hotlinking).  Save it to your desktop. Then run these commands (the first two commands require that you either have an Internet connection, or have your [Ubuntu installation CD enabled as a software repository]("https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD")):
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
scripts/driver-select atl1c
make
sudo make install
```

Then reboot.  Hopefully your ethernet will work automatically after reboot; if not, run:
```

sudo modprobe atl1c
```

to insert the driver.  Let me know how it goes.

We can probably make your wireless work too, if you're interested.

Three years latter, I get the same problem with ethernet card driver on Ubuntu 64bits. the above solution fixes it. Thanks.

---

### Post by BertrandL4 on 2013-03-16
Hello,

My card is now running after doing the above suggestion. I Installed Ubuntu 64 on my Toshiba L770 4 weeks ago and immediately lost my ethernet connexion. I searched many forums and didn't get this one. I tested other solutions but didn't get results. So I thought this was a hardware problem and gave back my computer which has yet under garanty. They change mothercard. One week ago I got back my computer and installed again Ubuntu 64. I lost again the ethernet connexion. But not when booting on Ubuntu 32 or windows. Today I apply the above instructions and the driver is now working.
So I cannot give you old outputs of commands, but I remenber I got :
[B]lshw -C Network
[/B]_Output :_
WARNING: you should run this program as super-user.
*-network UNCLAIMED

---

