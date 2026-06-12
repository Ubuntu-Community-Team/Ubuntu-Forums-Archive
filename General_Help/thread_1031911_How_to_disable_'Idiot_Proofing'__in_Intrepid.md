---
title: "How to disable 'Idiot Proofing'  in Intrepid"
date: 2009-01-05
forum: General Help
---

### Post by NT4usB on 2009-01-05
Any way to turn off the failsafe xorg and 'automatic' network config?
Trying to get the video to work on a GA-EG41M and having xorg rebuild itself slows the process.
Want to assign a static IP... just plain old eth0, yet automatic thinks I should have a different IP.
Ubuntu is getting more 'Windows' like every release.
Is it time to try a different distro?

---

### Post by mikeman141 on 2009-01-05
Setting a static IP is fairly simple.  Right click on the networkmanager applet in the system tray and click edit connections.  Find the connection you are interested in, click edit, go to the IPv4 tab and change from DHCP to manual.  You can configure it from there.

Definitely a lot easier than doing it in windows.  

Don't know much about your xorg problem...sorry..

---

### Post by Iowan on 2009-01-05
There are a lot of distros available.  Use what works best for you.  [Here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround that may help with the static address problem.

---

### Post by dcstar on 2009-01-05
> **Iowan said:**
> There are a lot of distros available.  Use what works best for you.  [Here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround that may help with the static address problem.

I believe that there have been updates to the Network Manager since that thread was started.

---

### Post by NT4usB on 2009-01-05
> **mikeman141 said:**
> Setting a static IP is fairly simple.  Right click on the networkmanager applet in the system tray and click edit connections.  Find the connection you are interested in, click edit, go to the IPv4 tab and change from DHCP to manual.  You can configure it from there.

btdt.
Put in the IP I wanted (in a completely different window than prior releases btw, wtf do they have to change it just for the sake of changing something. Very Windows like...) Used to autocomplete the netmask... not no more.
ifconfig eth0 shows a different IP.
ifdown eth0 says eth0 doesn't exist.
ifdown -a and I still have a connection.
Not mentioned in the notes. One has to create the new entry, then delete the 'auto', then we get the IP we want.
So, now it's working with the correct IP, but wait!
```
ct@p42:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:d0:ac:f5  
          inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fed0:acf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2617 (2.6 KB)  TX bytes:7793 (7.7 KB)
          Interrupt:21 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ct@p42:~$ sudo ifdown -a
[sudo] password for ct: 
Ignoring unknown interface eth0=eth0.
ct@p42:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:d0:ac:f5  
          inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fed0:acf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2709 (2.7 KB)  TX bytes:7793 (7.7 KB)
          Interrupt:21 Base address:0x8000 

ct@p42:~$ sudo ifdown -h
Usage: ifdown <options> <ifaces...>

Options:
	-h, --help		this help
	-V, --version		copyright and version information
	-a, --all		de/configure all interfaces marked "auto"
	--allow CLASS		ignore non-"allow-CLASS" interfaces
	-i, --interfaces FILE	use FILE for interface definitions
	-n, --no-act		print out what would happen, but don't do it
				(note that this option doesn't disable mappings)
	-v, --verbose		print out what would happen before doing it
	--no-mappings		don't run any mappings
	--force			force de/configuration
ct@p42:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
ct@p42:~$ 

```
Still doesn't believe eth0 exists...

NT4 was easy to configure.
This BS is a whole lot like newer Windows though, if you ask me.

---

### Post by NT4usB on 2009-01-05
> **dcstar said:**
> I believe that there have been updates to the Network Manager since that thread was started.

Well, if there was, they don't work. Still (creates auto, which I deleted and) reverts to auto after boot.
Now to follow that thread and see if I can fix it.
I wouldn't mess with Intrepid at all except it's the only one with a chance to get the G41 graphics to work.

---

### Post by Arup on 2009-01-06
Easy solution for the network issue, I posted the workaround in this forum a while back. To set static IP, first turn off DHCP in router. Then set a range of IP for LAN. After that open up network configuration in Intrepid. Delete all the auto entries. Then add a new entry, make sure to name it, select the system tab. Then add your MTUm IP, DNS etc. When you apply, it will ask you for root password, make sure to check the permanent authentication. You are all set.

---

### Post by NT4usB on 2009-01-06
Cool, thanks.
Still, have to wonder how this is easier or better than the way it's done on Dapper, or Edgy, or Feisty, or Gutsy, or Hardy.
Someone had way too much spare time to go and screw up a GUI that's worked fine for years.
Sorry I missed your original post. Been busy searching for solutions to the video issue. Never thought I'd be on a tangent, dealing with something so simple as network config.
S'pose now is the time to learn how to configure without using the GUI... If it will let me.

---

### Post by jrusso2 on 2009-01-06
The more they try to make it easier the harder it becomes if something doesn't work to fix it.

---

### Post by NT4usB on 2009-01-06
> **jrusso2 said:**
> The more they try to make it easier the harder it becomes if something doesn't work to fix it.
One of the things I enjoyed about Linux, when I first tried it in May of '06, was being able to tinker with it and learn. 
Took a solid month to get MythTV running on Dapper the first time. Took a couple hours to flatline it and get it going again, when I discovered I had the partitioning jacked and 200 GB I couldn't use.
Guess I learned a little something in that month.
One of the things I hate the most about Windows is wizards...

---

### Post by Arup on 2009-01-06
At least there is a solution in Gnome, in Kubuntu or Fedora, no other way but manual editing network config file or DHCP, no GUI. I like that method but I need to teach Ubuntu for first timers so have to make it all GUI or else they would run away.

---

### Post by jrusso2 on 2009-01-06
> **NT4usB said:**
> One of the things I enjoyed about Linux, when I first tried it in May of '06, was being able to tinker with it and learn. 
Took a solid month to get MythTV running on Dapper the first time. Took a couple hours to flatline it and get it going again, when I discovered I had the partitioning jacked and 200 GB I couldn't use.
Guess I learned a little something in that month.
One of the things I hate the most about Windows is wizards...


The problem is when they change the way it works. Like bullet proof x.  Before I could fix any X problems with nano, now I don't know how to fix them with bullet proof x.

---

### Post by NT4usB on 2009-01-06
> **jrusso2 said:**
> The problem is when they change the way it works. Like bullet proof x.  Before I could fix any X problems with nano, now I don't know how to fix them with bullet proof x.

Perzactly...

---

