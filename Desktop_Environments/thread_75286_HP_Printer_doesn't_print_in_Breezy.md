---
title: "HP Printer doesn't print in Breezy"
date: 2005-10-13
forum: Desktop Environments
---

### Post by jordilin on 2005-10-13
Hi everybody,
I've an old HP Deskjet 820Cxi. It's correctly detected but if I send something to be printed, it doesn't print anything. What's curious is that I can print with the Hoary Live Cd. There's a bug open with the number 16066, but there's hasn't been any solution.
In /var/log/cups/error_log I get this:
I [13/Oct/2005:17:57:40 +0200] New printer 'DeskJet-820C' added by 'root'.
I [13/Oct/2005:17:57:46 +0200] Adding start banner page "none" to job 7.
I [13/Oct/2005:17:57:46 +0200] Adding end banner page "none" to job 7.
I [13/Oct/2005:17:57:46 +0200] Job 7 queued on 'DeskJet-820C' by 'jordilin'.
I [13/Oct/2005:17:57:46 +0200] Started filter /usr/lib/cups/filter/pstops (PID 32566) for job 7.
I [13/Oct/2005:17:57:46 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 32567) for job 7.
I [13/Oct/2005:17:57:46 +0200] Started backend /usr/lib/cups/backend/hp (PID 32568 ) for job 7.
E [13/Oct/2005:17:57:46 +0200] PID 32567 stopped with status 3!
I [13/Oct/2005:17:57:46 +0200] Hint: Try setting the LogLevel to "debug" to find out more.

Which says that the process f**oomatic-rip is stopped with status 3!**!!.
I've compared the settings between Hoary and Breezy and they are the same. Just incredible !! I can print with Hoary, and not in Breezy,
Simply, I don't want to switch to micro$oft to print a file, so any help or workaround,
Thanks,

---

### Post by ElVirolo on 2005-10-13
Same prob with HP Deskjet 710C ... Several bugs reports have been sent concerning this problem ...

---

### Post by openmind on 2005-10-13
I fixed my 712C by going into the .conf file and forcing it to use *only* the 712C option by commenting out everything else **except** my printer. (I think it was trying to use 720 by default).

---

### Post by ElVirolo on 2005-10-13
There's only one printer listed in my conf file ... Thanks anyway.

---

