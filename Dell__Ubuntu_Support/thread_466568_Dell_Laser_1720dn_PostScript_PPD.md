---
title: "Dell Laser 1720dn PostScript PPD"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by claudiob on 2007-06-06
Does anybody here know where is possible to get the PPD for the Dell Laser 1720dn to use on Ubuntu 7.04?

On Dell website there is a link to some "drivers" for OpenSUSE but the file is corrupted... 

Thanks.

---

### Post by Brian96 on 2007-07-05
Did you ever find anything? I am looking for these drivers as well.

---

### Post by claudiob on 2007-07-05
Didn't find yet.

---

### Post by Brian96 on 2007-07-07
I was able to install the .deb file from the Dell website.

I am running off of a server install, so I had to install cupsys to make it work (I think, anyway; I know I installed cupsys and then it worked, but it might have been a coincidence). The .deb file installs a dell printer manager app that was really easy to configure. Then adding the printer worked much like the Windows install.

What problem did you have with the deb?

---

### Post by claudiob on 2007-07-09
> **Brian96 said:**
> 
What problem did you have with the deb?

I can't find any .deb file on Dell... can you give the direct link?
Thanks

[COLOR="Red"]..I just found it inside the SuSE Linux driver download... now I give it a try.[/COLOR]

---

### Post by jnet3000 on 2007-07-18
Dell 1720dn printer installation on Ubuntu (7.04 Feisty Fawn)
The Dell printer manager for GNOME seems to find only PCL instance of printer, so when you printer, it prints Postscript to it and it turns out scramble.  Here's a workaround that seems to work well for me.

Workaround (with postscript instance of printer installed on Windows server):
* Select desktop Start Here > System Administration > Printing
* Double click New Printer
* Click on the detected Dell 1720dn and click Forward
-or-
* Add as Windows Printer:
    -- Click Network Printer and Select Windows Printer (SMB) (Note: Dismiss the numerous annoying prompts for password for hosts in the Windows domain)
    -- Enter server name for Host Name
    -- Enter Printer Name -- use the *Postscript* instance share name of printer from Windows
    -- Enter <Windows-Domain>\user for Username
    -- Enter password
    -- Click Forward

* Select Dell for Manufacturer
* Select S2500 for Model (this one works for me but not sure which is best)
* Select Postscript for Driver -- MUST
* Click Forward
* Enter your printer Name, Description and Location
* Click Apply

-----

The Dell Driver Manager Way (which incorrectly prints Postscript to PCL emulation):
* Download driver at,
[http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R149777&formatcnt=1&libid=0&fileid=198972](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R149777&formatcnt=1&libid=0&fileid=198972)
* tar xzvf <driver.tar.gz
* dpkg -i <driver>.deb
* Run the script as prompted after installing .deb
* Select 'Install Dell applications' during installation

Note: If you select Exit at that time, you can manually run it again:

    sudo /usr/local/dell/unix_prt_drivers/bin/gnome_menu_utility.sh

* It installs Dell printer manage in GNOME menu
* Select Start Here > System Tools > Dell Print Drivers
* Click Device Manager
* Click Add
* Click Search next to IP Address/Host Name
* Enter xx.xx.xx.0 for 'IPv4 subnet', where xx.xx.xx is the first three numbers of printer IP address
* Click Start
* Click on the print server found
* Click OK
* Enter device name, for example, Dell_1720dn
Note: Here's the problem, the Dell Printer installation on Windows server installs both PCL and PS instances, but it only finds the PCL version, causing it to print Postscript to PCL emulation and it comes out scrambled
* Click Next
* Click Finish
* Click Close back on Virtual Device Manager

* Right click My Printers under All Printers in tree view
* Click Group Manager
* Enter Printer Queue Name, for example, Dell_1720dn
* Select Dell Laser Printer 1700 for Printer Type
* Click Next
* Click Next
* Click Finish
* Need to restart application for the application to see new printer

---

### Post by seldenthuis on 2007-07-27
If you have the driver CD, you can also find the driver under /unix/packages.  Just double-click on printer-drivers-linux-glibc2.deb.

However, I've had some problems with this driver since several programs do not let me print with it (gThumb, GIMP etc.) and Adobe Acrobat does not let me change the properties, which is really a pain if you want to switch between simplex and duplex.  What I would really like is a PPD file for the 1720dn, but unfortunately Dell doesn't supply this.  At least not directly, since there is a way to get it if you have the CD.

For some reason Dell includes the PPD (in compressed form) in the Windows driver on the CD.  It is absent from the online version and Windows doesn't seem to use it, since it's still compressed after the install, but I'm glad they didn't remove it from the CD.

Here is how you install it.

Make sure the CD is mounted, open a terminal and go to the driver directory:
```
cd /usr/share/ppd/custom
```

