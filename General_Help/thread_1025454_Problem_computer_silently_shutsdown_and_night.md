---
title: "Problem: computer silently shutsdown and night"
date: 2008-12-30
forum: General Help
---

### Post by Spikius on 2008-12-30
Firstly i would like to apologize for my ENG and for something you might not understand :)

Secondly - straight to the whole point of thread:

Whis is happening to me from 8.04 version of ubuntu and i dont know where to look for and answer. My PC works like 24/7 and i have apache2 server and torrent program running, so 6-7 hours when i sleep and in which PC stops its not in my interest.

Ok this is how it works: whis .. thing.. is happening **ONLY** and night, and **ALWAYS** at 4.30 - 5 AM. When i wake up, i click monitor button to turn it on, i move my mouse to clear it from screensaver, and system time is setted to like 4.35AM, or 4.51AM or 4.45AM.. XChat disconnets with reason ** Disconnected (Invalid argument).* All network activity is lost and obviously its resuming to its normal state. PC actualy newer loses its power, its not loging me of, its not actualy shuting itself down, i just dont know what happens :)

So, what i already did:
* Disabled screensaver > maybe he does something > tests proved that its not it becouse at day i can leave pc for an hour or for a whole day, with screensaver active, no such problem as at night.
* Power management > put computer to sleep is setted to "never", iv disabled power management from my startup and even sessions.. Wanna guess is there a problem? :) yup...
So after a while somebody told be to look in system log.. And either im blind (well i wear glases but not im not that bad :() or there is nothing to do with that.:

PC crashed to 4.47 AM this time...

[QUOTE=Kernel last few lines before crash]Dec 30 04:30:01 b33r CRON[20158]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 30 04:30:02 b33r CRON[20158]: pam_unix(cron:session): session closed for user root
Dec 30 04:35:02 b33r CRON[20771]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 30 04:35:03 b33r CRON[20771]: pam_unix(cron:session): session closed for user root
Dec 30 04:39:02 b33r CRON[21259]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 30 04:39:03 b33r CRON[21259]: pam_unix(cron:session): session closed for user root
Dec 30 04:40:01 b33r CRON[21430]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 30 04:40:01 b33r CRON[21430]: pam_unix(cron:session): session closed for user root
Dec 30 04:45:01 b33r CRON[21962]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 30 04:45:02 b33r CRON[21962]: pam_unix(cron:session): session closed for user root[/QUOTE]

I think network is actualy something to do with this.
[QUOTE=daemon log]
Dec 30 01:25:21 b33r dhclient: DHCPREQUEST of 88.223.*.* on eth0 to 88.223.*.* port 67
Dec 30 01:25:21 b33r dhclient: DHCPACK of 88.223.*.* from 88.223.*.*
Dec 30 01:25:21 b33r dhclient: bound to 88.223.*.* -- renewal in 20975 seconds.
Dec 30 04:37:07 b33r NetworkManager: <info>  Sleeping... 
Dec 30 04:37:07 b33r NetworkManager: <info>  (eth0): now unmanaged 
Dec 30 04:37:07 b33r NetworkManager: <info>  (eth0): device state change: 8 -> 1 
Dec 30 04:37:07 b33r NetworkManager: <info>  (eth0): deactivating device (reason: 37). 
Dec 30 04:37:08 b33r NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 5097 
Dec 30 04:37:08 b33r NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
Dec 30 04:37:08 b33r NetworkManager: <info>  (eth0): cleaning up... 
Dec 30 04:37:08 b33r NetworkManager: <info>  (eth0): taking down device. 
Dec 30 04:37:08 b33r NetworkManager: <info>  (eth0): carrier now OFF (device state 1) 
Dec 30 04:37:09 b33r avahi-daemon[4543]: Withdrawing address record for 88.223.*.* on eth0.
Dec 30 04:37:09 b33r avahi-daemon[4543]: Leaving mDNS multicast group on interface eth0.IPv4 with address 88.223.*.*.
Dec 30 04:37:09 b33r avahi-daemon[4543]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 30 04:37:09 b33r avahi-daemon[4543]: Withdrawing address record for fe80::213:46ff:feeb:428c on eth0.
Dec 30 04:37:11 b33r NetworkManager: <info>  Waking up... 
Dec 30 04:37:11 b33r NetworkManager: <info>  (eth0): now managed 
Dec 30 04:37:11 b33r NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Dec 30 04:37:11 b33r NetworkManager: <info>  (eth0): bringing up device. 
Dec 30 04:37:11 b33r NetworkManager: <info>  (eth0): preparing device. 
Dec 30 04:37:11 b33r NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Dec 30 04:37:11 b33r NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Dec 30 04:37:11 b33r NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Dec 30 04:37:11 b33r NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 30 04:37:11 b33r NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 30 04:37:11 b33r NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Dec 30 04:37:11 b33r NetworkManager: <info>  dhclient started with pid 21074 
Dec 30 04:37:11 b33r NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 30 04:37:11 b33r dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 30 04:37:11 b33r dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 30 04:37:11 b33r dhclient: All rights reserved.
Dec 30 04:37:11 b33r dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Dec 30 04:37:11 b33r dhclient: 
Dec 30 04:37:11 b33r NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Dec 30 04:37:11 b33r dhclient: Listening on LPF/eth0/00:13:46:eb:42:8c
Dec 30 04:37:11 b33r dhclient: Sending on   LPF/eth0/00:13:46:eb:42:8c
Dec 30 04:37:11 b33r dhclient: Sending on   Socket/fallback
Dec 30 04:37:12 b33r dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec 30 04:37:12 b33r dhclient: DHCPOFFER of 88.223.*.* from 88.223.*.*
Dec 30 04:37:12 b33r dhclient: DHCPREQUEST of 88.223.*.* on eth0 to 255.255.255.255 port 67
Dec 30 04:37:12 b33r dhclient: DHCPACK of 88.223.*.* from 88.223.*.*
Dec 30 04:37:12 b33r NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Dec 30 04:37:12 b33r NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec 30 04:37:12 b33r NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Dec 30 04:37:12 b33r NetworkManager: <info>    address 88.223.*.*
Dec 30 04:37:12 b33r NetworkManager: <info>    prefix 21 (255.255.248.0) 
Dec 30 04:37:12 b33r NetworkManager: <info>    gateway 88.223.*.* 
Dec 30 04:37:12 b33r NetworkManager: <info>    hostname '88.223.*.*' 
Dec 30 04:37:12 b33r NetworkManager: <info>    nameserver '88.223.0.1' 
Dec 30 04:37:12 b33r NetworkManager: <info>    nameserver '88.222.0.1' 
Dec 30 04:37:12 b33r NetworkManager: <info>    domain name 'dokeda.lt' 
Dec 30 04:37:12 b33r NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec 30 04:37:12 b33r NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Dec 30 04:37:12 b33r NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Dec 30 04:37:12 b33r avahi-daemon[4543]: Joining mDNS multicast group on interface eth0.IPv4 with address 88.223.*.*.
Dec 30 04:37:12 b33r avahi-daemon[4543]: New relevant interface eth0.IPv4 for mDNS.
Dec 30 04:37:12 b33r avahi-daemon[4543]: Registering new address record for 88.223.*.* on eth0.IPv4.
Dec 30 04:37:12 b33r dhclient: bound to 88.223.*.* -- renewal in 21465 seconds.
Dec 30 04:37:12 b33r avahi-daemon[4543]: Registering new address record for fe80::213:46ff:feeb:428c on eth0.*.
Dec 30 04:37:13 b33r NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Dec 30 04:37:13 b33r NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Dec 30 04:37:13 b33r NetworkManager: <info>  Activation (eth0) successful, device activated. 
Dec 30 04:37:13 b33r NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec 30 04:37:49 b33r ntpdate[21142]: step time server 91.189.94.4 offset 28.891191 sec[/QUOTE]

Other logs just show up that ufw is working...
> Dec 30 04:45:18 b33r kernel: [108099.138188] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:13:46:eb:42:8c:00:15:17:63:03:75:08:00 SRC=193.46.*.* DST=88.223.*.* LEN=60 TOS=0x00 PREC=0x00 TTL=59 ID=32399 DF PROTO=TCP SPT=45271 DPT=8080 WINDOW=5840 RES=0x00 SYN URGP=0


So if anyone know where i should look for and answer - pls tell me :)
For that ill send you the best beer pic ill find on internet :D

