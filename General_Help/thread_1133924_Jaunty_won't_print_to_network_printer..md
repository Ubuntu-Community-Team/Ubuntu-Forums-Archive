---
title: "Jaunty won't print to network printer."
date: 2009-04-23
forum: General Help
---

### Post by Captain Rotundo on 2009-04-23
I upgraded to jaunty yesterday, and now whenever I print to one of two network printers that I use many times a day I get error messages that it may not be connected. the printer properties say:

Processing - recoverable: Network host '192.168.1.119' is busy; will retry in 30 seconds...

Prior to the upgrade it worked fine, both printers work on other machines, I have now tried removing the printers, re-adding them, rebooting and various other combinations of them.

I don't even know where to start to troubleshoot this, any pointers would be great.

---

### Post by Captain Rotundo on 2009-04-23
/var/log/cups/error_log says:

cupsdAuthorize: Local authentication certificate not found!

---

### Post by adonet on 2009-04-24
Same problem here. Printer works in Intrepid, printer works with a small workaround in Hardy. prinyter worked fine in Feisty. Also works fine from Vista and XP.
In Jaunty is doens't print. The same story that happened the first 2 monts of Hardy seems to happen again.

I have an ordinairy HP laserjet connected to a printserver at 192.168.2.10 and jaunty is complaining that the printer might not be connected.

Is there any workaround?

---

### Post by Peter09 on 2009-04-24
Have you tried reinstalling the printer?

---

### Post by Captain Rotundo on 2009-04-24
Every combination of re-installing and re-booting that you can imagine has been tried.  Also I have no problem printing from other machines running jaunty, so I am only seeing it on this one.

---

### Post by Peter09 on 2009-04-25
Have you tried the cups interface using a browser

