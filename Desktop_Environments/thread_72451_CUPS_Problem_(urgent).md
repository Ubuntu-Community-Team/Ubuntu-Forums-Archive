---
title: "CUPS Problem (urgent)"
date: 2005-10-06
forum: Desktop Environments
---

### Post by Floker on 2005-10-06
Hi

My system wont start CUPS. If i select «restart cups server» from the controlcenter, it complains that there is no running cups server.

«/etc/init.d/cupsys start» does start the server, well it says so, but actually the error message is teh same.

What goes wrong in there?
I've set up the printer correctly, a couple of times.

My computer runs:
Kubuntu 5.04 Hoary
KDE 3.4.0
Linux 2.6.10-5 386

A few messages:

stefano@stefano:~$ /etc/init.d/cupsys start
* Starting Common Unix Printing System: cupsd [ ok ]

stefano@stefano:~$ /etc/init.d/cupsys restart
* Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 13!

stefano@stefano:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

The Setup-Assistent recognizes my Printer at the USB port, and it detects the correct model.

Thanks, i'll appreciate.
Floker

btw: urgent means urgent, i have to print an important document utill tommarow.

---

### Post by 11hjpphty76lkjj on 2005-10-06
Floker,

Can we try putting CUPS into debug mode and see what the error is exactly?

In terminal

sudo gedit /etc/cups/cupsd.conf

Find this section:

# LogLevel: controls the number of messages logged to the ErrorLog
# file and can be one of the following:
#
#     debug2	Log everything.
#     debug	Log almost everything.
#     info      Log all requests and state changes.
#     warn      Log errors and warnings.
#     error     Log only errors.
#     none      Log nothing.
#

LogLevel debug

--

Make sure loglevel is set to debug.

Then save exit, restart cups.

tail -f /var/log/cups/error_log

