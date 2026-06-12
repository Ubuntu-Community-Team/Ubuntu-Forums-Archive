---
title: "Not able to print with JetDirect"
date: 2006-01-15
forum: General Help
---

### Post by fsnelting on 2006-01-15
Hello!

I recently switched from an ibook to using Ubuntu on a VAIO S5M laptop and most of the experience has been enjoyable -- no regrets whatsoever.

A few things I could not resolve, and not being able to print is the one that hurts the most. 

I have got a HP 6MP printer connected through a JetDirect EX PLUS box, and than to a hub. I can't connect to the printer directly, because it does not have Ethernet nor USB.

I printed a test page from JetDirect on my HP laserprinter 6MP and it gives me 192.0.0.192 as the IP address (which is the default address according to the HP JetDirect manual).

If I use system > applications > printers with this address, port 9100, HP JetDirect, and select the correct printer driver, the printer is addded to the list but does not seem to connect to the printer or send any data: 

[I]Printer State: processing, accepting jobs. 
"Unable to connect to IPP host: Connection timed out"[/I]

I've tried any other combination I could think of, but no luck.

I'm not familiar with network setups but guessed that the default IP might be the problem, and followed this post: [http://www.ubuntuforums.org/showthread.php...]("http://www.ubuntuforums.org/showthread.php?t=88639&page=2") I downloaded the JetDirect webadmin software, but on install it gave me:

* "The computer system does not meet HP Web Jetadmin 8.0 requirements"*

I don't have a Windows machine around to try and configure the printer from (do have a Mac, but no software is provided for OSX by HP) and I'm getting stuck.

I would much appreciate your help, or hints to specific page(s) to look at for solutions. I've tried each tip I could find here on this forum, but might get the order wrong or something.

Thanks a lot, 

Femke

---

### Post by JimS on 2006-01-15
...
1.  If you are still under warrentee, call HP.
2.  Check for jetdirect forums on google, etc.

[COLOR="RoyalBlue"]JimS[/COLOR]
Prostate Cancer Aware
...

---

### Post by fsnelting on 2006-01-15
Thanks Jim,

The JetDirect is more than five years old so I'm afraid that won't help. I have tried my best on HP troubleshooting sites and forums and tried as many tips + tricks as I could find but nothing helped. I'm new to networkprinting admin (Mac on various systems has always been plug and play) so I am really drowning here...

Femke

---

### Post by MJSOnline on 2006-01-15
I too had the same probem using my HP LaserJet 3320 MFD.

I went to System > Admin > Printers > Add Printer > Clicked on JetDirect > Added the IP address of my HP printer via the JetDirect box > Selected my model of printer > Appiled the recommend printer driver, Postscript > And hit Apply.

Printed a test page and every thing works ok.

Power off the printer for a min, on again. Then rebbot your pc.

Worked for me.
Matthew

---

### Post by fsnelting on 2006-01-15
Thanks Matthew, 

This is the way it should work ;-) but it obviously doesn't. I'm still looking all over... and getting desperate...

The HP [help page]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=115&prodSeriesId=27321&prodTypeId=18972&prodSeriesId=27321&objectID=bpj02836#N10205") (I understand only half of it :-() tell me that "In most networks, it may be necessary to use a Route Add command to resolve this address on the computer" so that is what I am doing now...

Femke

---

### Post by MJSOnline on 2006-01-15
> **fsnelting]Thanks Matthew, 

