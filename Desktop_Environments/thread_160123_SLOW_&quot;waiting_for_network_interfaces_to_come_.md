---
title: "SLOW &quot;waiting for network interfaces to come up&quot;"
date: 2006-04-14
forum: Desktop Environments
---

### Post by stando007 on 2006-04-14
Hi!
I have Ubuntu on my HP nx6110 notebook and boot is very slow - when I see the message "waiting for network interfaces to come up..." it hangs on about 1 minute and then continue booting.

How could I make it faster? Maybe some setting of network is wrong? btw, I am almost newbie in linux systems....

---

### Post by johnnymac on 2006-04-14
it sounds like it's slow to get a dhcp address for whatever you use for a dhcp server.  Are you set-up to pull addresses from a route or dhcp-server?  Or, do you connect directly to your modem from your provider?

---

### Post by Ubuntuud on 2006-04-14
I get that when I am not in the neighbourhood of a wireless (or wired) network. I think DHCP is searching for a network that isn't there.

---

### Post by joelito on 2006-04-14
I'm using a similar laptop (The model with the Broadcom wireless)

What I did after getting the ndiswrapper drivers to work was installing gtk-wifi ( [http://www.ubuntuforums.org/forumdisplay.php?f=74](http://www.ubuntuforums.org/forumdisplay.php?f=74) ) and using that to configure the wireless connection...

I disabled the NIC after removing the cable to prevent the same problem with boot times...

BTW...

Make sure the blue light is blinking before trying to connect to the wireless network or else will probably not work

---

### Post by stando007 on 2006-04-14
[QUOTE=joelito]I'm using a similar laptop (The model with the Broadcom wireless)

What I did after getting the ndiswrapper drivers to work was installing gtk-wifi ( [http://www.ubuntuforums.org/forumdisplay.php?f=74](http://www.ubuntuforums.org/forumdisplay.php?f=74) ) and using that to configure the wireless connection...

I disabled the NIC after removing the cable to prevent the same problem with boot times...

BTW...

Make sure the blue light is blinking before trying to connect to the wireless network or else will probably not work[/QUOTE]

My wifi works OK since I first installed ubuntu. But I have the problem with slow boot. I tried to disable Ethernet Card, (I am using wifi) and configured wifi card not to get adress from DHCP, but static IP.
The problem with slow boo still remains :(

---

### Post by joelito on 2006-04-14
I will post my /etc/network/interfaces file so you can use as a reference to manualy setup the network

use the command [ gksudo gedit  ] by pressing alt+f2 

paste this and save it as your /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface


```

restart the networking service from the terminal with the command [ sudo /etc/init.d/networking restart ]

Then the screen from system -> administration -> networking dialog shoud look like the screenshot i'm posting

The program I mentioned in my original post(gtk-wifi) will be the one to use to connect to the diferent networks (Screenshot added)

---

### Post by stando007 on 2006-04-14
[QUOTE=joelito]I will post my /etc/network/interfaces file so you can use as a reference to manualy setup the network

use the command [ gksudo gedit  ] by pressing alt+f2 

paste this and save it as your /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface


```

restart the networking service from the terminal with the command [ sudo /etc/init.d/networking restart ]

Then the screen from system -> administration -> networking dialog shoud look like the screenshot i'm posting

The program I mentioned in my original post(gtk-wifi) will be the one to use to connect to the diferent networks[/QUOTE]

OK, now the boot is fast, but when "waiting for n.i. to come up" comes, there is message failed.
But now if I want to connect to my network AP, I have to run gtkwifi. Is it possible to make it automatic?

Another thing I find out in linux is that sometimes if I enter URL adress of some site, I have to wait 10-30sec until there is an response (it looks like the problem contacting DNS with message "Looking up www.someadress.com"). When the page loads, then everything is ok, it is fast when I am browsing it, but when In windows this problem never occur. 
But this problems happens only sometimes. Sometimes it seems to be ok. Isn't it possible that linux is trying contacting some other resources instead of contacting DNS first?

---

### Post by joelito on 2006-04-14
Did you added the gtkwifi applet to the panel?

appears as Wireless Connection Manager in the Add to panel window

And I get the "failed" message when loading the ntpdate service. I removed the file /etc/rcS.d/S51ntpdate to disable it... (That service just syncronizes the clock with some server)

You could also add the main networks you use to the list of prefered networks in gtkwifi preferences

---

### Post by stando007 on 2006-04-15
[QUOTE=joelito]Did you added the gtkwifi applet to the panel?

appears as Wireless Connection Manager in the Add to panel window

And I get the "failed" message when loading the ntpdate service. I removed the file /etc/rcS.d/S51ntpdate to disable it... (That service just syncronizes the clock with some server)

You could also add the main networks you use to the list of prefered networks in gtkwifi preferences[/QUOTE]

How do I add gtkwifi to the panel?

I am wondering what everything is possible to do with linux... But I feel lost in the huge amount of settings and modules.. :(

---

### Post by joelito on 2006-04-15
just right click the panel, then click "add to panel" you should se a window with a list of applet icons divided by sections, the gtkwifi applet(if installed properly) appears in the section "internet." Just select it and off you go...

By the way I'm assuming that you are using the standard Ubuntu installation(With the gnome desktop)

As for your comment on being able to do anything but feeling lost in the sea of settings and modules... I can tell you that this sea is better to navigate than earlier distros like RH 7.x and old Corel... Of course we're both lucky for not navigating the Gentoo and Slackware oceans :)

---

