---
title: "Cups-pdf printer paused and don't resume"
date: 2005-03-10
forum: Desktop Environments
---

### Post by lyly on 2005-03-10
Hi!

I'm trying to install a pdf printer using cups-pdf package (new printer installed with Generic/Postscript color driver). When sending a test page, The logs give:

```
 
I [10/Mar/2005:11:13:38 +0100] New printer 'postscript-color-printer' added by 'root'.
I [10/Mar/2005:11:13:50 +0100] Adding start banner page "none" to job 1.
I [10/Mar/2005:11:13:50 +0100] Adding end banner page "none" to job 1.
I [10/Mar/2005:11:13:50 +0100] Job 1 queued on 'postscript-color-printer' by 'lyly'.
I [10/Mar/2005:11:13:50 +0100] Started filter /usr/lib/cups/filter/pstops (PID 10568) for job 1.
I [10/Mar/2005:11:13:50 +0100] Started backend /usr/lib/cups/backend/cups-pdf (PID 10569) for job 1.
E [10/Mar/2005:11:13:50 +0100] PID 10569 stopped with status 0!
I [10/Mar/2005:11:13:50 +0100] Hint: Try setting the LogLevel to "debug" to find out more.

``` 

After having loglevel changed to debug the output becomes:
```
 
I [10/Mar/2005:11:17:15 +0100] Printer 'postscript-color-printer' started by 'root'.
D [10/Mar/2005:11:17:15 +0100] StartJob(1, 0x80965e8)
D [10/Mar/2005:11:17:15 +0100] StartJob() id = 1, file = 0/1
D [10/Mar/2005:11:17:15 +0100] job-sheets=none,none
D [10/Mar/2005:11:17:15 +0100] banner_page = 0
D [10/Mar/2005:11:17:15 +0100] StartJob: argv = "postscript-color-printer","1","lyly","Test Page","1","","/var/spool/cups/d00001-001"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[2]="USER=root"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[3]="CHARSET=utf-8"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[4]="LANG=en_US"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[5]="TZ=Europe/Zurich"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[6]="PPD=/etc/cups/ppd/postscript-color-printer.ppd"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[11]="DEVICE_URI=cups-pdf:/"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[12]="PRINTER=postscript-color-printer"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[15]="CUPS_SERVER=localhost"
D [10/Mar/2005:11:17:15 +0100] StartJob: envp[16]="IPP_PORT=631"
D [10/Mar/2005:11:17:15 +0100] StartJob: statusfds = [ 6 7 ]
D [10/Mar/2005:11:17:15 +0100] StartJob: filterfds[1] = [ 8 -1 ]
D [10/Mar/2005:11:17:15 +0100] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [10/Mar/2005:11:17:15 +0100] StartJob: filterfds[0] = [ 9 10 ]
D [10/Mar/2005:11:17:15 +0100] start_process("/usr/lib/cups/filter/pstops", 0xbfff0b70, 0xbffefee0, 8, 10, 7)
I [10/Mar/2005:11:17:15 +0100] Started filter /usr/lib/cups/filter/pstops (PID 10827) for job 1.
D [10/Mar/2005:11:17:15 +0100] StartJob: backend = "/usr/lib/cups/backend/cups-pdf"
D [10/Mar/2005:11:17:15 +0100] StartJob: filterfds[1] = [ -1 8 ]
D [10/Mar/2005:11:17:15 +0100] start_process("/usr/lib/cups/backend/cups-pdf", 0xbfff0b70, 0xbffefee0, 9, 8, 7)
I [10/Mar/2005:11:17:15 +0100] Started backend /usr/lib/cups/backend/cups-pdf (PID 10828) for job 1.
D [10/Mar/2005:11:17:15 +0100] ProcessIPPRequest: 5 status_code=0
D [10/Mar/2005:11:17:15 +0100] [Job 1] Page = 595x842; 18,36 to 577,806
D [10/Mar/2005:11:17:15 +0100] [Job 1] slowcollate=0, slowduplex=0, sloworder=0
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%Title: PPR Test Page
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%Pages: 1
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%DocumentNeededResources: font Helvetica
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%EndComments
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%BeginProlog
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%EndProlog
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%BeginSetup
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%IncludeResource: font Helvetica
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%IncludeFeature: *PageSize A4
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%EndSetup
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%Page: 1 1
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%Page: 1 1
D [10/Mar/2005:11:17:15 +0100] [Job 1] pw = 559.0, pl = 770.0
D [10/Mar/2005:11:17:15 +0100] [Job 1] PageLeft = 18.0, PageRight = 577.0
D [10/Mar/2005:11:17:15 +0100] [Job 1] PageTop = 806.0, PageBottom = 36.0
D [10/Mar/2005:11:17:15 +0100] [Job 1] PageWidth = 595.0, PageLength = 842.0
D [10/Mar/2005:11:17:15 +0100] [Job 1] 0 %%BeginDocument: /home/jdub/Documents/Canonical/Logos/Ubuntu_logo.eps
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%Title: Ubuntu final logo
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%Creator: FreeHand 10.0
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%CreationDate: 15/9/04 11:16 am
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%BoundingBox: 0 0 350 81
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%FHPathName:Work:CANONICAL SOFTWARE:Ubuntu:UBUNTU Identity:Ubuntu final logo
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%FHPageNum:1
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%DocumentSuppliedResources: procset Altsys_header 4 0
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%ColorUsage: Color
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%DocumentProcessColors: Black
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%DocumentCustomColors: (PANTONE 2965 CVC)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ (PANTONE 151 CVC)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ (PANTONE 1235 CVC)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ (PANTONE 179 CVC)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ (0r 43g 61b)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ (244r 72g 0b)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ (251r 139g 0b)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ (212r 0g 0b)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%CMYKCustomColor: 1 0.38 0 0.69 (PANTONE 2965 CVC)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ 0 0.43 0.87 0 (PANTONE 151 CVC)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ 0 0.275 0.76 0 (PANTONE 1235 CVC)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ 0 0.79 0.94 0 (PANTONE 179 CVC)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ 0.7613 0.5271 0.6244 0.7124 (0r 43g 61b)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ 0.0017 0.7251 0.8508 0 (244r 72g 0b)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ 0.0032 0.4248 0.8274 0 (251r 139g 0b)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%+ 0.0176 0.9327 0.9184 0 (212r 0g 0b)
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%EndComments
D [10/Mar/2005:11:17:15 +0100] [Job 1] 1 %%BeginFont: Times-Roman
D [10/Mar/2005:11:17:15 +0100] ReadClient: 5 POST / HTTP/1.1
D [10/Mar/2005:11:17:15 +0100] ProcessIPPRequest: 5 status_code=1
E [10/Mar/2005:11:17:15 +0100] PID 10828 stopped with status 0!

``` 

