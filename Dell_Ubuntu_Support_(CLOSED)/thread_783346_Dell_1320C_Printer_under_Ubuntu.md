---
title: "Dell 1320C Printer under Ubuntu"
date: 2008-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jamesc on 2008-05-05
Just to say I've figured out how to get my DELL 1320C Printer working under Ubuntu, (gutsy, but hardy as well) plugged into the network.  It doesn't seem to have a standard printer driver available.

I followed the instructions at:

[http://www.xtr.org/jeff/notes/linux/dell_1320c_printer_linux_install.txt](http://www.xtr.org/jeff/notes/linux/dell_1320c_printer_linux_install.txt)

*except*

After downloading the tar with an /rpm inside I used 'alien' to convert it to a .deb, then had to add the user to the lpadmin group since I was getting a password prompt when installing. (Didn't happen with an attached USB printer...)  Make sure to set the option for the paper feeder, but then set the default to be tray one before you print a test page.

Just recording this here for anyone else looking for hints and or so when I forget how I did it in several months I can look it up.


-James

---

### Post by blizzrdof77 on 2008-05-08
Hey,

I have been trying to get my dell "1320c" printer working on Hardy Heron 8.04 Ubuntu, but I have an Intel Core2 processor, which will not work with i386 rpms.  Does anyone know how i can either convert or somehow acquire a driver that will work for my laptop (dell xps m1330).

Thanks!

---

### Post by jamesm.tecz on 2008-08-30
Try plugging in a flash disk.
Boot to a i386 Live CD of Hardy
Download the driver from the above listed site.
Alienize the rpm
Copy the .deb to your flash
Kill your 'chine
Reboot
Run dpkg on the file.....

post back let us know if it works :)

---

### Post by davidstillson on 2008-09-16
this works like a charm!  Thanks for finding a fix for this...

At first, I was adding the optional tray, not selecting tray 1 as the default tray, but once I figured it out, it was smooth sailing.

---

### Post by Mithrilhall on 2008-11-07
This worked great.

Thanks for posting.

---

### Post by Tilex on 2008-12-02
Hi!!

It worked great on my 8.04 32-bit laptop but I when I install it on my 8.10 64-bit PC, it does not work at all.

I mean, I install the driver, choose it as FX->C252..., change the printer options at the end, and whenever I try to print a test page it says it sent it to the printer but in the printer manager I see the job as being "stopped" right away.  The printer never wakes up from standby and the test page never gets printed.

Any thought guys?

---

### Post by ytsejam1138 on 2008-12-02
I'm also having a similar problem now with the 1320c and 8.10.  I can print the test page fine, but I cannot print anything else that longer than one page.  I have to select each page individually to print.  Doesn't matter what it is, PDF, DOC, TXT.

---

### Post by Tilex on 2008-12-02
I've got exactly the same problem.

I can now send a job to the printer, but if the document is more than 1 page it prints 1 page, then the yellow exclamation mark blinks.  If I press the "continue" button, it'll re-print the same page and blink again.

I had another 20-page document where it printed 2 pages at the time before blinking.

Very weird...

Has anybody successfully fixed this?

---

### Post by figjam on 2008-12-12
Thanks! These work brilliantly. Installed on 8.10

---

### Post by Tilex on 2008-12-12
Congrats!
Do you have 32-bit or 64-bit system?
Because on 64-bit it seems that we can't print more than 2 pages in a row...

---

### Post by ytsejam1138 on 2008-12-31
I have found the solution to get this printer working properly.

```
System > Administration > Printing and right click on your printer, selecting Properties. 
Settings > Device URI
If you see something like socket://your_printer_ip_address:9100 just change socket to lpd and remove the :9100 off the end. 
Then click on apply.
```


Mine didn't have the 9100 port, so I just changed socket to lpd and it works perfect now.  I found the solution on this webpage:  [http://p-s.co.nz/wordpress/?p=227](http://p-s.co.nz/wordpress/?p=227)

---

### Post by dmitriyp13 on 2009-04-02
I got this to work out on my x64 and Intrepid:

1. download the above zip file (Xerox C525, [http://www.fujixerox.com.au/support/downloaddriver?productId=307&operatingSystemCode=Linux](http://www.fujixerox.com.au/support/downloaddriver?productId=307&operatingSystemCode=Linux))

2. extract the zip file to get the rpm file

3. using an x86 system and alien, convert the rpm to a deb file

4. copy the resulting deb file back to the x64 system and install it with the "--force-architecture" option

5. install the printer as usual, but when asked for the printer make, choose the ppd file from "/usr/share/cups/model/FujiXerox/en/FX_DocuPrint_C525_A_AP.ppd"

6. enjoy


I can post the deb file if its helpful to others

---

### Post by Tilex on 2009-04-02
Do you guys have the "can't print more than 2 pages in a row" issue ?

Under OpenOffice or Okular Document Viewer, I can't print out more than 2 pages at a time (the printer stops and a yellow light blinks).

However, with Office 2007 (installer under Wine) and Acrobat Reader 8, it prints fine.

[-o<

---

### Post by ytsejam1138 on 2009-04-02
> **ytsejam1138 said:**
> I have found the solution to get this printer working properly.

```
System > Administration > Printing and right click on your printer, selecting Properties. 
Settings > Device URI
If you see something like socket://your_printer_ip_address:9100 just change socket to lpd and remove the :9100 off the end. 
Then click on apply.
```


Mine didn't have the 9100 port, so I just changed socket to lpd and it works perfect now.  I found the solution on this webpage:  [http://p-s.co.nz/wordpress/?p=227](http://p-s.co.nz/wordpress/?p=227)

After doing the above, I'm now able to print multiple pages at one time.

---

### Post by ytsejam1138 on 2009-04-07
> **Tilex said:**
> Do you guys have the "can't print more than 2 pages in a row" issue ?

Under OpenOffice or Okular Document Viewer, I can't print out more than 2 pages at a time (the printer stops and a yellow light blinks).

However, with Office 2007 (installer under Wine) and Acrobat Reader 8, it prints fine.

[-o<

Tilex, your problem might lie with Kubuntu.  Xubuntu also has the same issues.  [http://ubuntuforums.org/showpost.php?p=7030706&postcount=10](http://ubuntuforums.org/showpost.php?p=7030706&postcount=10)  So far the only workaround has been to install Ubuntu.

---

### Post by ikkepjo on 2009-04-13
Unfortunately, somehow now ubuntu does not work either??? 

Now I have identical 3 page behavior in both Ubuntu and Xubuntu, and it still continues to work perfectly in XP ... drives me up the wall ...

Peter

---

### Post by makley on 2009-07-24
> **dmitriyp13 said:**
> I got this to work out on my x64 and Intrepid:

1. download the above zip file (Xerox C525, [http://www.fujixerox.com.au/support/downloaddriver?productId=307&operatingSystemCode=Linux](http://www.fujixerox.com.au/support/downloaddriver?productId=307&operatingSystemCode=Linux))

2. extract the zip file to get the rpm file

3. using an x86 system and alien, convert the rpm to a deb file

4. copy the resulting deb file back to the x64 system and install it with the "--force-architecture" option

5. install the printer as usual, but when asked for the printer make, choose the ppd file from "/usr/share/cups/model/FujiXerox/en/FX_DocuPrint_C525_A_AP.ppd"

6. enjoy


I can post the deb file if its helpful to others

I'm a N00b--it would be helpful to me. Will this work on Jaunty?

---

### Post by pp. on 2009-07-25
The procedure in post #1 works very well in 9.04 on an Asus eee for a networked printer. No need to add my user account to the lpadmin group as it already was there.

The detailed instruction says to ***select "FX"***. It took me a while until I realised that "FX" was an entry in the list of manufacturers (where "Xerox" is another entry).

Thanks for posting. Saved me much embarrassment since I had failed to check the vendor's specification and assumed that the printer worked with Linux out of the box.

---

### Post by dmitriyp13 on 2009-07-28
**Update: **This works in Jaunty too.

> **dmitriyp13 said:**
> I got this to work out on my x64 and Intrepid:

1. download the above zip file (Xerox C525, [http://www.fujixerox.com.au/support/downloaddriver?productId=307&operatingSystemCode=Linux](http://www.fujixerox.com.au/support/downloaddriver?productId=307&operatingSystemCode=Linux))

2. extract the zip file to get the rpm file

3. using an x86 system and alien, convert the rpm to a deb file

4. copy the resulting deb file back to the x64 system and install it with the "--force-architecture" option

5. install the printer as usual, but when asked for the printer make, choose the ppd file from "/usr/share/cups/model/FujiXerox/en/FX_DocuPrint_C525_A_AP.ppd"

6. enjoy


I can post the deb file if its helpful to others

Since people keep asking me for this deb file, I'll post it here.  Enjoy.

---

### Post by yamagami on 2009-11-26
After following all the steps to run this on Jaunty 64bit, using the deb file posted, changing socket to lpd etc., it all works great, except that I'm still getting the 2 page limit issue... Has anyone gone past that?
H

---

### Post by TangoRom on 2010-05-12
Tilex,

I'm experiencing the same problem with my printer. Jumps to "stopped" right away as soon as I send the print test.
I'm using KDE with lucid lynx 10.4 on 64-bit asus A52J laptop.

Does anyone got an answer on how to properly install dell 1320c printer on a 64-bit ubuntu? (hope so) :)

thx

---

### Post by westcloud on 2010-07-07
I'm also looking for the solution. waiting.

---

### Post by dt_matthews on 2010-09-02
> **dmitriyp13 said:**
> **Update: **This works in Jaunty too.



Since people keep asking me for this deb file, I'll post it here.  Enjoy.

hi dmitri,

i'm running lucid 10.04 64 bit and despite following your instructions i am not able to print - I get the error;

"Print error: There was a problem sending document..."

Did you encounter and overcome this?

TIA,
dan

---

### Post by dt_matthews on 2010-09-03
> **westcloud said:**
> I'm also looking for the solution. waiting.

Hi, did you ever resolve this on 64 bit - I cannot despite following Dmitri's post?

---

### Post by maggiev on 2010-09-14
> **TangoRom said:**
> Tilex,

I'm experiencing the same problem with my printer. Jumps to "stopped" right away as soon as I send the print test.
I'm using KDE with lucid lynx 10.4 on 64-bit asus A52J laptop.

Does anyone got an answer on how to properly install dell 1320c printer on a 64-bit ubuntu? (hope so) :)

thx

Solution:
System > Administration > Printing | Right click for properties > Installable Options > choose 250 sheet feeder | goto Printer Options > choose Paper Source > Tray 1 (250 sheets)

Default is to use the manual feeder, which is why the paper doesn't feed and/or it says out of paper.

---

### Post by dt_matthews on 2010-09-14
> **maggiev said:**
> Solution:
System > Administration > Printing | Right click for properties > Installable Options > choose 250 sheet feeder | goto Printer Options > choose Paper Source > Tray 1 (250 sheets)

Default is to use the manual feeder, which is why the paper doesn't feed and/or it says out of paper.

I think that is the resolution for 32bit - it appears some 64bit systems (mine included) have some other problem which is stopping  the driver working...

---

### Post by jimmybarcelona on 2010-09-25
> **ytsejam1138 said:**
> I have found the solution to get this printer working properly.

```
System > Administration > Printing and right click on your printer, selecting Properties. 
Settings > Device URI
If you see something like socket://your_printer_ip_address:9100 just change socket to lpd and remove the :9100 off the end. 
Then click on apply.
```


Mine didn't have the 9100 port, so I just changed socket to lpd and it works perfect now.  I found the solution on this webpage:  [http://p-s.co.nz/wordpress/?p=227](http://p-s.co.nz/wordpress/?p=227)


This worked great for me on ubuntu 10.04 32bit system. This is great, because I've had this printer and not been able to use it for over a year now. I knew there was a way to get it up and running, but was unsuccessful until today. Thanks for the tip!

---

### Post by MAMAS on 2010-10-13
This printer drives me crazy - I tied everything now:
1) Installed the Xerox C525 .deb [http://zoffix.com/other/Installing-Dell-1320c-Color-Laser-Printer-on-Ubuntu](http://zoffix.com/other/Installing-Dell-1320c-Color-Laser-Printer-on-Ubuntu)
2) Selected the 250 paper tray
3) In the URI field: changed to _lpd_ instead of _socket_ and deleted the _9100_ value

When I try to print something the printing goes on endless!!!! First the page gets printed - then the printer says: out of paper (although the tray is full!!) - when i tpush the tray in and out the print job gets printed out again - although the print queue is empty - this goes on endlessly!!!

What can I do????? Please help - I've spent more than 5 hours just today trying to get this **uck printer to do its job!

---

### Post by bluefrogprince on 2010-11-04
> **dmitriyp13 said:**
> Since people keep asking me for this deb file, I'll post it here.  Enjoy.

Thank you very much for this - worked perfectly for me on 10.04 (at least as far as printing a test page, not tried multiple pages as yet).

---

### Post by timgood on 2011-04-14
For me, using 10.10 64bit, printing works perfectly except when printing from Firefox or Thunderbird. Then after print job is completed, I get the yellow exclamation mark. If I reset the paper draw, the job is repeated. But turning the printer off and back on resets the printer. Driving me mad! Any explanation why printing from HTML should have this result?

---

### Post by Tilex on 2011-04-14
Hi timgood,

I also have the yellow exclamation mark after I print from various sources, but I press the cancel button (red cross) **twice** on the printer, the printer comes back to normal without re-printing the document.  

Try it out !

Alex

---

### Post by timgood on 2011-04-14
> **Tilex said:**
> Hi timgood,

I also have the yellow exclamation mark after I print from various sources, but I press the cancel button (red cross) **twice** on the printer, the printer comes back to normal without re-printing the document.  

Try it out !

Alex

Thanks Alex - will give it a go. Anyone else with this problem?

---

### Post by naich on 2011-05-16
> **timgood said:**
> Thanks Alex - will give it a go. Anyone else with this problem?

Yup.  Ubuntu 10.10. When printing from Open Office it prints 3 pages and then hangs.  The status page (open up the printer's IP in your browser) says it's out of paper.

A work around is to print 2 pages at a time, which is a pain in the asre.

---

### Post by Tilex on 2011-05-17
> **naich said:**
> Yup.  Ubuntu 10.10. When printing from Open Office it prints 3 pages and then hangs.  The status page (open up the printer's IP in your browser) says it's out of paper.

A work around is to print 2 pages at a time, which is a pain in the asre.

I rarely print from Open Office directly ; I export to PDF before, than print.

I found out that Okular wasn't too good at printing with my Dell, but Acrobat Reader did print perfectly fine (even 50+ pages document).  Try it !

---

### Post by jackharvest on 2011-05-20
> **timgood said:**
> For me, using 10.10 64bit, printing works perfectly except when printing from Firefox or Thunderbird. Then after print job is completed, I get the yellow exclamation mark. If I reset the paper draw, the job is repeated. But turning the printer off and back on resets the printer. Driving me mad! Any explanation why printing from HTML should have this result?

How did you manage to install the deb on x64 architecture? Even with --force-all I'm getting nowhere on my x64 system (Ubuntu 11)

---

### Post by Brimfulof2 on 2011-08-15
Well, I've been struggling with this for a couple of days and getting nowhere. I followed all the instructions on this page and the various other forums discussing the issue, but every time I tried to print a test page it just stopped.

Eventually trying to configure the printer through the CUPS web interface (just to see if it would make any difference - it's at [http://localhost:631](http://localhost:631) the username and password you need are your system username and password) and I got this error message:

```
Unsupported format 'application/vnd.cups-command'
```I found this page and followed the instructions: [http://phorm.phormix.com/site/node/13](http://phorm.phormix.com/site/node/13)

Which are to run these commands:

[LIST=1]
[*]```
sudo apt-get install libgutenprintui2-1 ups-driver-gutenprint foomatic-db-gutenprint ijsgutenprint hpijs
``` (ensures correct packages are installed - I got an error here that it couldn't find one of the files, but it doesn't seem to matter).
[*]```
sudo ln -sf /usr/share/cups/mime/pstoraster.convs /etc/cups/pstoraster.convs 
```(this creates a symlink between the correct file and the correct place)
[/LIST]
I don't know if both steps are necessary, but I did them both and I'm up and running, so thought I'd share in case anyone else is pulling their hair out like I was.

---

### Post by ubun2geek on 2011-08-15
Anyone try HPLIP? It works awesome for me! 
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by ubun2geek on 2011-08-15
OOPS! I should have paid better attention.
Wish they had one for Dell Printers. (Thought you were talking about dell pcs) :)

---

### Post by Tyndarus on 2011-09-13
Hello

i'm having same problem as some of you:
printing job from openoffice documents prints 3 pages and then fails.
no problem when printing txt and pdfs. Also remark that the exclamation mark always stays orange, no matter what.

My dell 1320c is usb connected to a vostro 400. I've installed same  printer on the same way (using fujixerox c525 ppd) on medion akoya,  there it worked perfect...

The error i was 
Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
which changed to 

[cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
after i did (according to [http://ubuntuforums.org/showthread.php?t=1314487](http://ubuntuforums.org/showthread.php?t=1314487))
sudo apt-get install gs-esp 
after a complete reinstall and linking the printer to the fujixerox ppd the error stayed the same.

looks like quite an irritating bug...

gtz
Tyndarus

---

### Post by ewano on 2012-12-18
Mainly for reference of others trying to get a Dell 1320c network printer to work with Ubuntu 12.04 64bit Precise.

I've successfully managed to get this working using the instructions found here:

[http://zoffix.com/other/Installing-Dell-1320c-Color-Laser-Printer-on-Ubuntu](http://zoffix.com/other/Installing-Dell-1320c-Color-Laser-Printer-on-Ubuntu)

It's now working so far with no glitches or problems.

```
wget http://zoffix.com/content-pics/dell_printer/fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb
``````
sudo dpkg -i --force-architecture fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb
```Add printer using the system setting printing dialog and use URI lpd://your.printer.IP.address

Select printer from the list FX-> FX_DocuPrint_C525_A_AP

Make sure you add the 250 sheet feeder. Don't print a test page when it asks. Right click and select properties. Under "Printer Options" select the paper source as "Auto" and then click Apply and OK.

You should now be ready to print.

Good luck..

---

### Post by npp on 2013-04-26
Just got this working on 13.04 - fantastic - cheers!!!

Made my Friday.

:D

---

### Post by russell6 on 2013-09-26
> **ewano said:**
> Mainly for reference of others trying to get a Dell 1320c network printer to work with Ubuntu 12.04 64bit Precise.

I've successfully managed to get this working using the instructions found here:

[http://zoffix.com/other/Installing-Dell-1320c-Color-Laser-Printer-on-Ubuntu](http://zoffix.com/other/Installing-Dell-1320c-Color-Laser-Printer-on-Ubuntu)

It's now working so far with no glitches or problems.

```
wget http://zoffix.com/content-pics/dell_printer/fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb
``````
sudo dpkg -i --force-architecture fuji-xerox-docuprint-c525-a-ap_1.0-2_i386.deb
```Add printer using the system setting printing dialog and use URI lpd://your.printer.IP.address

Select printer from the list FX-> FX_DocuPrint_C525_A_AP

Make sure you add the 250 sheet feeder. Don't print a test page when it asks. Right click and select properties. Under "Printer Options" select the paper source as "Auto" and then click Apply and OK.

You should now be ready to print.

Good luck..

Thanks, another note, select 64Mb for the memory option.  Got this working in Mint 15 just now.

---

