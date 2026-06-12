---
title: "lost about ubuntu"
date: 2009-06-13
forum: General Help
---

### Post by Stronze on 2009-06-13
im new to linux and i was trying out fedora but a pal told me about ubuntu and its the best linux OS.

i dual installed onto my laptop with vista 32 bit.

1st problem im having.

when i try to save anything on HHD. (including a txt file pasted below)
it tells me im out of space and need to free up space.

no clue why.
this laptop has 2 110 gig HHD built in.
the second one is empty and the primary one is only 75% full.

the second problem im having

i tried to connect the wireless but everytime i enter the password,it changes it to some random long password when it fails to connect and i click show password.

the help files i was reading got me confused and lost.(which isnt hard to do)
this about all the info i could collect.

even this info has me lost.

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:3f:4a:d0
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:74:a6:eb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:55:40:40:99:94
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
stronze@stronze-laptop:~$ sudo iwconfig
[sudo] password for stronze: 
Sorry, try again.
[sudo] password for stronze: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by kevinlyfellow on 2009-06-13
First off, welcome to the forums.  Hopefully we can get things straightened out for you.

Onto the lack of space issue.  What you need to do is let us know how all your partitions are set up and how much memory is available.  Hit alt-f2 and run gnome-terminal.

In the terminal, type
```
df -h
```

And post it up here.

The networking can come later, that may be an issue with the inability to write to the disk.

Oh, and do feel free to try other distros.  Not every shares the same opinion on which is best.  That really is up for you to decide.

---

### Post by Stronze on 2009-06-13
stronze@stronze-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             2.3G  2.3G     0 100% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M   84K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  192K 1007M   1% /dev
tmpfs                1007M  484K 1006M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/mmcblk0p1        953M  112M  841M  12% /media/disk
/dev/sdc1             464G  233G  231G  51% /media/disk-1
/dev/sdc5             2.3G  2.2G   46M  98% /media/disk-2

---

### Post by kevinlyfellow on 2009-06-13
What it looks like to me is that your root directory was only given 2.3 gigabytes.  I get it from this line:

```
/dev/sdb2 2.3G 2.3G 0 100% /
```

2.3 gigs is a bit small for ubuntu.  But there some things that we can do to help the problem a little bit.  It seems like this not the only partition on your second harddrive, correct?  If so then maybe we can find more room on that disk.  

Basically this is what I'm thinking.  By default ubuntu mounts all of your directories on one partition on the harddrive.  But, we can choose to use different partitions for different directories.  This is extremely useful for the /home directory since it usually contains the bulk of the disk usage.  So, if we get another partition, we will be able to mount your home directory on that partition and you will be able to use the computer.

Alternatively, what you can do is find some extra space and just do a reinstall on a larger partition.

---

### Post by Stronze on 2009-06-13
let me repost cuz i noticed my external HDD and my lil mem stick pluged in.

so over all suggestion is reinstall and select a better partition?

am i able to remove all ubuntu and reinstall without damaging vista?

---

### Post by kevinlyfellow on 2009-06-13
Well, it's really up to you and also kinda depends on how your harddrives are set up.  If you abhor reinstallation, we can get it running properly without it.  But it will be more work, and perhaps time than a reinstallation. 

If you haven't done anything important on ubuntu yet and want to relatively seamless experience then my suggestion is to install ubuntu on a drive where you can have at least 6 gigs + room for all of the stuff you want to do on ubuntu (movies, videos...).  

If you have done something important that you would like to keep and also are interested in getting dirty right away, then find more space on your harddrive that you are will to use and we will go from there.

BTW, I'll be signing off soon, so you may need to hold your horses unless someone else joins the thread

---

### Post by Stronze on 2009-06-13
reinstall then cuz i got nothin on it.

ill work that out while i wait for someone else.

---

### Post by albinootje on 2009-06-13
> **Stronze said:**
> reinstall then cuz i got nothin on it.

ill work that out while i wait for someone else.

Depending on the amount of software that you're planning to install I recommend at least 5 Gb of space for / and a separate /home is nice to have.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Stronze on 2009-06-13
i reinstalled onto the 110 gig HDD that is empty.

came back on vista to get the commands for terminal.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             106G  3.3G   97G   4% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M   84K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  156K 1007M   1% /dev
tmpfs                1007M  516K 1006M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
that problem is fixed.
good thing i left it empty cuz vista can see it from computer folder.

now i need to get wifi working.
i enter the wap password and it fails to connect and comes back with a different password.
db22cb62664fb92438adda69956c295f59ea9d823e35f5094f5da51b17e76131

---