And because you have an HP printer you might want to check out [http://hpinkjet.sf.net](http://hpinkjet.sf.net)

I'm by all means not a CUPS expert...but I'll do what i can..

Aaron

---

### Post by boerner on 2005-10-06
Hello,
Don't know if I had the same problem, but had similiar symptoms...
I had set up my Hoary box as a print server for a small network, and had the same problems you did. I checked the cups log file (located in /var/log/cups) and it pointed me to a network issue. The "server" was actually getting its IP through DHCP and its IP had changed after I rebooted it. I had to manually go in to the cups configuration file in the /etc directory and change the IP address that the cups demon was listening on.
How about you post the last bits of your cups error_log so I can take a look...

---

### Post by Floker on 2005-10-06
```
root@stefano:~ # tail -f /var/log/cups/error_log
I [06/Oct/2005:17:04:20 +0200] LoadPPDs: No new or changed PPDs...
I [06/Oct/2005:17:04:20 +0200] Full reload complete.
I [06/Oct/2005:18:32:30 +0200] Scheduler shutting down normally.
I [06/Oct/2005:18:33:57 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [06/Oct/2005:18:33:57 +0200] Configured for up to 100 clients.
I [06/Oct/2005:18:33:57 +0200] Allowing up to 100 client connections per host.
I [06/Oct/2005:18:33:57 +0200] Full reload is required.
I [06/Oct/2005:18:33:58 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 2349 PPDs...
I [06/Oct/2005:18:33:58 +0200] LoadPPDs: No new or changed PPDs...
I [06/Oct/2005:18:33:58 +0200] Full reload complete.

root@stefano:~ # /etc/init.d/cupsys
 * Usage: /etc/init.d/cupsd {start|stop|restart|force-reload}
root@stefano:~ # /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
root@stefano:~ # tail -f /var/log/cups/error_log
D [06/Oct/2005:20:19:54 +0200] ReadClient: 5 POST /classes/ HTTP/1.1
D [06/Oct/2005:20:19:54 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:19:54 +0200] CloseClient: 5
D [06/Oct/2005:20:19:54 +0200] AcceptClient: 4 from localhost:631.
D [06/Oct/2005:20:19:54 +0200] ReadClient: 4 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:19:54 +0200] ProcessIPPRequest: 4 status_code=1
D [06/Oct/2005:20:19:54 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:19:54 +0200] CloseClient: 4
D [06/Oct/2005:20:19:54 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:19:54 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:19:54 +0200] AcceptClient: 4 from localhost:631.
D [06/Oct/2005:20:19:54 +0200] CloseClient: 5
D [06/Oct/2005:20:19:54 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Oct/2005:20:19:54 +0200] ProcessIPPRequest: 4 status_code=0
D [06/Oct/2005:20:19:54 +0200] ReadClient: 4 GET /printers/deskjet.ppd HTTP/1.1
D [06/Oct/2005:20:19:54 +0200] SendFile: 4 file=5
D [06/Oct/2005:20:19:54 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:19:54 +0200] ReadClient: 5 POST / HTTP/1.1
D [06/Oct/2005:20:19:54 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:19:54 +0200] CloseClient: 5
D [06/Oct/2005:20:19:59 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:19:59 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:19:59 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:19:59 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:19:59 +0200] CloseClient: 5
D [06/Oct/2005:20:19:59 +0200] ReadClient: 6 POST /classes/ HTTP/1.1
D [06/Oct/2005:20:19:59 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:19:59 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:19:59 +0200] CloseClient: 6
D [06/Oct/2005:20:19:59 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:19:59 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:19:59 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:19:59 +0200] CloseClient: 5
D [06/Oct/2005:20:19:59 +0200] ReadClient: 6 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:19:59 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:19:59 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Oct/2005:20:19:59 +0200] ProcessIPPRequest: 4 status_code=0
D [06/Oct/2005:20:19:59 +0200] CloseClient: 6
D [06/Oct/2005:20:19:59 +0200] ReadClient: 4 GET /printers/deskjet.ppd HTTP/1.1
D [06/Oct/2005:20:19:59 +0200] SendFile: 4 file=5
D [06/Oct/2005:20:19:59 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:19:59 +0200] ReadClient: 5 POST / HTTP/1.1
D [06/Oct/2005:20:19:59 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:19:59 +0200] CloseClient: 5
D [06/Oct/2005:20:20:04 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:04 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:04 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:04 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:20:04 +0200] CloseClient: 5
D [06/Oct/2005:20:20:04 +0200] ReadClient: 6 POST /classes/ HTTP/1.1
D [06/Oct/2005:20:20:04 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:20:04 +0200] CloseClient: 6
D [06/Oct/2005:20:20:04 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:04 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:04 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:04 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:20:04 +0200] CloseClient: 5
D [06/Oct/2005:20:20:04 +0200] ReadClient: 6 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:04 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:20:04 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Oct/2005:20:20:04 +0200] ProcessIPPRequest: 4 status_code=0
D [06/Oct/2005:20:20:04 +0200] CloseClient: 6
D [06/Oct/2005:20:20:04 +0200] ReadClient: 4 GET /printers/deskjet.ppd HTTP/1.1
D [06/Oct/2005:20:20:04 +0200] SendFile: 4 file=5
D [06/Oct/2005:20:20:04 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:04 +0200] ReadClient: 5 POST / HTTP/1.1
D [06/Oct/2005:20:20:04 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:04 +0200] CloseClient: 5
D [06/Oct/2005:20:20:09 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:09 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:09 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:09 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:20:09 +0200] CloseClient: 5
D [06/Oct/2005:20:20:09 +0200] ReadClient: 6 POST /classes/ HTTP/1.1
D [06/Oct/2005:20:20:09 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:20:09 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:09 +0200] CloseClient: 6
D [06/Oct/2005:20:20:09 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:09 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:09 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:20:09 +0200] CloseClient: 5
D [06/Oct/2005:20:20:09 +0200] ReadClient: 6 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:09 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:20:09 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Oct/2005:20:20:09 +0200] ProcessIPPRequest: 4 status_code=0
D [06/Oct/2005:20:20:09 +0200] CloseClient: 6
D [06/Oct/2005:20:20:09 +0200] ReadClient: 4 GET /printers/deskjet.ppd HTTP/1.1
D [06/Oct/2005:20:20:09 +0200] SendFile: 4 file=5
D [06/Oct/2005:20:20:09 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:09 +0200] ReadClient: 5 POST / HTTP/1.1
D [06/Oct/2005:20:20:09 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:09 +0200] CloseClient: 5
D [06/Oct/2005:20:20:14 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:14 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:14 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:14 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:20:14 +0200] CloseClient: 5
D [06/Oct/2005:20:20:14 +0200] ReadClient: 6 POST /classes/ HTTP/1.1
D [06/Oct/2005:20:20:14 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:20:14 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:14 +0200] CloseClient: 6
D [06/Oct/2005:20:20:14 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:14 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:14 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:20:14 +0200] CloseClient: 5
D [06/Oct/2005:20:20:14 +0200] ReadClient: 6 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:14 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:20:14 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Oct/2005:20:20:14 +0200] ProcessIPPRequest: 4 status_code=0
D [06/Oct/2005:20:20:14 +0200] CloseClient: 6
D [06/Oct/2005:20:20:14 +0200] ReadClient: 4 GET /printers/deskjet.ppd HTTP/1.1
D [06/Oct/2005:20:20:14 +0200] SendFile: 4 file=5
D [06/Oct/2005:20:20:14 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:14 +0200] ReadClient: 5 POST / HTTP/1.1
D [06/Oct/2005:20:20:14 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:14 +0200] CloseClient: 5
D [06/Oct/2005:20:20:19 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:19 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:19 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:19 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:20:19 +0200] CloseClient: 5
D [06/Oct/2005:20:20:19 +0200] ReadClient: 6 POST /classes/ HTTP/1.1
D [06/Oct/2005:20:20:19 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:20:19 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:19 +0200] CloseClient: 6
D [06/Oct/2005:20:20:19 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:19 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:19 +0200] CloseClient: 5
D [06/Oct/2005:20:20:19 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:19 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:19 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:19 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Oct/2005:20:20:19 +0200] ProcessIPPRequest: 4 status_code=0
D [06/Oct/2005:20:20:19 +0200] CloseClient: 5
D [06/Oct/2005:20:20:19 +0200] ReadClient: 4 GET /printers/deskjet.ppd HTTP/1.1
D [06/Oct/2005:20:20:19 +0200] SendFile: 4 file=5
D [06/Oct/2005:20:20:19 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:19 +0200] ReadClient: 5 POST / HTTP/1.1
D [06/Oct/2005:20:20:19 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:19 +0200] CloseClient: 5
D [06/Oct/2005:20:20:24 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:24 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:24 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:24 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:20:24 +0200] CloseClient: 5
D [06/Oct/2005:20:20:24 +0200] ReadClient: 6 POST /classes/ HTTP/1.1
D [06/Oct/2005:20:20:24 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:20:24 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:24 +0200] CloseClient: 6
D [06/Oct/2005:20:20:24 +0200] ReadClient: 5 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:24 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:24 +0200] AcceptClient: 6 from localhost:631.
D [06/Oct/2005:20:20:24 +0200] CloseClient: 5
D [06/Oct/2005:20:20:24 +0200] ReadClient: 6 POST /printers/ HTTP/1.1
D [06/Oct/2005:20:20:24 +0200] ProcessIPPRequest: 6 status_code=1
D [06/Oct/2005:20:20:24 +0200] CloseClient: 6
D [06/Oct/2005:20:20:24 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Oct/2005:20:20:24 +0200] ProcessIPPRequest: 4 status_code=0
D [06/Oct/2005:20:20:24 +0200] ReadClient: 4 GET /printers/deskjet.ppd HTTP/1.1
D [06/Oct/2005:20:20:24 +0200] SendFile: 4 file=5
D [06/Oct/2005:20:20:24 +0200] AcceptClient: 5 from localhost:631.
D [06/Oct/2005:20:20:24 +0200] ReadClient: 5 POST / HTTP/1.1
D [06/Oct/2005:20:20:24 +0200] ProcessIPPRequest: 5 status_code=1
D [06/Oct/2005:20:20:24 +0200] CloseClient: 5

AND SO ON ;)

```


so. i dont get get it anyways.


i wonder if it would help to remove cups and ALL its components (even the kde printing comps.) and delete the entire configuration, then reinstall it.

but i dont know whicht are the important packages and config.

nevertheless, thanks for the help you Aaron and boerner!

hth ;)

