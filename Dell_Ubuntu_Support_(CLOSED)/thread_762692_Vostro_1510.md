---
title: "Vostro 1510?"
date: 2008-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drr104 on 2008-04-22
Has anyone tried installing Ubuntu on either the Vostro 1310 or 1510? I assume these models are quite different to the 1500 and 1700.
They look like a nice alternative to the XPS range (i.e. cheaper :))

---

### Post by StefAndrew on 2008-04-23
I read that these are not available in the US until May 1st, so probably not a lot of people have one yet to try and install Ubuntu on it yet.  I know on my 1500 it works fine, but this looks like it is based off the newer chipset from Intel.

Also, they look VERY boxy.  Lots of hard edges.  The nice thing is the slot loading CD/DVD tray though.  If you don't mind the squareness of them, they look like an alternative to XPS.  I have to admit I do love my Vostro 1500.  And I don't mind it being plain old black and what most would consider bland.  I like it that way.

I'll try to do some digging on the international dell pages to see if I can find some specs on them.

---

### Post by Matsuri on 2008-05-24
Dell Vostro 1510
2.1GHz Pentium Dual Core (I think 3 mb cache)
3 GB ram
NVidia GeForce 8400M GS 256MB Onboard
160GB Hard drive
X-HiBright Wide Screen (1440x900)

I just recently purchased a Dell Vostro 1510 and dual booted it with Windows XP and Ubuntu Hardy Heron. The install took very well. It recognizes the battery, media menu that is on the keyboard, and even includes working settings for laptop lid shut, hibernation and adv. screen saver settings. I managed to get wireless running by installing ndiswrapper and downloading the Dell wireless drivers for my card and installing them through the ndiswrapper interface. 

Automatically sets the screen res. to 1440x900. However, you must do a system update and make sure the "new" NVidia drivers are installed to enable the Desktop effects. Desktop effects worked on both settings.

So far I have run into almost no problems at all. The only "problems" I've encountered is for some reason Dell placed a NTFS partition for windows, FAT32 and FAT16 partitions that I do not know what they are for. Any help? The other "problem" is that for some reason upon repartitioning the hard drive and shrinking the NTFS windows partition it would not allow me to reserve a 1GB swap partition for whatever reason. When I allocated space for either the Linux partition or the SWAP it made the titled the remaining space as "Unusable" and denied me any access to it. With 3GB of ram SWAP won't do a whole lot for me but it would be nice to have it.

Other than those small issues everything seems to be running perfectly. Time will tell. PM or EMail me if you want more details on getting the wireless enabled!

Matsuri

---

### Post by Disty on 2008-05-29
Just to note - i bought a Vostro 1510 with the WUXGA (1900*1200) screen- arrived yesterday. I was thinking it would be as difficult to get hardy heron on it as it is to get it on the 1500's- I popped the cd in just to check, and it worked like a dream.

As the other fella said, enable the restricted nvidia drivers for compiz + better bit depth, but native resolution seems to work out of the box. I didn't have any trouble with the wireless- recognized automatically. Webcam also works. Haven't got the bluetooth option so can't comment there. I had trouble going into standby the second time.

Definately recomment the highest res sreen - it sealed the deal for me.

The near-perfect compatibility makes me wonder whether Ubuntu will become a stock option on these too? I reckon the 1510 is prettier too ;)

---

### Post by keryonic on 2008-05-29
I have a Vostro 1310 and installed Ubuntu 8.04 (Hardy Heron). Everything works well except the microphone. At first Nvidia card was not loaded but it worked then it updated automatically and proposed Nvidia driver which works fine. I have spent a lot of time fine tuning my computer and loading it with softwares I needed. I come from Windows and I had to learn a lot (still learning). A good advice is to install only (if possible) softwares with repositories. I had a problem installing Google Earth directly from the web site because the last version didn't work but the one (older) in the repository works perfectly. I had another problem with a DVB TV USB stick. I messed with my config and the webcam disappeared. I gave up with TV. Because I am a total noob, sometimes I spend too much time finding a solution to a stupid problem but most of the time I find a solution on the web. Ubuntu is a very good alternative for work and leasure and I think it has a bright future. Neverthless, I have a double boot with Vista (My laptop came with it) and in Virtualbox, I installed XP which is very fast (slight problems with some USB devices and with the webcam) but usually I never use Windows anymore.

