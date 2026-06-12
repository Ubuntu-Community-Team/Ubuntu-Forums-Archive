---
title: "Bluetooth issues with pin"
date: 2006-02-09
forum: Desktop Environments
---

### Post by Garyu on 2006-02-09
I found this thread on connecting to mobile phones and using a bluetooth headset for Skype and similar applications:
[http://www.ubuntuforums.org/showthread.php?t=75978&highlight=kbluetoothd+pin](http://www.ubuntuforums.org/showthread.php?t=75978&highlight=kbluetoothd+pin)

The only problem is, it doesn't work for me, even though it seems to work for other people. And when posting my problem there, I didn't get any response, so I'm trying a new thread and a different forum and hope my luck changes. 

Everything installs easily enough. The only thing is that the HOWTO refers to a file named "link_key" and it is really named pin, but that is a simple rename/link or simply point the kbluetoothd config to the "pin" file instead.

So when I left-click the kbluetoothd icon in the tray Konqueror fires up and lists my bluetooth devices: "Dan-Erik" (my SonyEricsson Z1010 mobile phone) and "Jabra BT110" (my bluetooth headset). 

1) Mobile phone. Clicking on the mobile icon in Konqueror brings up a long list of services available. During this stage my mobile signals that someone is communicating with it, so I guess kbluetoothd fetches this service list from the mobile phone. I want to transfer files, so I click "OBEX File transfer". This brings up a dialogue in my mobile asking if I want to add "Minotaur" (my computer name) and I choose yes and the mobile asks me for a PIN-code. So I enter the code that I stated in my "/etc/bluetooth/pin" but I get the reply "wrong password", so I try entering "0000" instead and "1234", but none of those work. So connection is terminated on account of bad password.

2) Jabra BT-110 headset. Left-click in Konqueror on the Jabra icon simply brings up a message "Pairing not allowed". The headset IS in pairing mode, I checked and double-checked this. 

Any suggestions anyone?

BTW, I tried sending files from the Z1010 mobile phone to the computer with bluetooth, and nothing happened. Seems like kbluetoothd isn't accepting incoming traffic. 

Oh and yes, I have tried "/etc/init.d/bluez-utils restart" and I have restarted kbluetoothd a number of times. I have not rebooted, but that should not be necessary should it?

---

### Post by GeneralZod on 2006-02-09
No, rebooting should absolutely not be necessary ;)

I didn't see any mention of your editing /etc/hcid.conf to contain the correct pin_helper.  Open up that file, and replace the pin_helper line with

```

pin_helper /usr/lib/kdebluetooth/kbluepin;

```

and restart bluez-utils.  Make sure that the kbluepin file is indeed installed on your system.

---

### Post by Garyu on 2006-02-09
[QUOTE=GeneralZod]No, rebooting should absolutely not be necessary ;)
I didn't see any mention of your editing /etc/hcid.conf to contain the correct pin_helper.  Open up that file, and replace the pin_helper line with
**pin_helper /usr/lib/kdebluetooth/kbluepin;**
and restart bluez-utils.  Make sure that the kbluepin file is indeed installed on your system.[/QUOTE]

I tried both "usr/lib/kdebluetooth/kbluepin" AND "/usr/bin/bluez-pin" AND "/usr/bin/bluepin" but none of those work. Thank you for trying though. =)
EDIT: oh, and yes, I checked that they were installed.

---

