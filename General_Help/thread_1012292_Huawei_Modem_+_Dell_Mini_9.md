---
title: "Huawei Modem + Dell Mini 9"
date: 2008-12-15
forum: General Help
---

### Post by Barry762 on 2008-12-15
Would someone please kindly explain how to install this Modem [http://shop.vodafone.co.uk//shop/mobile-broadband-devices/usb-modem-stick?compatible=false](http://shop.vodafone.co.uk//shop/mobile-broadband-devices/usb-modem-stick?compatible=false) (Which i am led to beleive is the Huawei E172) On to my Dell Mini 9 (Ubuntu 8.04) Ive spent hours trawling and trying ideas but nothing seems to work... TIA__

---

### Post by rampageoberon on 2008-12-15
Hi, I use the E220 modem and have found a few ways to get it to work. I do hope some of the methods work for you.

Please try either of these 2 graphical methods.

[LIST=1]
[*][https://forge.betavine.net/frs/?group_id=12&release_id=200](https://forge.betavine.net/frs/?group_id=12&release_id=200) - [https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/)
[*][http://umtsmon.sourceforge.net/](http://umtsmon.sourceforge.net/)
[/LIST]

If they don't work I guess we can try wvdial which is a command line application

Hope that helps

---

### Post by Barry762 on 2008-12-16
Still no joy afraid. It seems as though the Modem is not being recognised ? 

lsusb

and

dmesg | tail

Bus 001 Device 008: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 001 Device 002: ID 0c45:63e4 Microdia
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c040 Logitech, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000 

3775.102870] usb 1-8: new high speed USB device using ehci_hcd and address 8
[ 3775.246117] usb 1-8: configuration #1 chosen from 1 choice
[ 3775.247713] usb-storage: probe of 1-8:1.0 failed with error -5
[ 3775.247777] option 1-8:1.0: GSM modem (1-port) converter detected
[ 3775.248110] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
[ 3775.260817] usb-storage: probe of 1-8:1.1 failed with error -5
[ 3775.260889] option 1-8:1.1: GSM modem (1-port) converter detected
[ 3775.261182] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1
[ 3779.259123] scsi10 : SCSI emulation for USB Mass Storage devices
[ 3779.262598] usb-storage: device found at 8
[ 3779.262610] usb-storage: waiting for device to settle before scanning
[ 3783.270392] scsi11 : SCSI emulation for USB Mass Storage devices
[ 3783.273245] usb-storage: device found at 8
[ 3783.273263] usb-storage: waiting for device to settle before scanning
[ 3784.258566] usb-storage: device scan complete
[ 3784.261519] scsi 10:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
[ 3784.297534] sr0: scsi-1 drive
[ 3784.297793] sr 10:0:0:0: Attached scsi CD-ROM sr0
[ 3784.297974] sr 10:0:0:0: Attached scsi generic sg1 type 5
[ 3788.267647] usb-storage: device scan complete
[ 3788.269625] scsi 11:0:0:0: Direct-Access HUAWEI MMC Storage 2.31 PQ: 0 ANSI: 2
[ 3788.277054] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 3788.277285] sd 11:0:0:0: Attached scsi generic sg2 type 0

---

### Post by rampageoberon on 2008-12-16
> **Barry762 said:**
> Still no joy afraid. It seems as though the Modem is not being recognised ? 

lsusb

Bus 001 Device 008: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 001 Device 002: ID 0c45:63e4 Microdia
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c040 Logitech, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000 


Hi there,

The modem is being recognised fine. It seems that you are using the E220 modem rather than the E172 modem that you first wrote. Have you tried installing the "vodafone mobile office" application?

Download and install the following deb package. It will ask to install 15 dependencies. [https://forge.betavine.net/frs/download.php/76/vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb](https://forge.betavine.net/frs/download.php/76/vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb)

You can then access it from Applications -> Internet -> Vodafone Mobile .... I find that if I start with the modem plugged in then this doesn't work. So workaround is unplug the modem, plug it back in and start the Vodafone application.

Do let me know if you get any errors, if so we can try umtsmon or wvdial.

---

### Post by Barry762 on 2008-12-16
Many thanks** rampageoberon** for your continued help. Seems strange the Modem in the link above is the one I'm using which I understand to be the E172, however lsusb says its a E220 ?
I have 

When I D/L the deb package the installer says...

status : Error : Wrong architecture i386

Sorry Im a complete noob when it comes to Linux Ubuntu, but thanks for baring with me.

---

### Post by rampageoberon on 2008-12-16
Ah okay, you probably will have to do it from source then. Download the source tarball at [https://forge.betavine.net/frs/download.php/77/vodafone-mobile-connect-card-driver-for-linux-1.99.17.tar.gz](https://forge.betavine.net/frs/download.php/77/vodafone-mobile-connect-card-driver-for-linux-1.99.17.tar.gz) and follow the instructions in the INSTALL file.

Here's another way with "wvdial". Its a command line way but fairly easy to setup.

Create a directory huawei within your home directory to mount the modem's storage device. The device will be at scd0, scd1 or something similar. Try them out one by one to see which mounts correctly.

```
mkdir ~/huawei
sudo mount /dev/scdX ~/huawei
```

Once the drive is mounted copy the 'SysConfig.dat' file to your desktop/home folder and open it with gedit.

```
cp ~/huawei/SysConfig.dat ~/Desktop/
gedit ~/Desktop/SysConfig.dat
```

Now run wvdialconf as root

```
sudo wvdialconf
gksu gedit /etc/wvdial.conf
```

You then need to edit the '/etc/wvdial.conf' file with the appropriate parameters. My wvdial.conf file looks like this (you will get the username and password options from the SysConfig.dat)

```
[Dialer Pin]
Baud = 9600
Modem = /dev/ttyUSB0
Init1 = AT+CPIN=<yourpin>

[Dialer Vodafone]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Stupid Mode = 1
Phone = <from SysConfig.dat>
Password = <from SysConfig.dat>
Username = <from SysConfig.dat>
```

Note: If you don't have a pin then you don't need the [Dialer Pin] section.

To connect to the internet run the following command.

```
wvdial Pin
wvdial Vodafone
```

Hope that helps. Please report your progress on this

---

### Post by Barry762 on 2008-12-16
Thanks again rampageoberon, got to nip out now however, will try your advice later 

regards

---

### Post by khelben1979 on 2008-12-16
Maybe [this link]("http://ubuntuforums.org/showthread.php?t=843973") can help you out?

---

### Post by Barry762 on 2008-12-16
> **rampageoberon said:**
> Ah okay, you probably will have to do it from source then. Download the source tarball at [https://forge.betavine.net/frs/download.php/77/vodafone-mobile-connect-card-driver-for-linux-1.99.17.tar.gz](https://forge.betavine.net/frs/download.php/77/vodafone-mobile-connect-card-driver-for-linux-1.99.17.tar.gz) and follow the instructions in the INSTALL file.

Here's another way with "wvdial". Its a command line way but fairly easy to setup.

Create a directory huawei within your home directory to mount the modem's storage device. The device will be at scd0, scd1 or something similar. Try them out one by one to see which mounts correctly.

```
mkdir ~/huawei
sudo mount /dev/scdX ~/huawei
```

Once the drive is mounted copy the 'SysConfig.dat' file to your desktop/home folder and open it with gedit.

```
cp ~/huawei/SysConfig.dat ~/Desktop/
gedit ~/Desktop/SysConfig.dat
```

Now run wvdialconf as root

```
sudo wvdialconf
gksu gedit /etc/wvdial.conf
```

You then need to edit the '/etc/wvdial.conf' file with the appropriate parameters. My wvdial.conf file looks like this (you will get the username and password options from the SysConfig.dat)

```
[Dialer Pin]
Baud = 9600
Modem = /dev/ttyUSB0
Init1 = AT+CPIN=<yourpin>

[Dialer Vodafone]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Stupid Mode = 1
Phone = <from SysConfig.dat>
Password = <from SysConfig.dat>
Username = <from SysConfig.dat>
```

Note: If you don't have a pin then you don't need the [Dialer Pin] section.

To connect to the internet run the following command.

```
wvdial Pin
wvdial Vodafone
```

Hope that helps. Please report your progress on this

Not to sure how to edit this ???

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Password = <Your Password>
New PPPD = yes
; Username = <Your Login Name>
Modem = /dev/ttyUSB0
Baud = 9600

---

### Post by rampageoberon on 2008-12-16
I'm assuming that the following is the content of your /etc/wvdial.conf file. So this is what it should look like.

Note please put the correct username and password and phone number from the SysConfig.dat file as I instructed before.

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = <Target Phone Number>
ISDN = 0
Password = <Your Password>
New PPPD = yes
Username = <Your Login Name>
Modem = /dev/ttyUSB0
Baud = 9600
Stupid Mode = 1
```

Then run the following to connect. (This assumes the sim doesn't require a pin)

```
wvdial Defaults
```

Hope that gets you working

---

### Post by Barry762 on 2008-12-16
Yes its the contents, however Ive jumped the gun a bit, Im not sure I understand this bit therefore not done it.

Create a directory huawei within your home directory to mount the modem's storage device. The device will be at scd0, scd1 or something similar. Try them out one by one to see which mounts correctly.

Sorry once again for being thick ! but I really do appreciate your patience

---

### Post by rampageoberon on 2008-12-16
Okay, so now the configuration settings for the modem are stored on a virtual CDROM within. So we want to access the configuration files.

To view the files on the modem we need to mount the block device to somewhere where you can access it. I presume it will either be /dev/scd0 or /dev/scd1. Do the following commands and check the contents by going to "Places -> huawei" for a file called 'SysConfig.dat'.

```
mkdir ~/huawei
sudo mount /dev/scd0 ~/huawei
```

If the file is not there when you run the following command then you need to check /dev/scd1. So run the following command to unmount device (if something was mounted)

```
sudo umount ~/huawei
```

Once you see the SysConfig.dat file, open it and locate the Phone number, Username and Password and edit the /etc/wvdial.conf file accordingly.

hope thats better

---

### Post by Barry762 on 2008-12-16
barry@barry:~$ mkdir ~/huawei
mkdir: cannot create directory `/home/barry/huawei': File exists
barry@barry:~$ sudo mount /dev/scd0 ~/huawei
mount: block device /dev/scd0 is write-protected, mounting read-only
barry@barry:~$

---

### Post by rampageoberon on 2008-12-16
What seems to be the problem? By the looks of things the drive has mounted fine. You need to extract the username, password and phone number from the SysConfig.dat file and put the details in the /etc/wvdial.conf file. (let me know if that file doesn't exist)

---

### Post by Barry762 on 2008-12-16
Sorry rampageoberon Im at a loss ! I managed to get a Huawei cd image on to the desktop but when I click on it 3 files appear but wont let me open them. Still not sure what you mean by SysConfig.dat file and how to locate it. :confused:

---

### Post by rampageoberon on 2008-12-17
Hmm, okay paste here the output when you do the following command

```
ls -la ~/huawei
```

Try the following details:

Phone = *99#
Username = web
password = web

If possible call up customer care and ask them for the details if the above are incorrect.

hope that helps

---

### Post by Barry762 on 2008-12-17
I thought we might have cracked it...

 WvDial: Internet dialer version 1.60
--> Warning: section [Dialer Vodafone] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Dec 17 08:11:34 2008
--> Pid of pppd: 6565
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> Using interface ppp0
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> Authentication (CHAP) started
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> Authentication (CHAP) successful
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> pppd: [18]&#65533;[06][08]H&#65533;[06][08]
--> Disconnecting at Wed Dec 17 08:11:36 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ

Below... output from ls -la ~/huawei

barry@barry:~$ barry@barry:~$ ls -la ~/huawei
bash: barry@barry:~$: command not found
barry@barry:~$ total 8
bash: total: command not found
barry@barry:~$ drwxr-xr-x  2 barry barry 4096 2008-12-16 16:11 .
bash: drwxr-xr-x: command not found
barry@barry:~$ drwxr-xr-x 44 barry barry 4096 2008-12-17 07:46 ..
bash: drwxr-xr-x: command not found
barry@barry:~$ barry@barry:~$ 
bash: barry@barry:~$: command not found
barry@barry:~$ 
barry@barry:~$

---

### Post by rampageoberon on 2008-12-17
Ok this is looking better. Now I had the exit code 16 errors before and that can be if the line is barred, or username and password are incorrect.

If possible please call vodafone customer care and find out what the correct details are.

Do report your progress please. Hope you are able to connect soon

---

### Post by Barry762 on 2008-12-17
I called Voda C/S the info you offered is correct,see below

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = web
Password = web
Baud = 9600

Dont know where to go from here 

PS This dongle works perfectly on my Vista Machine.

---

### Post by rampageoberon on 2008-12-17
Ok that config looks correct. Please add one line "Stupid Mode =1"

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = web
Password = web
Baud = 9600
Stupid Mode =1
```

and connect with command "wvdial"

It should ideally work, if it doesn't i'm not sure what the problem could be.

---

### Post by Barry762 on 2008-12-17
> **rampageoberon said:**
> Ok that config looks correct. Please add one line "Stupid Mode =1"

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = web
Password = web
Baud = 9600
Stupid Mode =1
```

and connect with command "wvdial"

It should ideally work, if it doesn't i'm not sure what the problem could be.

I think that just sums me up lol "Stupid Mode =1"

---

### Post by rampageoberon on 2008-12-17
I trust that worked for you then? If so please mark thread as solved and enjoy :)

---

### Post by Barry762 on 2008-12-17
Ahhhh... no luck after adding stupid mode

 Disconnecting at Wed Dec 17 10:30:32 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 40 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ


Thanks so much for your valuble time spent on this, think I will just have to carry on using it on my Vista system instead

---

### Post by rampageoberon on 2008-12-17
Hmm, thats odd.

Do call up vodafone and inform them that you are getting the error: The link was terminated because the peer is not responding to echo requests

Sorry can't help further. I'm out of ideas.

---

