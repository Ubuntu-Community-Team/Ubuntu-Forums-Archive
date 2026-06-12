---
title: "Network: device not managed"
date: 2009-04-21
forum: General Help
---

### Post by mark0495 on 2009-04-21
Hello everybody, 

I upgraded to Xubuntu 9.04 yesterday, and it works very well. However, there is a cross at my network button. When I hover over the icon, it says:

> Wired network
Device not managed

As you see, I still have access to the internet, but maybe it can become a problem in the future?

Can anyone help me? Thanks already

Mark

---

### Post by Floppyjoe on 2009-04-29
Same problem here.

When I change managed=false to managed=true in /etc/NetworkManager/nm-system-settings.conf I lose internet connectivity. I also get this warning when I restart networking after changing managed=false to managed=true :
> WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.

Does anyone know how to fix this?

---

### Post by beoba on 2009-05-01
I've got the same thing on a fresh install of 9.04-amd64 with a Thinkpad T61p. The network device is a: 00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03). Oddly enough, my wireless connection works great.

To get around the problem, I have to manually re-init my wired connection periodically by running "sudo dhclient eth0" in a command prompt.

I've previously used 8.10-amd64 and Fedora 10-amd64 on this laptop, and Network Manager worked perfectly in those, so I think this is a 9.04-specific regression.

---

### Post by Xzenome on 2009-05-01
I think I may be having the same problem. I'd file a bug, but I'm not too sure what's wrong. Someone else could though.

---

### Post by anilsarwal on 2009-05-03
I have the same problem. Can someone please help asp?
Thanks

---

### Post by Wiesental on 2009-05-03
I am a beginner with Ubuntu. After upgrading to jaunty, I have no network connection. The network icon, the rising columns, shows a small red box with an "x"--unlikely a good sign. I have gone through the steps in the help files. The problem seems deeper. Any ideas?

---

### Post by chuck7 on 2009-05-16
I have the same problem.

---

### Post by eewo on 2009-06-15
Same problem here

---

### Post by procras on 2009-06-15
This thread looks a bit similar [http://ubuntuforums.org/showthread.php?t=1169604]("http://ubuntuforums.org/showthread.php?t=1169604").

Try the old fashioned was of getting the networking to work;
the command line!

---

### Post by MC JJ Lazer Fists on 2009-06-22
I got my networking together after a couple days of fighting.....yehaw.  I'm just going to go through the whole spiel, and hopefully it will help someone.

I was upgrading from 8.04LTS, to 8.10 which hosed my network connections.  

I got it to work well enough, by editing the /etc/network/interfaces file, and switching my eth1 (The connection that I should have been using), to etho, to look like the following:

/etc/network/interfaces
-----------------------------------------------------------------------------------------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp
auto eth0

#iface eth1 inet dhcp
#auto eth1
-----------------------------------------------------------------------------------------------------------------------------

After rebooting, I found that I couldn't load pages from my local apache server.  But I could connect to the outside world fine.

I then upgraded to 9.04, which should have fixed the issues, but it didn't.

I switched once again edited  /etc/network/interfaces, uncommenting the eth1 line, while forgetting to recomment the eth0 lines.  So when I rebooted, nm-applet showed a red x, and no managed connections....bummer.  I could however use the network normally, and local pages were loading fine.

I went back, fixed the interfaces, so that eth1 was the only interface.  Then edited /etc/NetworkManager/nm-system-settings.conf, and changed managed=false to managed = true.

/etc/NetworkManager/nm-system-settings.conf
 -----------------------------------------------------------------------------------------------------------------------------
 [main]
plugins=ifupdown,keyfile

[ifupdown]
**managed=true**
 -----------------------------------------------------------------------------------------------------------------------------

After rebooting, all was well.  I tried restarting the network, and the nm-applet, manually, but the applet would not restart without hanging,  so I had to reboot.

Also, my nis server got hosed, so somewhere in here, I reinstalled that as well.  I don't think that had anything to do with the applet being crazy, but ya never know.

Here are some of the somewhat helpful links I followed, trying to fix this...
[http://ubuntuforums.org/showthread.php?p=6814830](http://ubuntuforums.org/showthread.php?p=6814830)
[http://www.craigmayhew.com/blog/2009/06/ubuntu-904-wired-network-device-not-managed/](http://www.craigmayhew.com/blog/2009/06/ubuntu-904-wired-network-device-not-managed/)

---

### Post by sdowney717 on 2009-10-27
same here however in my case i set up bridged networking with vbox and manually setup the connection
the original file just has these 2 lines
auto lo
iface lo inet loopback


> #auto lo
#iface lo inet loopback

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet manual

auto br0
iface br0 inet static
        address 192.168.1.100
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth2
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

---

### Post by radu.c on 2010-01-08
Strange enough, this happened to me just now, on Ubuntu 9.10, after installing some updates (which included a new kernel). I installed the updates, rebooted the system, and NM decided not to manage my wire anymore, while keeping the wifi.

I'm now in the process of rebooting, after making the changes mentioned in the previous posts.:popcorn:

---

### Post by Dlambert on 2012-03-02
Same problem, Xubuntu 11.10.

---

### Post by asnd16 on 2012-08-24
> **Dlambert said:**
> Same problem, Xubuntu 11.10.

I got the same issue, I was able to use the command > sudo dhclient eth0  to get it working.  

But how do I get this to work with the Network Manager automatically?

---