### Post by Stronze on 2009-06-13
how would i start in solving my wifi problem?

---

### Post by Stronze on 2009-06-14
i connected using my 360 ethernet cable and updated system but that did not solve the problem.

---

### Post by Stronze on 2009-06-14
i tried following the guide but some of it was over my head.
some of it is info i dont have cuz its not my router.

> [quote]stronze@stronze-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface> 
stronze@stronze-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.> stronze@stronze-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:6B:5F:81:D9
                    ESSID:"Kunkler"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=71/100  Signal level:-63 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 00074B756E6B6C6572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483931363035341054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180200F4000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000002432545ad
                    Extra: Last beacon: 1840ms ago
          Cell 02 - Address: 00:1C:10:92:D4:C2
                    ESSID:"StarGate_Command"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level:-33 dBm  Noise level=-93 dBm
                    Encryption key:on
                    IE: Unknown: 001053746172476174655F436F6D6D616E64
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000ad8bc6f18b
                    Extra: Last beacon: 16ms ago

pan0      Interface doesn't support scanning.> stronze@stronze-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:3f:4a:d0
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:74:a6:eb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:88:0a:eb:92:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes> stronze@stronze-laptop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlano inet dhcp
> stronze@stronze-laptop:~$ sudo ifdown -v lo inet
Configuring interface lo=lo (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
ifconfig lo down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
ifdown: interface inet not configured> stronze@stronze-laptop:~$ sudo ifdown -v lo inet
Configuring interface lo=lo (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
ifconfig lo down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
ifdown: interface inet not configured
stronze@stronze-laptop:~$ sudo ifup -v lo inet
Configuring interface lo=lo (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/dhclient3-apparmor
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
ifconfig lo 127.0.0.1 up
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant
Ignoring unknown interface inet=inet.
> [FONT=monospace]
[/FONT]stronze@stronze-laptop:~$ iwevent [FONT=monospace]
[/FONT]Waiting for Wireless Events from interfaces...
03:34:20.531623   wlan0    Scan request completed
03:34:20.531786   wlan0    Set Mode:Managed
03:34:20.531809   wlan0    Set Frequency:2.462 GHz (Channel 11)
03:34:20.542308   wlan0    Custom driver event:ASSOCINFO(ReqIE6e64010802040b160c12182432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIEdd090010180201f4000000)
03:34:20.561804   wlan0    New Access Point/Cell address:00:1C:10:92:D4:C2
03:34:24.566241   wlan0    New Access Point/Cell address:Not-Associated
03:34:25.572137   wlan0    Custom driver event:ASSOCINFO(ReqIE6e64010802040b160c12182432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIEdd090010180201f4000000)




[/quote]

---

### Post by albinootje on 2009-06-14
> **Stronze said:**
> i tried following the guide but some of it was over my head.

Which guide was that ? Please provide the link.

And did you copy & paste this ?
> 
stronze@stronze-laptop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlano inet dhcp

because there's wlano instead wlan0 on one line.
It might not matter much because Network Manager probably ignores it.

Did you try wicd ? [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by Stronze on 2009-06-14
i wish i could tell you what guide but i nodded off with my laptop next to me and woke up with prolly 1000 firefox help tabs

Ubuntu Jaunty - what is this?

---

### Post by Stronze on 2009-06-14
SUCCESS

thanks for the help.
no i just gotta get it like i want it.

---

### Post by kevinlyfellow on 2009-06-14
Glad to see everything works now!  Wireless can be a bit tricky on linux.  

Well, now you are on the fun part.  If you are interested in more themes try [http://www.gnome-look.org/](http://www.gnome-look.org/) and if you want to customize the special effects on your computer install compizconfig-settings-manager.

Have fun!

---

### Post by stoner_di on 2009-06-14
I want to ask someone tried to incorporate the bootup logo ( mini tux in the top left of the display to load the system).
Perform all necessary for this:
- when compiling the kernel, I select this:

Support for frame buffer devices FB->VESA VGA graphics support FB_VESA

Select all in the:

Console display driver support ->

selct all in the:

Bootup logo LOGO->

-in the GRUB, in the file menu.lst fix this row:

kernel /boot/vmlinuz-2.6.29.3 root=UUID=d5b52903-5…. video=vesafb vga=0×0323 ro quiet

-in the file /etc/modprobe.d/blacklist-framebuffer.conf, comment this row:

#blacklist vesafb

-in the file /etc/initramfs-tools/modules, add:

fbcon
vesafb

-in the end update initramfs this command:

update-initramfs -u

In all my UBUNTU not load boot logo!!!!!!!!

---