---

### Post by boerner on 2005-10-06
Well...nothing seems to jump out and bite me :-)

I think your course of un-installing all of the cups packages and re-installing and then reconfiguring might be the best course of action. To give you an idea of what I was seeing:

[06/Oct/2005:13:31:05 -0400] Listening to 7f000001:631
I [06/Oct/2005:13:31:05 -0400] Listening to a28100b:631
I [06/Oct/2005:13:31:05 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [06/Oct/2005:13:31:05 -0400] Configured for up to 100 clients.
I [06/Oct/2005:13:31:05 -0400] Allowing up to 100 client connections per host.
I [06/Oct/2005:13:31:05 -0400] Full reload is required.
I [06/Oct/2005:13:31:07 -0400] LoadPPDs: Read "/etc/cups/ppds.dat", 2349 PPDs...
I [06/Oct/2005:13:31:10 -0400] LoadPPDs: No new or changed PPDs...
I [06/Oct/2005:13:31:10 -0400] Full reload complete.
E [06/Oct/2005:13:31:10 -0400] StartListening: Unable to bind socket for address 0a28100b:631 - Cannot assign requested address.

It was the last line that made me think of a network issue. Sorry I can't seem to be of more help. Fortunately, using apt-get to un-install and re-install cups shouldn't be too bad.

---

### Post by 11hjpphty76lkjj on 2005-10-06
I'm not sure either.  This might be a long shot...but go to 

System>Admin>Users

double click on your user name

then user prevs

make sure a check mark is next to "setup printers"

not sure why this would help. but I read it as a resolution to a similiar problem with another cups user..

Aaron

---

### Post by Floker on 2005-10-06
its already enabled. i even istalled gnome to prove this :D 
(i run kde)

its just wicked

---

### Post by 11hjpphty76lkjj on 2005-10-06
hmm it sounds like re-installing cups might be the next step. Although i'm not sure about how to do this, I'm assuming it's apt-get remove cups or libcups or something... and then re-install.  although wait a sec, if you use synpatic or knaptic search for cups and do a re-install and see what happens..

Aaron

---

### Post by Floker on 2005-10-06
status quo after reinstall of all printing related comonents...

---

### Post by 11hjpphty76lkjj on 2005-10-06
Just for the heck of it have you tried installing HPLIP?

I doubt it will fix CUPS issues, just curious.  Also I'm assuming you are connected via usb cable, try disconnecting it and restarting cups? see if there are any errors in the cups log and syslog (/var/log/messages) then reconnect and see if there are any errors. restart, etc.  I'm thinking is lets make sure the cable isn't bad or something.

You have a very naughty CUPS there.

Aaron

---

### Post by Floker on 2005-10-06
the bad: it has worked with debian, perfectly. and i havnt changed my setup. ill try to install some packs

i'll go to bed now, tomarrow i'll post again after i have tried some things.
see ya

---

