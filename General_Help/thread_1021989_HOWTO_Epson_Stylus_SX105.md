---
title: "HOWTO Epson Stylus SX105"
date: 2008-12-26
forum: General Help
---

### Post by thraxy on 2008-12-26
I've noticed that there are quite a few people having problems getting their Epson Stylus SX105 All-In-One machine working.

Here's how I got the printer working under Hardy and Intrepid (scanner is still unresolved, to my knowledge):

Go to [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

Select the driver for Epson Stylus NX100/SX100/TX100/TX101/TX105/TX106,Epson ME 300 and fill in the other required information.

Download the file that matches your version of Ubuntu (8.04,8.10).

Extract the file to a folder, open terminal and cd into the folder (example: cd /home/username/Documents).

Installation for Hardy Heron:
```
sudo bash pips-snx100-ubuntu8.04-3.3.0-CG.install
```

Installation for Intrepid Ibex:
```
sudo bash pips-snx100-ubuntu8.04-3.5.0-CG.install
```

You should now be able to use your printer. Good luck!

---

### Post by chrismarsh1987 on 2008-12-31
i followed your instructions but it wont print, when i go through the trouble shooting options it allows me to print a test page but not the page i want to print, it reads cannot write page 1 image. any ideas?

---

### Post by chrismarsh1987 on 2008-12-31
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest snx100 (default)>,
 'cups_instance': None,
 'cups_queue': 'snx100',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'ekplp',
 'cups_printer_dict': {'device-uri': u'ekplp:/var/ekpd/ekplp0',
                       'printer-info': u'snx100',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Epson Stylus NX100, Photo Image Print System',
                       'printer-state': 3,
                       'printer-state-message': u"Can't write page 1 image",
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135180,
                       'printer-uri-supported': u'ipp://localhost:631/printers/snx100'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Ink': u'COLOR',
                                            u'PageRegion': u'A4_AUTO',
                                            u'PageSize': u'A4_AUTO',
                                            u'Quality': u'PLAIN_S'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'',
                      'device-info': u'Epson Inkjet Printer #1',
                      'device-make-and-model': u'Photo Image Print System'}}
