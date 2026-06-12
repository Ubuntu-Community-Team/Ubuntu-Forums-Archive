---
title: "cups network printing"
date: 2005-07-18
forum: Desktop Environments
---

### Post by rosslaird on 2005-07-18
Cups seems to be one  of the Linux applications that is really arcane. I've switched from Debian Sid to Ubuntu on the second of the machines of my small network (which has 2 machines, the other one being on Ubuntu), and now I can't seem to get network printing working again (it did work before I switched). As I recall, I had a very difficult time setting up remote printing before, and here we go again.

The newly-minted Ubuntu machine has the printer attached to it, and the other machine needs to be able to print across the network.  (Printing locally works fine, by the way).

I have changed cupsd.conf on the machine with the printer to allow acces from the network and specific machine. (Allow, Deny settings seem correct.)
I have turned browsing on in the cups browsing file and in cupsd.conf (with browsing allowed for the network and specific ip of the network machine).

I have tried all kinds of settings in cupsd.conf to get this to work, and I'm stymied.
I have looked through countless threads here and elsewhere.

Part of the difficulty is not knowing where the problem might be: it could be on the cups server (in the configuration somewhere) and it could be on the networked machine. Also, it's really tough to know which printer address is the correct one on the remote machine: I've tried all of these

ipp://192.168.2.101:631/printers/Stylus-Photo-750 (this what the web interface reports on the machine with the printer)