[http://localhost:631](http://localhost:631)

---

### Post by Captain Rotundo on 2009-04-27
what username and password should I use for this ?

---

### Post by adonet on 2009-04-27
> **Captain Rotundo said:**
> what username and password should I use for this ?

I used my own username and password. I get the same error messages.

I got a series of updates of CUPS this afternoon, but the problem persists.

---

### Post by Captain Rotundo on 2009-04-27
I have confirmed this myself, network printing is completely broken for me in jaunty.

---

### Post by jfrelin on 2009-04-27
Same here- worked fine on intrepid, did the upgrade, now after many reinstalls, new drivers, etc can't get it to work on D-link print server.  Regular hardwired network printer works fine.

---

### Post by celem on 2009-04-27
I have a similar, but not identical problem. Since I feel that this is really a Networking/SAMBA problem, I posted there. My post is at:
[http://tinyurl.com/cc2yhv](http://tinyurl.com/cc2yhv)

---

### Post by andrewskinner3 on 2009-04-30
I have the same problem - HP2600n prints fine from 8.10 but does not print from jaunty. I have installed latest version of HPLIP (says its udated for 9.04) but although it is now detected by the setup process the printing system itself cannot connect to the printer.:(

---

### Post by adonet on 2009-05-01
After many updates the printer still isn't working. I posted a bug on launchpad, but no result so far.

---

### Post by bailunrui on 2009-05-01
I think this is related to problem that I've been having:
[http://ubuntuforums.org/showthread.php?t=1144217]("http://ubuntuforums.org/showthread.php?t=1144217").

I still haven't found a solution.

---

### Post by JamieKitson on 2009-05-03
Have you guys tried enabling browsing in cups.conf?

---

### Post by srdjo on 2009-05-03
I have the same problem.

Jaunty clean install - browsing enabled in config.

I get the same error for 3 different printers.

Don't want to go back to 8.10, but I must use printers.

p.s. All worked fine on 8.04 and 8.10.

Tried to delete cups and install it again - no luck.

Can anyone help us with this ?

---

### Post by srdjo on 2009-05-03
This seems to be a big problem since there are about 8-10 threads about printing problem with 9.04 only on first 7 pages.

Can it be that no one knows what could be wrong ?

---

### Post by Lety on 2009-05-08
In my freshly installed Jaunty to print over Windows network I install my printer driver (Samsung). Then I go to /usr/share/ppd/Samsung/ - there are lots of Gzipped ppd files for a range of printer models. I choose the model I need and extract MyPrinterModel.ppd file to /usr/share/ppd/Samsung/ .
The I go to System-> Administration->Printing, choose New Printer ->Network Printer -> Windows printer via Samba.
Under SMB Printer type, for example,  smb://workgroup/MachineName/   , click browse then. The window appears with the machine name and printer name - choose printer. I choose the printer and click Forward. In the next window I check 'Provide ppd file ' and find the previously extracted file (/usr/share/ppd/Samsung/MyPrinterModel.ppd). After that I finish the wizard and print over the network is working.  
I'm not sure whether you must install any printer drivers, but what required is a ppd-file for your printer. 

There are ppd-files for some printers: /usr/share/ppd/openprinting/

P.S. Checked on Jaunty and Intrepid with two remote Windows-running machines with one shared printer each .

---

### Post by rayfos on 2009-05-13
My experience is similar except that with a usb local printer I got no errors and no print output (hp2410 and a Dell 530s jaunty).

Multiple re-installs of printer.

Any suggestions would be much valued.

Thanks

:p

---

### Post by phflupp on 2009-05-18
I've been reading this thread and others, but even after installing non-ubuntu versions of HPLIP, completely removing them, and re-installing the Ubuntu versions I still cannot connect to my D-Link 323 network printer -which broke for me with the 9.04 Jaunty upgrade.

The only thing I can offer this discussion is that CUPS reports a network connection error.

I have tried various network printer connection options. None worked for me.
-P.

---

### Post by nx2ho on 2009-07-01
Ubuntu 9.04 installed on FS Amilo Pro. Samba sharing of the WinXP printer did not work, as in the above messages. I could see and use SharedFolder and other shared (in WinXP) but no printer ...

Had in the same network an older installation of Ubuntu 9.04, updated from 7.04 ???? (not quite sure..)   Anyway, the printer sharing worked perfectly.

Compared the installed CUPS packages in both.  The older installation had

kde-printer-applet   4:4.2.2-0ubuntu2.

Installed the above in the new (laptop) machine. 

And guess what ?????

Thereafter I could install and use my samba printer on WinXP.

Is there a package missing in Ubuntu 9.04  ??

Somebody pls check....

---

### Post by Christian_Joe_Linux on 2009-08-13
HP1200PSC "Can't create temporary file"
	Description: USBprinter
Location: USB
Printer Driver: HP PSC 1200 Series hpijs, 3.9.2
Printer State: idle, accepting jobs, published.
Device URI: hp:/usb/psc_1200_series?serial=MY39JF216H5H

---

### Post by rcayea on 2009-08-13
If it is an HP printer, I would start here...

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by rogerw05465 on 2009-09-18
Any further update on this issue? I have a Brother MFC-6800 and cannot get it printing - although it did for a while(?). Then I tried the Linksy Print Server, it failed, tried to revert to straight USB and have not had it working since. No errors showing, print job goes through - black holed in the printer itself, by the look.

---

### Post by Victorino Tom on 2009-09-18
Hi,

        The got Ubuntu Linux server to share it's printer with Windows XP. After setting up samba  and getting it to a state where the server PC appeared in the workgroup Also make sure Ubuntu knows about the printer. CUPS, the unix printing thing, is installed by default on Ubuntu and all the above is too trivial to comment on. Unfortunately, sharing the printer is not so trivial.



 [Discount printer copier]("http://www.tonerpirate.com")

---

### Post by colin.p on 2009-09-18
I got my HP 6500 wireless printer working flawlessly after a long while searching. In my case it was because for some reason hplip installed the printer using its host name, instead of the IP. After posting to the launchpad question forum, I got an answer:
[https://answers.launchpad.net/hplip/+question/81249](https://answers.launchpad.net/hplip/+question/81249)
When I start the HP Device Mgr, the printer is located imediately and all functions work. On my wifes Vista laptop, it takes five minutes, or so, for it to find the printer, so it seems that it is having the same problem with finding the printer by host name.

Colin

---