This is the way it should work  said:**
> help page[/URL] (I understand only half of it :-() tell me that "In most networks, it may be necessary to use a Route Add command to resolve this address on the computer" so that is what I am doing now...

Femke
This may sound odd but you have checked the JetDirect ip address by pressing and resetting the JetDirect box at the rear of the printer?  I ask as it took me over 3hours to figure that out.

Matthew

---

### Post by fsnelting on 2006-01-15
> This may sound odd but you have checked the JetDirect ip address by pressing and resetting the JetDirect box at the rear of the printer?

Yes I did... on the external JetDirect box it is a green button on the top that reads 'test'. Hard to miss... No reset button though. (have unplugged it to try whether that made any difference... not)

The 'route add' command gives me all kinds of options and "bogus netmask"... I clearly have no idea what I am doing. hmm.

Femke

---

### Post by MJSOnline on 2006-01-15
[QUOTE=fsnelting]Yes I did... on the external JetDirect box it is a green button on the top that reads 'test'. Hard to miss... No reset button though. (have unplugged it to try whether that made any difference... not)

The 'route add' command gives me all kinds of options and "bogus netmask"... I clearly have no idea what I am doing. hmm.

Femke[/QUOTE]

Have you tried to Auto Config package on the CD that cane with the printer?

Or this? [http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=uk&prodTypeId=18972&prodSeriesId=66359&taskId=135]("http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=uk&prodTypeId=18972&prodSeriesId=66359&taskId=135")
As that is want I did for mine.
Matthew

---

### Post by Madstone on 2006-01-15
[I]Printer State: processing, accepting jobs. 
"Unable to connect to IPP host: Connection timed out"[/I]

It seems to me that you are having a networking issue.  The 192.0.0.192 is the default address the JetDirect uses when either of the following conditions exist

A)  No DHCP server is available on your network 
B)  A proper static IP has not been configured for the JetDirect

How does your laptop any other PC, etc get there IP addresses now?  Do you have a router or PC that provides DHCP somewhere on your network?

If you do have a DHCP server somewhere on your network that provides the IP addresses to your laptop then do this on the JetDirect box

1) On the back of the JetDirect reset all the buttons to the default position
Auto,100MB,Half Duplex (Note the positions first in case you need to go back)
2) Unplug the JetDirect
3) Press and hold the Test button
4) While holding down the Test button plug in the power
5) Keep holding the test button for about 10 seconds and release

After 30 seconds or so if a DHCP server is available the JetDirect should be able to get an IP address from the server and you should see the new address when you print a test page.  Whatever the address is you should be able to open firefox and point to that IP and manage the JetDirect with a web interface.  For example 192.168.0.5.  You don't need the JetAdmin software

---

### Post by fsnelting on 2006-01-17
> It seems to me that you are having a networking issue. The 192.0.0.192 is the default address the JetDirect uses when either of the following conditions exist

A) No DHCP server is available on your network
B) A proper static IP has not been configured for the JetDirect

How does your laptop any other PC, etc get there IP addresses now? Do you have a router or PC that provides DHCP somewhere on your network?

Thanks for confirming that issue, Madstone. 

My setup is as follows: Laptop => 3Com OfficeConnect Hub => Jetdirect EX Plus => HP Laserjet 6MP
There are currently no other computers connected to this network, but I need the printserver + hub to convert the printer plug to Ethernet.

I have reset the JetDirect and now it gives me the IP address 0.0.0.0

From the HP manual:  
"*Some print servers may show the TCP/IP address as 0.0.0.0 if a LAN cable is not connected, or if the print server cannot detect the network connection due to a bad cable, hub, or LAN link speed configuration problem.*"

So... I am trying to figure out what is wrong with the network setup now; the problem is clearly there, and NOT with Ubuntu. I'll report back when I have figured it out.

Thanks again, and sorry to have bothered this forum with stuff that is external.

Femke

---

### Post by fsnelting on 2006-03-29
Ok, here's an update on my printing problem:

I finally gave up on configuring the HP Jet-Direct network setup and ordered a "keyspan mini port replicator (UPR-112)". It came in today and guess what... I am finally printing!

With the help of this device I changed my old printer cable into a usb plug. The driver for the replicator is included in the Linux kernel, so no installation necessary there. I needed to restart my computer with the replicator connected for it to recognise the printer (CAUTION: unplug the connector when shutting down; I needed to unplug the battery to make my laptop shut down in the end :-(), but Cups than miraculously recognised my printer and installing was just one click. 

Thanks for your help... I am so glad this is finally resolved!

Femke

---

