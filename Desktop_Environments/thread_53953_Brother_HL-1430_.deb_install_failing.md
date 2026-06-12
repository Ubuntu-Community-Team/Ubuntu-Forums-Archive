---
title: "Brother HL-1430 .deb install failing"
date: 2005-08-02
forum: Desktop Environments
---

### Post by notmatt on 2005-08-02
Hi all

I'm trying to install my Brother HL-1430.  I've got the relevant driver from the Brother website and tried to install it using:

dpkg -i hl1430lpr-1.1.2-1.i386.deb

This produced a load of errors, so checking the brother website I noticed that I'd missed the --force-all option.  I tried that and got the same errors.

```
(Reading database ... 81070 files and directories currently installed.)
Preparing to replace hl1430lpr 1.1.2-1 (using hl1430lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1430lpr ...
/var/lib/dpkg/info/hl1430lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1430lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1430lpr-1.1.2-1.i386.deb
``` 

I'm a bit clueless when it comes to printing under linux, I got this printer specifically because it is supposed to work ok under linux, I'll be a bit gutted if I can't get it working.

Any advice?

---

### Post by amohanty on 2005-08-03
Do you have cupsys and libcupsys installed?

If you do lpd is located in /usr/lib/cupsys/backend.

If the driver absolutely requires it, you might try (and I am not sure if it will work) to create a symlink to it in /etc/init.d

HTH
AM

---

### Post by notmatt on 2005-08-03
[QUOTE=amohanty]Do you have cupsys and libcupsys installed?

If you do lpd is located in /usr/lib/cupsys/backend.

If the driver absolutely requires it, you might try (and I am not sure if it will work) to create a symlink to it in /etc/init.d

HTH
AM[/QUOTE]
 Ok, I tried to do that.  lpd is in /usr/lib/cups/backend on my system so I tried:

sudo ln -s /usr/lib/cups/backend/lpd /etc/init.d/         

That helped after a fashion.  I got a different error message, so I tried apt-get clean, which didn't do much, still got the same error.

```
/home/data/installers$ sudo dpkg -i --force-all hl1430lpr-1.1.2-1.i386.deb
(Reading database ... 81070 files and directories currently installed.)
Preparing to replace hl1430lpr 1.1.2-1 (using hl1430lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1430lpr ...
Usage: /etc/init.d/lpd job-id user title copies options [file]
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Usage: /etc/init.d/lpd job-id user title copies options [file]
dpkg: error processing hl1430lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
Usage: /etc/init.d/lpd job-id user title copies options [file]
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 hl1430lpr-1.1.2-1.i386.deb
``` 

Is there away of getting rid of or tweaking those install scripts?  

This has totally screwed up my apt-get and I was getting along so well with it also.  I've had problems with apt-get on a server I once administrated :)

eg when I try to install anything:

[CODE]
Reading package lists... Done
Building dependency tree... Done
E: The package hl1430lpr needs to be reinstalled, but I can't find an archive for it.
[CODE]

Any help much appreciated.  Thanks.

---

### Post by amohanty on 2005-08-04
You probably dont want to do a --force-all. what was the problem is you didnt force the install?

AM

---

### Post by notmatt on 2005-08-04
[QUOTE=amohanty]You probably dont want to do a --force-all. what was the problem is you didnt force the install?

AM[/QUOTE]
 Originally I didn't put the force-all in.  But the Brother website tells you to put the force-all in, so I did.  I'll try with out later.

---

### Post by notmatt on 2005-08-04
[QUOTE=notmatt]Originally I didn't put the force-all in.  But the Brother website tells you to put the force-all in, so I did.  I'll try with out later.[/QUOTE]
 I get the same errors even without the --force-all option.

---

