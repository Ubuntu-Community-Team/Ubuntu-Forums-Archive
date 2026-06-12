---
title: "stumped with printer setup"
date: 2009-02-28
forum: General Help
---

### Post by worksofcraft on 2009-02-28
I have HP Photosmart P1000. This printer has always worked with Windows. On Linux (Ubuntu 8.04) it prints the test page just fine... but...

When I come to print a simple text file from gedit, or even using Open Office what I get are countless pages with one single line of gibberish across the top of an otherwise blank page. It looks absolutely nothing like the Print Preview of my document.

I have tried switching everything off and restarting it but same result.
I have no idea what to try next :confused:
any help and suggestions will be greatly appreciated

---

### Post by hansdown on 2009-02-28
Hi worksofcraft.

There is a solved thread that should help.

[http://ubuntuforums.org/archive/index.php/t-960123.html](http://ubuntuforums.org/archive/index.php/t-960123.html)

---

### Post by kyphi on 2009-02-28
Linuxprinting reports that this unit works perfectly with the hpijs driver.  For full functionality use the hplip driver which includes the hpijs driver.

The current version of hplip is 3.9.2.

Download the driver from [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Full installation instructions are on this site.

---

### Post by Matsukaze on 2009-02-28
Also see the [Openprinting]("http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_P1000") site for information on the best driver to use with your printer. HP has a [support site]("http://hplipopensource.com/hplip-web/index.html") if you're using their HPLIP driver.

---

### Post by worksofcraft on 2009-02-28
Thanks for those excellent links :)
Alas  :( it looks like there is still some sort of problem:

It says

Print queue setup failed
Please restart CUPS and try again

so I went into System-Administration-Services and found a thing called Printer service (cupsys) which I unticked, reticked and tried
sudo hp-setup again... I even tried restarting the computer with and without cupsys... it definitely dowsn't like it if no print service running, but otherwise same result :confused:

I'll also try the hp support site but meanwhile if anyone has ideas... thanks in advance!

---

### Post by kyphi on 2009-02-28
Usually you plug the printer into the USB slot and start it up and it works.

I have never used "sudo hp-setup" on any of my HP printers.

In Firefox try: [http://localhost:631](http://localhost:631) and click on Printers.  Your printer should be identified.

Your printer is obviously working but not communicating with your computer.

---

### Post by worksofcraft on 2009-03-01
Sure enough localhost:631 identifies my printer

Description: p1000
Location:
Printer Driver: HP Photosmart p1000 hpijs, hpijs 3.9.2
Printer State: processing, accepting jobs, published.
Device URI: hp:/usb/PhotoSmart_P1000?serial=ES07D170W1HP 

Sadly when I click on "print test page" a little errors box pops up to tell me there is a communication error and I can't vene get the line of gibberish anymore :(

---

### Post by kyphi on 2009-03-01
Did you download and install the hplip-3.9.2.run file?

To install it, "cd" (change directory) to the location of the file on your computer and type ```
sh hplip-3.9.2.run
```

When asked, choose "a" for automatic installation.

---

### Post by worksofcraft on 2009-03-01
thanks, yes I did that, but had to do a chmod 777 on it first.
It progresses fine until it gets to where I have to either unplug and replug your printer, or reboot the computer and run hp-setup (tried both) and that is where I get "Printer queue setup failed :confused:".

---

### Post by kyphi on 2009-03-01
Does this walkthrough tell you anything new?

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by Matsukaze on 2009-03-01
If you haven't already, install the hplip-doc package ("apt-get install hplip-doc" or use Synaptic). Open the help file at file:///usr/share/doc/hplip-doc/HTML/index.html. There is a troubleshooting section in this file that may help. One thing it suggests is to run "hp-check -t" which will give a bunch of information about any problems with your setup.

---

### Post by worksofcraft on 2009-03-02
> **kyphi said:**
> Does this walkthrough tell you anything new?

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Nice walk through but it sadly doesn't help with my printer problem :(

Just to be sure the hardware is working I made my computer dual boot and checked that it really can print OK from Windows (confirmed).

So I'm trying to discover how I get CUPS diagnostics... like is there a log file somewhere? The search for "diagnostics" in localhost:631 revealed nothing.

I'm plugging in an old canon i350 printer previously known to work, but that now produces no output: Somehow the whole CUPS system appears to have got broken so even buying a new printer probably won't help.

---

### Post by kyphi on 2009-03-02
> I'm trying to discover how I get CUPS diagnostics... like is there a log file somewhere? 

[http://www.cups.org/articles.php?L198+TFAQ+Q](http://www.cups.org/articles.php?L198+TFAQ+Q)

---

### Post by worksofcraft on 2009-03-02
> **Matsukaze said:**
> If you haven't already, install the hplip-doc package ("apt-get install hplip-doc" or use Synaptic). Open the help file at file:///usr/share/doc/hplip-doc/HTML/index.html. There is a troubleshooting section in this file that may help. One thing it suggests is to run "hp-check -t" which will give a bunch of information about any problems with your setup.


I removed all the hp stuff and tried again.
sh hplip-3.9.2.run
progress nicely up to the point where it detects my printer and then it just says "Print queue setup failed , please restart CUPS and try again".
Restarting CUPS and trying again produces exactly the same result.

hp-check -t

produces a lot of OK messages up to the point where it says:

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
PDF
---
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: cups-pdf:/
PPD: /etc/cups/ppd/PDF.ppd
PPD Description: Generic PDF file generator
Printer status: printer PDF is idle.  enabled since Wed 02 Jul 2008 22:22:03 NZST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
PHOTOSMART_P1000
----------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/PhotoSmart_P1000?serial=ES07D170W1HP
PPD: /etc/cups/ppd/PHOTOSMART_P1000.ppd
PPD Description: HP Photosmart p1000 hpijs, hpijs 3.9.2
Printer status: printer PHOTOSMART_P1000 now printing PHOTOSMART_P1000-43.  enabled since Tue 03 Mar 2009 11:20:06 NZDT

>>> This sort of confirms it was unable to set up the print queue but doesn't give me any idea why not :confused:

Meanwhile I've managed to have a look at the CUPS debug output so I'll post the part hoping I found the relevant bits.

p.s. In CUPS it does identify my printer:
Description: PHOTOSMART_P1000
Location:
Printer Driver: HP Photosmart p1000 hpijs, hpijs 3.9.2
Printer State: processing, accepting jobs, published.
Device URI: hp:/usb/PhotoSmart_P1000?serial=ES07D170W1HP

---

### Post by worksofcraft on 2009-03-02
> **kyphi said:**
> [http://www.cups.org/articles.php?L198+TFAQ+Q](http://www.cups.org/articles.php?L198+TFAQ+Q)

Thanks, that is very helpful... sometimes I wonder how to figure out which directory files are stored in...

So I cleaned out the CUPS log file and restarted CUPS
I [03/Mar/2009:11:19:06 +1300] Listening to 127.0.0.1:631 (IPv4)
I [03/Mar/2009:11:19:06 +1300] Listening to /var/run/cups/cups.sock (Domain)
I [03/Mar/2009:11:19:06 +1300] Loaded configuration file "/etc/cups/cupsd.conf"
I [03/Mar/2009:11:19:06 +1300] Using default TempDir of /var/spool/cups/tmp...
I [03/Mar/2009:11:19:06 +1300] Configured for up to 100 clients.
I [03/Mar/2009:11:19:06 +1300] Allowing up to 100 client connections per host.
I [03/Mar/2009:11:19:06 +1300] Using policy "default" as the default!
I [03/Mar/2009:11:19:06 +1300] Full reload is required.
I [03/Mar/2009:11:19:06 +1300] Loaded MIME database from '/etc/cups': 36 types, 39 filters...
D [03/Mar/2009:11:19:06 +1300] Loading printer PDF...
D [03/Mar/2009:11:19:06 +1300] Loading printer PHOTOSMART_P1000...
etcetera

>>> then I go in to localhost:631 and print test page
no apparent problems for many messages until the following

....Get-Jobs ipp://localhost:631/printers/PHOTOSMART_P1000
D [03/Mar/2009:11:20:18 +1300] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [03/Mar/2009:11:20:18 +1300] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [03/Mar/2009:11:20:18 +1300] cupsdCloseClient: 12
D [03/Mar/2009:11:20:18 +1300] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [03/Mar/2009:11:20:18 +1300] PID 25907 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [03/Mar/2009:11:20:18 +1300] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [03/Mar/2009:11:20:18 +1300] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [03/Mar/2009:11:20:18 +1300] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [03/Mar/2009:11:20:18 +1300] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [03/Mar/2009:11:20:18 +1300] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [03/Mar/2009:11:20:18 +1300] cupsdReadClient: 7 GET /cups.css HTTP/1.1
D [03/Mar/2009:11:20:18 +1300] cupsdAuthorize: Authorized as cjs using Basic
D [03/Mar/2009:11:20:18 +1300] cupsdSendError: 7 code=304 (Not Modified)
D [03/Mar/2009:11:20:18 +1300] cupsdReadClient: 7 GET /images/top-left.gif HTTP/1.1
D [03/Mar/2009:11:20:18 +1300] cupsdAuthorize: Authorized as cjs using Basic
D [03/Mar/2009:11:20:18 +1300] cupsdSendError: 7 code=304 (Not Modified)
D [03/Mar/2009:11:20:18 +1300] cupsdAcceptClient: 10 from localhost:631 (IPv4)
D [03/Mar/2009:11:20:18 +1300] cupsdAcceptClient: 12 from localhost:631 (IPv4)
D [03/Mar/2009:11:20:18 +1300] cupsdReadClient: 10 GET /images/top-middle.gif HTTP/1.1
D [03/Mar/2009:11:20:18 +1300] cupsdAuthorize: Authorized as cjs using Basic
D [03/Mar/2009:11:20:18 +1300] cupsdSendError: 10 code=304 (Not Modified)
D [03/Mar/2009:11:20:18 +1300] cupsdAcceptClient: 13 from localhost:631 (IPv4)
D [03/Mar/2009:11:20:18 +1300] cupsdReadClient: 12 GET /images/top-right.gif HTTP/1.1
D [03/Mar/2009:11:20:18 +1300] cupsdAuthorize: Authorized as cjs using Basic
D [03/Mar/2009:11:20:18 +1300] cupsdSendError: 12 code=304 (Not Modified)
D [03/Mar/2009:11:20:18 +1300] cupsdReadClient: 7 GET /images/tab-right.gif HTTP/1.1
D [03/Mar/2009:11:20:18 +1300] cupsdAuthorize: Authorized as cjs using Basic
D [03/Mar/2009:11:20:18 +1300] cupsdSendError: 7 code=304 (Not Modified)

>>> So the next question is what can the error 304 mean ?

p.s. ATM I don't see much point persevering with the Canon printer as it too won't print the test page and I'll just end up getting more confused.

---

### Post by kyphi on 2009-03-03
As I understand it, error 304 means that a previously failed connection cannot be rectified.

The only things that I can think of is that a dependency is not satisfied - that would have shown up as a notification when you installed hplip.

Try ```
apt-cache depends hplip
```

You might like to post this problem on Launchpad under this heading: Print queue setup failed, please restart CUPS and try again.

[https://launchpad.net/hplip](https://launchpad.net/hplip)

---

### Post by worksofcraft on 2009-03-04
> **kyphi said:**
> As I understand it, error 304 means that a previously failed connection cannot be rectified.

The only things that I can think of is that a dependency is not satisfied - that would have shown up as a notification when you installed hplip.

Try ```
apt-cache depends hplip
```

You might like to post this problem on Launchpad under this heading: Print queue setup failed, please restart CUPS and try again.

[https://launchpad.net/hplip](https://launchpad.net/hplip)

thanks
I suspect the problem could be one of...
  Conflicts: hpijs
  Conflicts: <hplip-base>
  Replaces: <hplip-base>
  Replaces: hplip-data

Is there some way to remove the conflicts completely before I retry installation?

Meanwhile, yes I will try that Launchpad thing. I'm desperately trying to migrate away from Windows for my work but lack of printing capability is not inspiring any confidence in my coleagues either :( If only we had some Linux gurus on site... but then perhaps I can fill that spot... eventually ;)

---

### Post by kyphi on 2009-03-04
What do you want to reinstall - is it Ubuntu? CUPS? HPLIP?

I would try [https://launchpad.net/hplip](https://launchpad.net/hplip) first before doing anything else.

I run three HP printers - just plug them in and everything works.


Addendum:  Please check that you have permission to print by going to System, Administration, Users and Groups.  Unlock the screen by entering your login password, click on your name to highlight it and open "Properties" followed by "User Privileges".  Ensure that all the boxes are ticked.  After that click OK and then Close.  If all the boxes were not ticked, you will have to log out and then back in again.

---

### Post by worksofcraft on 2009-03-12
Thanks Kyphi :) The input is appreciated and yes I did make sure I had all the permissions. Alas I had work to do and I would quite happily have ditched the hp printer and gone back to my old cannon but since installing hplip, no printers work anymore... so back to Windows I went :(

I have no idea how to uninstall hplip and suspect it would create a whole new set of problems. Hp photosmart isn't exactly new technology, so perhaps it will all work if I reformat the hard drive and start from scratch, or perhaps it just doesn't work full stop... another dead end waste of time.

---

### Post by kyphi on 2009-03-12
I am sorry to read that your efforts have not met with success.  I also run an HP Photosmart which works perfectly and have recently upgraded hplip to version 3.9.2.
I am at a loss to understand why the hplip installation does not work for you and the only course of action I can recommend is to post your HP printer problem on Launchpad: [https://launchpad.net/hplip](https://launchpad.net/hplip).

I assume that you have set your printer as the default printer in System, Administration, Printing.

---

### Post by worksofcraft on 2009-04-12
Thanks Kyphi... I did persevere with launchpad and the conclusion is that this is an old printer for which software is supplied "as is". Win XP is apparently less fussy about USB errors than Linux which might explain why that still works, but I tested on Windows 7 beta and that doesn't look like it is going to work with existing P1000 drivers while no new ones are expected... so looks like I need a new printer. Fingers crossed I pick one that will enjoy long term support ;D


> **kyphi said:**
> I am sorry to read that your efforts have not met with success.  I also run an HP Photosmart which works perfectly and have recently upgraded hplip to version 3.9.2.
I am at a loss to understand why the hplip installation does not work for you and the only course of action I can recommend is to post your HP printer problem on Launchpad: [https://launchpad.net/hplip](https://launchpad.net/hplip).

I assume that you have set your printer as the default printer in System, Administration, Printing.

---

### Post by worksofcraft on 2009-06-10
Just for the record...
Installed Ubuntu Jaunty Jackalope (9.04) on a brand new disk drive used hplip-3.9.4b This time it found the printer and didn't complain about setting up and installing, but I still can't get it to print anything :(

... luckily I can still boot to Windows XP and that works fine when I want to print.

---

### Post by 4Orbs on 2009-06-10
A few days ago I set up my printer on Xubuntu for the first time and nearly went nuts trying to overcome a similar problem. I finally found the solution on the CrunchBang forum. In the folder /etc/cups/ssl there are (only) two symlinks that point somewhere incorrectly. I renamed those symlinks (as root) by adding -bogus to the filename and my printer immediately began working exceptionally well. It's something you may want to try. If it doesn't work, rename the links back to original.

---

### Post by worksofcraft on 2009-06-11
cjs@cjsUbuntu:~$ cd /etc/cups/ssl
bash: cd: /etc/cups/ssl: Permission denied
cjs@cjsUbuntu:~$ sudo cd /etc/cups/ssl
[sudo] password for cjs: 
sudo: cd: command not found
cjs@cjsUbuntu:~$ 


omg **** Linux I've had enough :P

---

### Post by colau on 2009-06-11
> **worksofcraft said:**
> cjs@cjsUbuntu:~$ cd /etc/cups/ssl
bash: cd: /etc/cups/ssl: Permission denied
cjs@cjsUbuntu:~$ sudo cd /etc/cups/ssl
[sudo] password for cjs: 
sudo: cd: command not found
cjs@cjsUbuntu:~$ 


omg **** Linux I've had enough :P
```

su
password:
cd /etc/cups/ssl

```

---

### Post by worksofcraft on 2009-06-13
su
Password: 
su: Authentication failure


I think Ubuntu doesn't have a user "root"... no doubt there is some way to create one but with all this administrative complexity preventing me from actually using my personal computer...

Does it not suggest that Linux is simply an inappropriate choice of Operating System in the home?

---

### Post by constl on 2009-08-10
I had the same problem and have solved it as described on the following launchpad site:
[U][https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/405193](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/405193)
[/U]
Afterwards I had to do a...
  	 	 	 	 	 	  sudo chmod 644 024_hpmud.rules
...and a reboot of the system

---

### Post by worksofcraft on 2009-12-22
Well I'm baffled... After a break from Linux, I rebooted ubuntu, let it do it's updates and hey-presto the good old P1000 is working just fine now even though I didn't change any settings. I suspect an unidentified upgrade fixed the problem so I'll just mark it as solved even it's still a total mystery to me. Thanks all for your input either way :)

---

