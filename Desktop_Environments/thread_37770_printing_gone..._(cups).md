---
title: "printing gone... (cups)"
date: 2005-05-28
forum: Desktop Environments
---

### Post by dmallery on 2005-05-28
hi

yesterday i removed a machine from my network after years of service.  it had been running a version of knoppix.  it had been printing correctly with cups for ages.  so had all the other nodes (all ubuntu).

this morning none of the remaining nodes can print.

i have tried: restarting cups (/etc/init.d/cupsys restart)

manipulating via system..administration..printing: deleting and adding printer with no test pages working.

removing and reinstalling cups via apt

dpkg-reconfigure cupsys

rebooting.

stopping cupsys on the other nodes.


yes, i can ping the printer (10.42.42.200)

yes, the correct printer (xerox n17) shows up as the default (if i print from firefox)

yes, the lpr, lpq and lprm commands seem to work but nothing happens.

there is no ethernet activity on the led on the back of the printer when i lpr something.

this is the only printer on the network and there are no local printers.

this n17 has worked for years and can print status pages.

i have always managed to get printing to work before, but this time i'm stumped.

i'd be very grateful for a pointer

thanks

dave mallery

---

### Post by clb137 on 2005-05-28
hello

Is the printer connected to another machine, if so what OS is it using,  or is it a LAN connected printer



clinton

---

### Post by dmallery on 2005-05-28
it's on network, not connected to any machine otherwise.
10.42.42.200
there are only linux machines on net.  currently have stopped cups on all but this one.

thanks

dave

---

### Post by cwaldbieser on 2005-05-28
You mentioned the machine you removed from the network was running knoppix.  Do you still have a knoppix live CD lying around somewhere?  You could boot one of your existing machines from that and use the Printer Wizard and see if you can print.  If memory serves me correctly, the wizard can scan your network and pretty much configure itself.  You could then compare those settings to your other computers to see if you notice something that has changed.

---

### Post by dmallery on 2005-05-28
hi

thanks for responding!

one of the other machines that had had cups disabled was still knoppix.

