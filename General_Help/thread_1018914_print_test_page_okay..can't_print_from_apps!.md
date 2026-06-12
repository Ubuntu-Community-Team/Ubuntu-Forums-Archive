---
title: "print test page okay..can't print from apps!"
date: 2008-12-22
forum: General Help
---

### Post by fewjr on 2008-12-22
Hello All,
I had a little trouble getting my network printer going. I have a HP Photosmart C4200 connected to my Wife's Vista computer. My Ubuntu 8.10 computer and my Wife's computer are connected to a router. I did get the printer recognized on the Ubuntu machine. It actually printed a test page just fine, but I cannot print from any applications (webpage, pdf doc, etc.). I haven't seen anything as of yet to help me figure this out. Can anyone help?

Thanks
fewjr

---

### Post by jay li on 2008-12-22
I think you need to set it first as the default printer. 
To do so, go to "System" menu on the panel then to "Preferences" then to "Default Printer" and select the HP printer as the default printer. 

And if I remember right, you should have a settings option of your HP printer (only if the printer is connected to your machine), so check those settings too.

---

### Post by fewjr on 2008-12-22
The printer was shown there. I clicked to set as default, but it did not help.

---

### Post by jay li on 2008-12-22
Did you find the HP preferences window itself?

---

### Post by fewjr on 2008-12-22
Do you mean System>Preferences>HPLIP Toolbox? That is there.

---

### Post by jay li on 2008-12-22
I don't know, try it. 
You see, I have HP printer too (DESKJET 930C) but it's not connected right now, so I can't be sure. 
But what I do remember is that there should be an option for your printer settings somewhere.

---

### Post by rbmorse on 2008-12-22
Open synaptic (system > administration >synaptic package manager)  and click on the search icon. Enter

cups

in the dialog and check the version number of the CUPS files on your system.  

A couple of days ago there were were some system upgrades that produced the same symptoms you report on my machine. Subsequently, some of the CUPS files were also updated (to 1.3.9-2ubuntu6) and corrected the problem for me. 

If you don't have 1.3.9-2ubuntu6 installed, you might try to manually check for updates and see if any CUPS related files are waiting to be installed.

---

### Post by fewjr on 2008-12-22
I checked cups it is installed. It is version 1.3.9-2ubuntu4 and it states that it is the latest version.

---

### Post by rbmorse on 2008-12-22
How odd.  I have 1.3.9-2ubuntu6 on both my 32 and 64 bit installations. 

In any case, if they ever get around to pushing 1.3.9-2ubuntu6 to your update server, it might cure the problem like it did for me. 

Good luck!

---

### Post by jay li on 2008-12-22
I think I found it what you looking for... 
Just go to system > administration > printing. 
Mark your printer, right click on it and select properties. 
Now, start to play with settings there.

---

### Post by fewjr on 2008-12-22
yeah...thats where you print the test page from.

---

### Post by dwanders on 2008-12-23
I am experiencing this same thing (I think) - All the printers that I had installed (4 all together) worked fine a couple of days ago [cant remember the last time I actually printed anything out]. Today when I go to print, the Print button is grayed out. From FireFox, Gimp, Text Editor etc... however - if I go to System > Administration > Printing all the printers are there and I can print test pages from there without any problems. 

Pretty frustrating. When I am in the Printing Dialog, all I can do is PrintToFile - if I select a printer, the print button gets grayed out. If there is a way to roll back a CUPS upgrade, or force a newer version I would like the steps. My current install looks like it is: 

      cupsys 1.3.7-lubuntu32. 

Thanks in advance.

---

