---
title: "Not Printing on HP LaserJet 4+"
date: 2009-04-08
forum: General Help
---

### Post by HilltopSC on 2009-04-08
I think I have configured the printer correctly - software correctly found printer on LPT 1/parallel port and installed the driver recommended ("HP LaserJet 4 Plus v2013.111 postscript [en] (recommended").

Selecting "Print Test Page" results in the computer believing it has sent the print to printer successfully. The printer shows an error message - "W2 Invalid Pers". Resetting the printer results in the message "user Test Page X" where user = computer name and X = page number of test pages previously sent. I have tried nine different combinations of drivers and ports and the results are the same. I know, it begins to sound as if it is an HP issue. Unfortunately, this printer is about 15 years old, but still a workhorse. 

This is a dual boot machine with XP Pro on the other partition. 

Thanks

---

### Post by HilltopSC on 2009-04-08
I have corrected my own problem. The issue was with the HP LJ 4+. The driver that Ubuntu automatically chose was based upon the Postscript option being already loaded on the printer. It was not. 

By researching the HP users manual, the error code, "W2 Invalid Pers" was fully explained as

 "W2 INVALID PERS                 
REQUESTED LANGUAGE NOT AVAILABLE


 The job was not printed because the requested personality,  
 such as PostScript, was not installed. Install the language in
 which the files are sent, together with enough memory to
 support that language."

Correction: change the driver to that of, "HP LaserJet 4 Plus Foomatic/LJet 4"  The correct driver does NOT send Postscript to the printer. 

Hopefully, this will aid other newbies...

---

### Post by Mike Zimmer on 2009-06-15
You recommend "HP LaserJet 4 Plus Foomatic/LJet 4" as the driver, but I am not clear on the following:

1 - where I obtain the driver
2 - how I tell Ubuntu how to use this driver in the printer definition.

Can someone help here?

Thanks

---

### Post by nevans on 2010-03-30
I have a fresh install of 9.10 and when I print to my HP laserjet 4 plus on a parrellel port, it shows a "W2 invalid pers" error.  As a side note this printer worked fine on my 7.10 installation.  I tried re-installing the HPLIP drivers.  No success.  I am also not given the option to change drivers when I set it up.  I cannot find the foomatic driver and while I have used Ubuntu for a while I am by no means fluent in using terminal to install printers manually.  Any guides or help would be appreciated.

Neal

---

### Post by nevans on 2010-04-07
OK for future reference.

My laserjet 4+ printer has a parallel and a tcp/ip connection.  I finally gave up on the parallel port and set it up on the tcp/ip port.  When I went to set up the network connection, low and behold there was the foomatic driver.   I also specified a laserjet 4 as I saw on some other post.  The printer now works.

Solution: abandon the parallel port.

---

### Post by Nikos.Alexandris on 2010-05-11
> **nevans said:**
> OK for future reference.

My laserjet 4+ printer has a parallel and a tcp/ip connection.  I finally gave up on the parallel port and set it up on the tcp/ip port.  When I went to set up the network connection, low and behold there was the foomatic driver.   I also specified a laserjet 4 as I saw on some other post.  The printer now works.

Solution: abandon the parallel port.

Hi!

I have access to a LaserJet 4 MPlus printer but I have no idea how to set it up via a local LAN. Is there a step-by-step guide?

So far I have connected the printer to the LAN router (in which laptops can be connected either through LAN cables or WLAN). How to I get the printer's IP?

Thanks

---

### Post by kiddjmadd on 2010-08-30
i had same problem. found a link that showed how to change driver thru cups server page. i was able to change printer driver at [http://localhost:631/](http://localhost:631/) and selecting "Administration" tab. I used HP LaserJet 4 Plus hpijs pcl3, 3.10.2. Seems to work now. I have CUPS 1.4.3. I may try another driver since that one is for a color laserjet. Main thing for me was to not use the "recommended" postscript printer driver. Good luck :)

---