### Post by ElVirolo on 2005-10-15
[https://bugzilla.ubuntu.com/show_bug.cgi?id=16066](https://bugzilla.ubuntu.com/show_bug.cgi?id=16066)

---

### Post by RedTDI on 2005-10-15
I [15/Oct/2005:11:10:27 -0400] Adding start banner page "none" to job 32.
I [15/Oct/2005:11:10:27 -0400] Adding end banner page "none" to job 32.
I [15/Oct/2005:11:10:27 -0400] Job 32 queued on 'DeskJet-722C' by 'dennis'.
I [15/Oct/2005:11:10:27 -0400] Started filter /usr/lib/cups/filter/pstops (PID 8672) for job 32.
I [15/Oct/2005:11:10:27 -0400] Started filter /usr/lib/cups/filter/foomatic-rip (PID 8673) for job 32.
I [15/Oct/2005:11:10:27 -0400] Started backend /usr/lib/cups/backend/parallel (PID 8674) for job 32.
E [15/Oct/2005:11:10:31 -0400] PID 8673 stopped with status 3!
I [15/Oct/2005:11:10:31 -0400] Hint: Try setting the LogLevel to "debug" to find out more.

I am getting the same thing with my HP-722c That apparently has the correct driver installed.

Dennis

---

### Post by rdsmith1 on 2005-10-16
I have the  same problem with my HP K-60

---

### Post by RedTDI on 2005-10-16
[QUOTE=openmind]I fixed my 712C by going into the .conf file and forcing it to use *only* the 712C option by commenting out everything else **except** my printer. (I think it was trying to use 720 by default).[/QUOTE]

In which .conf file did you do make these changes in?

Dennis

---

### Post by w.hill on 2005-10-16
I'm trying to print to a Magicolor 2300DL attached to a Win2000 box via SAMBA and Iam suffering from the same problem.

I can print to a Lexmark T614 via IPP!

---

### Post by justmehere on 2005-10-17
[QUOTE=w.hill]I'm trying to print to a Magicolor 2300DL attached to a Win2000 box via SAMBA and Iam suffering from the same problem.

I can print to a Lexmark T614 via IPP![/QUOTE]

I've got a 2300DL network connected and it prints fine from windows, OSX and from firefox in ubuntu but all other ubuntu apps print in black and white only. I'm currently using foo2zjs with a socket connection on port 9100. I've also had it working via lpd and iip but with the same results.

:¬{ Nigel

---

### Post by openmind on 2005-10-17
[quote=RedTDI]In which .conf file did you do make these changes in?
 
Dennis[/quote]
 
Embarrasing I know, but I can't remember right now!
 
I'm at work at the moment, but in about an hour I'll be on my home box and I'll come back.
 
Edit: Sorry, but I just remembered! pnm2ppa.conf, there's a bunch of printers in there that are available for use, I just Commented out (#) all of them except One. My exact model number, and it worked.
 
When I went through the final Breezy upgrades, I had to set it up again from scratch. (Printers in Preferences?).

---

### Post by bluck on 2005-10-17
[QUOTE=w.hill]I'm trying to print to a Magicolor 2300DL attached to a Win2000 box via SAMBA and Iam suffering from the same problem.

I can print to a Lexmark T614 via IPP![/QUOTE]

in this case, on the win2k box have you set up print services for unix?

---

### Post by 11hjpphty76lkjj on 2005-10-17
Hold on you guys.  I help test linux and HP printers so I want to help fix this.  Have you tried installing the HPLIP program?

[http://hpinkjet.sf.net](http://hpinkjet.sf.net)

I've tested dozens and dozens of printers using Ubuntu, Fedora Core, Mandriva and others using HPLIP and HP printers.  Let me review the messasges here and do some quick testing, but if possible check your compatibility on the HPLIP site and use this software.

Aaron

---

### Post by 11hjpphty76lkjj on 2005-10-17
[QUOTE=jordilin]Hi everybody,
I've an old HP Deskjet 820Cxi. It's correctly detected but if I send something to be printed, it doesn't print anything. What's curious is that I can print with the Hoary Live Cd. There's a bug open with the number 16066, but there's hasn't been any solution.
In /var/log/cups/error_log I get this:
I [13/Oct/2005:17:57:40 +0200] New printer 'DeskJet-820C' added by 'root'.
I [13/Oct/2005:17:57:46 +0200] Adding start banner page "none" to job 7.
I [13/Oct/2005:17:57:46 +0200] Adding end banner page "none" to job 7.
I [13/Oct/2005:17:57:46 +0200] Job 7 queued on 'DeskJet-820C' by 'jordilin'.
I [13/Oct/2005:17:57:46 +0200] Started filter /usr/lib/cups/filter/pstops (PID 32566) for job 7.
I [13/Oct/2005:17:57:46 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 32567) for job 7.
I [13/Oct/2005:17:57:46 +0200] Started backend /usr/lib/cups/backend/hp (PID 32568 ) for job 7.
E [13/Oct/2005:17:57:46 +0200] PID 32567 stopped with status 3!
I [13/Oct/2005:17:57:46 +0200] Hint: Try setting the LogLevel to "debug" to find out more.

Which says that the process f**oomatic-rip is stopped with status 3!**!!.
I've compared the settings between Hoary and Breezy and they are the same. Just incredible !! I can print with Hoary, and not in Breezy,
Simply, I don't want to switch to micro$oft to print a file, so any help or workaround,
Thanks,[/QUOTE]


If you are using parallel port try the HPLIP 0.9.6.  Your printer should be supported.  I've tested Ubuntu Hoary and it worked correctly.  I'll try Breezy tommorow.  But it should work.  Installing the dependencies are a tad tricky, the HPLIP site needs to be update.  I'll work with you on the list as needed.  But if you get an error search synaptic for the missing pacakages.  I'll get a full list in the morning.

Aaron

---

### Post by 11hjpphty76lkjj on 2005-10-17
If you are having a specific issue with an HP printer please try these steps first:

go to [http://hpinkjet.sf.net](http://hpinkjet.sf.net)

Check if your printer is supported!  A very large number of them are.

Install these deps:
sudo apt-get install build-essential
sudo apt-get libcupsys2-dev
sudo apt-get snmp
(I think that's all of them..)

Download and install the software per the instructions for DEBIAN.  Although some of the deps are different. (See above)

Make sure to install your printer in your printer manager your system. (kde, gnome, etc)  When you install it make SURE to select the correct URI for your printer, it will look like:

hp:/usb/Deskjet_3900_series/Serial=**********

If there is a specific issue with a specific printer I will gladly test your printer (if I have access to a similiar one) with breezy and verify that it will work (or not depending on the case).  Printing should be easy and straight forward, and really once the software is installed it should be.

However there is a bug in Firefox where it will not print out 'some' websites for some reason, but others work.  So keep that in mind.  But openoffice, gimp, kview and others work great.

Let me know.

Aaron

---

### Post by guiri on 2005-10-19
I had have similar problem with a hp 710c

The solution was in the /etc/pnm2ppa.conf
I use pnm2ppa because 710 is only supported by this
In this document apears the following text

#-----------set the printer model---------------------------
# The printer model will normally be set by a -v <model> command
# line argument. Otherwise, if not set in the configuration file
# it defaults to the 710/720 series. Remove/comment out the line
# "version 0" below to get the default choice.
#
# If there is more than one "version" entry activated, the last one
# will be used. The printer version can also be set with the command line
# option e.g., "-v 720".

version
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000

I only have to put the model in the version line
the tex now is

#-----------set the printer model---------------------------
# The printer model will normally be set by a -v <model> command
# line argument. Otherwise, if not set in the configuration file
# it defaults to the 710/720 series. Remove/comment out the line
# "version 0" below to get the default choice.
#
# If there is more than one "version" entry activated, the last one
# will be used. The printer version can also be set with the command line
# option e.g., "-v 720".

version 710
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000

I suppose that with anothers printers the system configuration tool don't select the printer.

---

### Post by openmind on 2005-10-19
[quote=guiri]I had have similar problem with a hp 710c
 
The solution was in the /etc/pnm2ppa.conf
I use pnm2ppa because 710 is only supported by this
In this document apears the following text
 
#-----------set the printer model---------------------------
# The printer model will normally be set by a -v <model> command
# line argument. Otherwise, if not set in the configuration file
# it defaults to the 710/720 series. Remove/comment out the line
# "version 0" below to get the default choice.
#
# If there is more than one "version" entry activated, the last one
# will be used. The printer version can also be set with the command line
# option e.g., "-v 720".
 
version
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000
 
I only have to put the model in the version line
the tex now is
 
#-----------set the printer model---------------------------
# The printer model will normally be set by a -v <model> command
# line argument. Otherwise, if not set in the configuration file
# it defaults to the 710/720 series. Remove/comment out the line
# "version 0" below to get the default choice.
#
# If there is more than one "version" entry activated, the last one
# will be used. The printer version can also be set with the command line
# option e.g., "-v 720".
 
version 710
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000
 
I suppose that with anothers printers the configuration tool don't uncoment the printer.[/quote]
 
Thanks man, that's exactly what I did, (Except mine was the 712). That's what I was trying to describe above.

---

### Post by guiri on 2005-10-19
[QUOTE=openmind]Thanks man, that's exactly what I did, (Except mine was the 712). That's what I was trying to describe above.[/QUOTE]

it was nothing

---

### Post by Mrtn on 2005-10-19
I have a HP Deskjet 895 Cxi and I also cannot get it to work :(

If anybody knows how I could fix this I'd be very grateful.

Edit: I already got it to work. It seemed it needed a restart after connecting before it would print.

---

### Post by irv on 2005-10-19
I had the same problem with My HP Laserjet 1300. It would print to the print Q and never go to the printer. I found a fix. I had two printer setup when I did the upgrade to 5.10 so I uninstalled both of them and then reinstalled the 1300. I just tried printing from Thunderbird and Open Office Writer and everthing printed out. Problem solved. Hope this helps all.:p :p  This calls for two smiles.

---

### Post by Pocito on 2005-10-20
[QUOTE=ElVirolo]Same prob with HP Deskjet 710C ... Several bugs reports have been sent concerning this problem ...[/QUOTE]
I can't print using my locally connected HP Deskjet 710C. This printer works in several other distos- Mandriva, Fedora, PClinuxOS. Is there no way to get it working with Ubuntu?

Problem solved. I edited  /etc/pnm2ppa.conf as suggested by guiri in an earlier post in this thread. Now the printer works well.

Thanks guiri!!

---

### Post by w.hill on 2005-10-21
The Magicolor 2300DL is directly attached to the Win2000 box with a parallel cable. The printer is shared.

I cannot print to the share from Breezy. Job shows up as "abort". I can print to the same share from two Gentoo boxes. (Both SPARCs).

I can print from Breezy to the T614 using IPP. 

smbclient shows the existence of the share (not suprising) from Breezy.

---

### Post by Pocito on 2005-10-21
Problem solved. I edited the /etc/pnm2ppa.conf file as suggested by guiri in an earlier post in this thread.

Thanks guiri!!!

---

### Post by guiri on 2005-10-21
[QUOTE=Pocito]Problem solved. I edited the /etc/pnm2ppa.conf file as suggested by guiri in an earlier post in this thread.

Thanks guiri!!![/QUOTE]

it was nothing

---

### Post by jordilin on 2005-10-21
Mr. Guiri pointed out the correct answer. Bug solved!!
The problem is solved by editing the /etc/pnm2ppa.conf and writing your printer model. I can now print with my Hp Deskjet 820 Cxi,

---

### Post by babylon_n_ting on 2006-01-01
I edited pnm2ppa.conf to refer to 'version 710' (I have a Deskjet 710C). After making this change I could print OK. But as soon as I tried to access the printer from a Windows XP machine via Samba the printer stopped working and has not worked since.

Any ideas?

---

### Post by BLTicklemonster on 2007-11-12
Deskjet 720C. I followed everything in here, and it won't print.

---

### Post by 11hjpphty76lkjj on 2007-11-13
Are you using the hplip that was pre-installed with ubuntu?  Can you run hp-check and post the log?  If you are using the deb possible to uninstall and install from source?  [http://hplip.sf.net](http://hplip.sf.net).

A

---

### Post by guiri on 2007-11-15
> **BLTicklemonster said:**
> Deskjet 720C. I followed everything in here, and it won't print.

Dear BLTicklemonster, its many time ago I changed this printer by another. I dont remember how configure it. I wish you resolve problen soon

---

