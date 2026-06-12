---
title: "Inspiron 1501 wireless not working need help!!!"
date: 2008-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wickedninjalo430 on 2008-05-21
Alright. Got an Inpsiron 1501 + Hardy 8.04.
Wireless light is on, and the task bar network manager can sometimes see the wireless networks around me, and when it does it still wont connect. I know this thread is repetitive but I've tried everything else on other forms. PLZ Help.

BTW. I have been around since 7.04, but I'm still learning the Ubuntu ropes. Please explain everything in layman's terms.

Already tried this site. [http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html](http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html)

didnt work

---

### Post by AaronMT on 2008-05-22
All you have to do is open the Hardware Drivers and enable the wireless device to download the custom firmware. System -> Administration -> Hardware Drivers.

---

### Post by sam_delta on 2008-05-22
what network card do you have?, if you dont know, open a terminal and type
```
lspci
```

my guess is that it is a broadcom, and you need to do what AaronMT told you, open hardware driveres and enable them, just make sure you have a internet cable plugged in aas it might need to download some firmware. if no drivers are listed,, youll have to install them with this command

```
sudo aptitude install b43-fwcutter
``` then restart/check for hardware drivers under AaronMT specified in the previous post

remember that youll need an internet connection for the previous steps, so make sure you plug your ethernet cable

IMPORTANT all those recomendations assume that you have a broadcom wireless, if your not sure, open a terminal and type the first command specified in this post

tell us how it goes
sam

---

### Post by wickedninjalo430 on 2008-05-22
joe@joe-laptop:~$ lspci

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)


joe@joe-laptop:~$ sudo aptitude install b43-fwcutter
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been kept back:
  apport apport-gtk evolution-data-server evolution-data-server-common gdm 
  gnome-keyring libcamel1.2-11 libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 
  libgdata-google1.2-1 libgdata1.2-1 libgnome-keyring0 libgnutls13 
  libgtk-vnc-1.0-0 libpam-gnome-keyring openssl-blacklist python-apport 
  python-problem-report xserver-xorg-core 
The following NEW packages will be installed:
  b43-fwcutter 
0 packages upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
Need to get 0B/15.8kB of archives. After unpacking 102kB will be used.
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 133853 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a011-1_i386.deb) ...
Setting up b43-fwcutter (1:011-1) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

Wireless still wont connect to network. 
Broadcom driver is not shown in hardware drivers.

---

### Post by sam_delta on 2008-05-22
you have 25 updates available, try going into system>administration>update manager, and do all available updates, that might help. 

as far as i know, installing b43-fwcutter asks if you want to download a firmware, which i didnt saw on your posts, try making all available updates and check if now appears under hardware drivers, if not, proceed to installing b43-fwcutter again.

 tell us how it goes
sam,

---

### Post by wickedninjalo430 on 2008-05-22
I installed all updates and still nothing.

---