---

### Post by cmnorton on 2008-12-30
This may have nothing to do with your problem, but might be worth trying:

Look to see if any crontabs exist other than /etc/crontab

sudo ls -l /var/spool/cron/crontabs

If such crontabs exist, look into them.

I don't use XChat. What are its configuration possibilities? You don't need to post those here. I am just wondering if there is some XChat configuration parameter that might cause your problem to occur.

Can you shut off XChat for one night to see if this problem still occurs?

---

### Post by redilyn on 2008-12-30
```
Dec 30 04:37:07 b33r NetworkManager: <info> Sleeping... 
```

Your nic seems to be going to sleep, or network manager...

You don't have any power managment setup in your BIOS do you??

---

### Post by Spikius on 2008-12-30
> **redilyn said:**
> ```
Dec 30 04:37:07 b33r NetworkManager: <info> Sleeping... 
```

Your nic seems to be going to sleep, or network manager...

You don't have any power managment setup in your BIOS do you??

none that i know of.. my pc is prety old and there is no fancy power saving stuff in bios...

where can i setup that my network woundt go to sleep :)

orany workaround? like wakup call? :D

> **cmnorton said:**
> This may have nothing to do with your problem, but might be worth trying:

Look to see if any crontabs exist other than /etc/crontab

sudo ls -l /var/spool/cron/crontabs

