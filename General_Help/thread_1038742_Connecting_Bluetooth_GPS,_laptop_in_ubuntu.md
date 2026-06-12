---
title: "Connecting Bluetooth GPS, laptop in ubuntu"
date: 2009-01-13
forum: General Help
---

### Post by shanu4 on 2009-01-13
Hi All,
I am having problem to connect Bluetooth enabled GPS (GPS 10x#87551) to my Bluetooth enabled(built in) laptop. Recently I install Ubuntu in my laptop. I did not installed any software related to Bluetooth. I want to connect my GPS unit to laptop. I could see Bluetooth icon on my task bar, and I selected &#8220;setup new device&#8221;. It is recognizing the GPS unit. Instead of  asking me for the pin number, it is automatically assigning some pin number and failing to connect. 

Through the on line forms I did the following in the terminal.

~$ hcitool dev 
Devices: 
	hci0	00:1F:E2:DE:8B:41 

~$ hcitool scan 
Scanning ... 
	00:05:4F:08:75:51	Garmin GPS 10x #87551 

gksu gedit /etc/bluetooth/rfcomm.conf

Here is my rfcomm.conf file. I updated the below bluetooth address of the device with the hcitool scan of the GPS unit.

# 
# RFCOMM configuration file. 
# 

#rfcomm0 { 
#	# Automatically bind the device at startup 
#	bind no; 
# 
#	# Bluetooth address of the device 
#	device 11:22:33:44:55:66; 
# 
#	# RFCOMM channel for the connection 
#	channel	1; 
# 
#	# Description of the connection 
#	comment "Example Bluetooth device"; 
#}

gksu gedit /etc/bluetooth/hcid.conf 

I came to know that hcid.conf file is missing in my bluetooth directory. I don't know whether this is unique to each and every system. I copied hcid.conf file from on line to my system. But it is not working. 
I don't know what to do at this point. Do I need to install any software. Someone please help me...

Thanks in advance...

---

### Post by eee1000huser on 2009-02-23
Did you ever resolve this problem? i.e. did you find the missing hcid.conf?

---

### Post by HuckleSmothered on 2009-05-09
I have a missing hcid.conf file as well.

My situation:
Trying to setup a Bluetooth USB Dongle to connect to bluetooth devices. This worked in Intrepid, and am just trying to get it setup now in Jaunty. 

/etc/bluetooth contents:
> audio.conf  input.conf  main.conf  network.conf  rfcomm.conf

Ran the command: sudo find / -iname hcid.conf 
Thought this would find the missing file, it found zero results.

hciconfig -a results:
> hci0:	Type: USB
	BD Address: 00:15:83:0B:65:95 ACL MTU: 1017:8 SCO MTU: 64:8
	UP RUNNING 
	RX bytes:348 acl:0 sco:0 events:11 errors:0
	TX bytes:38 acl:0 sco:0 commands:11 errors:0
	Features: 0xff 0xff 0x8d 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: 
	Link mode: SLAVE ACCEPT 
	Name: 'BCM2045B3'
	Class: 0x000000
	Service Classes: Unspecified
	Device Class: Miscellaneous, 
	HCI Ver: 2.0 (0x3) HCI Rev: 0x4027 LMP Ver: 2.0 (0x3) LMP Subver: 0x430e
	Manufacturer: Broadcom Corporation (15)

When I got to Preferences | Bluetooth it only has a General tab. I forget the name of the tab, but it is missing one.

Ideas?

---

### Post by John Hill on 2009-08-11
This thread has gone cold, but it is the right subject so I will post my version of a similar problem here.

I am running jaunty on a Mini9 and have a BT USB dongle, trying to attach a Globalsat BT-359.  I am hoping eventually to have Viking see the GPS for real-time, but I use Viking a ton as is, so I don't want to change to a different app if possible.

Basically, I am new to Ubuntu, but I spent a lot of time reading different threads on this.  They are all a little different, so it is difficult to follow, but I have taken a bunch of steps, and I bet some of those will yield diagnostics clues for the right person.

I use Blueman for a bluetooth utility, because it is the only one that allows a connection between my netbook/dongle and the gps.

From piecing the overall chain of communication together, I take it that Viking looks to gpsd, gpsd needs to be associated with rfcomm0, rfcomm0 needs to assoc. to hci0 and hci0 is the dongle, which is already communicating for me with the gps.

I ran a bunch of the suggested steps and I attach the results herein.

Also, I had no hcid.conf file, either, but I am starting to wonder if that is just managed a different way now.

Hcitoool scan returns nothing, just scans and then returns to normal prompt.

Anyway, here goes.  Any help is greatly appreciated!!!!:)
[COLOR=Indigo]john@john-netbook:~$ hciconfig -a
hci0:    Type: USB
    BD Address: 00:15:83:15:A3:6E ACL MTU: 672:4 SCO MTU: 48:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:99353 acl:144 sco:0 events:10272 errors:0
    TX bytes:57209 acl:280 sco:0 commands:9985 errors:0
    Features: 0xff 0x3e 0x85 0x38 0x18 0x18 0x00 0x00
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'john-netbook-0'
    Class: 0x5a210c
    Service Classes: Networking, Capturing, Object Transfer, Telephony
    Device Class: Computer, Laptop
    HCI Ver: 2.0 (0x3) HCI Rev: 0xc5c LMP Ver: 2.0 (0x3) LMP Subver: 0xc5c
    Manufacturer: Cambridge Silicon Radio (10)

john@john-netbook:~$ hcitool con
Connections:
    < ACL 00:0D:B5:36:D5:8E handle 1 state 1 lm MASTER

john@john-netbook:~$ hcitool dev
Devices:
    hci0    00:15:83:15:A3:6E

sudo gedit /etc/bluetooth/rfcomm.conf
#
# RFCOMM configuration file.
#

rfcomm0 {
    # Automatically bind the device at startup
    bind yes;

    # Bluetooth address of the device
    device 00:15:83:15:A3:6E;

    # RFCOMM channel for the connection
    channel    1;

    # Description of the connection
    comment "Bluetooth Adapter";
}

john@john-netbook:~$ gpsd /dev/rfcomm0
john@john-netbook:~$ 
(Returns nothing)[/COLOR]

---

### Post by HuckleSmothered on 2009-08-12
I had to use the following commands to get a BT dongle working on my previous laptop.
Connect the dongle to the computer just before running these and see if it gets you closer.
> sudo /etc/init.d/bluetooth restart
sudo hciconfig hci0 reset

---

### Post by delhist on 2009-08-13
I could never get gpsd working, so I used iGo 8 through Wine. This might help someone:
sudo ln -s /dev/rfcomm0 /dev/ttyS4 and then choosing COM port 5 in iGo.

Now I've tried to connect my BT-339 with gnome bluetooth applet, and I can't find it in /dev . I think I'll have to switch back to using old good rfcomm.

---

### Post by John Hill on 2009-08-27
Thanks, but no luck so far.  I will continue to investigate and post a solution when I find one.

---

