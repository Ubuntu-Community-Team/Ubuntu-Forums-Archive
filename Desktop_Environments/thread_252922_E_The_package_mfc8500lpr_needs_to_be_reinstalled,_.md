---
title: "E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Jheric on 2006-09-07
Hi,

Whenever I try to run Synaptic or click the update icon I get this:
> 
E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Also I cannot use synaptic... no repositories are loading and the above is the only error I'm getting.

I tried running $ sudo apt-get remove mfc8500lrp and it just says:
> 
Reading package lists... Done
Building dependency tree... Done
E: The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.

Thank you for reading my post!

-Jheric

---

### Post by Jheric on 2006-09-07
Update:

This is still an issue and it is even stopping programs like Automatix which lists the same error above no matter what program I am trying to dl.

So you  know, mfc8500lpr is a driver for my brother printer. It didn't work so I ended up using a ppd driver instead, which works fine. But I don't know why this driver has turned into such a monkey wrench in my system!

---

### Post by desperado666 on 2006-09-07
You installed a Debian .deb package from brother. But some of them are not usable for Ubuntu. Try the rpm packages and "alien" them. 

Got the very same problem with MFC 9180 Printer.

---

### Post by Jheric on 2006-09-07
The printer is working via the ppd files that came on the CD. I need to remove this file cause it's screwing up my system! Apt-get remove doesn't work. Is there another way to remove a messed up package??

-Jheric

---

### Post by desperado666 on 2006-09-07
dpkg --force-help

---

### Post by Jheric on 2006-09-07
Thanks for the help but it's still not gone. The remove failed even with the force:

> dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 125508 files and directories currently installed.)
Removing mfc8500lpr ...
/var/lib/dpkg/info/mfc8500lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing mfc8500lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8500lpr

Any idea how I can get rid of this thing??

-Jheric

---

### Post by Jheric on 2006-09-07
Doesn't anyone know what's wrong here?

---

### Post by Jheric on 2006-09-07
Despite the fact that only one person offered any advice, I found a way to resolve this.

> dpkg - warning, overriding problem because --force enabled:
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
(Reading database ... 125508 files and directories currently installed.)
Removing mfc8500lpr ...
**/var/lib/dpkg/info/mfc8500lpr.postrm**: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing mfc8500lpr (--remove):
subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
mfc8500lpr

The line bolded above seemed to be the problem so I deployed a root-nautilis there and deleted the file. Then I ran the following and it fixed my problem:

> sudo dpkg --remove --force-remove-reinstreq mfc8500lpr

Hope that helps someone some day.

---

### Post by con on 2006-09-12
Hi Jheric
I'd the same prolem with another Brother driver (fax4100lpr) and your solution worked for me, cheers :D

---

### Post by BartlebyScrivener on 2006-10-17
Jheric,

BIG HELP. Thanks. I had the same problem with a Brother Network Printer driver for HL-1870N

Thanks for posting the solution.

rd

---

### Post by tubasoldier on 2006-10-30
Your fix worked for me! Thanks for posting your solution.

---

### Post by whistlerspa on 2006-11-20
Thanks solved my problem with fax4100lpr as well. :) 

But I still can't get my Brother MFC-210C to print though

---

### Post by KillerKiwi on 2007-02-22
Legand that fixed it

---

### Post by Jose Catre-Vandis on 2007-03-08
Thanks, thought I had borked my system - this rescued me with  Brother DCP-540CN install/uninstall

---

### Post by djshag on 2007-05-30
This helped for me as well with my MFC 240C Printer!

Thanks a lot! :p

---

### Post by dolphin_oracle on 2007-05-30
FYI

The file in question is a 3 or 4 line text file that tells dpkg how to clean up after an installation.  It references restarting lpr, which most people don't install since they are using cups.

You can also fix this problem by commenting out the lpr lines and letting dpkg process the file, which in effect will tell dpkg to do nothing.

---

### Post by Towerblock on 2007-06-26
Hey a big thanks on this! I was having the same problem with that brother mfc8500 driver..locked my system updates as well..:)

Thanks again for taking the time to post your fix! ;)

---

### Post by Harcat on 2007-08-08
:lolflag:

Im about to take Jheric's advice and initiate a removal but am not sure what a root-nautilus is or how to execute it other


Thanks in advance for advice

---

### Post by Tokke on 2007-09-29
> **Jheric said:**
> Despite the fact that only one person offered any advice, I found a way to resolve this.



The line bolded above seemed to be the problem so I deployed a root-nautilis there and deleted the file. Then I ran the following and it fixed my problem:



Hope that helps someone some day.


Thx, worked excellent for me.

---

### Post by Phearicle on 2007-09-30
Okay im getting the same message only this is with VirtualBox so my message is 
'The package virtualbox needs to be reinstalled, but I can't find an archive for it.'
So I tried taking your advice and replaced the 'mfc8500lpr' with 'VirtualBox' (Ya I know. I'm really newby with Linux) but its telling me there is no directory with that name. So until I fix this I can't use Synaptic Package Manager so I really need help.  :confused:

Thanks in advance!

---

### Post by tyeo098 on 2007-10-02
Ahh Me Too What Do I Do!!!!!

---

### Post by billio on 2007-11-19
I have a similar problem with cupswrapper for the DCP330C - the response being :

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 99048 files and directories currently installed.)
Removing dcp330ccupswrapper ...
/var/lib/dpkg/info/dcp330ccupswrapper.prerm: 3: /usr/local/Brother/Printer/dcp330c/cupswrapper/cupswrapperdcp330c: not found
dpkg: error processing dcp330ccupswrapper (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/dcp330ccupswrapper.postinst: 3: /usr/local/Brother/Printer/dcp330c/cupswrapper/cupswrapperdcp330c: not found
cp: cannot stat `/usr/share/cups/model/brdcp330c.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dcp330ccupswrapper

I am not confident enough to know what to do next. Is the best thing to re-install 7.10 because I am left in the state where I cannot do any system updates ?.

A little bit annoying because loading the printer drivers was straightforward for 7.04.

Bill

---

### Post by billio on 2007-11-19
I decided to try modifying the offending files to allow the remove to complete. It worked. Bill

---

### Post by whiskyansoda on 2008-04-15
Hi there, I have the samen messenge but with 
E: The package Emesene needs to be reinstalled, but I can't find an archive for it.

jorge@jorge-laptop:~$ sudo dpkg --remove --force-remove-reinstreq emesene
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 96095 files and directories currently installed.)
Removing emesene ...
The generated cache was invalid.
dpkg: error processing emesene (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 emesene


But it doenst work.... do you have some ideas?

---

