---
title: "Wireless networking not working on Dell XPS m1530"
date: 2008-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Perfect_Insanity on 2008-08-31
I recently decided to dual boot Ubuntu alongside Vista which came installed on my laptop. Installation went fine and everything appears to be working as it should do except the built in wireless shows no sign of life. I am new to Ubuntu but I installed 8.04.1, and all the available updates using a cable to connect to the internet hoping this might fix the problem but to no avail. 

I have read about other people who have had the same problem and they suggested adding noapic when booting Ubuntu and disabling the wi-fi catcher in the bios but neither have even shown signs of solving the problem. I tried upgrading the bios version from A07 to A08 but this messed up my touchpad and didn't solve the wireless problem so i switched back to A07. As a last resort i tried installing windows wireless drivers, and adding the windows driver for my card which was apparently recognised but after rebooting still no luck. I really don't know what else i can try to solve this problem so any help would be appreciated.

Thanks in advance

---

### Post by laurence91 on 2008-09-03
Hi, the wireless adapter should have worked out of the box so to speak, i have the intel PRO/Wireless 3945ABG adpater on the m1530 with a visa/kubuntu dual boot.

What i have noticed is the wireless doesnt start and $iwlist doesnt show the network adapter, what i would suggest is you go into the terminal and 

$ sudo lshw -class network

this should give you a readout of your network adapters, if you can see your wireless adapter then it should also give you your driver details. (mine being iwl3945)

$ sudo modprobe -r iwl3945
$ sudo modprobe -a iwl3945

then restart

this works the all the time for me, $iwlist should then show you any routers available but i would suggest using the GUI ie Knetworkmanager in my case.

On a second note i posted about this some time ago and it was suggested to upgrade to the m1730 drivers which are 6months newer than the current m1530 by dell.