i used the wizard to configure and came up with the same deal.  i sent a test page (which didn't print) and then was able to see the job from this machine:

labfrog:~>> lpq
tmpprinter_VGHlH6lv is not ready
Rank    Owner   Job     File(s)                         Total Size
1st     root    1       KDE Print Test                  15360 bytes
labfrog:~>>

 with the addition of that "tmpprinter" business.

the n17 defined on this machine does not show the lkde print test job.

so there's a difference.

dave

---

### Post by dmallery on 2005-05-28
maybe not

after i finished with the kde print wizard, the n17 got the name "lp"
and this is the output:
labfrog:~>> lpq
lp is not ready
Rank    Owner   Job     File(s)                         Total Size
1st     root    2       KDE Print Test                  15360 bytes
labfrog:~>> 

so the tmp printer was an artifact.

but i can't see the kde unit from this machine save thru lpq.  it does not show up on the printers window.

slowly going mad...

dave

---

### Post by dmallery on 2005-05-28
another data point:  i swapped the printer controller hardware completely.

symptoms follow.  so it ain't the hardware.... (i was worried)

dave

---

### Post by dmallery on 2005-05-28
some more observations:

printer properties reports:

status: Ready: Network host '10.42.42.200' is busy:
will retry in 30 seconds...

also, while setting up, network scan does NOT find printer.  have to manually enter url.  also the knoppix wizard did not find it either...

if i do a port scan on the ip address:
80 open www
515 open printer
2000 open sieve
2501 open unknown

no sign of port 631 yet 631 shows up on this machine's netstat.
think i am confused about sockets...


dave

---

### Post by cwaldbieser on 2005-05-28
Is there a firewall configured on the machine in question blocking the port?

---

### Post by dmallery on 2005-05-29
good morning.

i don't think so:
labtwin:~>> iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
labtwin:~>>

the only firewall is between the local net and the satellite modem.

the fact that the printer seems unable to communicate and that it does not report a 631 socket on an nmap seems to be the heart of the problem.

i have a huge backlog of ebay labels to print.  i think i will try to jury rig up a parallel port connection for this morning.

i believe that the machine i turned off (older knoppix) had made a workable conection with the printer and the other machines were just using it via the older machine.  now that it's gone, they can't get a good connection.

after i clear my backlog, i'll go back to the problem.

thanks

dave

---

### Post by dmallery on 2005-05-29
more madness:

on a parallel port connection, i get the same:

Status:     Ready: Parallel port busy; will retry in 30 seconds.


so i'm off to find another printer to substitute.


losing it in nm

dave

---

### Post by dmallery on 2005-05-29
first he tries a good lj4+ on the parallel port

suddenly, there is no more parallel port... the new printer box only suggests usb printers.  he switches back to the xerox printer, the parallel that was there 10 minutes ago is gone.  only usb.

that was the amd64 box.

so he changes the cable over to the "normal" i386 box.  it can't find any ports.

he considers grinding telescope mirrors for a hobby.

. . .does the default kernel have a parallel port?????

dave

and later, to be painfully correct, he repeats the above with a different parallel cable.  no joy in mudville

---

### Post by dmallery on 2005-05-29
the 11:00 am saga:

he gets an lj4+ with jet-direct.  goes blind configuring the ip address.

sets it up with cups for a jetidirect printer 

changes (he thinks) all the paper sizes from a4 to letter.

sends a test page and the printer asks for a4!!!!!

tries many combinations and still the printer wants a4.

deletes and replaces the printer, this time the paper sizes come up right on the properties window, but the printer still demands a4

is there something with the jet direct card??

...

11:48

he gets another lj4+ .. moves the jet direct card.  fortunately, the ip address moves with the card.

tries another paper tray

still the !@#$@!#$ thing demands a4.

mirror grinding looks better and better...

11:54 he removes the printer from the i386 machine and creates it on the amd64

exactly the same result.

so the thing that has not changed is the cups....

does that mean that there is an "A4" lurking in the cups config menus????

12:05 the only "A4" in /etc/cups is in a comment about xpdf....

---

### Post by cwaldbieser on 2005-05-29
Well, I am running Kubuntu, so I forget a little what the Gnome interface looks like, but from the KDE interface to CUPS (KControl -> Printers), I select the printer in the top pane, then choose the [Instance] tab.  I choose the printer instance in the lower pane (Default), and then hit the [Settings] button on the right side of that pane.  There I get a dialog where I can set the paper size and view the driver info to make sure it thinks the paper size is what it should be.

Also, when I go to actually print, a dialog comes up that lets me select the printer properties and change the paper size (properties button) for that printing.

If it is not working at that point...well, at least you have those nice clear skies in NM.  In PA, it is so hazy in the evenings that I consider it lucky if I can see the Great Orion Nebula with binoculars.

If it makes you feel any better, I have had mixed success with network printing (several Linux distros & Windows), too.  Sometimes it seems like it is drivers and sometimes permissions.  I fiddle with it for days, and nothing.  Then one day, it decides to work.  Other times, it's a snap.  Gremilns?  I dunno.

Hang in there!

---

### Post by dmallery on 2005-05-29
hi

thanks!  the kde wizard is MUCH better than GNOME.  it lets you change the printer name from "Laserjet-4-Plus' to "lp" and so forth.

i will go out to the nearest kde machine and try from there. (out to my shop where the pix server and the backup live)...

i have been running linux full time since '97 and have never had such a stickey wicket.

later

dave

---

### Post by dmallery on 2005-05-29
SUCCESS!!!!!!

memo to our south african friends:

there is a cultural A4 artifact stuck somewhere in your implementation.

after ALL of the above, i was able to go to a Knoppix machine and print correctly after using the knoppix wizard to set up an network printer.  (yes, jet-direct).
even with klaus' .de leanings, i could purge the lingering A4 curse...

i am going to go out there again and see if i can set up my xerox n17 to work correctly.

thanks again

dave mallery

---

### Post by dmallery on 2005-05-30
a post-mortem update.

the problem with getting my printing back was rooted in history:  several years back i had gotten the printer to work with the then main machine running knoppix and promptly forgotten all the details.

all my attempts to get it to print since the departure of the old node were using :631 as a socket.  in reality, the printer uses :9100 just like a jet direct.

so i have re-established printing in my network as before.  a little humbler and wiser.

thanks to all who helped!

dave

---