### Post by sam_delta on 2008-05-23
follow the steps on [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

sam

---

### Post by wickedninjalo430 on 2008-05-26
didnt work. followed all steps as directed, and on the last step this is the output i got.

joe@joe-laptop:~/WLANBroadcom$ sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
;you should delete that at /usr/sbin/ndiswrapper line 868, <MODPROBE> line 116.

---

### Post by sam_delta on 2008-05-26
whats the output of 
```
ndiswrapper -l
```

sam

---

### Post by wickedninjalo430 on 2008-05-26
I actually just found a fix on another forum.

2. WLAN Interface naming. Fix wlan0_rename, wmaster0_rename, etc...
> I had to do this to get my wireless NIC to function correctly. (wlan0 doesn't work. It'll still end up wlan0_rename)
>> Should be a temp fix as I'd assume the kernel devs will address this bug (already on launchpad)

Replace instances of <driver> with your wireless driver. (b43, iwl3945, madwifi, etc)

1. Alter the the NICs persistent interface name:
Code:

gksu gedit /etc/udev/rules.d/70-persistent-net.rules

2. Now remove any interfaces already listed with your WLAN NIC's MAC address.

3. Add the following and then save and exit: (Replace 00:00:00:00:00:00 with your WLAN NIC's MAC address.)
Code:

# PCI device 0x14e4:0x4311 (<driver>)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:00:00:00:00", NAME="eth1"

4. Now create an alias for eth1 and your driver, in my case b43: (b43, iwl3955, madwifi, etc...)
Code:

echo 'alias eth1 <driver>' | sudo tee /etc/modprobe.d/<driver>

5. Reboot 

[http://ubuntuforums.org/showthread.php?t=649038&highlight=solved+b43](http://ubuntuforums.org/showthread.php?t=649038&highlight=solved+b43)

---

### Post by sam_delta on 2008-05-26
so now your wireless is working??
if so, im glad you made it work... and enjoy ubuntu :)
sam

---

### Post by wickedninjalo430 on 2008-05-26
ok nevermind. that only worked for a few minutes then stopped.

here is ndiswrapper -l output

joe@joe-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

---

### Post by sam_delta on 2008-05-26
type the following commands
```
sudo aptitude remove b43-fwcutter
```

then
```
sudo gedit /etc/init.d/wirelessfix.sh
```

an empty file will open
copy the following into that file
> #!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

save the file and close it

then type the following commands
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
sudo update-rc.d wirelessfix.sh defaults
```

restart your computer, and should work

tell us how it goes
sam

---

### Post by sam_delta on 2008-05-26
sry, double post

sam

---

### Post by wickedninjalo430 on 2008-05-26
ok I did what you said and heres what happened in a terminal.

joe@joe-laptop:~$ sudo aptitude remove b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  networkstatus 
The following packages will be REMOVED:
  b43-fwcutter 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 340kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 133832 files and directories currently installed.)
Removing b43-fwcutter ...
Removing networkstatus ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
joe@joe-laptop:~$ sudo gedit /etc/init.d/wirelessfix.sh
joe@joe-laptop:~$ cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
joe@joe-laptop:/etc/init.d$ sudo update-rc.d wirelessfix.sh defaults
 System startup links for /etc/init.d/wirelessfix.sh already exist.
joe@joe-laptop:/etc/init.d$ 


I will now reboot and tell you how it goes.

---

### Post by wickedninjalo430 on 2008-05-26
Didnt work. It doesn't see any networks now.

---

### Post by sam_delta on 2008-05-26
post the output of "cat /etc/init.d/wirelessfix.sh"

sam

---

### Post by wickedninjalo430 on 2008-05-26
joe@joe-laptop:~$ cat /etc/init.d/wirelessfix.sh
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44 
joe@joe-laptop:~$

---

### Post by sam_delta on 2008-05-26
try manually typing each command into the terminal
```
sudo modprobe -r b44
sudo modprobe -r b43
sudo modprobe -r b43legacy
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44 
```

sam

---

### Post by wickedninjalo430 on 2008-05-26
joe@joe-laptop:~$ modprobe -r b44
FATAL: Error removing b44 (/lib/modules/2.6.24-17-generic/kernel/drivers/net/b44.ko): Operation not permitted
joe@joe-laptop:~$ sudo modprobe -r b44
joe@joe-laptop:~$ sudo modprobe -r b43
joe@joe-laptop:~$ sudo modprobe -r b43legacy
joe@joe-laptop:~$ sudo modprobe -r ssb
joe@joe-laptop:~$ sudo modprobe -r ndiswrapper
joe@joe-laptop:~$ sudo modprobe ndiswrapper
joe@joe-laptop:~$ sudo modprobe b44
joe@joe-laptop:~$ 
 
still no networks

---

### Post by sam_delta on 2008-05-26
just incase, ,use sudo ar the beggining on the first command, and retype everything,,

i duno what going wrong here. driver appears present, and we already did hardy fix.

type  "sudo ndiswrapper -m" and see if it stills return errors

also, i would like to see the output of ```
iwconfig
sudo ifconfig scan
```

im sry this is taking too long
sam

---

### Post by wthex on 2008-05-27
I have a Dell Inspiron E1505 and experienced some trouble with the wireless setup.

Without the details, of which it looks like most of them you already performed, I basically just used the windows driver and ndiswrapper.

It works however, I still don't see any wireless networks if I right click the network manager icon and select "Edit Wireless Networks".

The good news is when you left click the Network Manager icon and choose "Manual Configuration..." you will find a list of networks; in a round-about way.

When the manual configuration window appears you should see something that says "Wireless Connection". If you don't, the driver still has not been recognized.

If you do then you need to select it then click properties.

Uncheck "Enable roaming mode".

Under Wireless settings, in the Network Name (ESSID) drop down you will find a list of wireless networks.

I'm sure this isn't supposed to work this way, but it worked for me. I don't do a lot of "roaming" and normally only use my laptop on my home network.

Hope that helps...

wthex

---

### Post by sam_delta on 2008-05-27
@wthex

you can try another network mangaer such as wifi-radar or Wicd, you can download both from the repositories (synaptic package manager) or by simply typing "sudo aptitude install wifi-radar"

note that you MIGHT (not sure) need to close gnome-network manager to make it work, if it works, just uninsall gnome-network manager

sam

---

### Post by wickedninjalo430 on 2008-05-27
joe@joe-laptop:~$ sudo ndiswrapper -m
[sudo] password for joe: 
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
;you should delete that at /usr/sbin/ndiswrapper line 868, <MODPROBE> line 117.
joe@joe-laptop:~$ iw config
bash: iw: command not found
joe@joe-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

joe@joe-laptop:~$ sudo ifconfig scan
scan: error fetching interface information: Device not found

Already Tried Wicd and wifi radar

---

### Post by sam_delta on 2008-05-27
to be honest, im not sure whats happening here. but, after some research, ive come with some things you may want to try. you might want to start a new thread under network and wireless section of the ubuntu forums, hopefully, you can get more answers from people that know what your problem is.

if you want to keep trying here, ill do my best to help you, and will keep researching on your problems according to your outputs

for now, you can try:

to fix the "module configuration already contains alias directive"
Look in your /etc/modules file. Is ndiswrapper listed multiple times? It should only be listed once.

now, could you copy the output of the command
"sudo lshw -C network"

thanks
sam

---

### Post by wickedninjalo430 on 2008-05-27
Ndiswrapper is listed only once.

joe@joe-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1b:fc:d8:87:34
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:89:c0:37
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.3 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

---

### Post by sam_delta on 2008-05-28
type the following
this will backlist the old driver bcm43xx, (there might be a conflict with your old drivers
```
sudo echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

then, restart, then check if it works/try "sudo ndiswrapper -m"

sam

---

### Post by wickedninjalo430 on 2008-05-28
joe@joe-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration contains directive install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
;you should delete that at /usr/sbin/ndiswrapper line 868, <MODPROBE> line 118.
joe@joe-laptop:~$

---

### Post by sam_delta on 2008-05-28
can you please post the output of  ```
cat /etc/modprobe.d/ndiswrapper
```

sam

---

### Post by wickedninjalo430 on 2008-05-28
joe@joe-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias pci:v000014E4d00004311sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00000009sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00000009sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv0000000Asd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Sun May 18 16:13:29 EDT 2008 
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
joe@joe-laptop:~$

---

### Post by sam_delta on 2008-05-28
open that file
```
sudo gedit /etc/modprobe.d/ndiswrapper
```
delete EVERYTHING, and type the following in the first line, it should look like this
> alias eth1 ndiswrapper
restart pc, and check if internet works, if it dont, post the output of the command ```
iwconfig
sudo ifconfig scan
```

sam

---

### Post by wickedninjalo on 2008-05-29
Ok I tried that now I cant even connect to my ethernet.

---

### Post by sam_delta on 2008-05-29
rewrite what was in the file before ```
sudo gedit /etc/modprobe.d/ndiswrapper
```

> alias pci:v000014E4d00004311sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00000009sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00000009sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv0000000Asd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Sun May 18 16:13:29 EDT 2008
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

sry but to be honest i duno what to try next. consider starting a new thread so other people with more knowledge will be able to help

also, this is a tough solution, but doing a fresh install and updating your system and start all over again might be better

sam

---

### Post by chili555 on 2008-05-30
@sam_delta

First of all it's:```
sudo iwlist eth1 scan
```Second, in my opinion, it's irresponsible to ask someone to delete an entire file without first making a backup.```
sudo cp /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.bak
```Then, when it all goes wacky, as it has here, you can get the old file back by reversing the command.

What do you think the chances are that this guy can re-type all that correctly? Could you? I know he could do a copy and paste, transfer it with a memory stick, etc., but isn't that a high price to pay?

As well, if you want to delete a couple of lines from a file, I suggest commenting them out so you can see and return to the previous version. You can even put in comments about why a line is commented out:```
#not using ethernet connection temporarily 03/24/2008
#auto eth0
iface eth0 inet dhcp
```

---

### Post by sam_delta on 2008-05-30
> **chili555 said:**
> @sam_delta

First of all it's:```
sudo iwlist eth1 scan
```Second, in my opinion, it's irresponsible to ask someone to delete an entire file without first making a backup.```
sudo cp /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.bak
```Then, when it all goes wacky, as it has here, you can get the old file back by reversing the command.

What do you think the chances are that this guy can re-type all that correctly? Could you? I know he could do a copy and paste, transfer it with a memory stick, etc., but isn't that a high price to pay?

As well, if you want to delete a couple of lines from a file, I suggest commenting them out so you can see and return to the previous version. You can even put in comments about why a line is commented out:```
#not using ethernet connection temporarily 03/24/2008
#auto eth0
iface eth0 inet dhcp
```
yeah, thanks for the recomendations, i keep learning from things like this, hopefully im getting better at assisting people in the future.

btw, "sudo iwlist scan" will also work , and will display a scan for each device

thnx again
sam

---