[http://ubuntuforums.org/showthread.php?t=903411](http://ubuntuforums.org/showthread.php?t=903411)

Cheers
Laurence

---

### Post by solaceinsilence9 on 2008-09-03
what kind of Dell do you have? This is a common problem for Dells. The manufacturers of our NIC (well, integrated nic atleast) dont offer a linux driver. depending on your type of dell and who makes your NIC id say more than likely youll have to use NDISwrapper to get your wifi going.

---

### Post by jasonkirk2006 on 2008-09-04
Welcome to Dell-victims group.

I own the same kind of notebook. I don't know what makes this one different but, it doesn't work in linux. I'm desperately seeking a solution for weeks but no luck!

Here are the methods used without success:

- Disabling WiFi Catcher from BIOS
- Removing and modprobing the iwl3945 module
- Doing the same thing with disable_hw_scan=1
- Booting with ubuntu 7.10 live CD (which uses ipw3945)

Besides, Vista works perfectly.

May be we should gather and press Dell for an answer :(

NOTE: For touchpad issue, there is a net solution. Just use i8042.nomux=1 kernel option. Search the forum, if you don't know how to add it.

---

### Post by jespdj on 2008-09-04
Whether it works or not depends on which wireless card you have in your laptop.

The Intel 3945 or 4965 WiFi adapters work out of the box and without any problems with Linux. I have an Intel 4965 in my M1530 and it works without any problems.

The "Dell brand" WiFi card is another story. That card uses a Broadcom chipset, and that's a manufacturer who is notorious for not providing Linux drivers or enough information so that someone can make a driver that works well.

Don't order a "Dell brand" WiFi card if you order a laptop from Dell.

---

### Post by jasonkirk2006 on 2008-09-05
> The Intel 3945 or 4965 WiFi adapters work out of the box and without any problems with Linux

I wouldn't say it without making a search about 3945 in the forum. I have a **Dell XPS M1530** with **Intel PRO/Wireless 3945ABG minicard** it does not work out-of-the-box in Linux! It's not Dell Wireless, it's Intel and it does not work.

Besides all harware related possibilities such as a malfunctioning chip or a contact issue, Windows Vista runs it very well. So i'm not sure if it is a driver problem or a linux kernel problem (dmesg error logs change when kernel version changes).

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
lshw -C network
```

---

### Post by esanchez on 2008-09-08
same problem here...
my m1530 used to work with the noacpi fix, however, that stopped working after the last updates.

here is my output:

 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d5:7a:39
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:a1:99:d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

best regards,
 -eduardo s.m.

---

### Post by accesshater on 2008-09-08
i have the same notebook, and it works just fine. i didnt have to do anything to make it work. (Only wpa-enterprise doesnt work for me)

And there is a new version of the bios (A09).

---

### Post by esanchez on 2008-09-08
got that Bios version, it came out of the box with it, but seems to have this weird problem...I'm using 64bit version of Hardy Heron.

Which version are you using? 

Best regards,
  -eduardo s.m.

---

### Post by esanchez on 2008-09-08
ufff...!
today I installed wicd[1], didn't liked it, I reinstall again the network manager, and the wireless is working again.

There's no technical explanation for this :(
Anyway, I'm still using the noacpi option in my menu.lst file.


[1]wicd.sourceforge.net

---

### Post by accesshater on 2008-09-09
> **esanchez said:**
> got that Bios version, it came out of the box with it, but seems to have this weird problem...I'm using 64bit version of Hardy Heron.

Which version are you using? 

Best regards,
  -eduardo s.m.

I am using the 32-bit version... do you think that that is the reason for the problem?

---

### Post by jasonkirk2006 on 2008-09-10
Doesn't matter. I installed both 32-bit and 64-bit versions of Hardy -  same problems in both. Plus, i tried other distros, tried kde and gnome and different kernel versions. Always the same.

---

### Post by dturvene on 2008-12-03
Hi -

I bought an M1530 (BIOS A08) with Intel 3945 wireless from Dell, pre-loaded with Ubuntu 8.04, about a month ago.  Everything worked great until today when I encountered a similar problem: while working, I lost the wireless signal and the wifi light went out.  I tried a number of recommendations from this site (e.g. BIOS disable "Wifi Catcher") without success.

I toggled the wifi button side of the laptop and the wireless light went back on.  I had to reboot (probably could have restarted NetworkManager or the network service) to recover the IP link.  After carrying this thing around for a month I doubt I could have hit the wireless switch while working at a desk.

Anyways, it's worth checking before booting up with "apic", or updating a driver, or replacing the wifi minicard.

And stay away from Dell wifi cards.  They use broadcom parts, which have NDA specs and thus cannot be open sourced.  Some people have tried to reverse engineer but I haven't had too much success; ndiswrapper still seems to be the best.

---

### Post by ussndmac on 2008-12-03
I have a 1530 with 3945.

I have a Linksys WAP that is older and only does 802.11b.

When I got the laptop from Dell with Ubuntu 8.0.4 loaded it would connect to the Linksys with wep key.

I have since reinstalled hardy, intrepid, and ubuntu studio (8.0.4) and have not been able to connect to the Linksys. (eith or without security)

I currently believe the drivers that get loaded can't handle 11b only connections and that Dell had done something (possible a backport) to get it to work.

Since it sees the wap and the wap log shows the laptop trying to connect, I'm guessing it's a driver issue.

Happy to be corrected if I'm wrong, I'd love to get it working.

---

### Post by dturvene on 2008-12-04
> **ussndmac said:**
> I have a 1530 with 3945.

I have a Linksys WAP that is older and only does 802.11b.

When I got the laptop from Dell with Ubuntu 8.0.4 loaded it would connect to the Linksys with wep key.

I have since reinstalled hardy, intrepid, and ubuntu studio (8.0.4) and have not been able to connect to the Linksys. (eith or without security)

I currently believe the drivers that get loaded can't handle 11b only connections and that Dell had done something (possible a backport) to get it to work.

Since it sees the wap and the wap log shows the laptop trying to connect, I'm guessing it's a driver issue.

Happy to be corrected if I'm wrong, I'd love to get it working.

For me, the 3945 802.11B/G h/w and driver work seemlessly with 802.11B and G access points.  Debugging ideas:

* Make sure the wireless is enable (the blue WiFi light is "on" on the laptop and should be aperiodically blinking.)

* Make sure the AP beacon is seen using "sudo iwlist wlan0 scan".  You do not need an SSID or encryption to see the beacon.

* Make sure you are using DHCP on wlan0

* Stop NetworkManager and use the command line to establish a wireless session. I haven't had to do this in years but try (as sudo):

iwconfig wlan0 essid <your essid>
iwconfig wlan0 key <your WEP key>
ifconfig wlan0 down
ifconfig wlan0 up

Use wireshark to monitor wlan0 traffic to see what's going out and coming in.  You should see ARP and DHCP discover packets being broadcast on the LAN and responses coming back.

HTH
Dave

---

### Post by Dano58 on 2008-12-17
Same hardware, similar problem. Dell 1530, Intel 3945, Ubuntu 8.04, Linksys WRT 54G would not connect or hold onto the WAP key.

This guy nailed it and solved the problem for me.

[http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04](http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04)

---