### Post by amohanty on 2005-08-05
> (Reading database ... 81070 files and directories currently installed.)
Preparing to replace hl1430lpr 1.1.2-1 (using hl1430lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1430lpr ... 

It seems you already have the package you are trying to install. Try this:

>> dpkg -r hl1430lpr
 and then try to install it.

AM

---

### Post by notmatt on 2005-08-15
```
dpkg: error processing hl1430lpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 hl1430lpr
```

I tried to reinstall as it suggested and then remove again, but that didnt work.  I tried to clear the apt get cache using apt get clear, that didnt help.

I think I'm going to have to read an apt-get guide on how to remove broken programs.  That looks bad to me.

Any ideas?

---

### Post by incinerator on 2005-08-15
I don't understand why you would install this deb in the first place. This is not windows-world where you have to download drivers from external sources for every tiny piece of hardware you have.

The Brother HL-1430 is natively supported by the printing system that comes with Kubuntu. That deb of yours is totally unnecessary.

Connect the printer to the computer, switch it on, then start the "Printers" application. Unfortunately I don't know the English name of the menu it is in, as I use a German KDE, but in German it is in "Dienstprogramme" (literal translation is "service programs"). Actually, that "Printers" application is part of the KDE Control Center, therefore you can find it by using the "System" button in the panel that is on the lower end of the main kde screen. Click that "System" button, then click the "Settings" button, then "Connected Devices" (or whatever), then "Printers".

Once you have started that "Printers" program, use the "Add Printer" button and proceed as directed, it should be fairly easy to go on from there. If not, KDE should have some documentation or you could just google around a wee bit.

Btw, I have a HL-1450 and it works fine without installing that strange deb you mentioned.

As for removing that bloody package, you will have to try installing it first, as the installation screwed up so early the operating system cannot remove it. If this is not successful you could just leave it there as it is, it should not matter to much.

Regards,
Dominik

[QUOTE=notmatt]Hi all

I'm trying to install my Brother HL-1430.  I've got the relevant driver from the Brother website and tried to install it using:

dpkg -i hl1430lpr-1.1.2-1.i386.deb

This produced a load of errors, so checking the brother website I noticed that I'd missed the --force-all option.  I tried that and got the same errors.

```
(Reading database ... 81070 files and directories currently installed.)
Preparing to replace hl1430lpr 1.1.2-1 (using hl1430lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1430lpr ...
/var/lib/dpkg/info/hl1430lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1430lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1430lpr-1.1.2-1.i386.deb
``` 

I'm a bit clueless when it comes to printing under linux, I got this printer specifically because it is supposed to work ok under linux, I'll be a bit gutted if I can't get it working.

Any advice?[/QUOTE]

---

### Post by notmatt on 2005-08-15
[QUOTE=incinerator]
The Brother HL-1430 is natively supported by the printing system that comes with Kubuntu. That deb of yours is totally unnecessary.

Connect the printer to the computer, switch it on, then start the "Printers" application. Unfortunately I don't know the English name of the menu it is in, as I use a German KDE, but in German it is in "Dienstprogramme" (literal translation is "service programs"). Actually, that "Printers" application is part of the KDE Control Center, therefore you can find it by using the "System" button in the panel that is on the lower end of the main kde screen. Click that "System" button, then click the "Settings" button, then "Connected Devices" (or whatever), then "Printers".

Once you have started that "Printers" program, use the "Add Printer" button and proceed as directed, it should be fairly easy to go on from there. If not, KDE should have some documentation or you could just google around a wee bit.
[/QUOTE]

Tried this, despite adding the printer to via the relevant KDE wizard (via the control center as you suggest) I still wasn´t able to get it going (It sends the file to the printer and then nothing).  So I went to give the drivers for LPR from the brother website a try.

[QUOTE=incinerator]
As for removing that bloody package, you will have to try installing it first, as the installation screwed up so early the operating system cannot remove it. If this is not successful you could just leave it there as it is, it should not matter to much.
[/QUOTE]

Heh, that damn package has screwed up my whole apt-get system.  It can´t install anything else atm.  I need to kill it somehow...

thanks for your help

---

### Post by notmatt on 2005-08-16
```
Unable to load a valid driver for printer brotherhl1430. Error message received from manager:
Internal error (no error message).
```

That is the error message that the KDE control center gves me.

---

### Post by incinerator on 2005-08-16
Hmmm, this is very odd. Are you sure you have all the important foomatic packages installed?

On my system, these are ```
foomatic-db  foomatic-db-engine foomatic-db-gimp-print foomatic-db-hpijs foomatic-filters foomatic-filters-ppds
```
Also, ghostscript should be installed, preferably ```
gs-esp
```.

Best check [http://www.linuxprinting.org/](http://www.linuxprinting.org/) that will tell you what driver works best. Afaik, the hl1250 driver they recommend (and which I use with my HL-1450) is part of ghostscript.

What other changes have you made to your system? Have you removed crucial packages, changed permissions etc. ?

---

### Post by vreemde eend on 2005-08-16
I've got exactely the same printer, no installation was needed, works perfect. That doesn't help you, but it's strange.

---

### Post by notmatt on 2005-08-18
[QUOTE=vreemde eend]I've got exactely the same printer, no installation was needed, works perfect. That doesn't help you, but it's strange.[/QUOTE]
 Apt-get is still broken but if I ever get it working I will check that I have those packages.

---

### Post by notmatt on 2005-08-18
[QUOTE=incinerator]Hmmm, this is very odd. Are you sure you have all the important foomatic packages installed?

On my system, these are ```
foomatic-db  foomatic-db-engine foomatic-db-gimp-print foomatic-db-hpijs foomatic-filters foomatic-filters-ppds
```
Also, ghostscript should be installed, preferably ```
gs-esp
```.

Best check [http://www.linuxprinting.org/](http://www.linuxprinting.org/) that will tell you what driver works best. Afaik, the hl1250 driver they recommend (and which I use with my HL-1450) is part of ghostscript.

What other changes have you made to your system? Have you removed crucial packages, changed permissions etc. ?[/QUOTE]

Yes I have got all of them installed.  I have managed to get the annoying brother deb off my system.

I don´t think I have changed anything.  

I did do:
```

sudo ln -s /usr/lib/cups/backend/lpd /etc/init.d/ 

```
To try and get the deb to install.

I have done some fiddling with X to try and get the monitor to work at the proper resolution.  I have made a few ln -s to try and get java to work with firefox working.  But I cannot see how they would effect things.

---

### Post by lonewolf72 on 2005-08-19
[QUOTE=notmatt]I have managed to get the annoying brother deb off my system.
[/QUOTE]

How did you get it off? (I tried to install a different brother drive and now I can't get rid of it (it crashed during install) and  I can't update either now...

---

### Post by incinerator on 2005-08-19
load [http://localhost:631/](http://localhost:631/) in your webbrowser to see if cups is actually running.
This also is the cups web administration interface, you could even configure your printers with if you don't want to use the kde tool.

If that doesn't work then your cups is knackered. try uninstalling cups or the package that owns the file involved in the symlink. find the right package by doing
```
dpkg -S <completefilenamewithpath>
```

Then delete the symlink and reinstall that package, make sure you have all the other necessary packages installed, like the foomatic and ghostscript stuff.

---

### Post by notmatt on 2005-08-19
CUPS works fine it seems.  I get this when trying to setup the printer:

```

Description: BROTHER HL-1430
Location:
Printer State: stopped, accepting jobs.
"Unable to open parallel port device file "/dev/lp0": Permission denied"
Device URI: parallel:/dev/lp0

```

Somewhere alonc the line I need to set permissions for a file or something.  Any ideas on what?

---

### Post by incinerator on 2005-08-22
Well, that looks like you have set up the printer to be connected to the parallel port instead of USB. Are you sure this reflects the state of your system?

---

### Post by notmatt on 2005-08-22
[QUOTE=incinerator]Well, that looks like you have set up the printer to be connected to the parallel port instead of USB. Are you sure this reflects the state of your system?[/QUOTE]

Yes the printer does connect via a Parallel port.  The Control Center is complaining that It cannot load the correct drivers, also.

---

### Post by GerritKok on 2005-08-22
It could by a permissions problem. Kubuntu seems a bit strange with this. I have the same printer. On Ubuntu it was recognized immediately and it worked perfectly without having to install a driver, on Kubuntu I had to add the printer manually and encountered a permissionproblem. Somewhere in this forum I found:

[I]Author : petertc
Date : 04-29-2005 03:58 PM
Title : Re: Cups

AH 

It's a permissions thing, 

just found this on a post on the ubuntu part of the forum
do:  sudo chmod o=rw /dev/usb/lp0  
and things work !!

this may be a bug ?[/I]

This worked for me (I have the printer connected on USB-port) and also here no driver needed to be installed. 

Gerrit

---

### Post by notmatt on 2005-08-23
[QUOTE=GerritKok]It could by a permissions problem. Kubuntu seems a bit strange with this. I have the same printer. On Ubuntu it was recognized immediately and it worked perfectly without having to install a driver, on Kubuntu I had to add the printer manually and encountered a permissionproblem. Somewhere in this forum I found:

[I]Author : petertc
Date : 04-29-2005 03:58 PM
Title : Re: Cups

AH 

It's a permissions thing, 

just found this on a post on the ubuntu part of the forum
do:  sudo chmod o=rw /dev/usb/lp0  
and things work !!

this may be a bug ?[/I]

This worked for me (I have the printer connected on USB-port) and also here no driver needed to be installed. 

Gerrit[/QUOTE]
 That and restarting CUPs seems to have done the trick.

Thanks everyone for all the help.

---