Page 7 (Printer state reasons):
{'printer-state-message': u"Can't write page 1 image",
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '2000000',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 30652L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_job_status': [(True,
                           9,
                           'snx100',
                           'life kist open air logo.jpg',
                           'Stopped',
                           {'Ink': u'COLOR',
                            'PageSize': u'A4',
                            'Quality': u'PLAIN_S',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-gb',
                            'document-format': u'application/pdf',
                            'job-hold-until': u'no-hold',
                            'job-id': 9,
                            'job-k-octets': 89,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/9',
                            'job-name': u'life kist open air logo.jpg',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'chris',
                            'job-preserved': True,
                            'job-printer-state-message': u"Can't write page 1 image",
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1230751640,
                            'job-printer-uri': u'ipp://nautilus:631/printers/snx100',
                            'job-priority': 100,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/9',
                            'job-uuid': u'urn:uuid:2d244fbf-35d5-3982-4e6a-aa6fcb8c29f6',
                            'number-up': 1,
                            'printer-uri': u'ipp://localhost:631/printers/snx100',
                            'time-at-completed': None,
                            'time-at-creation': 1230751097,
                            'time-at-processing': 1230751097})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [31/Dec/2008:19:26:11 +0000] cupsdCloseClient: 7',
               'D [31/Dec/2008:19:26:11 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [31/Dec/2008:19:26:11 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [31/Dec/2008:19:26:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [31/Dec/2008:19:26:11 +0000] Get-Jobs ipp://localhost/jobs/',
               'D [31/Dec/2008:19:26:11 +0000] [Job 9] Loading attributes...',
               'D [31/Dec/2008:19:26:11 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [31/Dec/2008:19:26:11 +0000] cupsdCloseClient: 7',
               'D [31/Dec/2008:19:26:11 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [31/Dec/2008:19:26:11 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [31/Dec/2008:19:26:11 +0000] cupsdAuthorize: No authentication data provided.',
               'D [31/Dec/2008:19:26:11 +0000] Create-Printer-Subscription /',
               'D [31/Dec/2008:19:26:11 +0000] cupsdCreateSubscription(con=0xb84e6088(7), uri="/")',
               'D [31/Dec/2008:19:26:11 +0000] pullmethod="ippget"',
               'D [31/Dec/2008:19:26:11 +0000] notify-lease-duration=86400',
               'D [31/Dec/2008:19:26:11 +0000] notify-time-interval=0',
               'D [31/Dec/2008:19:26:11 +0000] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [31/Dec/2008:19:26:11 +0000] Added subscription 16 for server',
               'I [31/Dec/2008:19:26:11 +0000] Saving subscriptions.conf...',
               'D [31/Dec/2008:19:26:11 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [31/Dec/2008:19:26:11 +0000] cupsdCloseClient: 7',
               'D [31/Dec/2008:19:26:12 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [31/Dec/2008:19:26:12 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [31/Dec/2008:19:26:12 +0000] cupsdAuthorize: No authentication data provided.',
               'D [31/Dec/2008:19:26:12 +0000] Get-Notifications /',
               'D [31/Dec/2008:19:26:12 +0000] cupsdIsAuthorized: requesting-user-name="chris"',
               'D [31/Dec/2008:19:26:12 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [31/Dec/2008:19:26:12 +0000] cupsdCloseClient: 7',
               'D [31/Dec/2008:19:27:12 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [31/Dec/2008:19:27:12 +0000] [Job 9] Unloading...',
               'D [31/Dec/2008:19:27:12 +0000] Report: clients=1',
               'D [31/Dec/2008:19:27:12 +0000] Report: jobs=6',
               'D [31/Dec/2008:19:27:12 +0000] Report: jobs-active=1',
               'D [31/Dec/2008:19:27:12 +0000] Report: printers=2',
               'D [31/Dec/2008:19:27:12 +0000] Report: printers-implicit=0',
               'D [31/Dec/2008:19:27:12 +0000] Report: stringpool-string-count=2602',
               'D [31/Dec/2008:19:27:12 +0000] Report: stringpool-alloc-bytes=10344',
               'D [31/Dec/2008:19:27:12 +0000] Report: stringpool-total-bytes=55928',
               'D [31/Dec/2008:19:27:12 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [31/Dec/2008:19:27:12 +0000] cupsdAuthorize: No authentication data provided.',
               'D [31/Dec/2008:19:27:12 +0000] Get-Notifications /',
               'D [31/Dec/2008:19:27:12 +0000] cupsdIsAuthorized: requesting-user-name="chris"',
               'D [31/Dec/2008:19:27:12 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [31/Dec/2008:19:27:12 +0000] cupsdCloseClient: 7',
               'D [31/Dec/2008:19:27:20 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [31/Dec/2008:19:27:20 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [31/Dec/2008:19:27:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [31/Dec/2008:19:27:20 +0000] Get-Job-Attributes ipp://localhost/jobs/9',
               'D [31/Dec/2008:19:27:20 +0000] [Job 9] Loading attributes...',
               'D [31/Dec/2008:19:27:20 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [31/Dec/2008:19:27:20 +0000] cupsdCloseClient: 7',
               'D [31/Dec/2008:19:27:20 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [31/Dec/2008:19:27:20 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [31/Dec/2008:19:27:20 +0000] cupsdAuthorize: No authentication data provided.',
               'D [31/Dec/2008:19:27:20 +0000] Cancel-Subscription /',
               'D [31/Dec/2008:19:27:20 +0000] cupsdIsAuthorized: requesting-user-name="chris"',
               'I [31/Dec/2008:19:27:20 +0000] Saving subscriptions.conf...',
               'D [31/Dec/2008:19:27:20 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [31/Dec/2008:19:27:20 +0000] cupsdCloseClient: 7',
               'D [31/Dec/2008:19:27:20 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [31/Dec/2008:19:27:20 +0000] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1',
               'D [31/Dec/2008:19:27:20 +0000] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}

