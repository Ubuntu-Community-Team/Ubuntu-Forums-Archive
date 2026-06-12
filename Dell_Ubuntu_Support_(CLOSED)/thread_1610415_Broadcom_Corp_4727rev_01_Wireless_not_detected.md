---
title: "Broadcom Corp 4727rev 01 Wireless not detected"
date: 2010-10-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lookout4lpe on 2010-10-31
I have a Dell 17R Dual Booted with Win7 and Ubuntu 10.04 LTS amd64.  I was successful in creating the partitions from the live disk and loaded 10.04 without any problems.  The wireless in the laptop works under Win7 but will not work when I go to Ubuntu. I have even disabled the wireless hookup and used a network cable to try to get to the interned via a wired hookup. With no luck I searched the forum and entered at the terminal:

 lspci

I went to the terminal and received this output:

len@len-laptop:~$ lspci                                                         
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18 )  
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18 )                                                     
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
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)                                                
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)                                                    
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)       
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)   
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)         
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)         
len@len-laptop:~$                                                               
len@len-laptop:~$                                                               

This showed that I was working with a “Broadcom Corporation Device 4727 (rev 01)” network controller.  
With no internet hookup, I placed the live cd in the disc drive, knowing that the driver needed was on the live cd at 
“cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/ lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 “.

I then ran:

sudo apt-get update


len@len-laptop:~$ sudo apt-get update                                           
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                       
  Could not resolve 'security.ubuntu.com'                                       
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                 
  Could not resolve 'archive.ubuntu.com'                                        
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US        
  Could not resolve 'archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/ lucid/restricted Translation-en_US
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

With all the failures I tried again.

I ran:
   
    sudo apt-get install bcmwl-kernel-source

len@len-laptop:~$ 
len@len-laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,187kB of archives.
After this operation, 3,969kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/ lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3
  File not found
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/ lucid/main fakeroot 1.14.4-1ubuntu1
  File not found
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)/ lucid/main patch 2.6-2ubuntu1
  File not found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_amd64.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
len@len-laptop:~$ 


Please help me get on line.  I am new to Ubuntu, but willing to learn.  Thanks, Len

---

### Post by Enigmapond on 2010-10-31
Have you simply tried using your wired connection and going to System/Administration/Hardware Drivers and letting it download the driver needed?

---

### Post by lookout4lpe on 2010-10-31
Thanks for your reply.  Yes, I have tried hooking up via network cable to my router and get no response.  When I boot to Win7 I do get wired and wireless connection.

---

### Post by Stray Wolf on 2010-11-01
I had a similar issue though I never allowed windows to boot on my laptop.  The fix for me was to toggle the WiFi button then restart.  I had to do it twice.  After the second time mine has worked every since.  If toggle solution works for you - you may have to do it every time you switch from booting windows to ubuntu.  I think windows turns of the WiFi card when it shuts down.

---

### Post by lookout4lpe on 2010-11-01
Thanks for your comment.  I tried your suggestion and cycled through Win7 back to Ubuntu and was not able to go to Ubuntu and get a wireless or wired internet connection.

---

### Post by ugm6hr on 2010-11-01
The problem is your wired card, not wifi.
The wifi will work - all you need do is download the drivers.
Unfortunately, downloading the drivers requires internet - so a bit of a catch 22.