As I can't see anything in this to help me finding what's going on, I hope some of you could tell me what's happening :-) Thank you

---

### Post by ashayh on 2005-05-09
Hello... did you solve this problem ?

---

### Post by Leszek Tarkowski on 2005-05-11
[QUOTE=ashayh]Hello... did you solve this problem ?[/QUOTE]
 You have to edit /etc/cups/cupsd.conf
sudo nano /etc/cups/cupsd.conf
change RunAsUser from Yes to No.
sudo /etc/init.d/cupsys restart
Restart cups: sudo /etc/init.d/cupsys restart

---

### Post by lonetree on 2005-05-30
hi guys, I followed through the instruction and got the pdf printer "work", at least it won't hang there like before, but one question, where does the output goes to?

:-(

regards

---

### Post by Rahn on 2005-06-10
puts them in ~/cups-pdf

---

### Post by Devi0s on 2005-07-13
I followed the directions above and got the Cups-pdf printer to function, but it's far from working.  In attempting to print webpages, images will sometimes print, but all the text is garbled.

There is no better solution than cups-pdf?  Maybe something equivalent to PDFCreator?

---

### Post by terranz on 2006-03-26
[QUOTE=Leszek Tarkowski]You have to edit /etc/cups/cupsd.conf
sudo nano /etc/cups/cupsd.conf
change RunAsUser from Yes to No.
sudo /etc/init.d/cupsys restart
Restart cups: sudo /etc/init.d/cupsys restart[/QUOTE]

Would this work for a real printer that won't stay un-paused?

---

