---
title: "Networkmanager not auto connecting on reboot"
date: 2014-02-27
forum: Desktop Environments
---

### Post by mtweldon on 2014-02-27
Having issues with reboot and my computer not auto connecting through the network manager

here is what is in 

$ cat /etc/networkmanager/networkmanager.conf

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=my:m:a:c,
[ifupdown]
managed=True

$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

In the gui I have all the boxes checked for auto connecting and all users

---

### Post by varunendra on 2014-03-01
> **mtweldon said:**
> 
[ifupdown]
managed=**[COLOR="#FF0000"]True[/COLOR]**


Since your /etc/network/interfaces file contains only lo interface entry, this shouldn't matter, but by default the above value is "false" and it should be (unless you intentionally want both the interfaces file and NM control the same interface.

Even if you changed it to "true", I think it should be in all small letters, although I'm not sure if the case matters here.

Apart from that, you didn't mention the more important obvious details -

Is it a wired interface (Ethernet) or wireless?
Which version and flavour (Ubuntu/Kubuntu/Xubuntu/Lubuntu...) of Ubuntu?
Fresh install or an upgrade?
Any particular events after which it started happening?

Technical details are important, but human understandable background details are MORE important. :)

---

### Post by mtweldon on 2014-03-01
I'll change it to false and see if that makes a difference.

It is for a wired connection. New install Ubuntu 13.1 

Perhaps it started after I installed openvpn, but I can't say for sure, I've only rebooted once or twice for some package upgrades.

---

### Post by varunendra on 2014-03-01
There should be a key file with the same name as the connection's name in /etc/NetworkManager/system-connections/ directory. Posting its contents, along with some others, may also give us some clue. These files can be read/write only by root, so you'll need root access to read its contents. Command for doing that, and others whose output may help -
```
sudo cat /etc/NetworkManager/system-connections/*<the key file>*
ifconfig -a
nm-tool
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
sudo lshw -numeric -C network
```

---

### Post by mtweldon on 2014-03-01
$ sudo cat /etc/NetworkManager/system-connections/Ethernet\ connection\ 1 
[802-3-ethernet]
duplex=full
mac-address=7:xx:xx

[connection]
id=Ethernet connection 1
uuid=xx
type=802-3-ethernet
timestamp=1393540412
secondaries=68a425c4-0468-42f4-ae32-f17093e6dd75;

[ipv6]
method=ignore

[ipv4]
method=auto
may-fail=false

|||

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr xx:xx  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fe5b:5191/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46355062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27178985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50770889898 (50.7 GB)  TX bytes:6650207235 (6.6 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:597652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:597652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:289003657 (289.0 MB)  TX bytes:289003657 (289.0 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.118.1.6  P-t-P:10.118.1.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:37813910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25129694 errors:0 dropped:9939 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:48317743518 (48.3 GB)  TX bytes:2918969847 (2.9 GB)


$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Ethernet connection 1] ----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           no
  HW Address:        xx:xx

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- VPN:  [vpn] -----------------------------------------------------
  State:             connected
  Default:           yes

  Message:

||

$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=xx:xx,
[ifupdown]
managed=false

$ cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

||


$ sudo lshw -numeric -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10EC:8168]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: xx:xx
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s

---

### Post by varunendra on 2014-03-01
Probably this is why it does not autoconnect -
> **mtweldon said:**
> 
$ nm-tool
....
- Device: eth0  [Ethernet connection 1] ----------------------------------------
  **Default:           [COLOR="#FF0000"]no[/COLOR]**
....

- VPN:  [vpn] -----------------------------------------------------
  State:             connected
  **Default:           [COLOR="#FF0000"]yes[/COLOR]**
