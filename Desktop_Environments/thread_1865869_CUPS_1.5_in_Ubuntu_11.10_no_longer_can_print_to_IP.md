---
title: "CUPS 1.5 in Ubuntu 11.10 no longer can print to IPP printer over TLS with auth"
date: 2011-10-20
forum: Desktop Environments
---

### Post by chris.poupart on 2011-10-20
I think that the title pretty much sums it up.

I have a CUPS print server here on campus running CUPS 1.4.2 on RHEL 6.

There are wildcard certificates configured for CUPS, printers are shared over IPP with encryption set to "required".

Basic authentication is also configured for the /printers directory.

CUPS clients on Ubuntu versions up to 11.04 work just fine with this setup. The user will add the printer, send a job, and they will be prompted to authenticate.

With Ubuntu 11.10, that no longer happens. Either on a machine upgraded from 11.04 (with working printers) or a new install.

With debug turned on on the server, I get the following error message:

```
D [20/Oct/2011:16:00:14 -0400] Report: clients=2
D [20/Oct/2011:16:00:14 -0400] Report: jobs=6
D [20/Oct/2011:16:00:14 -0400] Report: jobs-active=0
D [20/Oct/2011:16:00:14 -0400] Report: printers=5
D [20/Oct/2011:16:00:14 -0400] Report: printers-implicit=0
D [20/Oct/2011:16:00:14 -0400] Report: stringpool-string-count=1029
D [20/Oct/2011:16:00:14 -0400] Report: stringpool-alloc-bytes=8408
D [20/Oct/2011:16:00:14 -0400] Report: stringpool-total-bytes=22432
D [20/Oct/2011:16:00:14 -0400] cupsdReadClient: 11 POST /printers/Xerox_Color HTTP/1.1
D [20/Oct/2011:16:00:14 -0400] cupsdSetBusyState: Active clients
D [20/Oct/2011:16:00:14 -0400] cupsdAuthorize: No authentication data provided.
D [20/Oct/2011:16:00:14 -0400] cupsdIsAuthorized: username=""
D [20/Oct/2011:16:00:14 -0400] cupsdCloseClient: 11
D [20/Oct/2011:16:00:14 -0400] cupsdSetBusyState: Not busy
D [20/Oct/2011:16:00:14 -0400] cupsdAcceptClient: skipping getpeercon()
D [20/Oct/2011:16:00:14 -0400] cupsdAcceptClient: 11 from XXX.XXX.XXX.107:631 (IPv4)
D [20/Oct/2011:16:00:14 -0400] cupsdReadClient: 11 OPTIONS * HTTP/1.1
D [20/Oct/2011:16:00:14 -0400] cupsdSetBusyState: Active clients
D [20/Oct/2011:16:00:14 -0400] cupsdAuthorize: No authentication data provided.
E [20/Oct/2011:16:00:14 -0400] Unable to encrypt connection from XXX.XXX.XXX.107 - A TLS packet with unexpected length was received.
D [20/Oct/2011:16:00:14 -0400] cupsdCloseClient: 11
```

The problem seems to be twofold -- Problems the client can not negotiate an encrypted connection over TLS, and the client is never prompted to provide authentication, even though it is required.

I am hoping that someone has some ideas on how to proceed.  Obviously, ubuntu is quite popular on campus and I would love to be able to provide them with a printing solution!

---

### Post by jedimasterk on 2011-10-21
My Epson Stylus Photo R340 no longer is detected. Some update!. Cups is BROKEN!!. No longer can print a damm thing!!. Thanks CUPS!!!

---

### Post by chris.poupart on 2011-10-21
I should add, I can print to the queue just fine if I disable authentication.

I have also tried playing around with the client printers.conf file changing the "AuthInfoRequired" options to different things such as "username,password", "negociate" and "none".  No dice.

There don't seem to be any bug reports in launchpad that talk about this, so I came to the forms first, but I will open up a bug soon if no one has a good idea for how to solve it.

---

### Post by madengineer on 2011-10-21
I have essentially the same configuration as the OP, and same error. Debug is not enabled on my server, but I do get the "TLS packet of unexpected length" message in error_log. On the client side, it gives me mostly "Unable to get printer status", like so:

```
E [21/Oct/2011:11:58:32 -0700] [Job 30] Unable to get printer status.
E [21/Oct/2011:11:59:01 -0700] [Job 30] Unable to get printer status.
E [21/Oct/2011:11:59:38 -0700] [Job 30] Unable to get printer status.
E [21/Oct/2011:12:00:03 -0700] Returning IPP client-error-not-authorized for Print-Job (ipp://localhost:631/printers/Golem) from localhost
E [21/Oct/2011:12:00:06 -0700] [Job 30] Unable to get printer status.
E [21/Oct/2011:12:00:37 -0700] [Job 30] Unable to get printer status.
E [21/Oct/2011:12:01:06 -0700] [Job 30] Unable to get printer status.
E [21/Oct/2011:12:01:35 -0700] [Job 30] Unable to get printer status.
E [21/Oct/2011:12:01:37 -0700] [Job 30] Stopping unresponsive job!
```