thats the information from the trouble shooting. and i cant print the document, only test pages

---

### Post by Alexia_Death on 2009-01-04
The scanner works too. Down that page is a deb for iscan. Get and install it. It WORKS! I still cant belive it dully but it does! I can now digitally color some of my age old drawings.

---

### Post by brunovianna on 2009-01-05
Here it shows
----------------
Scanner Driver
This driver is currently not supported. 
----------------
Can you tell us what distribution and model you selected in the form to make the scanner file appear?

Thanks
Bruno

---

### Post by CK1 on 2009-02-26
I followed the instructions from the Avasys website and ran the ran pips install file pips-snx100-ubuntu8.04-3.3.0-CG.install. However, I get the following errors:-

"cp: cannot create regular file `/usr/local/EPAva/printer/snx100/uninstall-snx100.sh': No such file or directory
chmod: cannot access `/usr/local/EPAva/printer/snx100/uninstall-snx100.sh': No such file or directory
cp: target `/usr/local/EPAva/printer/snx100/.' is not a directory
Add printer setting at spool system...
./install-pips.sh: 240: /usr/local/EPAva/distro/ekpdsetup: not found
lpadmin: No such file or directory
Startup ekpd-tool...
./install-pips.sh: 240: ekpd-tool: not found
Installation is complete."

I am running Ubuntu 8.04 64bit. Any suggestions how to install the driver ?

I downloaded the scanner driver and this works OK.

---

### Post by linuxonbute on 2009-04-13
> **CK1 said:**
> I followed the instructions from the Avasys website and ran the ran pips install file pips-snx100-ubuntu8.04-3.3.0-CG.install. However, I get the following errors:-

"cp: cannot create regular file `/usr/local/EPAva/printer/snx100/uninstall-snx100.sh': No such file or directory
chmod: cannot access `/usr/local/EPAva/printer/snx100/uninstall-snx100.sh': No such file or directory
cp: target `/usr/local/EPAva/printer/snx100/.' is not a directory
Add printer setting at spool system...
./install-pips.sh: 240: /usr/local/EPAva/distro/ekpdsetup: not found
lpadmin: No such file or directory
Startup ekpd-tool...
./install-pips.sh: 240: ekpd-tool: not found
Installation is complete."

I am running Ubuntu 8.04 64bit. Any suggestions how to install the driver ?

I downloaded the scanner driver and this works OK.

I don't know if you have solved this yet but you need to be root to install to /usr/local/ and it's sub-directories.

the command you need is:

sudo pips-snx100-ubuntu8.04-3.3.0-CG.install

It will ask for your normal user password and then do the job.

HTH

---

### Post by CK1 on 2009-04-14
> **linuxonbute said:**
> I don't know if you have solved this yet but you need to be root to install to /usr/local/ and it's sub-directories.

the command you need is:

sudo pips-snx100-ubuntu8.04-3.3.0-CG.install

It will ask for your normal user password and then do the job.

HTH

I ran this after doing sudo bash to run it as root and got the error messages already identified. I have since upgraded to 8.10 and still get the same error messages. Anyone any ideas how to resolve this problem ?

---

### Post by Zetheroo on 2009-04-21
With this printer driver only some apps in Ubuntu print while the majority do not.

---

### Post by dolphinholmer on 2009-05-16
Should be out-of-the-box support for this printer now with Gutenprint 5.2.3

[https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/303511](https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/303511)

---

### Post by CK1 on 2009-05-21
I've now upgraded to Jaunty, 9.04 and the printer is working "out of the box". I had to delete the existing printer queues first to allow it to automatically set-up the printer queue properly.

---

### Post by nicozanf on 2009-08-26
I do confirm that the printer is working "out of the box" on Jaunty 9.04 - 64 bit. 
But in order to use the scanner feature I had to install the iscan = Image Scan! program from the epson/avasys web site (and reboot the pc).

---

### Post by eeried on 2009-10-29
Hello,

Thank you CK1 and nicozanf for your tests. The scanner works fine with the avasys driver.