Please publish and share your experience here. If you need any advice, I'll try to help.

---

### Post by Matsuri on 2008-06-03
> **keryonic said:**
> 
Please publish and share your experience here. If you need any advice, I'll try to help.

This is a Vostro 1510 thread. ;)

---

### Post by elastigirl on 2008-06-10
Thank you for this! I think I will be picking up this model myself. As a full Ubuntu convert, it would break my heart to see that I would have trouble with Hardy Heron on the Vostro 1510. This post is comforting!

Will get back to you if I have any issues with the wireless setup, will need your expertise :-)

---

### Post by Matsuri on 2008-06-15
Noticed an annoying glitch. When you are in XP and then reboot into the Ubuntu install, for some reason the wireless card doesn't initiate. However, if you simply reboot again into linux or boot into linux from shutdown the wireless works.

If I figure out the problem I'll post it or link to it here.

---

### Post by rony474 on 2008-06-15
using with vostro 1400 , and also tried vostro 1310 .. all ok ...

---

### Post by jgrabham on 2008-06-22
Great, I might order a Vostro 1510 this afternoon

1.8Ghz C2D
2GB
160GB
Intel onboard

£351

One question though, what are the multimedia controls like on ubuntu?

---

### Post by atulpathria on 2008-07-19
I order yesterday for Vostro 1510 R520703
2.0 C2D 800Mhz
2Gb 667Mhz Dual Channel Ram
Integrated Intel® Graphics Media Accelerator X3100
160 GB
15.4
DVD Writer Dual Layer
DOS installed


And i want to know if i install ubuntu 8.04 is any driver required or it automatically detects all.

---

### Post by David1998 on 2008-07-22
I have a new Vostro 1510 and am very happy with it. It has the T7250 (2.0 Ghz) Win XP, 3GB RAM, and the 256MB Nvidia GEFORCE 8400M. It has the Cyberlink PowerDVD 8.0 DVD Playback with the 8X DVD+/-RW, DL+/-R, W/RXO  DVD player - very nice and tidy.

I built an ISO of 8.04 and booted off the CD. The menu came up all right but when I choose run from CD, everything just freezes.  Any ideas?  I would like to run from CD before I set up to dual boot, you know just for practice.

Thanks

---

### Post by empty_tank on 2008-07-23
> **David1998 said:**
> 


I built an ISO of 8.04 and booted off the CD. The menu came up all right but when I choose run from CD, everything just freezes.  Any ideas?  I would like to run from CD before I set up to dual boot, you know just for practice.

Thanks

check the CD for problems.

---

### Post by eldragon on 2008-07-26
using the livecd with a vostro 1510 right now
intel wireless works (WEP) (copies files 2x faster than vista)
sound works
intel graphics work.
1280x800 res works ok
card reader works too

cant think on anything else to coment on..


it just works.

---

### Post by darthmob on 2008-07-26
I'm thinking about getting a 1310. there is no real difference in the included components so my question seems valid.

is anyone using the Intel®  4965AGN Wireless-N minicard?

---

### Post by Matsuri on 2008-08-01
> Great, I might order a Vostro 1510 this afternoon

1.8Ghz C2D
2GB
160GB
Intel onboard

Why settle at the 1.8, the 2.1 or 2.3 not to much more to add on to the price. The added speed with 2g of ram can really make the machine scream!

---

### Post by R%&amp;92GH&amp; on 2008-08-05
In my case, everything worked out of the box except:

- Wireless lan: I had to configure it using ndiswrapper and the windows drivers. Now it works.
- Built-in micro: Haven't managed it to work yet..
- Graphics card: It worked, but it's recommended to install the nvidia restricted drivers for better performance.