### Post by fewjr on 2008-12-23
I ran some commands that I saw in another thread to get some more information. Here is error_log:
```
D [23/Dec/2008:12:35:52 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:35:52 -0500] Report: clients=1
D [23/Dec/2008:12:35:52 -0500] Report: jobs=2
D [23/Dec/2008:12:35:52 -0500] Report: jobs-active=0
D [23/Dec/2008:12:35:52 -0500] Report: printers=1
D [23/Dec/2008:12:35:52 -0500] Report: printers-implicit=0
D [23/Dec/2008:12:35:52 -0500] Report: stringpool-string-count=325
D [23/Dec/2008:12:35:52 -0500] Report: stringpool-alloc-bytes=9472
D [23/Dec/2008:12:35:52 -0500] Report: stringpool-total-bytes=6856
D [23/Dec/2008:12:35:52 -0500] cupsdCloseClient: 8
D [23/Dec/2008:12:35:52 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:35:52 -0500] cupsdReadClient: 8 POST / HTTP/1.1
D [23/Dec/2008:12:35:52 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:35:52 -0500] CUPS-Get-Printers
D [23/Dec/2008:12:35:52 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [23/Dec/2008:12:35:52 -0500] cupsdAcceptClient: 9 from localhost (Domain)
D [23/Dec/2008:12:35:52 -0500] cupsdCloseClient: 8
D [23/Dec/2008:12:35:52 -0500] cupsdReadClient: 9 GET /printers/Photosmart-c4200.ppd HTTP/1.1
D [23/Dec/2008:12:35:52 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:35:53 -0500] cupsdCloseClient: 9
D [23/Dec/2008:12:35:55 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:35:55 -0500] cupsdReadClient: 8 POST /printers/Photosmart-c4200 HTTP/1.1
D [23/Dec/2008:12:35:55 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:35:55 -0500] Print-Job ipp://localhost:631/printers/Photosmart-c4200
D [23/Dec/2008:12:35:55 -0500] [Job ???] Auto-typing file...
I [23/Dec/2008:12:35:55 -0500] [Job ???] Request file type is application/pdf.
E [23/Dec/2008:12:35:55 -0500] Print-Job: Unauthorized
D [23/Dec/2008:12:35:55 -0500] cupsdSendError: 8 code=401 (Unauthorized)
D [23/Dec/2008:12:35:55 -0500] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [23/Dec/2008:12:35:55 -0500] cupsdCloseClient: 8
D [23/Dec/2008:12:36:21 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:36:21 -0500] cupsdAcceptClient: 9 from localhost (Domain)
D [23/Dec/2008:12:36:21 -0500] cupsdCloseClient: 8
D [23/Dec/2008:12:36:21 -0500] cupsdReadClient: 9 POST / HTTP/1.1
D [23/Dec/2008:12:36:21 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:36:21 -0500] CUPS-Get-Printers
D [23/Dec/2008:12:36:21 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
D [23/Dec/2008:12:36:21 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:36:21 -0500] cupsdCloseClient: 9
D [23/Dec/2008:12:36:21 -0500] cupsdReadClient: 8 GET /printers/Photosmart-c4200.ppd HTTP/1.1
D [23/Dec/2008:12:36:21 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:36:22 -0500] cupsdCloseClient: 8
D [23/Dec/2008:12:36:23 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:36:23 -0500] cupsdReadClient: 8 POST /printers/Photosmart-c4200 HTTP/1.1
D [23/Dec/2008:12:36:23 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:36:23 -0500] Print-Job ipp://localhost:631/printers/Photosmart-c4200
D [23/Dec/2008:12:36:23 -0500] [Job ???] Auto-typing file...
I [23/Dec/2008:12:36:23 -0500] [Job ???] Request file type is application/pdf.
E [23/Dec/2008:12:36:23 -0500] Print-Job: Unauthorized
D [23/Dec/2008:12:36:23 -0500] cupsdSendError: 8 code=401 (Unauthorized)
D [23/Dec/2008:12:36:23 -0500] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [23/Dec/2008:12:36:24 -0500] cupsdCloseClient: 8
```

Can anyone make heads or tails of this?

---

### Post by dwanders on 2008-12-23
Dont know if this is helpful to resolve this issue, but I just that my Lotus Notes (running in crossover office) is not experiencing this problem. I think [in my case anyway] this issue is with the Gnome Print Dialog box that comes up when the various applications try to use it.

---

### Post by dwanders on 2008-12-23
fewjr - does this sound the same as what your experiencing? Can you print to file, but when you select a printer, the button goes gray?

---

### Post by fewjr on 2008-12-23
No I do not think so....the print botton in menus are not greyed out.Here is a screenshot of what happens when I print from a gedit doc:
[IMG]http://i260.photobucket.com/albums/ii20/fewjr/screenshots/Screenshot-doc.png[/IMG]
I get the same error printing from pdf:
[IMG]http://i260.photobucket.com/albums/ii20/fewjr/screenshots/Screenshot-pdf.png[/IMG]
And when I print something from a webpage in Firefox, it goes all the way through the progress bar shown in the next screenshot, but nothing happens at the printer.
[IMG]http://i260.photobucket.com/albums/ii20/fewjr/screenshots/Screenshot-webpage.png[/IMG]
So I'm not sure if its Gnome or cups or what???

fewjr

---

### Post by fewjr on 2008-12-25
bump and Merry Christmas.

---

### Post by maclenin on 2009-01-12
I think [_this_]("http://ubuntuforums.org/showthread.php?p=6540160#post6540160") (i.e. my issue) might be related to your issue - and happy new year!

---

### Post by cmcanulty on 2010-04-20
I am having same problem. Can print a test page OK but anything else gets listed in queue as holding even though I have everything set to no hold. They never print.

---

### Post by Tsu Dho Nimh on 2010-06-21
With a new Brother DM-5370DW, I can print test pages, print from OpenOffice, can't print from gedit!

All gedit jobs go on hold, with a print time that is always a few minutes later than whatever time I check the print queue.

1 - it is set to be the default printer.
2 - it is a networked printer.
3 - gedit is not set to put jobs on hold, it is set to print jobs immediately.

ADDING: 
UBUNTU 9.04
GNOME 2.26.1

---