This is probably a bug in Network Manager that it does not let us set which connection to use by default (or I don't know how). A possible, but not always acceptable, workaround may be to disable "Autoconnect" on the other connection which it picks up by default.

Another, almost always acceptable but less smart, workaround is to use the /etc/network/interfaces file instead of Network Manager to manage the interfaces. You can clearly mark a connection as "default" there.

Yet another trick that may or may not work is to click the "Routes" button in your VPN connections settings in Network Manager and tick the box that says "Use this connection only for resources on its network". If you are using DHCP, tick the other box too that says "Ignore automatically obtained routes". That will disable that interface's gateway, thus *should* make the other one default.

**PS:**
Please always use 'Code' tags for posting command outputs. It preserves its formatting and characters and makes it more readable. Please follow the "Using Code Tags" link in my signature below to see how.

---

### Post by mtweldon on 2014-03-11
Sorry for the delay, had a last minute work trip that took me away for a bit, just getting back to being able to work on this problem.. still having it. I changed the routes setting, no luck.

I get this on boot.
```
:~$ dmesg | grep eth0
[    1.311583] r8169 0000:06:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000187c000, 74:d4:35:5b:51:91, XID 0c900800 IRQ 74
[    1.311585] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   18.194322] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.446537] r8169 0000:06:00.0 eth0: link down
[   21.446583] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.446625] r8169 0000:06:00.0 eth0: link down
[   21.446788] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.970038] r8169 0000:06:00.0 eth0: link up
[   22.970046] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

```
- Device: eth0  [Ethernet connection 2] ----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- VPN:  [vpn] -----------------------------------------------------
  State:             connected
  Default:           no

  Message:

```

not sure what the issue is

/edit - after selecting ignore IPV6

```
[    1.312439] r8169 0000:06:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000187c000, 74:d4:35:5b:51:91, XID 0c900800 IRQ 74
[    1.312442] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   17.959194] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.411413] r8169 0000:06:00.0 eth0: link down
[   20.411469] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.411501] r8169 0000:06:00.0 eth0: link down
[   20.411738] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.964436] r8169 0000:06:00.0 eth0: link up
[   21.964443] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
****
```

Well, rebooted again, finally getting a little more..

Got an "internal error on network manager" 

Says I have a modified networkmanager.conf file I took a screenshot. Had an issue with the upload, will try again in a bit.

Is this a problem here with my no-auto-default listed below? If so, what should I change it to? 


cat /etc/NetworkManager/NetworkManager.conf
```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=myeth0machere,
[ifupdown]
managed=false
```

---

### Post by varunendra on 2014-03-11
> **mtweldon said:**
> Is this a problem here with my no-auto-default listed below? If so, what should I change it to? 

cat /etc/NetworkManager/NetworkManager.conf
```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=myeth0machere,
[ifupdown]
managed=false
```

From "man NetworkManager.conf" -
>        **no-auto-default=**<hwaddr>,<hwaddr>,... | *
              Set devices for which NetworkManager shouldn't create default wired connection (Auto eth0). NetworkManager creates  a  default
              wired  connection  for any wired device that is managed and doesn't have a connection configured. List a device in this option
              to inhibit creating the default connection for the device.
              When the default wired connection is deleted or saved to a new persistent connection by a plugin, the MAC address of the wired
              device  is  automatically  added  to  this list to prevent creating the default connection for that device again.  Devices are
              specified by their MAC addresses, in lowercase. Multiple entries are separated by commas. You can use  the  glob  character  *
              instead of listing addresses to specify all devices.
              Examples:
              no-auto-default=00:22:68:5c:5d:c4,00:1e:65:ff:aa:ee
              no-auto-default=*
So I think it is normal if you have saved a custom profile for eth0. The messages "..not ready, ... link up" etc. in dmesg look normal too.

Maybe delete the current connection profile(s) (Ethernet connection 1,2), and create a New one with static IP assignment (set 'Method' to "Manual"). This should make the establishment of connection faster and more reliable. Make sure the IP you assign does not fall within the DHCP range of the router, else a IP conflict may occur.

---

### Post by mtweldon on 2014-03-12
Deleted all other connections and made a new manual connection with a manually assigned IP. No luck with that. Makes the connection just fine if I manually click up on the network manager and then select the connection, but on reboot it does nothing but say it's disconnected.

I just noticed this in the logs after rebooting.

```
Mar 12 06:50:59 server avahi-daemon[907]: Joining mDNS multicast group on interface eth0.IPv6 with address mac.
Mar 12 06:50:59 server avahi-daemon[907]: New relevant interface eth0.IPv6 for mDNS.
Mar 12 06:50:59 server avahi-daemon[907]: Registering new address record for mac on eth0.*.
Mar 12 06:51:02 server NetworkManager[1196]: <info> Auto-activating connection 'Ethernet connection 1'.
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) starting connection 'Ethernet connection 1'
Mar 12 06:51:02 server NetworkManager[1196]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 12 06:51:02 server NetworkManager[1196]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 12 06:51:02 server NetworkManager[1196]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Mar 12 06:51:02 server avahi-daemon[907]: Withdrawing address record for mac on eth0.
Mar 12 06:51:02 server avahi-daemon[907]: Leaving mDNS multicast group on interface eth0.IPv6 with address mac.
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 12 06:51:02 server avahi-daemon[907]: Interface eth0.IPv6 no longer relevant for mDNS.
Mar 12 06:51:02 server NetworkManager[1196]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Mar 12 06:51:02 server avahi-daemon[907]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.8.
Mar 12 06:51:02 server avahi-daemon[907]: New relevant interface eth0.IPv4 for mDNS.
Mar 12 06:51:02 server avahi-daemon[907]: Registering new address record for 192.168.1.8 on eth0.IPv4.
Mar 12 06:51:03 server NetworkManager[1196]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Mar 12 06:51:03 server NetworkManager[1196]: <info> Policy set 'Ethernet connection 1' (eth0) as default for IPv4 routing and DNS.
Mar 12 06:51:03 server NetworkManager[1196]: <info> Writing DNS information to /sbin/resolvconf
Mar 12 06:51:03 server dnsmasq[1601]: setting upstream servers from DBus
Mar 12 06:51:03 server postfix/master[2282]: reload -- version 2.10.2, configuration /etc/postfix
Mar 12 06:51:03 server NetworkManager[1196]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Mar 12 06:51:03 server NetworkManager[1196]: <error> [1394621463.455756] [nm-vpn-connection.c:1374] get_secrets_cb(): Failed to request VPN secrets #2: (6) No agents were available for this request.
Mar 12 06:51:03 server NetworkManager[1196]: <info> Policy set 'Ethernet connection 1' (eth0) as default for IPv4 routing and DNS.
Mar 12 06:51:03 server NetworkManager[1196]: <info> (eth0): device state change: secondaries -> failed (reason 'secondary-connection-failed') [90 120 54]
Mar 12 06:51:03 server NetworkManager[1196]: <info> Marking connection 'Ethernet connection 1' invalid.
Mar 12 06:51:03 server NetworkManager[1196]: <warn> Activation (eth0) failed for connection 'Ethernet connection 1'
Mar 12 06:51:03 server NetworkManager[1196]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 12 06:51:03 server NetworkManager[1196]: <info> (eth0): deactivating device (reason 'none') [0]
Mar 12 06:51:03 server avahi-daemon[907]: Withdrawing address record for 192.168.1.8 on eth0.
Mar 12 06:51:03 server avahi-daemon[907]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.8.
Mar 12 06:51:03 server avahi-daemon[907]: Interface eth0.IPv4 no longer relevant for mDNS
Mar 12 06:51:03 server NetworkManager[1196]: <warn> DNS: plugin dnsmasq update failed
Mar 12 06:51:03 server NetworkManager[1196]: <info> Removing DNS information from /sbin/resolvconf
Mar 12 06:51:03 server dnsmasq[1601]: setting upstream servers from DBus
Mar 12 06:51:03 server postfix/master[2282]: reload -- version 2.10.2, configuration /etc/postfix
Mar 12 06:51:04 server avahi-daemon[907]: Joining mDNS multicast group on interface eth0.IPv6 with address mac.
Mar 12 06:51:04 server avahi-daemon[907]: New relevant interface eth0.IPv6 for mDNS.
Mar 12 06:51:04 server avahi-daemon[907]: Registering new address record for mac on eth0.*.
Mar 12 06:51:08 server NetworkManager[1196]: <info> VPN service 'openvpn' disappeared
Mar 12 06:51:12  dbus[775]: last message repeated 3 times.
```

Is it failing because for some reason it can't obtain the VPN password? Don't know why it's saying can't get secrets because if I manually click connect it works just fine and connects to the VPN

---

### Post by varunendra on 2014-03-12
I've no idea about how VPN works or how NM works with VPN, so can't say much about what is happening and why.

However, doing a search for this error message -
```
Failed to request VPN secrets #2: (6) No agents were available for this request.
```
I hit the archlinux [wiki page]("https://wiki.archlinux.org/index.php/NetworkManager#VPN_not_working_in_Gnome"), which says -
> This is caused by the Gnome NM Applet expecting dialog scripts to be at /usr/lib/gnome-shell, when NetworkManager's packages put them in /usr/lib/networkmanager. As a "temporary" fix (this bug has been around for a while now), make the following symlink(s):
```
# For OpenConnect
ln -s /usr/lib/networkmanager/nm-openconnect-auth-dialog /usr/lib/gnome-shell/
```
```
# For VPNC (i.e. Cisco VPN)
ln -s /usr/lib/networkmanager/nm-vpnc-auth-dialog /usr/lib/gnome-shell/
```
This may need to be done for any other NM VPN plugins as well, but these are the two most common.
Not sure if this is indeed the problem, but seems to be worth checking/trying.

Previous to the above section, there is another section on the same page about setting up VPN to autoconnect. After reading that, it seems you need to do some extra work. Please take a look : [https://wiki.archlinux.org/index.php/NetworkManager#Use_dispatcher_to_connect_to_a_VPN_after_a_network-connection_is_established](https://wiki.archlinux.org/index.php/NetworkManager#Use_dispatcher_to_connect_to_a_VPN_after_a_network-connection_is_established)

---

### Post by mtweldon on 2014-03-12
Hmm I don't have gnome-shell as an option in my folders

```
gnome-bluetooth/           gnome-settings-daemon/
gnome-contacts/            gnome-settings-daemon-3.0/
gnome-keyring/             gnome-system-monitor/
gnome-screensaver/         gnome-user-share/
gnome-session/             gnome-vfs-2.0/
~~@server:/usr/lib$ cd gnome- (double tab to show all available results)

