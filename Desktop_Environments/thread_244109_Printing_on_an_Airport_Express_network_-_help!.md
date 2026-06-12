---
title: "Printing on an Airport Express network - help!"
date: 2006-08-25
forum: Desktop Environments
---

### Post by greggfathead on 2006-08-25
Hello:

My home wi-fi network is all Apple hardware based - an Airport Extreme base station and four Airport Express repeaters connected to various stereos and/or printers throughout my house.  I did this so that I could stream iTunes to any stereo in the house from any computer, and so far it works perfectly.  No issues conecting my Ubuntu laptop to the Airport network, it's working perfectly!

However - my Ubuntu laptop cannot print to the printers at all, the printers are USB-connected to the Airport Express access points. The Macs access the printers via Bonjour, but I cannot figure out how to get the Ubuntu machine to print to these printers!   Can someone help me with this?

Note: the Airport Express access points get their IP's dynamically from the router, however I could set these IP's to be static if need be.  Maybe that will solve the issue?

Does anyone know how I can set up my Ubuntu box to see those printers?  I've tried using my Unix Printer (LPD) setup and naming the Apple hardware to which the printer is attached, but no such luck - no printing magick happens.  

Any ideas would be greatly appreciated - take care, and have a great day!

---

### Post by DMHamm on 2006-11-01
Did you ever figure this out? I have a similar setup, except I only have one Airport Express connected to my DSL modem and the rest of my network (2 iBooks and 1 Ubuntu desktop) is connected totally through the wireless network.

Is there SOME way to do this? I remember about a year ago I was playing with Breezy on a Thinkpad and got the whole thing to work, but I seem to be stumped on Dapper.

Thank you.

---

### Post by greggfathead on 2006-11-01
Not yet, but I'm still hoping to figure it out soon.  I figured out how to print to the printer using XP, which was a nightmare (the figuring out part AND the using XP part :) ) and I just insttalled Edgy on a laptop and a box I'll use as a server, so it's back to the drawing board on this issue.  I'll keep you posted though!

---

### Post by crazedgremlin on 2006-12-18
> Not yet, but I'm still hoping to figure it out soon. I figured out how to print to the printer using XP, which was a nightmare (the figuring out part AND the using XP part ) and I just insttalled Edgy on a laptop and a box I'll use as a server, so it's back to the drawing board on this issue. I'll keep you posted though!


Couldn't you plug the printer into the ubuntu server and set it up as a shared printer?

---

### Post by stratofunkit on 2007-03-06
Hello:

My home wi-fi network is  Apple airport express hooked to a HP Photosmart printer and I have had this same problem since setting up Ubuntu. Printer says ready and document goes but never prints. I discovered by accident that I can make it print by setting print properties in Ubuntu to "detect LAN printers", then when my wife's Apple laptop is on and connected to the network, our printer will appear in the printers box in Ubuntu and prints just fine. When she shuts down her Macintosh, then the printer icon in Ubuntu goes away and I can no longer print. I tried copying the printer settings from the auto detected printer and setting up a new printer with them but that new printer won't work. I'm totally new to Linux (I've never used the command line), but this is the only problem I've had setting up and running Ubuntu. I used Apple's Bonjour program to find that printer on the Windows XP side of this machine. Maybe one day, some one out there who is really good with Apple & Linux will work this problem out. I'll keep checking back.
-Strat

---

### Post by crazedgremlin on 2007-03-07
@ stratofunkit:
That's because you have printer sharing enabled in os x.  I figured out I could do that *after* I had moved the printer off the airport express...  oh well

---

### Post by svenand on 2007-03-07
I have Ubuntu installed on my MacBook using Parallels Desktop. I am printing to
a printer connected to an Airport Express. I use CUPS to setup the printer. You
can read more in my blog.

[http://svenand.blogdrive.com/archive/14.html](http://svenand.blogdrive.com/archive/14.html)

---

### Post by dtracy1 on 2007-06-03
Look up the IP address of your Airport Express in the Airport Admin Utility. Then on the Ubuntu computer go to System-Administration-Printing and select New Printer. In Step 1 select Network Printer and TCP/socket, etc. Then enter the IP address you found for your Airport Express into the Host box; Port 9100 was automatically entered into the next box. Click Forward choose the appropriate manufacturer and model of your printer and click Forward. You can then name your printer as you like etc. Click Apply and you are finished.

---

### Post by RabidChipmunk on 2007-07-01
> **dtracy1 said:**
> Look up the IP address of your Airport Express in the Airport Admin Utility. 

Note that you can get all of the printer information using Avahi. If you install the Avahi browser it will give you the IP address and port of all zeroconf services on the net. I'm not sure why that isn't enough for the Gnome Printer util, but...

My airport printer is on port 9102. Haven't the foggiest why, but that's what Avahi says and it works. With a disturbingly long delay after adding stuff to the queue. So give it a chance when testing it. (Maybe 3-5 minutes.) Not sure about the cause of the delay, but the prints are nice.

---

### Post by p0rtlandcubsfan on 2007-12-31
i can use the airport base station for wireless on ubuntu on my 2nd gen macbook using madwifi, and i got the ip for my base station, but i can't figure out what port to use.  can somebody plese help, i'm a bit of a n00b.  :(

---

### Post by holbech on 2008-03-31
This worked for me:

System->Administartion->Printing
New Printer
AppSocket/HP JetDirect (used default port 9100)
entered ip
Used default for the rest, see attachment, hope this helps

---

### Post by renatoborges on 2008-05-25
all you have to do is install the avahi-utils by the synaptic package manager (system/administration/synaptic package manager) and after installation restart your system.

then go to system/administration/print and click the new printer button, your printer or printers, connected to the airport express should appear in the list of printers available for installation.

---

### Post by renatoborges on 2008-05-25
I am sorry;

---

