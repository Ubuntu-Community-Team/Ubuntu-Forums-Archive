---
title: "ubuntu server 8.10 problem"
date: 2009-03-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by saha on 2009-03-08
i have inspiron 1525

when i try to install any package then this is the standard output 

```
sudo apt-get install [COLOR="Red"]x[/COLOR]

E: package [COLOR="Red"]x[/COLOR] has no installation candidate
```

any ideas ?

---

### Post by ugm6hr on 2009-03-08
Potential problems:

1. Incorrect /etc/apt/sources.list
2. Incorrect package name
3. Package not available in repository (search here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) )

---

### Post by saha on 2009-03-08
package [COLOR="Red"]xinit[/COLOR] is exist 

and the same output still appear

---

### Post by ugm6hr on 2009-03-08
Give output from:

```
uname -a
cat /etc/apt/sources.list
```

---

### Post by saha on 2009-03-08
[COLOR="Red"]uname -a[/COLOR]

linux home 2.6.27-7-server #1 smp Fri oct 24 06:37:55 UTC 2008 i686 GNU/Linux

the [COLOR="Red"]second command[/COLOR] i can't put it's output because i have to write about 25 lines

you can tell me what are you looking for

---

### Post by ugm6hr on 2009-03-08
> **saha said:**
> the [COLOR="Red"]second command[/COLOR] i can't put it's output because i have to write about 25 lines

you can tell me what are you looking for

All of it. Use copy & paste with a USB if necessary. Or remote / ssh into it.

PS: I assume the server is online.

---

### Post by saha on 2009-03-08
how can i copy& paste in the command line of ubuntu server

it's the first time i use this kind of operating systems 

also can the usb work on this enviroment ?

---

### Post by ugm6hr on 2009-03-08
You can use USB, you just have to mount it manually.

Not sure if you can copy and paste from the Terminal directly, but you can certainly copy the file directly to USB, and edit using nano.

If you plug a USB drive in, then run command:

```
sudo fdisk -l
```

This will list your HD and also the USB stick.  You need to make a note of the relevant partition on the USB stick (something like /dev/sdb1)

Mount it as described here: [https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting](https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting)

Then copy the file:
```
cp /etc/apt/sources.list /media/external/sources.txt
```

Then unmount the USB:
```
sudo umount /media/external
```

Then unplug USB, and just upload the file here (or copy & paste).

EDIT: I just want to check - the server is online, isn't it?
To check - try:
```
sudo apt-get update
ping -c 2 208.67.219.101
```

---

### Post by sirebral on 2009-03-08
> **ugm6hr said:**
> You can use USB, you just have to mount it manually.

Not sure if you can copy and paste from the Terminal directly, but you can certainly copy the file directly to USB, and edit using nano.

Try Highlighting everything, then using a right click on your mouse and choose **Copy**.  I am not sure which OS you are accustomed too but a Right Click, Copy is pretty standard.  

Of course if you are using a one button mouse, try the **Edit** menu option.

---

### Post by chelrob on 2009-03-08
Open the file with a text editor.  Or copy the file to a usb stick.

---

### Post by saha on 2009-03-09
[COLOR="Red"]/etc/apt/sources.list[/COLOR]

> # 
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted

#deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


[COLOR="Red"]ping -c 2 208.67.219.101[/COLOR]

connect:network is unreachable

---

### Post by ugm6hr on 2009-03-09
> **saha said:**
> [COLOR="Red"]ping -c 2 208.67.219.101[/COLOR]

connect:network is unreachable

Should have thought of this first.

It won't work unless you are online.  You are not online.

How do you connect to the internet using the server?

See the wifi help link below (some of it is very relevant to wired connections).

---

### Post by saha on 2009-03-10
[COLOR="Red"]How do you connect to the internet using the server?[/COLOR]
i have no connection with the ubuntu server and i have no idea how to do that from the command line.
it's first time i use a server OS also command line OS 
i uses wired connection on ubuntu 

