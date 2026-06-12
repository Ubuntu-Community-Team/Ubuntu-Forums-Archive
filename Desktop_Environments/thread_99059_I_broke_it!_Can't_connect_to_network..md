---
title: "I broke it! Can't connect to network."
date: 2005-12-04
forum: Desktop Environments
---

### Post by nrwilk on 2005-12-04
So, this is the second time this has happened to me.

(see other thread here: [http://ubuntuforums.org/showthread.php?t=79023](http://ubuntuforums.org/showthread.php?t=79023))

This time I tried changing my hostname from localhost to something a bit less generic.  After the change (which worked) nothing which uses the network works.  Kopete, Akregator, Firefox, Opera, Everything.  I can't even ping other local computers.  When I go to KControl, my eth1 is disabled.  eth0 doesn't work, it's a motherboard problem.  When I try to enable eth1, it flashes on for a fraction of a second, and then back off.  I REALLY don't want to have to reinstall again in order to fix this.  I'm sure someone should know how to deal with this problem.

Can one not do something simple like change the hostname without borking the system?

Thanks for any help!

---

### Post by amohanty on 2005-12-04
How did you change your hostname?
Did you reboot?
Post contents of /etc/hosts

AM

---

### Post by nrwilk on 2005-12-04
I edited the hostname under KControl > internet & Network > Network Settings > Domain Name System tab.  I did restart, several times.  I tried to change it back to localhost, with no luck.

Here's the output from this
```
sudo cat /etc/hosts
```
command:
```
127.0.0.1 localhost.localdomain localhost LinuxCompy

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by amohanty on 2005-12-04
Add the following line to /etc/hosts by doing:

```
sudo gedit /etc/hosts
```

```
<your ip> <new host name>.localdomain <new host name>
```

right below this line:

```
127.0.0.1 localhost.localdomain localhost LinuxCompy
```

<your ip> should not be 127.0.0.1

To view the ip:

```
ipconfig
```

Also post the output of:

```
cat /etc/network/interfaces
```

HTH
AM

---

### Post by nrwilk on 2005-12-04
After editing /etc/hosts with that info and my ip (I assume that's supposed to be my internal IP - 192.168.0.2), all I get after trying to issue ANY command is this:
```

unable to lookup LinuxCompy via gethostbyname()

```

This means that I cannot sudo or kdesu into an editor to edit the file again.  How can I get around this?

---

### Post by amohanty on 2005-12-04
Is this what you named your machine:
LinuxCompy

The thing is what I just gave you is extra, you should not really need it.

So undo what I gave you, ie remove the line you added.
Check your /etc/hostname file and make sure it has only one word:
LinuxCompy

HTH
AM

---

### Post by nrwilk on 2005-12-04
I named it LinuxCompy at install, I tried to change it from LinuxCompy.  After going back to LinuxCompy, it still give me these issues.

Also, I was getting that error for all commands after I changed it the first time, but I don't know how I made that go away.

EDIT: I remembered that I can boot into recovery mode, and I redited that file to try to get my command access back.  We'll see if it works...

---

### Post by amohanty on 2005-12-04
What does this return:

```
hostname
```

---

### Post by nrwilk on 2005-12-04
LinuxCompy, which is the contents of the /ect/hostname file.

---

### Post by nrwilk on 2005-12-04
Fixed the issue with this:
```
unable to lookup LinuxCompy via gethostbyname()
```

I had accidentally put an "o" instead of a "0" in the IP.

Still cannot connect to anything on the network.  I am restarting after these changes, too.

---

### Post by amohanty on 2005-12-04
So what did you fix?
What do your following files look like:

/etc/hosts
/etc/hostname
/etc/network/interfaces

AM

---

### Post by nrwilk on 2005-12-04
For a while there, I was getting that error whenever I tried to use sudo, kdesu or su.  Now, I can use those commands without the error.

here are the output from the files you requested:
/etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp

iface eth0 inet 

```

/etc/hosts:
```
127.0.0.1 localhost.localdomain localhost LinuxCompy
192.168.0.2 DeepThought.localdomain DeepThought

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

/etc/hostname:
```
LinuxCompy

```

The hostname that I wanted was "DeepThought."

I have eth1 setup to automatically detect IP and subnet mask and all that crazy stuff.

Also, when I try to execute the ipconfig command you suggested earlier, I get an "BASH: ipconfig: unknown command" error.

---

### Post by amohanty on 2005-12-04
I am sorry, I made a typo the command is:
```
ifconfig
```

Ok if the hostname you want is DeepThought replace all occurances of LinuxCompy in /etc/hosts /etc/hostname with Deepthought

Also you can remove this line from /etc/hosts:
```
192.168.0.2 DeepThought.localdomain DeepThought
```
It was just a last ditch effort.

reboot

HTH
AM

---

### Post by nrwilk on 2005-12-04
Ok, the hostname now shows DeepThought.

But, I still can't connect to any network services.  even during bootup, setting time from ntp.ubuntu.org fails.

---

### Post by amohanty on 2005-12-04
And you replaced LinuxCOmpy in /etc/hosts?

If you goto: System->ADministration->Networking
select Ethernet Connection 
and click on activate what happens?

AM

---

### Post by nrwilk on 2005-12-04
I don't see a "networking" catagory under System Administration in KControl.
I'm using KDE, so under KControl > Internet & Networking > Network Settings I've tried to activate eth1, but it just flickers on, and then diables itself again.

---

### Post by amohanty on 2005-12-05
Sorry about that.. I use gnome, which has it differently. Can you post the output of the following command:

```
dmesg | tail
```

AM

---

### Post by nrwilk on 2005-12-05
Sorry, my girlfriend is sick, and I had to run out for some nausea medicine.  I won't be able to get back on until tomorrow morning (it's about 11:00 PM where I am).

The output from ```
dmesg | tail
``` is:
```
[4294710.526000] Bluetooth: L2CAP ver 2.7
[4294710.526000] Bluetooth: L2CAP socket layer initialized
[4294710.565000] Bluetooth: RFCOMM ver 1.5
[4294710.565000] Bluetooth: RFCOMM socket layer initialized
[4294710.565000] Bluetooth: RFCOMM TTY layer initialized
[4294712.102000] Linux agpgart interface v0.101 (c) Dave Jones
[4294712.111000] nvidia: module license 'NVIDIA' taints kernel.
[4294712.120000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[4294712.120000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[4294712.120000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005

```

Thanks so much for helping me with this!  Hopefully we can resolve this tomorrow.

Thanks.

EDIT: mistaken, I was.  I'll be able to stay up a bit later than I thought.

---

### Post by amohanty on 2005-12-05
And this was right after you tried to enable the eth1 interface?

Can you post the output of the following:

```
ifconfig
```

and then 

```
sudo ifconfig eth1 down
sudo ifconfig eth1 up
```

AM

---

### Post by nrwilk on 2005-12-05
Both of those commands give me absolutely no output.

I tried this as well:
```
sudo ifconfig eth1
```
and from that I get this:
```
eth1      Link encap:Ethernet  HWaddr 00:11:95:2A:37:02  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xac00 


```

---

### Post by amohanty on 2005-12-05
Damnit gotta get some sleep...
sorry I meant:

```
sudo ifconfig eth1 up
```

From the ifconfig o/p basically your h/w is fine, its just not binding to an address. This should bring it up. If after doing this ```
ifconfig
``` still returns the same result as in the previous post, try the following:

```
ifconfig eth1 192.168.0.2 netmask 255.255.255.0
route add 192.168.0.2 eth1
```

replace 192.168.0.2 with your local IP address. This will manually setup the NIC.

ALso make sure that if you are using a router with dhcp that dhclient is on:

```
ps aex | grep dhclient | grep -v grep
```

should return something like:

```
aseem@kandinsky:~$ ps aex | grep dhclient | grep -v grep
 5401 ?        Ss     0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0

```

AM

---

### Post by nrwilk on 2005-12-05
After doing that, I went to check out the status of eth1 in kcontrol, and it showed it as enabled.  But, still nothing would connect to the internet, or my local network.  After reboot, it is disabled again, and behaves as it has been behaving.

What could that simple step of renaming the computer have messed up so much?  Why would they include a textbox that you cannot fill in unless you want to spend time trying to figure out what it messed with?  Strange.

Should I just reinstall?

EDIT: I'm headin' off to bed.  At least I got some good homework done.

---

### Post by amohanty on 2005-12-05
Before you reinstall could you please post the output of the commands that I posted in the previous post. 

The reason is that if we dont figure out why this is happening, and a reinstall does not fix it, you will be back to square one. So figuring out what the problem will be better in the long run.

HTH
AM

---

### Post by nrwilk on 2005-12-05
sure thing! I'll brb with that output.

EDIT: here it is.

```
fealos@DeepThought:~$ sudo ifconfig eth1 up
Password:
fealos@DeepThought:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:11:95:2A:37:02
          inet6 addr: fe80::211:95ff:fe2a:3702/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:378 (378.0 b)
          Interrupt:18 Base address:0xac00

fealos@DeepThought:~$ sudo ifconfig eth1 192.168.0.2 netmask 255.255.255.0
fealos@DeepThought:~$ sudo route add 192.168.0.2 eth1
fealos@DeepThought:~$ ps aex | grep dhclient | grep -v grep
fealos@DeepThought:~$
```

---

### Post by nrwilk on 2005-12-05
After that, in kcontrol it shows eth1 as being enabled.  But, programs still cannot connect to the network.  Although, now they take a lot longer to tell me that they cannot connect.  before firefox would instatly tell me that it could not see ubuntuforums.org, butnow it takes more like 7 seconds to tell me.  The same with Kopete.

---

### Post by amohanty on 2005-12-05
```
fealos@DeepThought:~$ ps aex | grep dhclient | grep -v grep
fealos@DeepThought:~$
```

This tells me that you are not running yoru DHCP client daemon. If you are connected to your Cable/DSL modem via a router with DHCP you need to be running this. I am not currently on my boxen, but try this:

```
sudo dhclient eth1
```

dhclient manual:
[http://www.bind9.net/dhclient.8](http://www.bind9.net/dhclient.8)

Then see if you are connected using:

```
ping <router ip address - typically 192.168.0.1>
```

Also post the output of the the above two commands as well as the output of:

```
ifconfig
```

and 

```
route -n
```

HTH
AM

---

### Post by nrwilk on 2005-12-05
YAY!

after this command:
```
sudo dhclient eth1
```

that gets the connection back up.  I tried restarting to make sure that it would apply after a restart too, but it did not.  I had to reissue the above command.  Is there a place where that command is supposed to be in a script that executes at login, where it could have been removed from?  Or, is there a place where I can put it that will execute it while loading the kernel (before it tries to set the time through ntp)?  I noticed ntp syncing and samba daemons fail at startup.

We're getting closer!

---

### Post by amohanty on 2005-12-05
I think theres a way to do that. I dont have access to my box, I will take a look when I get home.

AM

---

### Post by bb002 on 2005-12-05
To configure my NIC I goto "System -> Administration -> Networking".

You said eth0 doesn't work so it should say "Device is not configured". if it doesn't you'll want to click eth0 then properties. Uncheck "Device is configured" and click ok.

View the properties of eth1 and make sure "Device is configured" is selected and configuration is set to "DHCP". Click "Activate" if eth1 isn't activated already. Make sure "Default gateway device" is eth1. Also check the "general" tab and see if it says your hostname is DeepThought, make is say DeepThought if it doesn't already. Click ok.


Doing this has always managed to fix the occasional conflict between my wireless card (eth0) and onboard NIC (eth1). The cause of my problem is a bit different but the problem itself is the same. 

Hopefully this will fix you up too.

---

### Post by nrwilk on 2005-12-05
Thanks a lot, bb002!  But, I'm running Kubuntu, so I don't have the system options that you have under Gnome.  Also, looking under KControl > Internet & Networking > Network Settings, when I right-click on the eth1 entry and choose properties, there is no "Device is Configured" option.

Thanks for trying, though!

So, the question is, what file was messed with that had the info the computer uses at startup to get connected to the network during bootup?  And, how can that file be fixed to resume normal activity?

---

### Post by amohanty on 2005-12-05
Make the networing thingy look like the attached image. Its for gnome, but there must be parallels in KDE:

[ATTACH]4179[/ATTACH]

---

### Post by nrwilk on 2005-12-05
Yeah, it's set to auto-detect DHCP, and it's enabled.  But, when I restart, it's no longer enabled.

---

### Post by amohanty on 2005-12-05
In your /etc/network/interfaces which you posted:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp

iface eth0 inet 

can you remove these lines:

```
address 127.0.0.1
netmask 255.0.0.0
```

```
iface eth0 inet
```

and try and reboot.

AM

---

### Post by nrwilk on 2005-12-05
This seems to have completely fixed the problem.  At startup, the ntp sync was successful, and the samba daemons initialized.  All network functionality is now working correctly.

Thank you so much, Amohanty!  You've been extremely helpful!  I can't wait until I know enough to be able to help with problems that are this technical.

---

### Post by amohanty on 2005-12-06
You are welcome.

AM

---

### Post by bobbymcsteels on 2006-02-10
so how would I configure a static ip??

---