If the custom folder doesn't exist, create it with:
```

cd /usr/share/ppd
sudo mkdir custom
sudo chown root:lpadmin custom
cd custom

```

Copy the driver from the CD:
[CODE
]sudo cp /media/cdrom/drivers/print/win_2kxp/dkabj540.gdl .
sudo cp /media/cdrom/drivers/print/win_2kxp/english/dkabj540.pp_ .
[/CODE]

The gdl-file contains the options list so you can easily change them in System->Administration->Printing.  The pp_-file is the compressed PPD.  To expand it you need the mscompress package:
```
sudo apt-get install mscompress
```

Expand and rename the PPD and clean up:
```

sudo msexpand dkabj540.pp_
sudo mv dkabj540.pp dkabj540.ppd
sudo rm dkabj540.pp_
sudo chown root:lpadmin dkabj540.*

```

Now that the driver is installed, you can add the printer.  Go to System->Administration->Printing and click New Printer.  If the printer is plugged in and turned on, it should already come up.  Click Forward.  Under Manufacturer, select Dell.  There should be three models available: 1720dn, M5200 and S2500.  Select the 1720dn and click Forward.  Give the printer a suitable name and click Apply.  Right-click on the printer and select Properties.  Under the Advanced tab you can see the effect of copying the gdl-file.  You can configure all the options.  To make sure the printer works, click Print a Test Page.

That's it.  Everything should work now.  I've checked the quality of the prints and it is exactly the same as what you get when you're using the other Dell driver (and noticeably better than using the HP driver suggested by openprinting.org).

PS:  I'm not posting the actual PPD and GDL files since I'm not sure if that's legal.  If you don't have the CD and do need the files, let me know and we can figure something out.

---

### Post by seldenthuis on 2007-07-28
Update: You can find the PPD and GDL files at [openprinting.org]("http://forums.linux-foundation.org/read.php?33,2614").

---

### Post by claudiob on 2007-09-01
Thanx a lot!

---

### Post by Brian96 on 2007-11-23
Thought I'd update this thread.

I had no trouble installing this printer in 7.10 using the printer manager that comes pre-installed. Here's what I did:

1. Under System ==> Admin, select Printing.
2. Select "New Printer."
3. If your printer is automagically discovered, select it. I found the S2500 drivers to work fine (although I haven't tried the M2500).

I had trouble at first because my printer is installed on a network and the printing manager did not pick it up. But I just selected the Appsocket/HPJetdirect option, and entered the IP address for my printer (which I got by pushing the "Continue" button on the printer).

---

### Post by barotto on 2008-02-04
I created a modified version of the PPD file by Dell, because the original, extracted from the Windows driver, lacks support for duplex and many other functions. 
My version enables duplex, multipage printing (up to 16 pages per sheet with line border), small font enhancer, toner darkness, all using PJL and Postscript commands. My PPD gives the same printing options and results as the Windows driver. It's even localized in english and italian.

All I want to do now is share my work with the community. The problem is that the copyright notice tells me that i can redistribute the PPD file as long as the content is not altered in any way from its original form...

Any ideas to solve this problem? Maybe a diff file to be used with the patch command?

This printer works perfectly in Ubuntu, has a Postscript 3 interpreter, understands PJL, has duplex unit, ethernet connection and 1200dpi hw resolution... it's even fast ...

If someone is interested let me know.

---

### Post by Elswood on 2008-02-24
I'm interested!  Have just ordered this printer and would like it to work perfectly in Gutsy!  Let me know...
Thanks!

---

### Post by seldenthuis on 2008-03-03
As barotto noted, the PPD extracted from the Windows driver lacks support for a.o. duplex printing. I've attached the PPD extracted from the Apple driver, which does support all those features.

To use it however, two lines in the PPD have to be changed. I cannot upload the modified version, since the license doesn't permit that, but the fix is simple. Remove lines 36 "*APPrinterIconPath: ..." and 41 "cupsFilter: ..." to stop CUPS from complaining about a missing filter.

I've tested the driver on the 1720dn and duplex works like a charm.

---

### Post by allaboutsam on 2008-03-04
Thank you, Seldenthius. Works like a charm.

---

### Post by agarzon on 2008-04-15
I got it working through a different workaround.
After seeing the Dell web site, I've found the directions to install it on Novell's SUSE. [(link),]("http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&dl=false&l=en&s=gen&docid=3B6DC657EA53DE8BE040A68F5B284D76&doclang=en&cs=") So I simply took Dell's word that the generic printer driver PCL6 worked fine with the printer and found out it works great.
Some extra details: Ubuntu 7.10. The printer is not local but network shared. The host system is a Windows XP Home machine.

---

### Post by rajan on 2008-07-02
post #6 by jnet3000 works for me with 8.04 on my wife's old toshiba laptop. 



thanks to jnet3000

---

