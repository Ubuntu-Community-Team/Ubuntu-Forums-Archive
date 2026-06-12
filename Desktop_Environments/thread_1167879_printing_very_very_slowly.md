---
title: "printing very very slowly"
date: 2009-05-23
forum: Desktop Environments
---

### Post by marbil84 on 2009-05-23
Hello, 

I have the following problem, but couldn't find a solution even after a long searching in the forums:

Printing pdfs takes sometimes very long time, I mean about 2 pages in an hour; but not all the time (see for example the log unter my post).

Sometimes it takes "only" a minute or two. The same by some gifs or jpegs.

I tried to reinstall the printer, but no luck.

My system is Kubuntu 8.04 32 bit, the printer ist HP Laserjet 1200. The printer is OK, there are no problems under WinXP.

I tried to analyse the cups.log, but I can see nothing there

Any ideas?

Thanks Martin


D [23/May/2009:15:30:57 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:15:30:57 +0200] Report: clients=1
D [23/May/2009:15:30:57 +0200] Report: jobs=508
D [23/May/2009:15:30:57 +0200] Report: jobs-active=0
D [23/May/2009:15:30:57 +0200] Report: printers=2
D [23/May/2009:15:30:57 +0200] Report: printers-implicit=0
D [23/May/2009:15:30:57 +0200] Report: stringpool-string-count=1549
D [23/May/2009:15:30:57 +0200] Report: stringpool-alloc-bytes=8024
D [23/May/2009:15:30:57 +0200] Report: stringpool-total-bytes=19144
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Printers
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Classes
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Default
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdCloseClient: 7
D [23/May/2009:15:30:57 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] Get-Printer-Attributes ipp://localhost/printers/hp1200
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 7 GET /printers/hp1200.ppd HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] cupsdAcceptClient: 11 from localhost (Domain)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Printers
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Classes
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Default
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdCloseClient: 11
D [23/May/2009:15:30:57 +0200] cupsdAcceptClient: 11 from localhost (Domain)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Printers
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Classes
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Default
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdCloseClient: 11
D [23/May/2009:15:30:57 +0200] cupsdAcceptClient: 11 from localhost (Domain)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Printers
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Classes
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] CUPS-Get-Default
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] Get-Printer-Attributes ipp://localhost/printers/hp1200
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] Get-Jobs ipp://localhost/printers/hp1200
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdCloseClient: 11
D [23/May/2009:15:30:57 +0200] cupsdCloseClient: 7
D [23/May/2009:15:30:57 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] Get-Printer-Attributes ipp://localhost/printers/hp1200
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 7 GET /printers/hp1200.ppd HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] cupsdCloseClient: 7
D [23/May/2009:15:30:57 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:30:57 +0200] Get-Printer-Attributes ipp://localhost/printers/hp1200
D [23/May/2009:15:30:57 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:30:57 +0200] cupsdReadClient: 7 GET /printers/hp1200.ppd HTTP/1.1
D [23/May/2009:15:30:57 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:00 +0200] cupsdAcceptClient: 11 from localhost (Domain)
D [23/May/2009:15:31:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:31:00 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:00 +0200] CUPS-Get-Printers
D [23/May/2009:15:31:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:31:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:31:00 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:00 +0200] CUPS-Get-Classes
D [23/May/2009:15:31:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:31:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:31:00 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:00 +0200] CUPS-Get-Default
D [23/May/2009:15:31:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:31:00 +0200] cupsdCloseClient: 11
D [23/May/2009:15:31:00 +0200] cupsdCloseClient: 7
D [23/May/2009:15:31:00 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:15:31:00 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:31:00 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:00 +0200] Get-Printer-Attributes ipp://localhost/printers/hp1200
D [23/May/2009:15:31:00 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:31:00 +0200] cupsdReadClient: 7 GET /printers/hp1200.ppd HTTP/1.1
D [23/May/2009:15:31:00 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:00 +0200] cupsdCloseClient: 7
D [23/May/2009:15:31:00 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:15:31:00 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:31:00 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:00 +0200] Get-Printer-Attributes ipp://localhost/printers/hp1200
D [23/May/2009:15:31:00 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:31:00 +0200] cupsdReadClient: 7 GET /printers/hp1200.ppd HTTP/1.1
D [23/May/2009:15:31:00 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:05 +0200] cupsdAcceptClient: 11 from localhost (Domain)
D [23/May/2009:15:31:05 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:31:05 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:05 +0200] CUPS-Get-Printers
D [23/May/2009:15:31:05 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:31:05 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:31:05 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:05 +0200] CUPS-Get-Classes
D [23/May/2009:15:31:05 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:31:05 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:31:05 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:05 +0200] CUPS-Get-Default
D [23/May/2009:15:31:05 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:31:05 +0200] cupsdCloseClient: 11
D [23/May/2009:15:31:05 +0200] cupsdAcceptClient: 11 from localhost (Domain)
D [23/May/2009:15:31:05 +0200] cupsdReadClient: 11 POST /printers/hp1200 HTTP/1.1
D [23/May/2009:15:31:05 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:05 +0200] Print-Job ipp://localhost/printers/hp1200
D [23/May/2009:15:31:05 +0200] print_job: auto-typing file...
D [23/May/2009:15:31:05 +0200] add_job: requesting-user-name="spravce"
I [23/May/2009:15:31:05 +0200] [Job 1719] Adding start banner page "none".
D [23/May/2009:15:31:05 +0200] Discarding unused job-created event...
I [23/May/2009:15:31:05 +0200] [Job 1719] Adding job file of type application/postscript.
I [23/May/2009:15:31:05 +0200] [Job 1719] Adding end banner page "none".
I [23/May/2009:15:31:05 +0200] [Job 1719] Queued on "hp1200" by "spravce".
D [23/May/2009:15:31:05 +0200] [Job 1719] hold_until = 0
D [23/May/2009:15:31:05 +0200] Discarding unused printer-state-changed event...
D [23/May/2009:15:31:05 +0200] [Job 1719] job-sheets=none,none
D [23/May/2009:15:31:05 +0200] [Job 1719] banner_page = 0
D [23/May/2009:15:31:05 +0200] [Job 1719] argv[0]="hp1200"
D [23/May/2009:15:31:05 +0200] [Job 1719] argv[1]="1719"
D [23/May/2009:15:31:05 +0200] [Job 1719] argv[2]="spravce"
D [23/May/2009:15:31:05 +0200] [Job 1719] argv[3]="A9ROEUgOuY"
D [23/May/2009:15:31:05 +0200] [Job 1719] argv[4]="1"
D [23/May/2009:15:31:05 +0200] [Job 1719] argv[5]="media=A4 finishings=3 number-up=1 Economode=On FastRes=FromPrintoutMode InputSlot=Default Manualfeed=Off PageRegion=A4 PageSize=A4 PrinterResolution=FromPrintoutMode PrintoutMode=Normal REt=Medium TonerDensity=3 job-uuid=urn:uuid:0f2f928c-bab2-3793-6349-603c791f2aa2"
D [23/May/2009:15:31:05 +0200] [Job 1719] argv[6]="/var/spool/cups/d01719-001"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[9]="SERVER_ADMIN=root@d02-32"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[10]="SOFTWARE=CUPS/1.3.7"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[12]="TZ=Europe/Vienna"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[13]="USER=root"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[16]="IPP_PORT=631"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[17]="CHARSET=utf-8"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[18]="LANG=en_GB.UTF8"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[19]="PPD=/etc/cups/ppd/hp1200.ppd"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[20]="RIP_MAX_CACHE=8m"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[21]="CONTENT_TYPE=application/postscript"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[22]="DEVICE_URI=hp:/usb/HP_LaserJet_1200?serial=00CNC2181788"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[23]="PRINTER=hp1200"
D [23/May/2009:15:31:05 +0200] [Job 1719] envp[24]="FINAL_CONTENT_TYPE=printer/hp1200"
I [23/May/2009:15:31:05 +0200] [Job 1719] Started filter /usr/lib/cups/filter/pstops (PID 16616)
I [23/May/2009:15:31:05 +0200] [Job 1719] Started filter /usr/lib/cups/filter/foomatic-rip (PID 16617)
I [23/May/2009:15:31:05 +0200] [Job 1719] Started backend /usr/lib/cups/backend/hp (PID 16618)
D [23/May/2009:15:31:05 +0200] Discarding unused job-state-changed event...
D [23/May/2009:15:31:05 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:31:05 +0200] cupsdAcceptClient: 12 from localhost (Domain)
D [23/May/2009:15:31:05 +0200] [Job 1719] Page = 595x842; 18,36 to 577,806
D [23/May/2009:15:31:05 +0200] [Job 1719] slow_collate=0, slow_duplex=0, slow_order=0
D [23/May/2009:15:31:05 +0200] [Job 1719] Before copy_comments - %!PS-Adobe-3.1
D [23/May/2009:15:31:05 +0200] [Job 1719] %!PS-Adobe-3.1
D [23/May/2009:15:31:05 +0200] [Job 1719] %ADO_DSC_Encoding: MacOS Roman
D [23/May/2009:15:31:05 +0200] [Job 1719] %%Title: File0002.PDF
D [23/May/2009:15:31:05 +0200] [Job 1719] %%Creator: Adobe Acrobat 9.1.0
D [23/May/2009:15:31:05 +0200] [Job 1719] %%For: spravce
D [23/May/2009:15:31:05 +0200] [Job 1719] %%CreationDate: 23/05/09, 15:31:00
D [23/May/2009:15:31:05 +0200] [Job 1719] %%BoundingBox: 25 36 570 806
D [23/May/2009:15:31:05 +0200] [Job 1719] %%HiResBoundingBox: 25.2994 36 569.7007 806
D [23/May/2009:15:31:05 +0200] [Job 1719] %%CropBox: 25.2994 36 569.7007 806
D [23/May/2009:15:31:05 +0200] [Job 1719] %%LanguageLevel: 3
D [23/May/2009:15:31:05 +0200] [Job 1719] %%DocumentNeededResources: (atend)
D [23/May/2009:15:31:05 +0200] [Job 1719] %%DocumentSuppliedResources: (atend)
D [23/May/2009:15:31:05 +0200] [Job 1719] %%DocumentNeededFeatures: (atend)
D [23/May/2009:15:31:05 +0200] [Job 1719] %%DocumentSuppliedFeatures: (atend)
D [23/May/2009:15:31:05 +0200] [Job 1719] %%DocumentData: Clean7Bit
D [23/May/2009:15:31:05 +0200] [Job 1719] %%PageOrder: Ascend
D [23/May/2009:15:31:06 +0200] [Job 1719] %%TargetDevice: (HP LaserJet 1200) (3010.000) 550
D [23/May/2009:15:31:06 +0200] [Job 1719] %%Pages: (atend)
D [23/May/2009:15:31:06 +0200] [Job 1719] %%DocumentProcessColors: (atend)
D [23/May/2009:15:31:06 +0200] [Job 1719] %%DocumentCustomColors: (atend)
D [23/May/2009:15:31:06 +0200] [Job 1719] %%EndComments
D [23/May/2009:15:31:06 +0200] [Job 1719] Before copy_prolog - %%BeginDefaults
D [23/May/2009:15:31:06 +0200] Discarding unused printer-state-changed event...
D [23/May/2009:15:31:06 +0200] [Job 1719] prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused
D [23/May/2009:15:31:06 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [23/May/2009:15:31:06 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:06 +0200] Get-Jobs ipp://localhost/jobs/
D [23/May/2009:15:31:06 +0200] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [23/May/2009:15:31:06 +0200] cupsdCloseClient: 11
D [23/May/2009:15:31:06 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [23/May/2009:15:31:06 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:31:06 +0200] CUPS-Get-Printers
D [23/May/2009:15:31:06 +0200] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [23/May/2009:15:31:06 +0200] cupsdCloseClient: 12
D [23/May/2009:15:31:06 +0200] [Job 1719] foomatic-rip version $Revision$ running...
D [23/May/2009:15:31:06 +0200] [Job 1719] Parsing PPD file ...
D [23/May/2009:15:31:06 +0200] [Job 1719] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option ColorSpace
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option Resolution
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option PrintoutMode
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option PageSize
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option PageRegion
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option ImageableArea
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option PaperDimension
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option InputSlot
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option Manualfeed
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option Copies
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option REt
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option TonerDensity
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option GSResolution
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option JCLResolution
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option FastRes
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option Economode
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option ColorMode
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option PrinterResolution
D [23/May/2009:15:31:06 +0200] [Job 1719] Added option Font
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] Parameter Summary
D [23/May/2009:15:31:06 +0200] [Job 1719] -----------------
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] Spooler: cups
D [23/May/2009:15:31:06 +0200] [Job 1719] Printer: hp1200
D [23/May/2009:15:31:06 +0200] [Job 1719] Shell: /bin/bash
D [23/May/2009:15:31:06 +0200] [Job 1719] PPD file: /etc/cups/ppd/hp1200.ppd
D [23/May/2009:15:31:06 +0200] [Job 1719] ATTR file: 
D [23/May/2009:15:31:06 +0200] [Job 1719] Printer model: HP LaserJet 1200 Foomatic/pxlmono (recommended)
D [23/May/2009:15:31:06 +0200] [Job 1719] Job title: A9ROEUgOuY
D [23/May/2009:15:31:06 +0200] [Job 1719] File(s) to be printed: 
D [23/May/2009:15:31:06 +0200] [Job 1719] <STDIN>
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'media=A4'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'finishings=3'
D [23/May/2009:15:31:06 +0200] [Job 1719] Unknown option finishings=3.
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'number-up=1'
D [23/May/2009:15:31:06 +0200] [Job 1719] Unknown option number-up=1.
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'Economode=On'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'FastRes=FromPrintoutMode'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'InputSlot=Default'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'Manualfeed=Off'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'PageRegion=A4'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'PageSize=A4'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'PrinterResolution=FromPrintoutMode'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'PrintoutMode=Normal'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'REt=Medium'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'TonerDensity=3'
D [23/May/2009:15:31:06 +0200] [Job 1719] Pondering option 'job-uuid=urn:uuid:0f2f928c-bab2-3793-6349-603c791f2aa2'
D [23/May/2009:15:31:06 +0200] [Job 1719] Unknown option job-uuid=urn:uuid:0f2f928c-bab2-3793-6349-603c791f2aa2.
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] ================================================
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] File: <STDIN>
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] ================================================
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] Reading PostScript input ...
D [23/May/2009:15:31:06 +0200] [Job 1719] --> This document is DSC-conforming!
D [23/May/2009:15:31:06 +0200] [Job 1719] Job claims to be DSC-conforming, but "%%BeginProlog" was missing before first line with another "%%Begin..." comment (is this a TeX/LaTeX/dvips-generated PostScript file?). Assuming start of "Prolog" here.
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] -----------
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginProlog
D [23/May/2009:15:31:06 +0200] [Job 1719] Before copy_setup - %%BeginSetup
D [23/May/2009:15:31:06 +0200] [Job 1719] Before page loop - %%Page: 1 1
D [23/May/2009:15:31:06 +0200] [Job 1719] Copying page 1...
D [23/May/2009:15:31:06 +0200] [Job 1719] pagew = 559.0, pagel = 770.0
D [23/May/2009:15:31:06 +0200] [Job 1719] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [23/May/2009:15:31:06 +0200] [Job 1719] PageLeft = 18.0, PageRight = 577.0
D [23/May/2009:15:31:06 +0200] [Job 1719] PageTop = 806.0, PageBottom = 36.0
D [23/May/2009:15:31:06 +0200] [Job 1719] PageWidth = 595.0, PageLength = 842.0
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%EndProlog
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] -----------
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginSetup
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *PrintoutMode Normal
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: PrintoutMode=Normal --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: PrintoutMode=Normal --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *PrinterResolution FromPrintoutMode
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: PrinterResolution=FromPrintoutMode --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %% FoomaticRIPOptionSetting: PrinterResolution=FromPrintoutMode
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: PrinterResolution=FromPrintoutMode --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *PageRegion A4
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: PageRegion=A4 --> Option will be set by PostScript interpreter
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *InputSlot Default
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: InputSlot=Default --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %% FoomaticRIPOptionSetting: InputSlot=Default
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: InputSlot=Default --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *Manualfeed Off
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: Manualfeed=Off --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %% FoomaticRIPOptionSetting: Manualfeed=Off
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: Manualfeed=Off --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *Copies 1
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: Copies=1 --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %% FoomaticRIPOptionSetting: Copies=1
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: Copies=1 --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *REt Medium
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: REt=Medium --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %% FoomaticRIPOptionSetting: REt=Medium
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: REt=Medium --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *TonerDensity 3
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: TonerDensity=3 --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %% FoomaticRIPOptionSetting: TonerDensity=3
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: TonerDensity=3 --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *FastRes FromPrintoutMode
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: FastRes=FromPrintoutMode --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %% FoomaticRIPOptionSetting: FastRes=@PrintoutMode
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: FastRes=FromPrintoutMode --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *Economode On
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: Economode=On --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %% FoomaticRIPOptionSetting: Economode=On
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: Economode=On --> Setting option
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginFeature: *PageSize A4
D [23/May/2009:15:31:06 +0200] [Job 1719] Option: PageSize=A4 --> Option will be set by PostScript interpreter
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%EndSetup
D [23/May/2009:15:31:06 +0200] [Job 1719] Inserting PostScript code for CUPS' page accounting
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] -----------
D [23/May/2009:15:31:06 +0200] [Job 1719] New page:  1 1
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginPageSetup
D [23/May/2009:15:31:06 +0200] [Job 1719] Inserting option code into "PageSetup" section.
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%EndPageSetup
D [23/May/2009:15:31:06 +0200] [Job 1719] End of page header
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%BeginPageSetup
D [23/May/2009:15:31:06 +0200] [Job 1719] Inserting option code into "PageSetup" section.
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: %%EndPageSetup
D [23/May/2009:15:31:06 +0200] [Job 1719] End of page header
D [23/May/2009:15:31:06 +0200] [Job 1719] Stopping search for page header options
D [23/May/2009:15:31:06 +0200] [Job 1719] Found: 6`(I<j^@sGi9Nf`W$\<^m[ddtVUO*mcUCcn+guiookm/TSHnQF5rG4*X.GAMRZ?U!)QMIu4q9m'lVZ8U
D [23/May/2009:15:31:06 +0200] [Job 1719] --> Output goes directly to the renderer now.
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] Starting renderer
D [23/May/2009:15:31:06 +0200] [Job 1719] JCL: ?%-12345X@PJL
D [23/May/2009:15:31:06 +0200] [Job 1719] @PJL SET MANUALFEED=OFF
D [23/May/2009:15:31:06 +0200] [Job 1719] @PJL SET COPIES=1
D [23/May/2009:15:31:06 +0200] [Job 1719] @PJL SET RET=MEDIUM
D [23/May/2009:15:31:06 +0200] [Job 1719] @PJL SET DENSITY=3
D [23/May/2009:15:31:06 +0200] [Job 1719] @PJL SET RESOLUTION=600
D [23/May/2009:15:31:06 +0200] [Job 1719] @PJL SET BITSPERPIXEL=2
D [23/May/2009:15:31:06 +0200] [Job 1719] @PJL SET ECONOMODE=ON
D [23/May/2009:15:31:06 +0200] [Job 1719] <job data> 
D [23/May/2009:15:31:06 +0200] [Job 1719] ?%-12345X@PJL RESET
D [23/May/2009:15:31:06 +0200] [Job 1719] 
D [23/May/2009:15:31:06 +0200] [Job 1719] renderer PID kid4=16636
D [23/May/2009:15:31:06 +0200] [Job 1719] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=pxlmono -r600x600 -sOutputFile=- - | perl -p -e 'if (! $did) { s/\xc0.\xf8\x26/\xc0\x01\xf8\x26/ && $did++; }'
D [23/May/2009:15:31:06 +0200] [Job 1719] Starting process 16637: "foomatic-gswrapper -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=pxlmono -r600x600 -sOutputFile=- - ..."
D [23/May/2009:15:31:06 +0200] [Job 1719] foomatic-gswrapper: gs '-sstdout=%stderr' '-dBATCH' '-dPARANOIDSAFER' '-dNOPAUSE' '-sDEVICE=pxlmono' '-r600x600' '-sOutputFile=%stdout' '-_'
D [23/May/2009:15:31:06 +0200] [Job 1719] GPL Ghostscript 8.61 (2007-11-21)
D [23/May/2009:15:31:06 +0200] [Job 1719] Copyright (C) 2007 Artifex Software, Inc.  All rights reserved.
D [23/May/2009:15:31:06 +0200] [Job 1719] This software comes with NO WARRANTY: see the file PUBLIC for details.
D [23/May/2009:15:31:06 +0200] Discarding unused job-progress event...
D [23/May/2009:15:31:06 +0200] Discarding unused printer-state-changed event...
D [23/May/2009:15:31:06 +0200] Discarding unused printer-state-changed event...
D [23/May/2009:15:32:02 +0200] Report: clients=1
D [23/May/2009:15:32:02 +0200] Report: jobs=509
D [23/May/2009:15:32:02 +0200] Report: jobs-active=1
D [23/May/2009:15:32:02 +0200] Report: printers=2
D [23/May/2009:15:32:02 +0200] Report: printers-implicit=0
D [23/May/2009:15:32:02 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:32:02 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:32:02 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:32:06 +0200] cupsdAcceptClient: 11 from localhost (Domain)
D [23/May/2009:15:32:06 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [23/May/2009:15:32:06 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:32:06 +0200] CUPS-Get-Printers
D [23/May/2009:15:32:06 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [23/May/2009:15:32:06 +0200] cupsdCloseClient: 11
D [23/May/2009:15:33:02 +0200] Report: clients=1
D [23/May/2009:15:33:02 +0200] Report: jobs=509
D [23/May/2009:15:33:02 +0200] Report: jobs-active=1
D [23/May/2009:15:33:02 +0200] Report: printers=2
D [23/May/2009:15:33:02 +0200] Report: printers-implicit=0
D [23/May/2009:15:33:02 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:33:02 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:33:02 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:34:08 +0200] Report: clients=1
D [23/May/2009:15:34:08 +0200] Report: jobs=509
D [23/May/2009:15:34:08 +0200] Report: jobs-active=1
D [23/May/2009:15:34:08 +0200] Report: printers=2
D [23/May/2009:15:34:08 +0200] Report: printers-implicit=0
D [23/May/2009:15:34:08 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:34:08 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:34:08 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:35:14 +0200] Report: clients=1
D [23/May/2009:15:35:14 +0200] Report: jobs=509
D [23/May/2009:15:35:14 +0200] Report: jobs-active=1
D [23/May/2009:15:35:14 +0200] Report: printers=2
D [23/May/2009:15:35:14 +0200] Report: printers-implicit=0
D [23/May/2009:15:35:14 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:35:14 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:35:14 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:36:01 +0200] Closing client 7 after 300 seconds of inactivity...
D [23/May/2009:15:36:01 +0200] cupsdCloseClient: 7
D [23/May/2009:15:36:23 +0200] Report: clients=0
D [23/May/2009:15:36:23 +0200] Report: jobs=509
D [23/May/2009:15:36:23 +0200] Report: jobs-active=1
D [23/May/2009:15:36:23 +0200] Report: printers=2
D [23/May/2009:15:36:23 +0200] Report: printers-implicit=0
D [23/May/2009:15:36:23 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:36:23 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:36:23 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:37:29 +0200] Report: clients=0
D [23/May/2009:15:37:29 +0200] Report: jobs=509
D [23/May/2009:15:37:29 +0200] Report: jobs-active=1
D [23/May/2009:15:37:29 +0200] Report: printers=2
D [23/May/2009:15:37:29 +0200] Report: printers-implicit=0
D [23/May/2009:15:37:29 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:37:29 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:37:29 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:38:35 +0200] Report: clients=0
D [23/May/2009:15:38:35 +0200] Report: jobs=509
D [23/May/2009:15:38:35 +0200] Report: jobs-active=1
D [23/May/2009:15:38:35 +0200] Report: printers=2
D [23/May/2009:15:38:35 +0200] Report: printers-implicit=0
D [23/May/2009:15:38:35 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:38:35 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:38:35 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:38:51 +0200] [Job 1719] Found: %%PYZ_?-/\A2)VKaRdkr2gsG2*aq[>J2[c'[_T<SlmAkONei#u73B4!B9D`,ULN2-(CHdWJGB-^_P3))
D [23/May/2009:15:38:51 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:15:38:51 +0200] [Job 1719] 
D [23/May/2009:15:39:36 +0200] Report: clients=0
D [23/May/2009:15:39:36 +0200] Report: jobs=509
D [23/May/2009:15:39:36 +0200] Report: jobs-active=1
D [23/May/2009:15:39:36 +0200] Report: printers=2
D [23/May/2009:15:39:36 +0200] Report: printers-implicit=0
D [23/May/2009:15:39:36 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:39:36 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:39:36 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:40:42 +0200] Report: clients=0
D [23/May/2009:15:40:42 +0200] Report: jobs=509
D [23/May/2009:15:40:42 +0200] Report: jobs-active=1
D [23/May/2009:15:40:42 +0200] Report: printers=2
D [23/May/2009:15:40:42 +0200] Report: printers-implicit=0
D [23/May/2009:15:40:42 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:40:42 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:40:42 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:41:48 +0200] Report: clients=0
D [23/May/2009:15:41:48 +0200] Report: jobs=509
D [23/May/2009:15:41:48 +0200] Report: jobs-active=1
D [23/May/2009:15:41:48 +0200] Report: printers=2
D [23/May/2009:15:41:48 +0200] Report: printers-implicit=0
D [23/May/2009:15:41:48 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:41:48 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:41:48 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:42:54 +0200] Report: clients=0
D [23/May/2009:15:42:54 +0200] Report: jobs=509
D [23/May/2009:15:42:54 +0200] Report: jobs-active=1
D [23/May/2009:15:42:54 +0200] Report: printers=2
D [23/May/2009:15:42:54 +0200] Report: printers-implicit=0
D [23/May/2009:15:42:54 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:42:54 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:42:54 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:44:00 +0200] Report: clients=0
D [23/May/2009:15:44:00 +0200] Report: jobs=509
D [23/May/2009:15:44:00 +0200] Report: jobs-active=1
D [23/May/2009:15:44:00 +0200] Report: printers=2
D [23/May/2009:15:44:00 +0200] Report: printers-implicit=0
D [23/May/2009:15:44:00 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:44:00 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:44:00 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:44:56 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:15:44:56 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:44:56 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:44:56 +0200] Get-Jobs ipp://localhost/jobs/
D [23/May/2009:15:44:56 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:44:56 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:44:56 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:44:56 +0200] CUPS-Get-Printers
D [23/May/2009:15:44:56 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:44:56 +0200] cupsdCloseClient: 7
D [23/May/2009:15:45:08 +0200] Report: clients=0
D [23/May/2009:15:45:08 +0200] Report: jobs=509
D [23/May/2009:15:45:08 +0200] Report: jobs-active=1
D [23/May/2009:15:45:08 +0200] Report: printers=2
D [23/May/2009:15:45:08 +0200] Report: printers-implicit=0
D [23/May/2009:15:45:08 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:45:08 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:45:08 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:46:14 +0200] Report: clients=0
D [23/May/2009:15:46:14 +0200] Report: jobs=509
D [23/May/2009:15:46:14 +0200] Report: jobs-active=1
D [23/May/2009:15:46:14 +0200] Report: printers=2
D [23/May/2009:15:46:14 +0200] Report: printers-implicit=0
D [23/May/2009:15:46:14 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:46:14 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:46:14 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:47:20 +0200] Report: clients=0
D [23/May/2009:15:47:20 +0200] Report: jobs=509
D [23/May/2009:15:47:20 +0200] Report: jobs-active=1
D [23/May/2009:15:47:20 +0200] Report: printers=2
D [23/May/2009:15:47:20 +0200] Report: printers-implicit=0
D [23/May/2009:15:47:20 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:47:20 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:47:20 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:48:26 +0200] Report: clients=0
D [23/May/2009:15:48:26 +0200] Report: jobs=509
D [23/May/2009:15:48:26 +0200] Report: jobs-active=1
D [23/May/2009:15:48:26 +0200] Report: printers=2
D [23/May/2009:15:48:26 +0200] Report: printers-implicit=0
D [23/May/2009:15:48:26 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:48:26 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:48:26 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:49:32 +0200] Report: clients=0
D [23/May/2009:15:49:32 +0200] Report: jobs=509
D [23/May/2009:15:49:32 +0200] Report: jobs-active=1
D [23/May/2009:15:49:32 +0200] Report: printers=2
D [23/May/2009:15:49:32 +0200] Report: printers-implicit=0
D [23/May/2009:15:49:32 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:49:32 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:49:32 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:50:38 +0200] Report: clients=0
D [23/May/2009:15:50:38 +0200] Report: jobs=509
D [23/May/2009:15:50:38 +0200] Report: jobs-active=1
D [23/May/2009:15:50:38 +0200] Report: printers=2
D [23/May/2009:15:50:38 +0200] Report: printers-implicit=0
D [23/May/2009:15:50:38 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:50:38 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:50:38 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:51:44 +0200] Report: clients=0
D [23/May/2009:15:51:44 +0200] Report: jobs=509
D [23/May/2009:15:51:44 +0200] Report: jobs-active=1
D [23/May/2009:15:51:44 +0200] Report: printers=2
D [23/May/2009:15:51:44 +0200] Report: printers-implicit=0
D [23/May/2009:15:51:44 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:51:44 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:51:44 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:52:50 +0200] Report: clients=0
D [23/May/2009:15:52:50 +0200] Report: jobs=509
D [23/May/2009:15:52:50 +0200] Report: jobs-active=1
D [23/May/2009:15:52:50 +0200] Report: printers=2
D [23/May/2009:15:52:50 +0200] Report: printers-implicit=0
D [23/May/2009:15:52:50 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:52:50 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:52:50 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:53:56 +0200] Report: clients=0
D [23/May/2009:15:53:56 +0200] Report: jobs=509
D [23/May/2009:15:53:56 +0200] Report: jobs-active=1
D [23/May/2009:15:53:56 +0200] Report: printers=2
D [23/May/2009:15:53:56 +0200] Report: printers-implicit=0
D [23/May/2009:15:53:56 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:53:56 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:53:56 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:55:02 +0200] Report: clients=0
D [23/May/2009:15:55:02 +0200] Report: jobs=509
D [23/May/2009:15:55:02 +0200] Report: jobs-active=1
D [23/May/2009:15:55:02 +0200] Report: printers=2
D [23/May/2009:15:55:02 +0200] Report: printers-implicit=0
D [23/May/2009:15:55:02 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:55:02 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:55:02 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:56:08 +0200] Report: clients=0
D [23/May/2009:15:56:08 +0200] Report: jobs=509
D [23/May/2009:15:56:08 +0200] Report: jobs-active=1
D [23/May/2009:15:56:08 +0200] Report: printers=2
D [23/May/2009:15:56:08 +0200] Report: printers-implicit=0
D [23/May/2009:15:56:08 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:56:08 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:56:08 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:57:14 +0200] Report: clients=0
D [23/May/2009:15:57:14 +0200] Report: jobs=509
D [23/May/2009:15:57:14 +0200] Report: jobs-active=1
D [23/May/2009:15:57:14 +0200] Report: printers=2
D [23/May/2009:15:57:14 +0200] Report: printers-implicit=0
D [23/May/2009:15:57:14 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:57:14 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:57:14 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:58:20 +0200] [Job 1719] Copying page 2...
D [23/May/2009:15:58:20 +0200] Report: clients=0
D [23/May/2009:15:58:20 +0200] Report: jobs=509
D [23/May/2009:15:58:20 +0200] Report: jobs-active=1
D [23/May/2009:15:58:20 +0200] Report: printers=2
D [23/May/2009:15:58:20 +0200] Report: printers-implicit=0
D [23/May/2009:15:58:20 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:58:20 +0200] Report: stringpool-alloc-bytes=9232
D [23/May/2009:15:58:20 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:15:58:20 +0200] [Job 1719] pagew = 559.0, pagel = 770.0
D [23/May/2009:15:58:20 +0200] [Job 1719] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [23/May/2009:15:58:20 +0200] [Job 1719] PageLeft = 18.0, PageRight = 577.0
D [23/May/2009:15:58:20 +0200] [Job 1719] PageTop = 806.0, PageBottom = 36.0
D [23/May/2009:15:58:20 +0200] [Job 1719] PageWidth = 595.0, PageLength = 842.0
D [23/May/2009:15:58:40 +0200] [Job 1719] Found: %%EndBinary
D [23/May/2009:15:58:40 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:15:58:40 +0200] [Job 1719] 
D [23/May/2009:15:58:40 +0200] [Job 1719] Found: %%PageTrailer
D [23/May/2009:15:58:40 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:15:58:40 +0200] [Job 1719] 
D [23/May/2009:15:58:40 +0200] [Job 1719] Found: %%Page: 2 2
D [23/May/2009:15:58:40 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:15:58:40 +0200] [Job 1719] 
D [23/May/2009:15:58:40 +0200] [Job 1719] 
D [23/May/2009:15:58:40 +0200] [Job 1719] -----------
D [23/May/2009:15:58:40 +0200] [Job 1719] New page:  2 2
D [23/May/2009:15:58:40 +0200] [Job 1719] Found: %%Page: 2 2
D [23/May/2009:15:58:40 +0200] [Job 1719] --> Output goes to the FIFO buffer now.
D [23/May/2009:15:58:40 +0200] [Job 1719] 
D [23/May/2009:15:58:40 +0200] [Job 1719] 
D [23/May/2009:15:58:40 +0200] [Job 1719] Found: %%BeginPageSetup
D [23/May/2009:15:58:40 +0200] [Job 1719] Inserting option code into "PageSetup" section.
D [23/May/2009:15:58:40 +0200] [Job 1719] Found: %%EndPageSetup
D [23/May/2009:15:58:40 +0200] [Job 1719] End of page header
D [23/May/2009:15:58:40 +0200] [Job 1719] 
D [23/May/2009:15:58:40 +0200] [Job 1719] Found: %%BeginPageSetup
D [23/May/2009:15:58:40 +0200] [Job 1719] Inserting option code into "PageSetup" section.
D [23/May/2009:15:58:40 +0200] [Job 1719] Found: %%EndPageSetup
D [23/May/2009:15:58:40 +0200] [Job 1719] End of page header
D [23/May/2009:15:58:40 +0200] [Job 1719] Stopping search for page header options
D [23/May/2009:15:58:40 +0200] [Job 1719] Found: T?:f(``:gh@uoMWqZND6Djrr^#dC:+J#5<9Ij9(nAQIF!FdZ%8%\bbM"hAlCl`>+I:?+7I+k%n3S:cG*
D [23/May/2009:15:58:40 +0200] [Job 1719] --> Output goes directly to the renderer now.
D [23/May/2009:15:58:40 +0200] [Job 1719] 
D [23/May/2009:15:59:04 +0200] Discarding unused job-progress event...
D [23/May/2009:15:59:04 +0200] Discarding unused job-progress event...
D [23/May/2009:15:59:04 +0200] Discarding unused printer-state-changed event...
D [23/May/2009:15:59:04 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:15:59:04 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:59:04 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:59:04 +0200] Get-Jobs ipp://localhost/jobs/
D [23/May/2009:15:59:04 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:59:04 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:15:59:04 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:15:59:04 +0200] CUPS-Get-Printers
D [23/May/2009:15:59:04 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:15:59:04 +0200] cupsdCloseClient: 7
D [23/May/2009:15:59:27 +0200] Report: clients=0
D [23/May/2009:15:59:27 +0200] Report: jobs=509
D [23/May/2009:15:59:27 +0200] Report: jobs-active=1
D [23/May/2009:15:59:27 +0200] Report: printers=2
D [23/May/2009:15:59:27 +0200] Report: printers-implicit=0
D [23/May/2009:15:59:27 +0200] Report: stringpool-string-count=1613
D [23/May/2009:15:59:27 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:15:59:27 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:00:33 +0200] Report: clients=0
D [23/May/2009:16:00:33 +0200] Report: jobs=509
D [23/May/2009:16:00:33 +0200] Report: jobs-active=1
D [23/May/2009:16:00:33 +0200] Report: printers=2
D [23/May/2009:16:00:33 +0200] Report: printers-implicit=0
D [23/May/2009:16:00:33 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:00:33 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:00:33 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:01:39 +0200] Report: clients=0
D [23/May/2009:16:01:39 +0200] Report: jobs=509
D [23/May/2009:16:01:39 +0200] Report: jobs-active=1
D [23/May/2009:16:01:39 +0200] Report: printers=2
D [23/May/2009:16:01:39 +0200] Report: printers-implicit=0
D [23/May/2009:16:01:39 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:01:39 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:01:39 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:02:45 +0200] Report: clients=0
D [23/May/2009:16:02:45 +0200] Report: jobs=509
D [23/May/2009:16:02:45 +0200] Report: jobs-active=1
D [23/May/2009:16:02:45 +0200] Report: printers=2
D [23/May/2009:16:02:45 +0200] Report: printers-implicit=0
D [23/May/2009:16:02:45 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:02:45 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:02:45 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:03:46 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:16:03:46 +0200] Report: clients=1
D [23/May/2009:16:03:46 +0200] Report: jobs=509
D [23/May/2009:16:03:46 +0200] Report: jobs-active=1
D [23/May/2009:16:03:46 +0200] Report: printers=2
D [23/May/2009:16:03:46 +0200] Report: printers-implicit=0
D [23/May/2009:16:03:46 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:03:46 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:03:46 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:03:46 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:16:03:46 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:16:03:46 +0200] Get-Jobs ipp://localhost/jobs/
D [23/May/2009:16:03:46 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:16:03:46 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:16:03:46 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:16:03:46 +0200] CUPS-Get-Printers
D [23/May/2009:16:03:46 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:16:03:46 +0200] cupsdCloseClient: 7
D [23/May/2009:16:04:53 +0200] Report: clients=0
D [23/May/2009:16:04:53 +0200] Report: jobs=509
D [23/May/2009:16:04:53 +0200] Report: jobs-active=1
D [23/May/2009:16:04:53 +0200] Report: printers=2
D [23/May/2009:16:04:53 +0200] Report: printers-implicit=0
D [23/May/2009:16:04:53 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:04:53 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:04:53 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:05:59 +0200] Report: clients=0
D [23/May/2009:16:05:59 +0200] Report: jobs=509
D [23/May/2009:16:05:59 +0200] Report: jobs-active=1
D [23/May/2009:16:05:59 +0200] Report: printers=2
D [23/May/2009:16:05:59 +0200] Report: printers-implicit=0
D [23/May/2009:16:05:59 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:05:59 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:05:59 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:07:05 +0200] Report: clients=0
D [23/May/2009:16:07:05 +0200] Report: jobs=509
D [23/May/2009:16:07:05 +0200] Report: jobs-active=1
D [23/May/2009:16:07:05 +0200] Report: printers=2
D [23/May/2009:16:07:05 +0200] Report: printers-implicit=0
D [23/May/2009:16:07:05 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:07:05 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:07:05 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:08:11 +0200] Report: clients=0
D [23/May/2009:16:08:11 +0200] Report: jobs=509
D [23/May/2009:16:08:11 +0200] Report: jobs-active=1
D [23/May/2009:16:08:11 +0200] Report: printers=2
D [23/May/2009:16:08:11 +0200] Report: printers-implicit=0
D [23/May/2009:16:08:11 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:08:11 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:08:11 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:08:17 +0200] [Job 1719] Found: %%oMd6TDAL5!,$=O]j;CW61l3N3[=4o[ijO)Yf]>6qhF':0q]`[5L\&NdM[mTTJ4M2$GL06EP3BOLu@;
D [23/May/2009:16:08:17 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:08:17 +0200] [Job 1719] 
D [23/May/2009:16:09:13 +0200] Report: clients=0
D [23/May/2009:16:09:13 +0200] Report: jobs=509
D [23/May/2009:16:09:13 +0200] Report: jobs-active=1
D [23/May/2009:16:09:13 +0200] Report: printers=2
D [23/May/2009:16:09:13 +0200] Report: printers-implicit=0
D [23/May/2009:16:09:13 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:09:13 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:09:13 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:10:19 +0200] Report: clients=0
D [23/May/2009:16:10:19 +0200] Report: jobs=509
D [23/May/2009:16:10:19 +0200] Report: jobs-active=1
D [23/May/2009:16:10:19 +0200] Report: printers=2
D [23/May/2009:16:10:19 +0200] Report: printers-implicit=0
D [23/May/2009:16:10:19 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:10:19 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:10:19 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:11:25 +0200] Report: clients=0
D [23/May/2009:16:11:25 +0200] Report: jobs=509
D [23/May/2009:16:11:25 +0200] Report: jobs-active=1
D [23/May/2009:16:11:25 +0200] Report: printers=2
D [23/May/2009:16:11:25 +0200] Report: printers-implicit=0
D [23/May/2009:16:11:25 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:11:25 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:11:25 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:12:31 +0200] Report: clients=0
D [23/May/2009:16:12:31 +0200] Report: jobs=509
D [23/May/2009:16:12:31 +0200] Report: jobs-active=1
D [23/May/2009:16:12:31 +0200] Report: printers=2
D [23/May/2009:16:12:31 +0200] Report: printers-implicit=0
D [23/May/2009:16:12:31 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:12:31 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:12:31 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:13:37 +0200] Report: clients=0
D [23/May/2009:16:13:37 +0200] Report: jobs=509
D [23/May/2009:16:13:37 +0200] Report: jobs-active=1
D [23/May/2009:16:13:37 +0200] Report: printers=2
D [23/May/2009:16:13:37 +0200] Report: printers-implicit=0
D [23/May/2009:16:13:37 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:13:37 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:13:37 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:14:43 +0200] Report: clients=0
D [23/May/2009:16:14:43 +0200] Report: jobs=509
D [23/May/2009:16:14:43 +0200] Report: jobs-active=1
D [23/May/2009:16:14:43 +0200] Report: printers=2
D [23/May/2009:16:14:43 +0200] Report: printers-implicit=0
D [23/May/2009:16:14:43 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:14:43 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:14:43 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:15:49 +0200] Report: clients=0
D [23/May/2009:16:15:49 +0200] Report: jobs=509
D [23/May/2009:16:15:49 +0200] Report: jobs-active=1
D [23/May/2009:16:15:49 +0200] Report: printers=2
D [23/May/2009:16:15:49 +0200] Report: printers-implicit=0
D [23/May/2009:16:15:49 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:15:49 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:15:49 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:16:55 +0200] Report: clients=0
D [23/May/2009:16:16:55 +0200] Report: jobs=509
D [23/May/2009:16:16:55 +0200] Report: jobs-active=1
D [23/May/2009:16:16:55 +0200] Report: printers=2
D [23/May/2009:16:16:55 +0200] Report: printers-implicit=0
D [23/May/2009:16:16:55 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:16:55 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:16:55 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:18:01 +0200] Report: clients=0
D [23/May/2009:16:18:01 +0200] Report: jobs=509
D [23/May/2009:16:18:01 +0200] Report: jobs-active=1
D [23/May/2009:16:18:01 +0200] Report: printers=2
D [23/May/2009:16:18:01 +0200] Report: printers-implicit=0
D [23/May/2009:16:18:01 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:18:01 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:18:01 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:19:07 +0200] Report: clients=0
D [23/May/2009:16:19:07 +0200] Report: jobs=509
D [23/May/2009:16:19:07 +0200] Report: jobs-active=1
D [23/May/2009:16:19:07 +0200] Report: printers=2
D [23/May/2009:16:19:07 +0200] Report: printers-implicit=0
D [23/May/2009:16:19:07 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:19:07 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:19:07 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:19:53 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:16:19:53 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:16:19:53 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:16:19:53 +0200] Get-Jobs ipp://localhost/jobs/
D [23/May/2009:16:19:53 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:16:19:53 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:16:19:53 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:16:19:53 +0200] CUPS-Get-Printers
D [23/May/2009:16:19:53 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:16:19:53 +0200] cupsdCloseClient: 7
D [23/May/2009:16:20:16 +0200] Report: clients=0
D [23/May/2009:16:20:16 +0200] Report: jobs=509
D [23/May/2009:16:20:16 +0200] Report: jobs-active=1
D [23/May/2009:16:20:16 +0200] Report: printers=2
D [23/May/2009:16:20:16 +0200] Report: printers-implicit=0
D [23/May/2009:16:20:16 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:20:16 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:20:16 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:21:22 +0200] Report: clients=0
D [23/May/2009:16:21:22 +0200] Report: jobs=509
D [23/May/2009:16:21:22 +0200] Report: jobs-active=1
D [23/May/2009:16:21:22 +0200] Report: printers=2
D [23/May/2009:16:21:22 +0200] Report: printers-implicit=0
D [23/May/2009:16:21:22 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:21:22 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:21:22 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:21:46 +0200] [Job 1719] Wrote 2 pages...
D [23/May/2009:16:21:46 +0200] PID 16616 (/usr/lib/cups/filter/pstops) exited with no errors.
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%EndBinary
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%PageTrailer
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%Trailer
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%DocumentNeededResources: 
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%DocumentSuppliedResources: procset Adobe_AGM_Image 1.0 0
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%DocumentNeededFeatures: 
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%DocumentSuppliedFeatures: *PageSize A4
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%DocumentProcessColors:  Cyan Magenta Yellow Black
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%DocumentCustomColors: 
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%CMYKCustomColor: 
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%RGBCustomColor: 
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%Pages: 2
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%BoundingBox: 25 36 570 806
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Found: %%EOF
D [23/May/2009:16:22:16 +0200] [Job 1719] --> Continue DSC parsing now.
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] 
D [23/May/2009:16:22:16 +0200] [Job 1719] Closing renderer
D [23/May/2009:16:22:28 +0200] Report: clients=0
D [23/May/2009:16:22:28 +0200] Report: jobs=509
D [23/May/2009:16:22:28 +0200] Report: jobs-active=1
D [23/May/2009:16:22:28 +0200] Report: printers=2
D [23/May/2009:16:22:28 +0200] Report: printers-implicit=0
D [23/May/2009:16:22:28 +0200] Report: stringpool-string-count=1613
D [23/May/2009:16:22:28 +0200] Report: stringpool-alloc-bytes=9264
D [23/May/2009:16:22:28 +0200] Report: stringpool-total-bytes=20224
D [23/May/2009:16:22:39 +0200] Discarding unused job-progress event...
D [23/May/2009:16:22:41 +0200] [Job 1719] Process 16637 ending: "foomatic-gswrapper -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=pxlmono -r600x600 -sOutputFile=- - ..."
D [23/May/2009:16:22:41 +0200] [Job 1719] KID3 exited with status 0
D [23/May/2009:16:22:44 +0200] [Job 1719] tail process done writing data to STDOUT
D [23/May/2009:16:22:44 +0200] [Job 1719] KID4 finished
D [23/May/2009:16:22:44 +0200] [Job 1719] KID4 exited with status 0
D [23/May/2009:16:22:44 +0200] [Job 1719] Renderer exit stat: 0
D [23/May/2009:16:22:44 +0200] [Job 1719] KID3 finished
D [23/May/2009:16:22:44 +0200] [Job 1719] Renderer process finished
D [23/May/2009:16:22:44 +0200] [Job 1719] 
D [23/May/2009:16:22:44 +0200] [Job 1719] Closing foomatic-rip.
D [23/May/2009:16:22:44 +0200] PID 16617 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.
D [23/May/2009:16:23:05 +0200] [Job 1719] prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused
D [23/May/2009:16:23:05 +0200] Discarding unused printer-state-changed event...
D [23/May/2009:16:23:05 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [23/May/2009:16:23:05 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:16:23:05 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:16:23:05 +0200] Get-Jobs ipp://localhost/jobs/
D [23/May/2009:16:23:05 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:16:23:05 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [23/May/2009:16:23:05 +0200] cupsdAuthorize: No authentication data provided.
D [23/May/2009:16:23:05 +0200] CUPS-Get-Printers
D [23/May/2009:16:23:05 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [23/May/2009:16:23:05 +0200] cupsdCloseClient: 7
D [23/May/2009:16:23:05 +0200] PID 16618 (/usr/lib/cups/backend/hp) exited with no errors.
D [23/May/2009:16:23:05 +0200] [Job 1719] File 0 is complete.
I [23/May/2009:16:23:05 +0200] [Job 1719] Completed successfully.
D [23/May/2009:16:23:05 +0200] Discarding unused printer-state-changed event...
D [23/May/2009:16:23:05 +0200] Discarding unused job-completed event...
D [23/May/2009:16:23:06 +0200] [Job 1719] Unloading...

---

### Post by ckonestroh on 2009-05-24
Had this problem for years now with PDF'S


Look some PDF's have embedded code by programs for page layout and background image to be a certain color...


The only solution I've found over the years is a old printer like dot matrix...

Still the problem is Dot Matrix is not able to read PDF files....

So your back to copy, cut and paste....

But lots of PDF's are read only no copy or paste...

Government is bad about PDF forms being a read only worried you will change the form....

Anyways try 127.0.0.1 should pullup your printer administration see if there is an option to print pdf's or not to....

There should be lots of options in your cups not sure what options this printer might have in cups....


Good luck....

---