If such crontabs exist, look into them.

I don't use XChat. What are its configuration possibilities? You don't need to post those here. I am just wondering if there is some XChat configuration parameter that might cause your problem to occur.

Can you shut off XChat for one night to see if this problem still occurs?

problem is not with xchat, that argument error just shows that network just stopped. like ping timeout error.

spike@b33r:~$ sudo ls -l /var/spool/cron/crontabs/
total 0

---

### Post by redilyn on 2008-12-30
I notice you say the system time is set at 4:XXam every morning.

If you don't mind me asking, what time of day do you get up? 

Seems the clock is frozen? is that correct? 
Does it reset to the correct time after you wake the computer?

You mention this is an old system. Have you checked to make sure the CMOS battery isn't getting weak?

You can usually check that in the BIOS. 
If not, you might want to put a new battery in if it hasn't been changed in the last 3-5 years.

---

### Post by Spikius on 2008-12-30
> **redilyn said:**
> I notice you say the system time is set at 4:XXam every morning.

If you don't mind me asking, what time of day do you get up? 

Seems the clock is frozen? is that correct? 
Does it reset to the correct time after you wake the computer?

You mention this is an old system. Have you checked to make sure the CMOS battery isn't getting weak?

You can usually check that in the BIOS. 
If not, you might want to put a new battery in if it hasn't been changed in the last 3-5 years.
usualy i go to sleep ~1 AM and wake up in 9-10 AM :)
Yes the clock freezes and so all the network connections and so on. Its like that it would sends it self into sleep or suspend mode, dont know how to call this, (well windows users must know this funcion)
and no, clock doest correct itself. I must reset time every morning.
Well old system.. Its now that old you know :D its a ~5years old PC and i have no problems with CMOS remembering its settings so i guess batery is kinda ok.

---

### Post by redilyn on 2008-12-30
Maybe this will help
[http://ubuntuforums.org/showthread.php?t=788276](http://ubuntuforums.org/showthread.php?t=788276)

Problem:
```

Despite the fact that I have disabled all the power management in the GUI, my new install of Hardy insists on entering suspend after 8 hours idle.

```

Solution:
```

Well after a few weeks of tinkering I was able to figure this out.

Here were the steps I followed to 100% disable all power management.

1. Installed Boot Up Manager

sudo apt-get install bum

2. De-select the following services

    * powernowd
    * apmd
    * acpi-support
    * acpid

3. Disable Gnome-Power-Manager from starting up when you boot into gnome.

System->Preferences->Sessions

Hope that helps anyone else who might be trying to trouble-shoot this.


```

---

### Post by Spikius on 2008-12-30
Problem with step 3:
There is NO Gnome-Power-Manager in my session startup :)

There is Gnome:
* Keyring daemon
* Login sound
* Settings Daemon
* settings daemon helper


edit: actualy, in bum there is no  
    * powernowd
    * apmd
    * acpid

---

### Post by redilyn on 2008-12-30
So you did find acpi-support with BUM?

I suppose you could try passing the acpi=off argument in grub although I don't know if it will help.

```

sudo gedit /boot/grub/menu.lst

```

Look for your kernel entry and add acpi=off
```

/vmlinuz-2.6.27-9-generic root=UUID=b3e79875-0842-45ee-9936-2f0bf4f3fae3 ro quiet splash [COLOR="Red"]acpi=off[/COLOR]

```

If that doesn't work, the only thing I can think of is to leave a terminal open which pings google.com all night :)

---

