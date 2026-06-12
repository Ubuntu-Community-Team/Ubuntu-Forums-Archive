---
title: "Slow boot into desktop"
date: 2017-06-09
forum: Desktop Environments
---

### Post by bsmith52 on 2017-06-09
Recently, my Ubuntu 16.04 LTS distro started to boot slowly, I have a m5a97 MB, FX 6300 AMD processor, and 16gb RAM. I also have Windows 7, Slackware, Debian 8.4 (recently added). Here's the output from dmesg:

[HTML]
[    9.185201] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[    9.185263] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[    9.185322] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[    9.185378] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[    9.609108] asus_wmi: ASUS WMI generic driver loaded
[    9.651492] asus_wmi: Initialization: 0x0
[    9.651511] asus_wmi: BIOS WMI version: 0.9
[    9.651550] asus_wmi: SFUN value: 0x0
[    9.651807] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input12
[    9.651901] asus_wmi: Number of fans: 1
[   12.153321] Adding 8191996k swap on /dev/sdb4.  Priority:-1 extents:1 across:8191996k FS
[   17.849740] audit: type=1400 audit(1497034726.639:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/ubuntu-core-launcher" pid=850 co$
[   17.851285] audit: type=1400 audit(1497034726.643:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=852 comm$
[   17.851293] audit: type=1400 audit(1497034726.643:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namesp$
[   17.851346] audit: type=1400 audit(1497034726.643:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=847 comm="apparmor_pa$
[   17.851355] audit: type=1400 audit(1497034726.643:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.ac$
[   17.851361] audit: type=1400 audit(1497034726.643:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" p$
[   17.851366] audit: type=1400 audit(1497034726.643:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script"$
[   17.851625] audit: type=1400 audit(1497034726.643:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" p$
[   17.851634] audit: type=1400 audit(1497034726.643:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//$
[   17.852310] audit: type=1400 audit(1497034726.643:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=855 comm="apparm$
[   17.936197] usblp 4-1:1.0: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0D17
[   17.936221] usbcore: registered new interface driver usblp
[   97.803348] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   98.186969] r8169 0000:02:00.0 enp2s0: link down
[   98.186971] r8169 0000:02:00.0 enp2s0: link down
[   98.187030] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   98.356599] [drm:drm_edid_block_valid [drm]] *ERROR* EDID checksum is invalid, remainder is 161
[   98.356602] Raw EDID:
[   98.356603]          00 ff ff ff ff ff ff 00 22 f0 89 28 01 01 01 01
[   98.356605]          0e 14 01 03 68 2c 19 78 2e ee 95 a3 54 4f ff ff
[   98.356606]          ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   98.356607]          ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   98.356607]          ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   98.356608]          ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   98.356609]          ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   98.356610]          ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   99.843513] r8169 0000:02:00.0 enp2s0: link up
[   99.843523] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[  100.840020] usblp0: removed
[  100.856371] usblp 4-1:1.0: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0D17
[  103.760536] [drm:drm_edid_block_valid [drm]] *ERROR* EDID checksum is invalid, remainder is 96
[  103.760538] Raw EDID:
[  103.760540]          00 ff ff ff ff ff ff 00 22 f0 89 28 01 01 01 01
[  103.760542]          0e 14 01 03 68 2c 19 78 2e ee 95 a3 54 4c 99 27
[/HTML]

I have successfully disabled ipv6, with no change.

I am retired, and been making changes to my computer systems. Recently, I loaded Vmware ESXi on another computer and used Firefox on Ubuntu to access a Centos session on the ESXi computer. Beyond the Debian install, I can't think of anything else that would have caused the problem. 

I am still a beginner on linux - so don't assume I did the customary things (though I have updated the software recently).

Thanks in advance for your help.

---

### Post by bsmith52 on 2017-06-10
I have been doing some checking around the Internet. It appears that the error seen at 98.356599 and 103.760536 can be caused by video card conflicts with X Windows (internal clock timings). Note that the remainder changes from 161 to 96. A flaky video card? This 10 year old Radeon 2400 video card has been abused - subjected to extreme hot and cold. I suspected the card might be on its last legs, so I ordered a new one a week ago from Newegg. It is scheduled for delivery today. I will replace and let you know if that fixes the issue.

Thanks to all who looked!

Best regards,
Bill

---

### Post by bsmith52 on 2017-06-10
Back again after installing my new video card. The good news is that I got rid of the errors. So my video card was in fact going bad. The bad news is that I am still getting 100 second boot times that should be less than 20:

```

[    9.226292] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
[    9.226369] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
[   10.166186] Adding 8191996k swap on /dev/sdb4.  Priority:-1 extents:1 across:8191996k FS
[   16.016643] audit: type=1400 audit(1497144305.903:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/ubuntu-core-launcher" pid=776 co$
[   16.017915] audit: type=1400 audit(1497144305.907:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=781 comm="app$
[   16.017972] audit: type=1400 audit(1497144305.907:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=778 comm$
[   16.017980] audit: type=1400 audit(1497144305.907:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namesp$
[   16.018206] audit: type=1400 audit(1497144305.907:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=773 comm="apparmor_pa$
[   16.018213] audit: type=1400 audit(1497144305.907:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.ac$
[   16.018218] audit: type=1400 audit(1497144305.907:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" p$
[   16.018223] audit: type=1400 audit(1497144305.907:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script"$
[   16.018653] audit: type=1400 audit(1497144305.907:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" $
[   16.018663] audit: type=1400 audit(1497144305.907:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//$
[   16.260633] r8169 0000:02:00.0 enp2s0: link down
[   16.260634] r8169 0000:02:00.0 enp2s0: link down
[   18.193798] r8169 0000:02:00.0 enp2s0: link up
[   19.225752] usb 4-2: new full-speed USB device number 3 using ohci-pci
[   19.394900] usb 4-2: New USB device found, idVendor=03f0, idProduct=0d17
[   19.394907] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   19.394912] usb 4-2: Product: hp LaserJet 1012
[   19.394916] usb 4-2: Manufacturer: Hewlett-Packard
[   19.394919] usb 4-2: SerialNumber: 00CNFB908388
[   20.002862] usblp 4-2:1.0: usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0D17
[   20.002885] usbcore: registered new interface driver usblp
[  100.581455] usblp0: removed
[  100.597932] usblp 4-2:1.0: usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0D17

```

I haven't kept up with what is going on in Ubuntu. But I am seeing some interesting things since I set up my other PC as a server with Vmware ESXi. (BTW, I know next to nothing about networking, but I found out that my server was set up with a static IP address of 192.168.1.100.)

```

bill@liamli:~$ ifconfig
enp2s0    Link encap:Ethernet  HWaddr 60:a4:4c:56:cc:c8  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:358866 (358.8 KB)  TX bytes:190852 (190.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:11940 (11.9 KB)  TX bytes:11940 (11.9 KB)

```

What is this enp2s0? What happened to eth0? 

In any case, I still need to do some more work. Anyone who has any insights, please let me know.

Thanks for all your help.
Best regards,
Bill

---

### Post by him610 on 2017-06-11
hello bsmith52,

Can't promise I can help; however, tell us more about your system.
```
inxi -b
```

```
systemd-analyze blame
```

---

### Post by bsmith52 on 2017-06-11
Thanks him610! I like that utility.

Unfortunately, I did not get to try it before I was able to figure it out. Once I cleared up some of the other issues, I went for a more detailed look at my boot process in /var/log/syslog. This led me to the following post:

[https://askubuntu.com/questions/711016/slow-boot-a-start-job-is-running-for-dev-disk-by](https://askubuntu.com/questions/711016/slow-boot-a-start-job-is-running-for-dev-disk-by)

I had the feeling this would work. I suspected that the vmware had something to do with my problem. The above post directly addresses that error.

I followed the instructions - that is:
1. Booted my system in gPartd
2. Deleted my swap partition
3. Recreated it (this gave it a new UUID)
4. Rebooted my system
5. Ran "sudo blkid" to get new UUID
6. Edited /etc/fstab and reaplaced the swap UUID with the new one
7. Rebooted, and... see for yourself:

```

[   15.669003] Adding 8191996k swap on /dev/sdb4.  Priority:-1 extents:1 across:8191996k FS
[   21.781906] audit: type=1400 audit(1497222871.563:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/ubuntu-core-launcher" pid=831 co$
[   21.783436] audit: type=1400 audit(1497222871.567:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=833 comm$
[   21.783444] audit: type=1400 audit(1497222871.567:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namesp$
[   21.783521] audit: type=1400 audit(1497222871.567:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=834 comm="app$
[   21.783593] audit: type=1400 audit(1497222871.567:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=828 comm="apparmor_pa$
[   21.783603] audit: type=1400 audit(1497222871.567:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.ac$
[   21.783609] audit: type=1400 audit(1497222871.567:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" p$
[   21.783615] audit: type=1400 audit(1497222871.567:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script"$
[   21.784473] audit: type=1400 audit(1497222871.567:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" $
[   21.784480] audit: type=1400 audit(1497222871.567:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//$
[   22.165368] r8169 0000:02:00.0 enp2s0: link down
[   22.165385] r8169 0000:02:00.0 enp2s0: link down
[   22.342585] usblp 4-2:1.0: usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0D17
[   22.342604] usbcore: registered new interface driver usblp
[   23.951590] r8169 0000:02:00.0 enp2s0: link up
[   27.916257] usblp0: removed
[   27.932887] usblp 4-2:1.0: usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0D17
[   33.444039] UDF-fs: warning (device sdc1): udf_load_vrs: No anchor found
[   33.444042] UDF-fs: Rescanning with blocksize 2048
[   33.465163] UDF-fs: warning (device sdc1): udf_load_vrs: No anchor found
[   33.465166] UDF-fs: Rescanning with blocksize 2048
[   33.472412] UDF-fs: INFO Mounting volume 'GParted-live', timestamp 2016/10/20 00:47 (1000)
[   33.529004] ISO 9660 Extensions: Microsoft Joliet Level 3
[   33.530097] ISOFS: changing to secondary root

```

Boot time now reduced from 100 seconds to 33 seconds!

So... the moral of the story is... if the output of dmesg doesn't give you the information to fix your problem, look elsewhere (in this case /var/log/syslog).

Thanks again to all who looked at my post. And him610 for your utility.

Best regards to all,
Bill

---