```

investigating the other page for VPN

---

### Post by mtweldon on 2014-03-12
Varun,

You are awesome, thanks so much for the link to the wiki.  I had no luck with the /usr/lib/gnome-shell solution but the following resolved absolutely everything:

```

 /etc/NetworkManager/system-connections/name of your VPN connection and change the password-flags and secret-flags from 1 to 0.
Alternatively put the password directly in the configuration file adding the section vpn-secrets: 

[vpn]
 ....
 password-flags=0
 
 [vpn-secrets]
 password=your_password
```

On reboot I now auto connect to eth0 and connect to my VPN automatically. Looks like the vpn-secrets failure was causing my network connection to fail completely and give up.

---

### Post by varunendra on 2014-03-12
Thanks for the compliment, and thanks to the mighty search engines! :)

That wiki page is indeed very useful. Another addition to my existing 100+ bookmarks. :p

---

### Post by fraser_john on 2015-01-14
> **mtweldon said:**
> Varun,

You are awesome, thanks so much for the link to the wiki.  I had no luck with the /usr/lib/gnome-shell solution but the following resolved absolutely everything:

```

 /etc/NetworkManager/system-connections/name of your VPN connection and change the password-flags and secret-flags from 1 to 0.
Alternatively put the password directly in the configuration file adding the section vpn-secrets: 

[vpn]
 ....
 password-flags=0
 
 [vpn-secrets]
 password=your_password
```

On reboot I now auto connect to eth0 and connect to my VPN automatically. Looks like the vpn-secrets failure was causing my network connection to fail completely and give up.

Top answer this, worked for Unbuntu 14.04 running Private Internet Access VPN (PIA).

Good stuff!

---