[http://.](http://.).. (same as above)
ipp://hostname:631
ipp://hostname

and so on.

Every time I do this, kcontrol reports that it can't connect to the printer, and "scan" doesn't find it. In fact, I think the kde printer scanning function in kcontrol is correct when it says it can't connect (in other words, I think the problem is in cupsd.conf).

I have two machines connected by a router. The ip of machine with the printer is 192.168.2.101.
The ip of the other machine is 192.168.2.100
My network is 127.0.0.1

Here are some excerpts:

<Location />
Order Deny,Allow
Deny From All
#Allow From All
Allow From 127.0.0.*
Allow From 192.168.2.*
</Location>

## Restrict access to local domain
#Order Deny,Allow
#Deny From All
#Allow From .mydomain.com
#</Location>


#BrowseAddress x.y.z.255
#BrowseAddress x.y.255.255
#BrowseAddress x.255.255.255
#BrowseAddress 255.255.255.255
BrowseAddress @LOCAL
#BrowseAddress @IF(name)
BrowseAddress 127.0.0.1
BrowseAddress 192.168.2.100
#


Any brilliant ideas?

Ross

---

### Post by aggiechemist on 2005-07-18
I think I see an error. At least this is what was stopping me for a couple of days. In your reference to add the printer from the second computer:

[http://127.1.1.1:631/printers/printername](http://127.1.1.1:631/printers/printername)

See the colon after the IP? That should send it to port 631. So you will also need to set you cupd.conf to be sure and scan port 631, I know that is discussed in the forums and Wikis on cups.

Hope that helps, it worked for me at least when I had this problem.

---

### Post by aggiechemist on 2005-07-18
There is a section of the cups config file that ensures that you operate on port 631. I seem to recall that I had to edit that before my print sharing would work. Since it isn't shown in your excert from the config file, perhaps it is a place to check.

---

### Post by rosslaird on 2005-07-18
Yup, I saw that in the conf file -- but the info says it looks at 631 by default. Anyway, I tried to specifically denote 631, and the cups server restarted with an error.

---

### Post by aggiechemist on 2005-07-19
I'm also kinda curious about the browse address section. I don't use that one myself (I just type in the IP address), but perhaps the KDE printer scanning device uses the browse address portion of the script. Have you tried adding both IP addresses to it? Its a bit of a shot in the dark, but could be worth the effort. Also, the network address thing you mention could be a concern. I really doubt your network is 127.0.0.1. That is almost universally a self reference address (kind of like a boomerang). If it broadcast from the maching with the printer, it will come back and let you do things locally. But it might be an issue if somewhere you treat that as the network for the second maching. 

The other idea that occurs is to take off the # before the "allow from all" comment. I think that would leave your printer wide open, might make it easier to connect to it.

Last, I have had problems in the past with firewalls. Do you have any firewall software on the windows machine? I have also seen firewalls in some hardware devices, but that is rare.

Good luck, I can't help but sympathize with you that printer sharing is one of the real shortcomings of Ubuntu.

---

### Post by rosslaird on 2005-07-19
[QUOTE=aggiechemist]Have you tried adding both IP addresses to it? Its a bit of a shot in the dark, but could be worth the effort.[/QUOTE]

Yup, tried that.

[QUOTE=aggiechemist]Also, the network address thing you mention could be a concern. I really doubt your network is 127.0.0.1. That is almost universally a self reference address (kind of like a boomerang). If it broadcast from the maching with the printer, it will come back and let you do things locally. But it might be an issue if somewhere you treat that as the network for the second machine. [/QUOTE]

I wasn't sure about this. I didn't think that 127.0.0.1 sounded right, actually, because I did seem to recall that it's a special type of address. But the in the config file, if I replace "Listen 127.0.0.1:631" with "Listen 192.168.2.100:631" cups restarts with an error. In the Browse settings, cupsd.conf asks for the "broadcast address," which I thought might be 127.0.0.1. Is the broadcast address 255.255.255.255 instead -- or somehing else? From my ifconfig it looks like it's something else, but I don't know enough to be sure:

   inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe4b:5689/64 Scope:Link

Wait -- I just changed Browse to 192.168.2.255, restarted cups,  and I can hear the printer chugging away in the other room! It must be printing out all the test pages I've sent trying to get this to work.

> The other idea that occurs is to take off the # before the "allow from all" comment. I think that would leave your printer wide open, might make it easier to connect to it.

I did try that, but without the browse settings it does not work.

> Last, I have had problems in the past with firewalls. Do you have any firewall software on the windows machine? I have also seen firewalls in some hardware devices, but that is rare.

Nope, not firewall.

Thanks very much for all the help. Next time I do a system upgrade, I'll remember to backup the cupsd.conf file first (I did backup all the home directories, but I tend to forget about other system files that I've tweaked).

Thanks again.

Ross

---

### Post by tomchuk on 2005-07-19
Here is every uncommented line from cupsd.conf from my Sarge server:
```

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
Port 631

BrowseAllow 127.0.0.1
BrowseAllow @LOCAL
BrowseDeny All

<Location />
Order Deny,Allow
Deny From All
Allow From @LOCAL
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From @LOCAL
</Location>

```

And the printers.conf entries on my laptop for the two network printers on the Sarge server:
```

<Printer DeskJet_932c>
Info HP DeskJet 932c Color Inkjet Printer
Location Home Network
DeviceURI ipp://kuro.tomchuk/printers/DeskJet_932c
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
<DefaultPrinter LaserJet_1012>
Info HP LaserJet 1012 B&W Laser Printer
Location Home Network
DeviceURI ipp://kuro.tomchuk/printers/LaserJet_1012
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

```

---

### Post by yetanothersteve on 2005-07-22
I have Ubuntu Hoary 5.04 with a HP LaserJet 5p attached. My wife's machine is running Suse 9.2.

These are the changes I made to cupsd.conf on the Ubuntu (192.168.11.2) machine so the Suse machine could find the printer from the YAST config tool and then print.

```

Uncommented and updated:
ServerName 192.168.11.2
ServerAdmin test@example.org

Added:
Listen 192.168.11.2:631
BrowseAddress @IF(eth0)
BrowseAllow 192.168.11.*

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.11.*
</Location>

``` 

The cups web site helped a little, but it was mostly going through the cupsd.conf line by line.

---