I haven't tried the external micro input (I would prefer the internal one to work), I haven't burnt any Cd or Dvd yet (but I've never had any issue with any computer regarding this), and I haven't tried the memory card reader (again, it usually works in every computer I've tried before, so..)

And it's just me, or the sound volume it's quite low?

---

### Post by hnafets on 2008-08-11
I have a vostro 1510 with vista/ubuntu dualboot (installed ubuntu under windows) and here's what I had to do to get wireless working

(i should note that I an a noob with regards to linux, so maybe this will help someone like me to try it out. it's really not hard and definetly worth it. the other things worked out right without any tweaking. plus, once you get internet everything becomes cake -- great online documentation and help):

1. boot up windows. I had to get the wireless driver for windows XP (the vista one did not work for me) from dell's driver website. open up the file that downloads, but once it extracts the contents of the exe, stop the driver installation.

2. boot up ubuntu and install the windwos wireless driver tool (preferences->synaptic package manager; at this point, insert the ubuntu cd and from the synaptic package manager pick add cd (it's under one of the menus up top))

3. once it's added, go to network and select ndisgtk to install and let it install it.

4. mount the windwos parition (for me it was /dev/sda3).

5. go into system->administration->windows wireless drivers and select add driver. if you cant see the windows wireless drivers you may need to reboot ubuntu. navigate to your mounted windows partition, under DELL\drivers\ and find the folder in which the windwows driver was extracted. look for the .inf file, open it and once the driver is installed it should work.

6. happy ending :)

---

### Post by fiscal.mamutinho on 2008-08-11
I have a Vostro 1510 and I'm having problems with the network card. Not the wireless, the wired one. It seems that Ubuntu detected correctly, but I can't get internet access.
Everything is set to automatic, and in windows I have the internet, but when I boot Ubuntu, it doesn't work. One strange thing is that ethtool says that the speed of the link is 1000, when it was supose to say 100. I tried to force speed 100 but it didn't work. I tried with ethtool -s eth0 speed 100 duplex full autoneg on, and I tried with autoneg off too.
Anyone has an idea what's happening??
Thanks!

---

### Post by riahc3 on 2008-09-07
> **fiscal.mamutinho said:**
> I have a Vostro 1510 and I'm having problems with the network card. Not the wireless, the wired one. It seems that Ubuntu detected correctly, but I can't get internet access.
Everything is set to automatic, and in windows I have the internet, but when I boot Ubuntu, it doesn't work. One strange thing is that ethtool says that the speed of the link is 1000, when it was supose to say 100. I tried to force speed 100 but it didn't work. I tried with ethtool -s eth0 speed 100 duplex full autoneg on, and I tried with autoneg off too.
Anyone has an idea what's happening??
Thanks!

That makes two of us. Ive found that restarting sometimes makes internet access avaliable...

Id try fixing wireless but I dont have a internet connection on the laptop.

---

### Post by Idefix82 on 2008-09-09
I have a Vostro 1710, also dual booting Ubuntu with XP and I have a similar problem with the wired ethernet card. One solution that I have read elsewhere is to enable wake-on-lan after shutdown under Win XP (you can do it in the hardware manager). Unfortunately it didn't resolve the issue for me but you can give it a shot.
Another thing which sometimes works is shutting down the laptop, unplugging it from any power source, waiting for about 20 seconds and starting it up again. Of course this is not a long term solution but I would be interested to hear if either has any effect for your computers.

---

### Post by r!ots on 2008-10-10
I recently installed Ubuntu Hardy Heron amd64 on a friend's Vostro 1510 and the installation went totally smooth.
The network and graphics card driver from the restricted drivers menu work flawlessly as well as sound and everything else does, but from time to time the laptop just freezes, so only a hard reset can be done. So far we couldn't relate those system hang-ups to any specific program, they just seem to happen sometimes. Has anyone of you experienced something similar? Are you using the x86- or the amd64-version? And why? I don't want to start a discussion about which one is better, I was only wondering whether this could be a reason for those strange freezes.

---

### Post by riahc3 on 2008-10-17
Core 2 Duo T5670
2GB
nVidia 8400gs
Intel 4965agn

Can't get wireless into monitor mode.
Brightness controls  is glitchy
The media buttons do NOT work
WiFi LED does not work (Does anyone know how to fix this on 8.04/2.6.24-19-generic?)
You MUST disable that the touchpad surface acts like the left click button because else its unusuable
Hibernation doesnt work (Wubi)
Sound settings dont work using "blue" keys on laptop

---

### Post by urugTON on 2008-11-03
I recently purchased a Vostro 1510.  Naturally Vista was there.

T5670, 2GB
WXGA+ LCD w/Intel X3100 onboard graphics
Intel 3945 WiFi
160 GB HD

FWIW, I'm new to Linux and I was trying very hard to configure a system that would not be too much of a challenge for a newbie to get running.  Dell has a 30 day no questions asked return policy.  I specified Intel for linux compatibility rather than price or performance.

I coaxed Vista to give me back 80GB, but no more.  That will get fixed as soon as I run out of space for linux.  Vista is there to prove that the delivered hardware worked and for a few applications such as Word.  I use Open Office, but sharing OO documents with MS users can be entertaining. 

Initially I installed 8.04.  Everything but the wireless worked out of the box.  Getting the wireless running required back ported drivers and Wicd.  No big a deal. 

This weekend I added the just released 8.10 to the laptop.  I don't trust upgrades so I did a fresh install of 8.10 to its own root partition.  I do share /home between the two.  Now I can successfully boot Vista, 8.04 & 8.10.  

Again everything worked out of box – even the wireless!  On 8.10, the wireless was configured for me.  I entered the pass phrase for the WPA connection (PSK was already set) and away I went.

I'm impressed with 8.10 and very happy with it at the moment. 

FWIW, the $50 extra for the higher resolution screen is a pleasant and worthwhile surprise.  My aging eyes can read far smaller text than I'd expected.  OTOH, the extra 1 GB I ordered in case I needed to run Vista for a bit is not getting used.  Oh well.

---

### Post by nexuz on 2008-11-09
> **urugTON said:**
> I recently purchased a Vostro 1510.  Naturally Vista was there.

T5670, 2GB
WXGA+ LCD w/Intel X3100 onboard graphics
Intel 3945 WiFi
160 GB HD

FWIW, I'm new to Linux and I was trying very hard to configure a system that would not be too much of a challenge for a newbie to get running.  Dell has a 30 day no questions asked return policy.  I specified Intel for linux compatibility rather than price or performance.

I coaxed Vista to give me back 80GB, but no more.  That will get fixed as soon as I run out of space for linux.  Vista is there to prove that the delivered hardware worked and for a few applications such as Word.  I use Open Office, but sharing OO documents with MS users can be entertaining. 

Initially I installed 8.04.  Everything but the wireless worked out of the box.  Getting the wireless running required back ported drivers and Wicd.  No big a deal. 

This weekend I added the just released 8.10 to the laptop.  I don't trust upgrades so I did a fresh install of 8.10 to its own root partition.  I do share /home between the two.  Now I can successfully boot Vista, 8.04 & 8.10.  

Again everything worked out of box – even the wireless!  On 8.10, the wireless was configured for me.  I entered the pass phrase for the WPA connection (PSK was already set) and away I went.

I'm impressed with 8.10 and very happy with it at the moment. 

FWIW, the $50 extra for the higher resolution screen is a pleasant and worthwhile surprise.  My aging eyes can read far smaller text than I'd expected.  OTOH, the extra 1 GB I ordered in case I needed to run Vista for a bit is not getting used.  Oh well.

I'm having some troubles with my ethernet card, I've tried everything, using the r1869 module or replacing it with the r8168, but my ethernet wont work!... it just suck!!... I dont know what to do about it!

---

### Post by urugTON on 2008-11-13
Nexus,

From where your post is located, I'm assuming that you have a Vostro 1510.

FWIW, I've tried several different versions of Ubuntu on 3 different computers and had no trouble with the wired connections.  OTOH, I'm not the best of linux networkers so I used Vista to check things before I loaded Ubuntu.  If you are using a Vostro 1510, I'd try to establish that the ethernet connection works under Vista - just to make certain that you're not fighting a hardware problem.  Let us know what happens with Vista.

To get any more help, would you post the results of a the following commands:

uname -a
lspci
ifconfig
ethtool -i eth0

It would also help if you could tell us a little about your network connection.  For instance, do you use a router or connect directly to a DSL/cable modem?  What kind of router and/or modem? 

Good luck.

---

### Post by nexuz on 2008-11-14
> **urugTON said:**
> Nexus,

From where your post is located, I'm assuming that you have a Vostro 1510.

FWIW, I've tried several different versions of Ubuntu on 3 different computers and had no trouble with the wired connections.  OTOH, I'm not the best of linux networkers so I used Vista to check things before I loaded Ubuntu.  If you are using a Vostro 1510, I'd try to establish that the ethernet connection works under Vista - just to make certain that you're not fighting a hardware problem.  Let us know what happens with Vista.

To get any more help, would you post the results of a the following commands:

uname -a
lspci
ifconfig
ethtool -i eth0

It would also help if you could tell us a little about your network connection.  For instance, do you use a router or connect directly to a DSL/cable modem?  What kind of router and/or modem? 

Good luck.

When I mount the module r8169 I get this:

nexuz@nexuz-ubuntu:~$ uname -a
Linux nexuz-ubuntu 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux
nexuz@nexuz-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
nexuz@nexuz-ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  direcciónHW 00:21:70:94:5b:89  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:1035802300 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:216 Dirección base: 0x6000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:1f:3c:8d:d1:23  
          inet dirección:10.0.0.5  Difusión:10.0.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::21f:3cff:fe8d:d123/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:382 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:445361 (445.3 KB)  TX bytes:66029 (66.0 KB)

wmaster0  Link encap:UNSPEC  direcciónHW 00-1F-3C-8D-D1-23-31-32-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nexuz@nexuz-ubuntu:~$ ethtool -i eth0
driver: r8169
version: 2.3LK-NAPI
firmware-version: 
bus-info: 0000:07:00.0

===========================================

and with the r8168 I get this:

nexuz@nexuz-ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  direcciónHW 00:21:70:94:5b:89  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:216 Dirección base: 0x6000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:1f:3c:8d:d1:23  
          inet dirección:10.0.0.5  Difusión:10.0.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::21f:3cff:fe8d:d123/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:1127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1022 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:1404665 (1.4 MB)  TX bytes:147407 (147.4 KB)

wmaster0  Link encap:UNSPEC  direcciónHW 00-1F-3C-8D-D1-23-31-32-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nexuz@nexuz-ubuntu:~$ ethtool -i eth0
driver: r8168
version: 8.009.00-NAPI
firmware-version: 
bus-info: 0000:07:00.0

======================================

Thanks.

---

### Post by m_pourfathi on 2008-11-30
Yup!

Vostro 1510 
Intel Core 2 Duo T9300, 2.5 GHz, L2 6 MB cache, 800 MHz FSB
4 GB Ram.
320 GB storage.

I installed it on my windows vista ultimate and works just fine.

---

### Post by nexuz on 2008-12-18
It's very strange... I'm using Fedora 10... and everything works great... I mean... everything... even my wired-card... that I was having trouble with. Does anyone have any idea why is that?... I want to use Ubuntu!

---

### Post by TheShadowMaster on 2009-02-05
I have absolutely no issues with Vostro1510 & Ubuntu 8.1. Everything works just fine including the media touch buttons. Only one issue is that fact that you cannot use aircrack with the internal wireless card, at this point there is not a supported driver, however, you can use it to produce authentication handshakes and generate traffic for WiFi in combination with a WUSB54GC type wireless usb card. Works brilliantly.

---

### Post by ehsan.s on 2009-02-20
hi everybody. 
I've got a vostro 1510.
I have same problem with each linux.I can't install Graphic driver. has anybody installed it? how?

---

### Post by joker535 on 2009-03-15
I just bought a 1510 during last months 2 day sale. It came with XP pro SP3/Vista business, C2D 1.8, 3G of DDR3, 250G HDD and DVD burner for $499. I swapped the dell g wireless for the intel a/b/g one in my other dell (both work fine in ubuntu, I just wanted a/b/g) and installed 8.10 with no problems. The wireless light flashes instead of being on solid but it works fine and doesn't hurt anything. I am extremely happy with it.

---

### Post by marn on 2009-04-06
My Vostro 1510 arrived three days ago and I installed Ubuntu 8.10 64 Bit after making sure that my hardware support would not be affected (nice email from technical support stating that the operating system has nothing to do with the hardware support and will not affect it in any way)

System: 2 Ghz Intel Core 2 Duo, 4 GB Ram, Intel Integriert GMA X3100, Wireless-N adapter 

Installation: as of yet no issues. Everything ran perfectly out of the box. What was nice, is that the power support (hibernation, standby etc) works perfectly (was a big problem with my old acer laptop). Webcam works with luvcview.

Yet to be tested: mic, VGA out, card-reader

I'm very pleased with the laptop (and Ubuntu ;)) All the lights work properly as well :p

---

### Post by combuster on 2009-04-11
I have Vostro 1310 and I would like you to post your experiences with upcoming jaunty. I never had problems with Ubuntu and 1310 but with jaunty beta I have a big problem with touchpad and keyboard. If someone can confirm that this is an issue common to all laptops with alps touchpad as Vostro:

[https://bugs.launchpad.net/ubuntu/+bug/359480](https://bugs.launchpad.net/ubuntu/+bug/359480)

---

### Post by Guillaumeb on 2009-04-19
Hi

I got a Dell Vostro 1510. Would love to install 9.04... Can't wait to read your experience .

---

### Post by zebobo on 2009-04-27
Report on bsd/ubuntu on dell vostro 1510:
I've got a vostro 1510 n-series (no windows-tax wohoo) with intel T5870 cpu
4 GB internal memory, enough hdd and integrated graphics card with an x300 ati core.
The wireless card is the dell integrated card and wired card is a realtek.

I ran the laptop on freebsd and it worked perfectly. Later on I installed ubuntu because I'm not the one using the laptop. That being said - this is what I experienced with ubuntu:

First I took some old Dapper Drake 64-bit cd and installed ubuntu - which worked like a charm although I had to run the install in safe graphics mode. Then I just ran a gksu dist-upgrade -c or something like that and had it upgrade to 8.04 Hardy Heron. 
I could have bet anything on that it wouldn't work, but I had to try - and was surprised with an upgrade function that actually worked!! kudos to ubuntu!!

The wlan-card was recognized directly in 8.04 and drivers (Broadcom STA) were installed. Wlan is working occasionally and I haven't really seen any pattern in when it doesn't. It worked similarily in bsd. Sometimes the device disappears. I'll check into that later.

ubuntu uses the vesa-driver for the x300, which is not optimal, and I don't really know if I want to try anything else right now... last time I tampered with the xorg.conf like I normally do in bsd things went real bad. Anyone got it working?

I've tried almost everything on the laptop and it's working more or less.  Even the media controls work nicely.

What does not work as it should yet is: the graphics chipset and the wlan.
\end{report}
please write a response if you found out something particularily about the wlan-card :)

---

### Post by mariannn_b on 2010-06-21
Hello!

I have a Dell Vostro 1510 with T9300 @  2,5GHz 3GB RAM nvidia 8400M GS.

Installed Ubuntu 10.04 but the temperature for CPU and GPU are going mad. The GPU is about 90 and CPU about 100-105 when using skype. They are all Celsius degrees. 
Anyone got something like this?

I have installed lm-sensors and they work fine only for CPU. I can only see the temperatures, no voltages, no fan speed and anything else.

Can you think of some solution?

---