I installed 
libltdl3_1.5.26-1ubuntu1_i386.deb (Hardy version since the package no longer exists for Jackalope) since this seems necessary
iscan_2.22.0-2.ltdl7_i386.deb
iscan_2.22.0-2_i386.deb

However I can't print directly an image from the scanner. I use Xsane > copy 

I configured Xsan "prefs" > "config" > "copy" in this way:
```
Name: EPSON Stylus SX100

Command: lpr

nber of copies: -#
```

Something must be wrong in my config. I didn't fill in the lpr command since it's an all in one. if the printer was independent I think I ought to enter ```
lpr -P usb://EPSON/Stylus%20SX100  
```

True, I haven't restarted the computer after installing the driver but I'm not sure this is necessary.

Before that there was a message saying the Epson may not be connected and I wonder if the USB cord could be flaky. I remember reading about bad USB cords. Edit: I changed the cord to no avail.

Well, I succeeded &#8212; after quitting Xsane. Then the Epson printed out the document in the scanner. Same thing with Iscan.

To sum up my problem: in order to print a document directly from the scanner I must quit Xsane after clicking the "Numerise" button.

Any idea how to make this task simpler? A workaround is to print directly from the machine itself, by pressing the right button. This works fine but it would be nice to learn how to do a "photocopy" from Xsane without quitting it ;-)

---

### Post by myklmar on 2010-01-02
> **Alexia_Death said:**
> The scanner works too. Down that page is a deb for iscan. Get and install it. It WORKS! I still cant belive it dully but it does! I can now digitally color some of my age old drawings.

Trying to get my scanner to work for ages.
AT LAST found this thread and it works!
Absolutely brilliant. Many,many thanks. xxxxx:lolflag:

---

### Post by jamoros on 2010-02-24
Hi,
I tried (maybe too fast without pay too much attention) to follow the advices in this post and I had no succesful anyway.
My situation is this:
EPSON SX105 working fine after do the things recommended in this very first post. Ubuntu 8.04 x86_64
After severals dist-upgrades ( 8.04 --> 8.10, 8.10 ---> 9.04, 9.04 --->9.10) my epson didn't print nothing. Scanning working well, but no printing.

Finally, openprinting worked ok:

[http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/gutenprint/binary-amd64/openprinting-gutenprint_5.2.4-1lsb3.2_amd64.deb](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/gutenprint/binary-amd64/openprinting-gutenprint_5.2.4-1lsb3.2_amd64.deb)
from  [http://www.openprinting.org/printer/Epson/Epson-Stylus_SX105](http://www.openprinting.org/printer/Epson/Epson-Stylus_SX105)

Good luck

P.D: Same machine Fedora 12 works out-of-the-box. I think this deb is the rpm convert to deb with alien (not sure)

---

### Post by Filip Ciklevski on 2010-05-14
Madame, Sir, good day,
 
I have Epson Stylus SX105 Print/Scan and when I try to scan I receive this information: No scanners detected, Please check your scanner is connected and powered on.
My Epson Stylus SX105 Print/Scan is powered on and I still receiving the same message.
 
Thank you in advance for your answer.
Regards.
Filip Ciklevski  
 
P.S. I am Lucid (10.04) user.

---

### Post by Filip Ciklevski on 2010-11-23
Can I have an **link** for EPSON STYLUS SX105 all in one **drivers**. Already considerable time I'm disoriented to find and make the necessary drivers for my EPSON STYLUS SX105 all in one.

I will appreciate your support, understanding and orientation.
Regards.
Filip Ciklevski

---

### Post by anglican on 2010-11-23
> **Filip Ciklevski said:**
> Can I have an **link** for EPSON STYLUS SX105 all in one **drivers**. Already considerable time I'm disoriented to find and make the necessary drivers for my EPSON STYLUS SX105 all in one.

I will appreciate your support, understanding and orientation.
Regards.
Filip CiklevskiIt was in the first message, but here it is again:

 [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

you'll find your printer does not appear on the drop down list so choose "Other" and the page that takes you to does list the SX105.

H

---

