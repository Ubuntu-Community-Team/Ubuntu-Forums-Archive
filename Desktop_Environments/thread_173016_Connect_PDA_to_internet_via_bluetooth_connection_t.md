---
title: "Connect PDA to internet via bluetooth connection to Laptop"
date: 2006-05-09
forum: Desktop Environments
---

### Post by MarkHn on 2006-05-09
Is it possible for a Bluetooth enabled Pocket PC to access the internet via a Laptop with a bluetooth dongle connected to the internet. 

The laptop is an AMD64 with 64bit Dapper. It is connected to the internet with broadband using its built in network card. 
I have a USB Bluetooth dongle ond the laptop and Both the laptop and the Pocket PC can see each other.

Can the laptop be configured to allow the pocket pc to access the internet over its bluetooth connection.

Thanks

---

### Post by MarkHn on 2006-05-11
Now the bluetooth manager in Gnome crashes each time I try to run it. 
So I haven't even managed to transfer files using bluetooth, nevermind get an internet connection working over it.](*,) 

Any ideas or similar problems :confused:

---

### Post by MiniJames on 2006-05-18
Well, I would love to be able to do this. But it took an hour to configure serial ports in Windows to achive this functionality so I hate to think what it would take to  make this work in Ubuntu.

For the record, im now completely switched to Dapper :)

---

### Post by tigrux on 2006-05-18
[QUOTE=MarkHn]Is it possible for a Bluetooth enabled Pocket PC to access the internet via a Laptop with a bluetooth dongle connected to the internet. 

The laptop is an AMD64 with 64bit Dapper. It is connected to the internet with broadband using its built in network card. 
I have a USB Bluetooth dongle ond the laptop and Both the laptop and the Pocket PC can see each other.

Can the laptop be configured to allow the pocket pc to access the internet over its bluetooth connection.

Thanks[/QUOTE]

Follow this:

[http://www.newt.com/debian/treo650.html](http://www.newt.com/debian/treo650.html)

It works in my Dell E1505 and my Treo 650.

---

### Post by MiniJames on 2006-05-19
Correct me if i'm wrong -- but that is for palm based PDAs? Mine is an HP iPAQ 1940 so I cant get very far with this tutorial. :(

EDIT

Thanks for the suggestion anyways :) If anyone knows about connecting iPAQs via a linux pc to the internet over bluetooth, we'd love to hear from you.

---

### Post by MiniJames on 2006-05-19
**UPDATE:**

I had a dig around the bluez-utils settings file and found this interesting section:

```
james@jameslaptop:~$ sudo gedit /etc/default/bluez-utils
```

```

############ PAND
#
# Run pand -- ethernet: creates new network interfaces bnep<N>
# that can be configured in /etc/network/interfaces
# set to 1 for enabled, 0 for disabled
PAND_ENABLED=0

# Arguments to pand
# Read the PAN howto for ways to set this up
# http://bluez.sourceforge.net/contrib/HOWTO-PAN
PAND_OPTIONS=""

# example pand lines
#
# Act as the controller of an ad-hoc network
# PAND_OPTIONS="--listen --role GN"
#
# Act as a network access point: routes to other networks
# PAND_OPTIONS="--listen --role NAP"
#
# Act as a client of an ad-hoc controller with number 00:11:22:33:44:55
# PAND_OPTIONS="--role PANU --connect 00:11:22:33:44:55"
#
# Connect to any nearby network controller (access point or ad-hoc)
# PAND_OPTIONS="--role PANU --search"

```

Looks like this could be configured to achieve the functionality we are after. Ill keep looking.

**UPDATE:**

from: [COLOR="Red"]http://bluez.sourceforge.net/contrib/HOWTO-PAN[/COLOR]

_This is what we want to setup:_

- Network Access Point (NAP):
  Acts as proxy, router or bridge between an existing network infrastructure
  (typically LAN) and (up to 7 active) wireless clients (PANUs).
```

                   +====================+
                   | LAN Infrastructure |
                   +====================+
                             |
                             |
                             |
                        +---------+
                        |   NAP   |
                        +---------+
                       /     |     \
                      /      |      \
                     /       |       \
                    /        |        \
                   /         |         \
                  /          |          \
              +------+    +------+    +------+
              | PANU |    | PANU |    | PANU |
              +------+    +------+    +------+

```

---

### Post by MiniJames on 2006-05-30
Anyone made any progress? ](*,)

---

### Post by MarkHn on 2006-05-31
It is fairly simple to get working using WindowsXP, but that's mot much good here. At least it proves it can be done, so it should also be possible using Ubuntu.

---

### Post by info2 on 2006-06-02
I currently also try to get my HP hx2110 PDA connected at least to my laptop (and later hopefully to the internet).

I followed the document from [http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN)
but i am unable to create the device ( bnep0 ).
Running the daemons hcid and pand as non-daemonized don't show any errors but hcid, telling me that it was not able to communicate with dbus due some restrictions.
But i think to get a network, hcid don't need to communicate with gnome-apps.


Building a NAP (Network AccessPoint) in Windows was nearly easy but i prefer not to boot that OS but for gaming.

I hope we can manage it :)

I managed it to connect to the laptop and surfing the local webserver. I'll write how o'Ve done that in a minute :)

---

### Post by info2 on 2006-06-02
This is how i connected the PDA to the Laptop and surfed the local webserver:

I've installed the bluez-utils and bluez-pin using synaptic. 

Following the Howto from [http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN) I've edited /etc/default/bluez-utils:

----
############ PAND
# set to 1 for enabled, 0 for disabled
PAND_ENABLED=1

# Arguments to pand
PAND_OPTIONS="--listen --role NAP"
----

I left the other lines as they've been.
To have an Ad-Hoc Network, you just need to change the role from NAP to GN.

I've restarted my Laptop some times, but i think a 
"sudo /etc/init.d/bluez-utils restart"
may have the same effect.

Within my bluetooth-utilities on the PDA, I can search for services on devices and found my laptop serving a "Network Access Point".
I created a connection and activated it.

Now i've tooked a look to the interfaces using "ifconfig -a" and saw that there was an unconfigured device "bnep0".
I gave that device an IP within the same range as my PDA is configured to.
(In my case : PDA=10.0.0.10, Laptop=10.0.0.1)

Than i started the InternetExplorer (hell, is there a firefox, mozilla or whatever available for PDA? :)  ), entered the IP of my Laptop (that is running apache) and it just works.



I hope you can manage it, too.


Using firestarter to share the Internet-Connection to the bnep0 -  adapter is working well :)

---

