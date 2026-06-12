---
title: "Yet another bluetooth thread"
date: 2005-12-17
forum: General Help
---

### Post by iam10ninjas on 2005-12-17
Okay, so I recently switched from GNOME to KDE and decided to try out the bluetooth capabilities of kdebluetooth. Setting up is fine. kbluetooth detects my bluetooth dongle and I can attempt to connect to my phone (a samsung e720).

Now, whenever I try to pair the phone to the computer, my phone asks for a pin. No worries so I pick a 4 digit number, then a dialogue box pops up asking for the pin. The problem is, before I get a chance to enter the pin on my computer, my phone has already requested the pin again.

HELP!!!

Here is my hcid.conf file.

```
#
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.7 2004/12/13 14:16:03 holtmann Exp $
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
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/lib/kdebluetooth/kbluepin;

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
	class 0xff0408;

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

```

I am *this* close to getting this to work. I really hate to say it, but XP handled this much better. Mind you, the software I got with my dongle *was* written specifically for windows, so I'm not surprised.

Any ideas or suggestions would be greatly appreciated.

P.S. I think I might prefer KDE to GNOME. It feels better for some reason.

---

### Post by fannymites on 2005-12-17
Maybe try changing the pin helper to 
pin_helper /usr/bin/bluepin;

---

### Post by iam10ninjas on 2005-12-17
[QUOTE=fannymites]Maybe try changing the pin helper to 
pin_helper /usr/bin/bluepin;[/QUOTE]
The same thing happens. I type the pin in on my phone, the dialogue box pops up but the phone has already requested the pin again.

Its really frustrating. I wonder if I can set a kind of timeout on my phone to wait 15 seconds or something before asking for the pin again...

---

### Post by fannymites on 2005-12-17
You could change the security manager option to auto instead of user to see if that helps.
It won't ask for the pin anymore but it will still ask if you want to accept a file or not.

---

### Post by iam10ninjas on 2005-12-17
[QUOTE=fannymites]You could change the security manager option to auto instead of user to see if that helps.
It won't ask for the pin anymore but it will still ask if you want to accept a file or not.[/QUOTE]
Makes not difference. I still get the "cannot connect" dialogue box. This is slightly frustrating.

Ho hum. I'm sure the developers will implement a better way to use bluetooth in upcoming releases. I just wish my phone had IrDA. Or I could afford a cable :-)

Thanks for your help, fannymites.

---

### Post by fannymites on 2005-12-17
I've had very mixed success with bluetooth on linux.  Sometimes it works and sometimes it doesn't.

One more thing you might want to try.  I've read in quite a lot of forum threads 
that pairing problems have been solved for a lot of people by changing the Local device class to ```
class 0x100100;
```

---

### Post by iam10ninjas on 2005-12-17
[QUOTE=fannymites]I've had very mixed success with bluetooth on linux.  Sometimes it works and sometimes it doesn't.

One more thing you might want to try.  I've read in quite a lot of forum threads 
that pairing problems have been solved for a lot of people by changing the Local device class to ```
class 0x100100;
```[/QUOTE]


YOU DA MAN! I have managed to cobble together a set of parameters in hcid.conf that work!

here is its:
```

#
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.7 2004/12/13 14:16:03 holtmann Exp $
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
	pin_helper /usr/lib/kdebluetooth/kbluepin;
	#pin_helper /usr/bin/bluepin;
	#pin_helper /usr/lib/blues-pin;

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
	class 0x100100;

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
```

Hopefully anyone searching for bluetooth help will find this and it might work for them also.

Once again, thank you fannymites. I really appreciate this. I now have one less reason to go back to windows.

---

### Post by fannymites on 2005-12-17
Glad to be of some help.
Just out of interest, could you post back and let me know if it is still working after a couple of reboots.  I've had it constantly stop and start working between boots even though I never change anything.  I seem to have solved it now but if you do have that problem let me know.

---