Under Ubuntu 11.04, I was using GNOME 2, and the first time I used this printer during any session, I would get an authentication dialog (sometimes after a short delay on the order of 30 seconds after requesting the print job), enter my login info for the server, and printing would then proceed. Now, no dialog and no printing, in either desktop environment. I tried to do a temporary non-secure workaround by adding my username and password to /etc/cups/printers.conf (so the URI changed to ipp://<username>:<password>@<host>/printers/<printer>) and restarting CUPS, but the result was the same, even when I also tried removing the AuthInfoRequired line.

I'm not sure where to proceed from here to debug--I have a vague idea that system-config-printer is responsible for this dialog, but don't know how it's supposed to work. chris.poupart, could you let me know if and when you post the bug so I can subscribe to it?

---

### Post by joaopinheiro on 2011-10-24
I use TurboPrint and everything worked fine, even when I had already installed U 11.10 in the main machine. The problem arose when I installed it on the second. Now I can no longer print from the second PC to the main one... Is there any fix for this to come up soon? Hope so...

---

### Post by chris.poupart on 2011-10-25
> **madengineer said:**
> 
I'm not sure where to proceed from here to debug--I have a vague idea that system-config-printer is responsible for this dialog, but don't know how it's supposed to work. chris.poupart, could you let me know if and when you post the bug so I can subscribe to it?

@madengineer I have had the bug open since Friday. Not a lot going on with it at the moment, but hopefully now that we are a workday again, it will pick up.

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/879625](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/879625)

---

### Post by bach on 2011-10-25
Same problem here. After upgrading from Ubuntu 11.04 to 11.10 I am no longer able to print to my HP Deskjet 810C.

---

### Post by sammiev on 2011-10-26
Ran into the same problem. I see the bug was reported but not assigned to anyone as of yet. I guess the waiting game is on.

---

### Post by magrc on 2011-11-09
Same here!!
Using Debian squeeze in the server (CUPS 1.4.4)
It works fine with Windows XP/Vista/7, Mac-OS and Ubuntu <=11.04 clients.
Then, clients upgraded to Ubuntu 11.10 stopped printing to the server.
Same error messages as posted by chris.poupart:
   cupsdAuthorize: No authentication data provided.
   cupsdIsAuthorized: username=""
Any solution yet?
Thanks for any help!

---

### Post by shaneo1 on 2011-11-14
Hey guys, there has been a ppa released at 
deb [http://ppa.launchpad.net/till-kamppeter/ppa/ubuntu](http://ppa.launchpad.net/till-kamppeter/ppa/ubuntu) oneiric main 

After reading the comments about it in bug [https://bugs.launchpad.net/ubuntu/oneiric/+source/cups/+bug/887094](https://bugs.launchpad.net/ubuntu/oneiric/+source/cups/+bug/887094) seems to have cleared up the problems with CUPS 1.5.0-8

A release has already happened for 12.04 daily build to take CUPS to 1.5.0-11, just wondering whether this is going to happen for 11.10, rather than using the PPA......

---

### Post by magrc on 2011-11-16
> **shaneo1 said:**
> Hey guys, there has been a ppa released at 
deb [http://ppa.launchpad.net/till-kamppeter/ppa/ubuntu](http://ppa.launchpad.net/till-kamppeter/ppa/ubuntu) oneiric main 

Hello shaneo1,
I've added the ppa repository in the Ubuntu 11.10 (cups client). The Cups package in that machine has changed from 1.5.0-8ubuntu4 to 1.5.0-8ubuntu5~ppa.
Nothing changed. When I try to send a print job to the server, the same erros I mentioned before appears.

---

### Post by sammiev on 2011-11-20
Well I do not see a fix in the near future. The bug still hasn't been assigned to anyone yet. Guess we will have to upgrade to 12.04 to get the fix.

---

### Post by magrc on 2011-12-15
Hello! My problem is solved.
Ubuntu 11.10 has CUPS 1.5.0-8ubuntu6 since yesterday in its repository. This version works fine with my CUPS server, Debian 6.0 with CUPS 1.4.4-7+squeeze1.
Thanks!

---

### Post by bartmc on 2012-01-04
> **magrc said:**
> Hello! My problem is solved.
Ubuntu 11.10 has CUPS 1.5.0-8ubuntu6 since yesterday in its repository. This version works fine with my CUPS server, Debian 6.0 with CUPS 1.4.4-7+squeeze1.
Thanks!

This update did not fix the problem for me. 

bart@bart-desktop:~$ apt-show-versions cups
cups/oneiric uptodate 1.5.0-8ubuntu6

syslog fun

Jan 3 18:29:46 bart-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0
Jan 3 18:29:46 bart-desktop udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.1/usb7/7-1
Jan 3 18:29:46 bart-desktop udev-configure-printer: Device already handled
Jan 3 18:29:46 bart-desktop udev-configure-printer: add /devices/pnp0/00:06/printer/lp0
Jan 3 18:29:46 bart-desktop udev-configure-printer: Failed to get parent
Jan 3 18:29:46 bart-desktop udev-configure-printer: add /module/lp
Jan 3 18:29:46 bart-desktop udev-configure-printer: Failed to get parent
Jan 3 18:29:46 bart-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0
Jan 3 18:29:46 bart-desktop udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.1/usb7/7-1
Jan 3 18:29:46 bart-desktop udev-configure-printer: Device already handled

my printer will print the first job fine, then, I have to unplug the printer and restart cups to get the 2nd job to print.


This was fine in the last release of cups, Anybody know a way to just back out the current cups version and go back to the old one? I've had about 16 hour worth of fun trying to get this to work and that's enough for me.

---

### Post by josemari37 on 2012-02-21
Hello,

It is **[COLOR=Red]regrettable and[/COLOR]****[COLOR=Red] [/COLOR]****[COLOR=Red]unfortunate[/COLOR]** that this bug, which has already occurred in recent updates of CUPS in Ubuntu 11.04, go on Ubuntu 11.10. The error message is:

 cupsdAuthorize: No authentication data provided.

And of course, the local (USB printer in my case) is not working! 

 Regards,

 Jose

---

