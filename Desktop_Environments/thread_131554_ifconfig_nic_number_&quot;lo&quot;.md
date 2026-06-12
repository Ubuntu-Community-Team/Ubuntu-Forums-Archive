---
title: "ifconfig nic number &quot;lo&quot; ????"
date: 2006-02-16
forum: Desktop Environments
---

### Post by GNUoob on 2006-02-16
dave@GNUbuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:C0:49:FA:36:4E
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:49ff:fefa:364e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:62762 (61.2 KiB)  TX bytes:18141 (17.7 KiB)
          Interrupt:19 Base address:0x2800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172370 (168.3 KiB)  TX bytes:172370 (168.3 KiB)

dave@GNUbuntu:~$


wtf is lo?

what i have setup is multi nics. im trying to setup the other one which is live on the internet. eth1 is internal going to my router which also is live on the web. i want the lo one to aquire a live address from comcast. how?

---

### Post by o_fortuna on 2006-02-16
[QUOTE=GNUoob]dave@GNUbuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:C0:49:FA:36:4E
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:49ff:fefa:364e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:62762 (61.2 KiB)  TX bytes:18141 (17.7 KiB)
          Interrupt:19 Base address:0x2800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172370 (168.3 KiB)  TX bytes:172370 (168.3 KiB)

dave@GNUbuntu:~$


wtf is lo?

what i have setup is multi nics. im trying to setup the other one which is live on the internet. eth1 is internal going to my router which also is live on the web. i want the lo one to aquire a live address from comcast. how?[/QUOTE]
lo is the internal "loopback." Every computer, including Windows and Ubuntu, has a loopback network. It's nothing to worry about, but it doesn't (I think?) connect to the internet. If you are wondering about it, Wikipedia has an [article]("http://en.wikipedia.org/wiki/Loopback") on it.

---

### Post by GNUoob on 2006-02-16
when i type "ifconfig lo" i get just the same as above?????

so how do i get a DHCP address for it?

---

### Post by engla on 2006-02-16
[QUOTE=GNUoob]when i type "ifconfig lo" i get just the same as above?????

so how do i get a DHCP address for it?[/QUOTE]
In short, **the 'lo' interface it not yours to play with**. It's neccessary and used by the system, so if you want another network interface, buy another network card.

---

### Post by GNUoob on 2006-02-16
[QUOTE=engla]In short, **the 'lo' interface it not yours to play with**. It's neccessary and used by the system, so if you want another network interface, buy another network card.[/QUOTE]


as i said above i have TWO nics in it

im trying to get the 'lo' one to recieve a DHCP from comcast.
the 'eth1' is getting successfully an address from my router

---

### Post by engla on 2006-02-16
Anyhow, anyway, regardless of your configuration 'lo' is not one of the NICs. If you rip them both out, 'lo' will be left there alone.

So you have another problem -- one of your NICs are not showing up; sadly, I'm not the man to fix that problem, I have no idea about such driver issues.

---

### Post by GNUoob on 2006-02-16
thank you

i was wondering why it would name it that???

eth1
eth2
eth0 all make sense

the lo just threw me and now i know where to start :)

---

### Post by GNUoob on 2006-02-16
here is what my install cd readme says for my drivers on the 'lo' nic....


<Quick install with proper kernel settings>

  Unpack the tarball :
	unzip r8169_linuxdrv_vxx.zip

  Change to the directory:
	cd r8169

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	make install
	depmod -a

-----

here is where im lost...

kubuntu-packages-jriddell-key.gpg
r8169
dave@GNUbuntu:~$ cd r8169/
dave@GNUbuntu:~/r8169$ ls
Makefile  README  src
dave@GNUbuntu:~/r8169$ make clean modules
bash: make: command not found
dave@GNUbuntu:~/r8169$ make install
bash: make: command not found
dave@GNUbuntu:~/r8169$

so what am i missing...??

---

### Post by polpak on 2006-02-16
[QUOTE=GNUoob]here is what my install cd readme says for my drivers on the 'lo' nic....

*...snip....*

so what am i missing...??[/QUOTE]

What you are missing is the point. The lo interface IS NOT A NIC. It's a loopback interface. If you have one nic it'd be eth0 if you have 2 they'd be eth0 and eth1. Leave lo alone. If you aren't seeing 2 eth interfaces than most likely one of your nics doesn't have a recognizable driver.

---

### Post by GNUoob on 2006-02-16
[QUOTE=polpak]What you are missing is the point. The lo interface IS NOT A NIC. It's a loopback interface. If you have one nic it'd be eth0 if you have 2 they'd be eth0 and eth1. Leave lo alone. If you aren't seeing 2 eth interfaces than most likely one of your nics doesn't have a recognizable driver.[/QUOTE]


wow...im gonna try to not be nasty here

the point YOUR missing is that i was trying to install the drivers for the NIC that was not recognized and i just humorfully called 'lo' above. by installing the drivers i was trying to get the OS to recognize the UN-recongized 2nd nic. my problem(singular) immediatly preceeding your response was in how to get the drivers installed. the problems prior to that did have to do with not understanding what a 'lo' was.

2 seperate things all wrapped together :)

now in windows land when you install drivers for unrecognized hardware this allows you to then use the device because it is now functional with proper drivers(recognition). does that not happen in linux???

---

### Post by GNUoob on 2006-02-16
any ideas on why my install isnt working?

thanks for any response

---

### Post by GNUoob on 2006-02-17
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp

what do i do here?

---

### Post by GNUoob on 2006-02-17
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

helps me but not with a 'lo' card


anyone...???







-------------------------------------------------
Hello,

The following will explain how to share your Internet connection:

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get:

# apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

# /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

# dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

# gedit /etc/sysctl.conf

8. Reboot. (Optional)

I hope this helps.

Good luck!
----------------------------------------------

above was borrowed but not usefull with a 'lo' card

---

### Post by RAOF on 2006-02-17
You might want to start a new thread, with a title like "help configuring second nic", possibly even in the "Hardware help" thread.  Posts in the right place get the most (useful) attention ;)

However, it seems that the kernel should have a driver for the r8169 cards already, unless this was added between 2.6.12 (which Breezy has) and 2.6.15 (which Dapper has).  I've only got Dapper, so I can't tell whether .12 has those drivers too, but 2.6.15 certainly does.

Finally, the reason your install wasn't working is that Ubuntu, by default, does not come with a build environment.  Those instructions were for compiling the drivers from source.  In order to do that, you'll need to (at least) install the "build-essential" package, and probably the "kernel-headers" and/or "kernel-source" packages.  If you don't know how to install packages, check out the "installing software" link in my sig.

---

### Post by GNUoob on 2006-02-17
bump :)

---

### Post by carlosqueso on 2006-02-17
Just for kicks, try typing ```
sudo ifup eth0
```  and see what it does.  After that, post the output of ```
lspci
```

---