### Post by MarioFrick on 2006-02-11
[QUOTE=Garyu]I tried both "usr/lib/kdebluetooth/kbluepin" AND "/usr/bin/bluez-pin" AND "/usr/bin/bluepin" but none of those work. Thank you for trying though. =)
EDIT: oh, and yes, I checked that they were installed.[/QUOTE]
I have exactly the same problem, both with the Sony Ericsson Z1010 and my Siemens S55... and the strange fact is that it worked perfectly time ago, then I didn't used this service for a while, and now I have your same problem, and I really don't understand how to solve it! Ubuntu never asked me for a PIN code, only the phone does, and then disconnects for timeout...:(

---

### Post by MarioFrick on 2006-02-11
Of course on /etc/bluetooth/pin I have 1234, but it never accepts it... :(

---

### Post by Garyu on 2006-02-11
Problem partly solved. =)

[http://www.ubuntuforums.org/showthre...3&page=1&pp=20](http://www.ubuntuforums.org/showthre...3&page=1&pp=20)

I found this thread about using gnome bluetooth tools. They work flawlessly, even if they are slower than the KDE things.

Using my Jabra BT110 headset still does not work though. :(

---

### Post by Garyu on 2006-02-11
gah... I'm going crazy... or rampage... or whatever...

I finally got things to work with gnome-obex-server instead of kbluetoothd... So I had lots of pictures I wanted to transfer from the phone. But you can only send one file at a time with gnome-obex-server. So when the popup asked "Always accept files from this (phone)" I answered yes to speed up the process. And after I did that nothing works any more... 

How do I remove this option? The only thing I get when I click on the gnome-bluetooth icon in the tray is "about" and "quit", and there isn't much helpt from entering "gnome-obex-server --help" in the terminal either... :(

EDIT: oh, I only had to restart the thing. sometimes it's good to have applications with amnesia... :)

---

### Post by daller on 2006-06-04
[QUOTE=GeneralZod]No, rebooting should absolutely not be necessary ;)

I didn't see any mention of your editing /etc/hcid.conf to contain the correct pin_helper.  Open up that file, and replace the pin_helper line with

```

pin_helper /usr/lib/kdebluetooth/kbluepin;

```

and restart bluez-utils.  Make sure that the kbluepin file is indeed installed on your system.[/QUOTE]

The file "/etc/hcid.conf" does not exist on my pc! - Is that a problem?

...I also have the "password-problem"!!!

---

### Post by daller on 2006-06-04
[QUOTE=Garyu]Problem partly solved. =)

[http://www.ubuntuforums.org/showthre...3&page=1&pp=20](http://www.ubuntuforums.org/showthre...3&page=1&pp=20)

I found this thread about using gnome bluetooth tools. They work flawlessly, even if they are slower than the KDE things.

Using my Jabra BT110 headset still does not work though. :([/QUOTE]

Can you please post the link in full length?

---

### Post by plurk on 2006-06-06
I've been having the same problem for about a day now.   I finally fixed it by changing the following the /etc/bluetooth/hcid.conf file:
security user;
pin_helper /usr/bin/bluez-pin;

Then restart the bluetooth services (/etc/initd.d/bluez-utils)

I'm also using the packages gnome-bluetooth and gnome-phone-manager from the universal repository.  Hope this helps.

---

### Post by mwheatland on 2006-06-21
[QUOTE=Garyu]I found this thread on connecting to mobile phones and using a bluetooth headset for Skype and similar applications:
[http://www.ubuntuforums.org/showthread.php?t=75978&highlight=kbluetoothd+pin](http://www.ubuntuforums.org/showthread.php?t=75978&highlight=kbluetoothd+pin)

The only problem is, it doesn't work for me, even though it seems to work for other people. And when posting my problem there, I didn't get any response, so I'm trying a new thread and a different forum and hope my luck changes. 

Everything installs easily enough. The only thing is that the HOWTO refers to a file named "link_key" and it is really named pin, but that is a simple rename/link or simply point the kbluetoothd config to the "pin" file instead.

So when I left-click the kbluetoothd icon in the tray Konqueror fires up and lists my bluetooth devices: "Dan-Erik" (my SonyEricsson Z1010 mobile phone) and "Jabra BT110" (my bluetooth headset). 

1) Mobile phone. Clicking on the mobile icon in Konqueror brings up a long list of services available. During this stage my mobile signals that someone is communicating with it, so I guess kbluetoothd fetches this service list from the mobile phone. I want to transfer files, so I click "OBEX File transfer". This brings up a dialogue in my mobile asking if I want to add "Minotaur" (my computer name) and I choose yes and the mobile asks me for a PIN-code. So I enter the code that I stated in my "/etc/bluetooth/pin" but I get the reply "wrong password", so I try entering "0000" instead and "1234", but none of those work. So connection is terminated on account of bad password.

2) Jabra BT-110 headset. Left-click in Konqueror on the Jabra icon simply brings up a message "Pairing not allowed". The headset IS in pairing mode, I checked and double-checked this. 

Any suggestions anyone?

BTW, I tried sending files from the Z1010 mobile phone to the computer with bluetooth, and nothing happened. Seems like kbluetoothd isn't accepting incoming traffic. 

Oh and yes, I have tried "/etc/init.d/bluez-utils restart" and I have restarted kbluetoothd a number of times. I have not rebooted, but that should not be necessary should it?[/QUOTE]


Hi Garyu,
I have had the same problem, and spent all night trying to fix it.
Finally I installed the Gnome drivers and when I restarted the next day I had an error message, but not your ordinary error message. It stated that I had the wrong device class set up in my hcid.conf file. Very handy to know!
After all this changing of the bluetooth pin helper and such, all I needed to do was change the device class.

Some people have replied to this post saying that they have had to buy a new bluetooth adaper / dongle, but I think this may have been their problem too.
Below is my new hcid.conf file so that you can see what I have changed:

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	#pin_helper /usr/bin/bluez-pin;
	#pin_helper /usr/bin/bluepin
	[COLOR="Red"]pin_helper /usr/lib/kdebluetooth/kbluepin[/COLOR]

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class [COLOR="Red"]0x120104;[/COLOR]

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption (Security Mode 3)
	#auth enable;
	#encrypt enable;
}



I hope this helps those of you out there that are getting the HID conrol problem / issue. Just change the bluetooth pin helper and the device class. Possible install the gnome bluetooth packages also.


By the way I am using Kubuntu clean install.
Thanks for all your help everyone. 

Michael Wheatland
michael at wheatland dot com dot au
+61 425 831 212
In Australia
Long live KDE and Ubuntu.

---

### Post by srf21c on 2006-09-23
=> Plurk:

> I've been having the same problem for about a day now. I finally fixed it by changing the following the /etc/bluetooth/hcid.conf file:
security user;
pin_helper /usr/bin/bluez-pin;

Then restart the bluetooth services (/etc/initd.d/bluez-utils)

Fuggin' SWEET!!...that solved the bluethooth PIN problem 'twixt my Moto V3 RAZR and Dapper workstation, thanks.  For those interested, I'm using an all gnome setup on my desktop, the phone is a GSM RAZR, and not sure about the  chipset for my USB bluetooth dongle.  It's just a cheapie I got off of ebay for a few bucks.

---

### Post by sphorbis on 2006-10-08
I have a Motorola h500 earpiece, but it won't connect to kbluetoothd. It says its not paired but its never asked me to pair it. Any suggestions?

---

### Post by thevilish on 2006-10-24
Hi!
I think I have a solution for PIN issue.

I think any program asking us for entering PIN don't look to /etc/bluetooth/pin file. We can set PIN in this way:


First of all: [FONT="Courier New"]sudo hcitool cc MA:CA:DD:RE:SS:00[/FONT] - if nothing appears -> OK
Second of all: [FONT="Courier New"]sudo hcitool auth MA:CA:DD:RE:SS:00[/FONT]

I have bluez-passkey-gnome installed and then bluetooth icon appears with baloontip - click on it - enter pin - repeat pin on your mobile and... voila!

IT WORKS! Now you can do what you want with your mobile ;) (MultiSync works, bluelink too)

I'm sorry for my english (I was sleepy at "tenses" lesson).

---