[COLOR="Red"]wifi help?[/COLOR]
doesn't help

---

### Post by ugm6hr on 2009-03-10
You need to give a lot more detail about your network setup.

That is why I pointed you to the wifi help link; so that you can provide information that would help us to.

Specifically:
static IP or DHCP?
Router setup?
Look for the Ethernet or Network controller in:
```
lspci
```
Ensure there is no disabled marker, andcheck what driver is being used in:
```
lshw -class network
```
Check if you have an ip address with:
```
ifconfig
```

If this is a simple home network with DHCP, then you should be able to plug in cable and then reboot; it will then connect.

---

### Post by saha on 2009-03-10
ok i need the name of those files to copy it's content here

---

### Post by ugm6hr on 2009-03-10
You can send command output to text files like this:

Change directory to USB stick (mount as previously):
```
cd /media/external
```

Then, send each output to a differently named text file.

e.g.

```
lshw -class network >>lshw.txt
lspci >>lspci.txt
ifconfig >>ifconfig.txt
```

The files should then be on the USB (remember to unmount).

---

### Post by saha on 2009-03-10
[COLOR="Red"]lshw[/COLOR]

  *-network DISABLED
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:5a:96:3b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: vnet0
       serial: 4e:8d:c1:cc:03:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:5a:96:3b
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: vnet0
       serial: 4e:8d:c1:cc:03:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=yes multicast=yes


[COLOR="Red"]ifconfig[/COLOR]

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107621 (107.6 KB)  TX bytes:107621 (107.6 KB)

vnet0     Link encap:Ethernet  HWaddr 4e:8d:c1:cc:03:d8  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::4c8d:c1ff:fecc:3d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:14080 (14.0 KB)


[COLOR="Red"]lspci[/COLOR]

selected ============>partion 8
kernel ================>/boot/vmlinuz-2.6.24-21-generic
=======================>root=UUID=9e709d35-ac51-4f32-88d6-6c301f0616fb ro quiet splash
===== intial ramdisk file ===>/boot/initrd.img-2.6.24-21-generic

other os ========================>from first sector of partion

\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
centos


selected ============>partion 5
kernel ================>/boot/xen.gz-2.6.18-92.el5
=======================>root=UUID=9e709d35-ac51-4f32-88d6-6c301f0616fb ro quiet splash
===== Extra modules ==>	/boot/vmlinuz-2.6.18-92.el5xen ro root=LABEL=/ rhgb quiet /boot/initrd-2.6.18-92.el5xen.img/boot/vmlinuz-2.6.18-92.el5xen ro root=LABEL=/ rhgb quiet
/boot/initrd-2.6.18-92.el5xen.img