Installing the driver without a wired connection is a pain...
[http://ubuntuforums.org/showthread.php?p=9263039#post9263039](http://ubuntuforums.org/showthread.php?p=9263039#post9263039)

Else, you could install wired driver first...
[http://ubuntuforums.org/showthread.php?p=9446984#post9446984](http://ubuntuforums.org/showthread.php?p=9446984#post9446984)

Or, my suggestion...
Just install 10.10 (maverick). That should have your wired driver as default, and so you could just plug in, and install wifi drivers with a single command:
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by lookout4lpe on 2010-11-01
I was begining to question the use of 10.04, but I was thinking of going back to 9.X.  I had read quite a few posts about the problems with the driver for this device.  Thanks for your suggestion, I will try 10.10.  I am downloading it now and will give you a status tomorrow.

---

### Post by ugm6hr on 2010-11-02
Any more problems - just report back....
Keeping fingers crossed for you!

---

### Post by lookout4lpe on 2010-11-02
Going to 10.10 has a few problems for me.  (My satellite took 8 hours to download the live 10.10 install disc.)  The iso file is now on a CD and I started the install process.  Since I have a dual boot partition setup now I selected to specify partitions manually.
They are currently:
        /dev/sda
	/dev/sda1 – fat16 – 104mb (Dell Utility)
	/dev/sda2 – ntfs – 15728mb (Recovery, boot flag)
	/dev/sda3 – ntfs – 238260mb (OS Win7)
	/dev/sda5 – ext4 – 235998mb (Ubuntu 10.04)
	/dev/sda6 – swap – 10011mb (linux swap)
I selected /dev/sda2 (boot loader) and selected /dev/sda5 as the partition table to change.
The edit partition screen showed size of 235998mb, I selected use as: ext4, and stopped when it asked format partition? and mount point?  Leaving format unchecked and selecting “/” as the mount point I said OK and the allocate drive space screen asked, install now?  I also noted that the boot loader entry reverted to the default value of dev/sda.

I was not comfortable proceeding with a format process without some further guidance since reading all the documentation did not give a hint about this manual partition process.  Do I need change only sda5 partition?   Should format be selected?  What is the correct mount point?  Do I need to re-enter the sda2 boot loader entry?  Should sda6 be changed and if so, how?

I was able to run 10.10 in trial mode and it did hook up to my wireless network.  If you can help me get the correct manual partitions set up, I think this will work.  Thank you.

---

### Post by ugm6hr on 2010-11-04
Manual partitioning is fairly straightforward when you understand what it means:
/dev/sda is the best option as "boot-loader"
/dev/sda5 is "/" (ext4) - select format
/dev/sda6 is linux-swap - the format option is normally blanked out

PS: If you want to make your installation future-proof, consider creating a separate "/home" partition - there are plenty of online tutorial on how to do so.

---

### Post by lookout4lpe on 2010-11-05
I did create another partition for “/home” and ran the complete installation.  Partitions are now:
/dev/sda (Was selected for boot loader)
/dev/sda1 – fat16 – 104mb (Dell Utility)
/dev/sda2 – ntfs – 15728mb (Recovery)
/dev/sda3 – ntfs – 238260mb (OS Win7)
/dev/sda5 – ext4 – 9770mb (“/home” Ubuntu 10.10)
/dev/sda6 – swap – 10016mb (linux swap)
/dev/sda7 – ext4 – 210020mb (“/” Ubuntu 10.10)
Ubuntu 10.10 loaded OK.  The restricted drivers for the wired card were not installed so I still cannot get online.  If I go back to live cd, the restricted drivers are loaded.  The wired (auto-eth0) became active and wireless was also available.  Also, after complete shut down I cannot boot into Win7 anymore.  The boot loader recycles to the selection screen and I can go back to Ubuntu 10.10 but not Win7.

---

### Post by ugm6hr on 2010-11-05
1. It would have made more sense to make /home bigger than / - the latter will almost never require more than 20GB.
2. I'm afraid I haven't had to use "Grub 2" to multiboot - I would suggest starting a different thread to ask how to reboot into W7.
3. Restricted drivers should not be required for the wired device - as far as I know, the drivers are open source.

Boot into the installed Ubuntu, and paste the output from the following commands back here:
```
lshw -class network
ifconfig
```
You may have to copy / save the text and reboot into LiveCD to get online.

---

### Post by lookout4lpe on 2010-11-05
Since I have no real data on the Ubuntu 10.10 install, I may redo it to resize the partitions, re-install, and then figure out the Grub 2 boot problem.  You are correct, wired device is loaded with live cd.  The notice for restricted drivers does show a notice that the driver for the Broadcom BCM4312 is not activitated. Activitating it brings up the wifi and connects the wireless network. I do not know why the installed Ubuntu doesn't do the same.

I will re-post to address the Grub 2 issue. The following is the output you requested.

len@len-Inspiron-N7010:~$ lshw -class network
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
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: f0:4d:a2:45:2f:1d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 multicast=yes
       resources: irq:45 memory:f0400000-f043ffff ioport:2000(size=128)
len@len-Inspiron-N7010:~$ 
len@len-Inspiron-N7010:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:45:2f:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)

len@len-Inspiron-N7010:~$

---

### Post by ugm6hr on 2010-11-06
I presume that ifconfig was run without an ethernet cable plugged in. If plugged, in at boot time, I would expect it to say something like:
```
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:45:2f:1d   
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0

```
As you have realized, the Restricted Driver is for wifi, not wired.
The reason it doesn't work when running from installed Ubuntu is either:
1. You still have a problem with wired (which I don't believe is true)
2. There is a bug (well known and irritating)

Check your ifconfig with a wired connection plugged in, and if it works:
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

If not, then post back exactly what happens when you do this, and also try:
```
ping -c 3 www.google.com
```
Also - compare the lshw / ifconfig's when using the Live CD with when using installed Ubuntu.

---

### Post by lookout4lpe on 2010-11-06
I have downloaded the Wireless driver with the Wired connection.  That allowed the wireless connection to be activated.  Now both work.  I have listed the outputs you asked for in the attached file, since they were long.

You may mark the post [Solved].  Thank you for your help.

I am now off to solve the Grub 2 issue.

---