other os ========================>from first sector of partion
                                                                                                                                                                                                                         
  |
    K  &#1711;
 p  *  &#1705;
 °  &#1601;  *
 &#1611;    &#1584;
      &#1591;
    é  è
 &#1611;    
      
   *  &#1611;
 @  &#1567;  (
 &#1584;  &#1588;  &#710;
 &#1588;  B  h
 B  R  P
 R    <
 &#1729;  &#1576;  ¼
 &#1576;  &#1614;  ¤
 &#1614;    &#1711;
   W  &#1572;
 `    &#1580;
 &#1711;  ¯  &#1588;
     0   &#1600;
 @   \   &#1606;
 p   &#1567;   &#1609;
 &#1584;   8!  ô
 @!  °!  
 &#1729;!  &#1600;!  
 0"  "#  
 *#  &#1578;#  $
 &#1711;$  &#1746;$  ,
  %  7%  4
 @%  ¢%  °
 ¢%  &#1607;%  &#1705;
 &#1607;%  &  &#8222;
 &  &#8220;&  p
 &#8220;&  Y'  \
 Y'  &#8364;'  L
 &#8364;'  «'  <
 &#1729;'  ù'  
 ù'  O)  &#1591;
 O)  f)  &#1576;
 &#1611;)  ,  <
 ,  K,  $
 K,  W,  
 `,  &#1662;,  l
 &#1662;,  &#1563;,  X
 &#1563;,  &#1579;,  H
  -  _-  |
 p-  &#338;-  &#8222;
 *-  ¼-  &#338;
 &#1584;-  &#1616;-  &#8221;
 p.  ×.  &#339;
 à.  )/  ¬
 0/  &#1681;/  ¼
 */  &#1609;/  &#1580;
  0  0  &#1600;
  0  F0  &#1606;
 &#1729;1  X3  &#1609;
 &#8364;3   4  
  4  @5  H
 &#1611;5  6  \
  6  p6  d
 *6  &#1609;6  &#1705;
 &#1609;6  ®7  &#8222;
 ®7  &#1575;7  t
 &#1584;7  &#8206;8  °
 9  :  &#1572;
 :  2:  
 2:  i:  &#1611;
 i:  x:  à
 *:  S;  
 `;  &#402;;  
 &#1711;;  ô;  $
  <  °>  ,
 &#1729;>  [?  x
 [?  @  d
 @  &#1670;@  T
 *@  &#1563;E  &#710;
 &#1729;E  àE  °
  F  %F  ¸
 0F  AF  è
 AF  èF  &#1584;
 èF  ëF  &#1729;
  G  &#8218;G  
 &#8218;G  *G  ü
 *G  icoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by saha on 2009-03-11
ugm6hr where are you man

---

### Post by ugm6hr on 2009-03-11
The Ethernet "Network disabled" comment is not good.

Make sure it is enables in BIOS.

Did you have Windows on the computer before?  If so - re-check the wifi help link, and look at the part about Windows power-saving at the end.

Otherwise, there must be some other way to enable it.

---

### Post by saha on 2009-03-12
i don't think network is disabled because i have ubuntu desktop on the same machine and it work 

but i think the problem in the configuration of the network driver because i skipped the network configuration while i installing the ubuntu server

---

### Post by ugm6hr on 2009-03-12
That would be the problem then.

I have never had to set up a network manually, since I have always used DHCP.

---

### Post by saha on 2009-03-12
i am using DHCP too

i think the problem on the network driver

can we check if the  ethernet is installed or not by a command

---

### Post by ugm6hr on 2009-03-12
lshw confirms the sky2 driver is installed.

What does your /etc/network/interfaces file look like?

I am no expert with manual networking, but perhaps you have no **auto eth0** entry?

It should look something like this (in addition to an **auto lo** entry):

```
auto eth0
iface eth0 inet dhcp
```

---

### Post by saha on 2009-03-14
[COLOR="Red"]auto & iface[/COLOR] command not found

---

### Post by ugm6hr on 2009-03-14
> **saha said:**
> [COLOR="Red"]auto & iface[/COLOR] command not found

Please read my post again.  They are not commands.

See what is in this file!

```
cat /etc/network/interfaces
```

---

### Post by saha on 2009-03-14
[COLOR="Blue"]sorry [/COLOR]

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


[COLOR="Red"]this means that ethernet is not recognised ,right ?[/COLOR]

---

### Post by ugm6hr on 2009-03-14
```
sudo nano /etc/network/interfaces
```

Add these lines to the bottom and save (Ctrl+X).

```
auto eth0
iface eth0 inet dhcp
```

Then reboot.

Then try the network again:

```
ping -c 2 208.67.219.101
```

---

### Post by saha on 2009-03-14
[COLOR="Red"]congratulations 

problem solved [/COLOR]

ok another thing ,do you know how to switch on to gui mode 

i tried [COLOR="Blue"]sudo init 5 [/COLOR]

it doesn't work

---

### Post by ugm6hr on 2009-03-14
> **saha said:**
> ok another thing ,do you know how to switch on to gui mode 

There is no GUI for Ubuntu server.

---

### Post by saha on 2009-03-14
ok thank you for your help very very much

---

