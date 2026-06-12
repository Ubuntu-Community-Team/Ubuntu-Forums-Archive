---
title: "HP 930C USB printer doesn#t print in ubuntu, windows ok"
date: 2009-04-08
forum: General Help
---

### Post by monkman on 2009-04-08
ubuntu 8.10, 64bit(up to date)
HP 930C USB printer

When i try to print i get an error(in my case in german)

[error-screenshot]("http://bayimg.com/JaOJaAaBN")

Diagnosis output
```
D [08/Apr/2009:10:41:44 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:41:44 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:41:44 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:41:44 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:44 +0200] Get-Jobs ipp://localhost/jobs/
D [08/Apr/2009:10:41:44 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:44 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:41:44 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:41:44 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:41:44 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:44 +0200] Create-Printer-Subscription /
D [08/Apr/2009:10:41:44 +0200] cupsdCreateSubscription(con=0x7f2e5c5b4940(7), uri="/")
D [08/Apr/2009:10:41:44 +0200] pullmethod="ippget"
D [08/Apr/2009:10:41:44 +0200] notify-lease-duration=86400
D [08/Apr/2009:10:41:44 +0200] notify-time-interval=0
D [08/Apr/2009:10:41:44 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [08/Apr/2009:10:41:44 +0200] Added subscription 3 for server
I [08/Apr/2009:10:41:44 +0200] Saving subscriptions.conf...
D [08/Apr/2009:10:41:44 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:44 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:41:45 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:41:45 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:41:45 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:45 +0200] Get-Notifications /
D [08/Apr/2009:10:41:45 +0200] cupsdIsAuthorized: requesting-user-name="monkman"
D [08/Apr/2009:10:41:45 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:45 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 7 POST /printers/DESKJET-930C HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] Print-Job ipp://localhost/printers/DESKJET-930C
D [08/Apr/2009:10:41:59 +0200] add_job: requesting-user-name="monkman"
D [08/Apr/2009:10:41:59 +0200] Adding default job-sheets values "none,none"...
I [08/Apr/2009:10:41:59 +0200] [Job 2] Adding start banner page "none".
I [08/Apr/2009:10:41:59 +0200] Saving subscriptions.conf...
I [08/Apr/2009:10:41:59 +0200] [Job 2] Adding end banner page "none".
I [08/Apr/2009:10:41:59 +0200] [Job 2] File of type application/postscript queued by "monkman".
D [08/Apr/2009:10:41:59 +0200] [Job 2] hold_until=0
I [08/Apr/2009:10:41:59 +0200] [Job 2] Queued on "DESKJET-930C" by "monkman".
I [08/Apr/2009:10:41:59 +0200] Saving subscriptions.conf...
D [08/Apr/2009:10:41:59 +0200] [Job 2] job-sheets=none,none
D [08/Apr/2009:10:41:59 +0200] [Job 2] banner_page = 0
D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[0]="DESKJET-930C"
D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[1]="2"
D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[2]="monkman"
D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[3]="Test Page"
D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[4]="1"
D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[5]="job-uuid=urn:uuid:f20942a7-3cc3-3999-48a3-6d3fdd816b11"
D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[6]="/var/spool/cups/d00002-001"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[9]="SERVER_ADMIN=root@pc-ubuntu"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[10]="SOFTWARE=CUPS/1.3.9"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[12]="TZ=Europe/Berlin"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[13]="USER=root"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[16]="IPP_PORT=631"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[17]="CHARSET=utf-8"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[18]="LANG=de_DE.UTF8"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[19]="PPD=/etc/cups/ppd/DESKJET-930C.ppd"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[20]="RIP_MAX_CACHE=8m"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[21]="CONTENT_TYPE=application/postscript"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[22]="DEVICE_URI=hp:/usb/DeskJet_930C?serial=ES04D1D2VVJJ"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[23]="PRINTER=DESKJET-930C"
D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[24]="FINAL_CONTENT_TYPE=printer/DESKJET-930C"
I [08/Apr/2009:10:41:59 +0200] [Job 2] Started filter /usr/lib/cups/filter/pstopdf (PID 6375)
I [08/Apr/2009:10:41:59 +0200] [Job 2] Started filter /usr/lib/cups/filter/pdftopdf (PID 6376)
I [08/Apr/2009:10:41:59 +0200] [Job 2] Started filter /usr/lib/cups/filter/foomatic-rip (PID 6377)
I [08/Apr/2009:10:41:59 +0200] [Job 2] Started backend /usr/lib/cups/backend/hp (PID 6379)
I [08/Apr/2009:10:41:59 +0200] Saving subscriptions.conf...
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] [Job 2] pstopdf argv[6] = 2 monkman Test Page 1 job-uuid=urn:uuid:f20942a7-3cc3-3999-48a3-6d3fdd816b11 /var/spool/cups/d00002-001
D [08/Apr/2009:10:41:59 +0200] [Job 2] PPD: /etc/cups/ppd/DESKJET-930C.ppd
D [08/Apr/2009:10:41:59 +0200] [Job 2] Getting input from file
D [08/Apr/2009:10:41:59 +0200] [Job 2] foomatic-rip version 4.0.0.195 running...
D [08/Apr/2009:10:41:59 +0200] [Job 2] Parsing PPD file ...
D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option PageSize
D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option ImageableArea
D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option PaperDimension
D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option ColorMode
D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option BlackCorrect
D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option Depletion
D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option Passes
D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option Font
D [08/Apr/2009:10:41:59 +0200] [Job 2]
D [08/Apr/2009:10:41:59 +0200] [Job 2] Parameter Summary
D [08/Apr/2009:10:41:59 +0200] [Job 2] -----------------
D [08/Apr/2009:10:41:59 +0200] [Job 2]
D [08/Apr/2009:10:41:59 +0200] [Job 2] Spooler: cups
D [08/Apr/2009:10:41:59 +0200] [Job 2] Printer: DESKJET-930C
D [08/Apr/2009:10:41:59 +0200] [Job 2] Shell: /bin/bash
D [08/Apr/2009:10:41:59 +0200] [Job 2] PPD file: /etc/cups/ppd/DESKJET-930C.ppd
D [08/Apr/2009:10:41:59 +0200] [Job 2] ATTR file:
D [08/Apr/2009:10:41:59 +0200] [Job 2] Printer model: HP DeskJet 930C Foomatic/cdj550
D [08/Apr/2009:10:41:59 +0200] [Job 2] Job title: Test Page
D [08/Apr/2009:10:41:59 +0200] [Job 2] File(s) to be printed:
D [08/Apr/2009:10:41:59 +0200] [Job 2] <STDIN>
D [08/Apr/2009:10:41:59 +0200] [Job 2]
D [08/Apr/2009:10:41:59 +0200] [Job 2] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [08/Apr/2009:10:41:59 +0200] [Job 2] Pondering option 'job-uuid=urn:uuid:f20942a7-3cc3-3999-48a3-6d3fdd816b11'
D [08/Apr/2009:10:41:59 +0200] [Job 2] Unknown option job-uuid=urn:uuid:f20942a7-3cc3-3999-48a3-6d3fdd816b11.
D [08/Apr/2009:10:41:59 +0200] [Job 2]
D [08/Apr/2009:10:41:59 +0200] [Job 2] ================================================
D [08/Apr/2009:10:41:59 +0200] [Job 2]
D [08/Apr/2009:10:41:59 +0200] [Job 2] File: <STDIN>
D [08/Apr/2009:10:41:59 +0200] [Job 2]
D [08/Apr/2009:10:41:59 +0200] [Job 2] ================================================
D [08/Apr/2009:10:41:59 +0200] [Job 2]
D [08/Apr/2009:10:41:59 +0200] [Job 2] Resolution:
D [08/Apr/2009:10:41:59 +0200] [Job 2] Page size: A4
D [08/Apr/2009:10:41:59 +0200] [Job 2] Width: 595, height: 842, absolute margins: , , ,
I [08/Apr/2009:10:41:59 +0200] Saving subscriptions.conf...
D [08/Apr/2009:10:41:59 +0200] [Job 2] Relative margins: 18, 36, 18, 36
D [08/Apr/2009:10:41:59 +0200] [Job 2] PPD options: -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842
D [08/Apr/2009:10:41:59 +0200] [Job 2] PostScript to be injected:
D [08/Apr/2009:10:41:59 +0200] [Job 2] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dPDFSETTINGS=/printer -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 - -
D [08/Apr/2009:10:41:59 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:41:59 +0200] [Job 2] GPL Ghostscript 8.63: Set UseCIEColor for UseDeviceIndependentColor to work properly.
D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] Get-Jobs ipp://localhost/jobs/
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] Get-Notifications /
D [08/Apr/2009:10:41:59 +0200] cupsdIsAuthorized: requesting-user-name="monkman"
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] Get-Job-Attributes ipp://localhost/jobs/2
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 8 from localhost (Domain)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 8 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] Get-Notifications /
D [08/Apr/2009:10:41:59 +0200] cupsdIsAuthorized: requesting-user-name="monkman"
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 11 from localhost (Domain)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Printers
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Classes
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Default
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Printers
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Classes
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Default
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdCloseClient: 8
D [08/Apr/2009:10:41:59 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:41:59 +0200] Get-Notifications /
D [08/Apr/2009:10:41:59 +0200] cupsdIsAuthorized: requesting-user-name="monkman"
D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:41:59 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:41:59 +0200] PID 6375 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [08/Apr/2009:10:41:59 +0200] [Job 2] Filetype: PDF
D [08/Apr/2009:10:41:59 +0200] [Job 2] Storing temporary files in /var/spool/cups/tmp
D [08/Apr/2009:10:41:59 +0200] PID 6376 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [08/Apr/2009:10:42:00 +0200] [Job 2] File contains 1 pages
D [08/Apr/2009:10:42:00 +0200] [Job 2] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -r300x300 -sDEVICE=cdj550 -dBitsPerPixel=1 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dDepletion=0 -sOutputFile=-   /var/spool/cups/tmp/foomatic-mgy8bl
D [08/Apr/2009:10:42:00 +0200] [Job 2] Starting process "kid3" (generation 1)
D [08/Apr/2009:10:42:00 +0200] [Job 2] Starting process "kid4" (generation 2)
D [08/Apr/2009:10:42:00 +0200] [Job 2] JCL: %-12345X@PJL
D [08/Apr/2009:10:42:00 +0200] [Job 2] <job data>
D [08/Apr/2009:10:42:00 +0200] [Job 2]
D [08/Apr/2009:10:42:00 +0200] [Job 2] Starting process "renderer" (generation 2)
D [08/Apr/2009:10:42:00 +0200] [Job 2] renderer exited with status 255
I [08/Apr/2009:10:42:00 +0200] Saving subscriptions.conf...
D [08/Apr/2009:10:42:00 +0200] [Job 2] Kid3 exit status: 3
E [08/Apr/2009:10:42:00 +0200] PID 6377 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [08/Apr/2009:10:42:00 +0200] PID 6379 (/usr/lib/cups/backend/hp) exited with no errors.
D [08/Apr/2009:10:42:00 +0200] [Job 2] File 0 is complete.
E [08/Apr/2009:10:42:00 +0200] [Job 2] Job stopped due to filter errors.
I [08/Apr/2009:10:42:00 +0200] Saving subscriptions.conf...
I [08/Apr/2009:10:42:00 +0200] Saving subscriptions.conf...
D [08/Apr/2009:10:42:00 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:00 +0200] Get-Jobs ipp://localhost/jobs/
D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:00 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:42:00 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:00 +0200] Get-Notifications /
D [08/Apr/2009:10:42:00 +0200] cupsdIsAuthorized: requesting-user-name="monkman"
D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:00 +0200] cupsdAcceptClient: 8 from localhost (Domain)
D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 8 POST / HTTP/1.1
D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:00 +0200] Get-Notifications /
D [08/Apr/2009:10:42:00 +0200] cupsdIsAuthorized: requesting-user-name="monkman"
D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Printers
D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Classes
D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Default
D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Printers
D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:00 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:42:00 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:00 +0200] Get-Notifications /
D [08/Apr/2009:10:42:00 +0200] cupsdIsAuthorized: requesting-user-name="monkman"
D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Classes
D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:00 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Default
D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:00 +0200] cupsdCloseClient: 8
D [08/Apr/2009:10:42:01 +0200] [Job 2] Unloading...
D [08/Apr/2009:10:42:07 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:42:07 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:42:07 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:07 +0200] Get-Job-Attributes ipp://localhost/jobs/2
D [08/Apr/2009:10:42:07 +0200] [Job 2] Loading attributes...
D [08/Apr/2009:10:42:07 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:07 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:42:07 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:42:07 +0200] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Apr/2009:10:42:07 +0200] cupsdAuthorize: No authentication data provided.
D [08/Apr/2009:10:42:07 +0200] Cancel-Subscription /
D [08/Apr/2009:10:42:07 +0200] cupsdIsAuthorized: requesting-user-name="monkman"
I [08/Apr/2009:10:42:07 +0200] Saving subscriptions.conf...
D [08/Apr/2009:10:42:07 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Apr/2009:10:42:07 +0200] cupsdCloseClient: 7
D [08/Apr/2009:10:42:07 +0200] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Apr/2009:10:42:07 +0200] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1
D [08/Apr/2009:10:42:07 +0200] cupsdAuthorize: No authentication data provided.
```

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest DESKJET-930C (default)>,
 'cups_instance': None,
 'cups_queue': 'DESKJET-930C',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/DeskJet_930C?serial=ES04D1D2VVJJ',
                       'printer-info': u'HEWLETT-PACKARD DESKJET 930C',
                       'printer-is-shared': True,
                       'printer-location': u'pc-ubuntu',
                       'printer-make-and-model': u'HP DeskJet 930C Foomatic/cdj550',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 143372,
                       'printer-uri-supported': u'ipp://localhost:631/printers/DESKJET-930C'},
 'cups_printer_remote': False,
 'hplip_output': (['',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 2.8.7)\x1b[0m',
                   '\x1b[01mSystem Tray Status Service ver. 0.1\x1b[0m',
                   '',
                   'Copyright (c) 2001-8 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 2.8.7)\x1b[0m',
                   '\x1b[01mDevice Information Utility ver. 4.1\x1b[0m',
                   '',
                   'Copyright (c) 2001-8 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mhp:/usb/DeskJet_930C?serial=ES04D1D2VVJJ\x1b[0m',
                   '',
                   '\x1b[01mDevice Parameters (dynamic data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  back-end                      hp                                                        ',
                   '  cups-printer                  DESKJET-930C                                              ',
                   '  cups-uri                      hp:/usb/DeskJet_930C?serial=ES04D1D2VVJJ                  ',
                   '  dev-file                                                                                ',
                   '  device-state                  -1                                                        ',
                   '  device-uri                    hp:/usb/DeskJet_930C?serial=ES04D1D2VVJJ                  ',
                   '  deviceid                                                                                ',
                   '  error-state                   101                                                       ',
                   '  host                                                                                    ',
                   '  is-hp                         True                                                      ',
                   '  panel                         0                                                         ',
                   '  panel-line1                                                                             ',
                   '  panel-line2                                                                             ',
                   '  port                          1                                                         ',
                   '  serial                        ES04D1D2VVJJ                                              ',
                   '  status-code                   5002                                                      ',
                   '  status-desc                                                                             ',
                   '\x1b[01m',
                   'Model Parameters (static data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  align-type                    1                                                         ',
                   '  clean-type                    1                                                         ',
                   '  color-cal-type                0                                                         ',
                   '  copy-type                     0                                                         ',
                   '  embedded-server-type          0                                                         ',
                   '  fax-type                      0                                                         ',
                   '  fw-download                   0                                                         ',
                   '  icon                          DESKJET_960C.png                                          ',
                   '  io-mfp-mode                   6                                                         ',
                   '  io-mode                       1                                                         ',
                   '  io-support                    2                                                         ',
                   '  job-storage                   0                                                         ',
                   '  linefeed-cal-type             0                                                         ',
                   '  model                         DeskJet_930C                                              ',
                   '  model-ui                      HP Deskjet 930c                                           ',
                   '  model1                        Deskjet 930c                                              ',
                   '  model2                        Deskjet 930cm                                             ',
                   '  panel-check-type              0                                                         ',
                   '  pcard-type                    0                                                         ',
                   '  plugin                        0                                                         ',
                   '  power-settings                0                                                         ',
                   '  pq-diag-type                  0                                                         ',
                   '  r-type                        0                                                         ',
                   '  r0-agent1-kind                3                                                         ',
                   '  r0-agent1-sku                 45 (51645A)                                               ',
                   '  r0-agent1-type                1                                                         ',
                   '  r0-agent2-kind                3                                                         ',
                   '  r0-agent2-sku                 78 (C6578DN/C6578AN)                                      ',
                   '  r0-agent2-type                2                                                         ',
                   '  scan-style                    0                                                         ',
                   '  scan-type                     0                                                         ',
                   '  status-battery-check          0                                                         ',
                   '  status-dynamic-counters       0                                                         ',
                   '  status-type                   1                                                         ',
                   '  support-released              1                                                         ',
                   '  support-type                  2                                                         ',
                   '  support-ver                   0.9.5                                                     ',
                   "  tech-class                    ['DJ9xx']                                                 ",
                   "  tech-subclass                 ['Normal']                                                ",
                   '  tech-type                     2                                                         ',
                   '  usb-pid                       1204                                                      ',
                   '  usb-vid                       03f0                                                      ',
                   '',
                   'Done.',
                   ''],
                  ['\x1b[31;01merror: Unable to communicate with device (code=12): hp:/usb/DeskJet_930C?serial=ES04D1D2VVJJ\x1b[0m',
                   '\x1b[31;01merror: Error opening device (Device not found).\x1b[0m',
                   '']),
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Adjustment': {u'BlackCorrect': u'0',
                                               u'Depletion': u'No'},
                               u'General': {u'ColorMode': u'BlackAndWhite',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4'},
                               u'Miscellaneous': {u'Passes': u'Default'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:HP;MDL:DeskJet 930C;CLS:PRINTER;DES:DeskJet 930C;SN:ES04D1D2VVJJ;',
                      'device-info': u'HP DeskJet 930C USB ES04D1D2VVJJ HPLIP',
                      'device-make-and-model': u'HP DeskJet 930C'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 1942,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(2,
                            u'Job stopped due to filter errors; please consult the error_log file for details.')],
 'test_page_job_id': [2],
 'test_page_job_status': [(False,
                           1,
                           'DESKJET-930C',
                           '708155601.pdf',
                           'Angehalten',
                           None),
                          (True,
                           2,
                           'DESKJET-930C',
                           'Test Page',
                           'Angehalten',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'de-de',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 2,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/2',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'monkman',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1239180127,
                            'job-printer-uri': u'ipp://pc-ubuntu:631/printers/DESKJET-930C',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/2',
                            'job-uuid': u'urn:uuid:f20942a7-3cc3-3999-48a3-6d3fdd816b11',
                            'printer-uri': u'ipp://localhost/printers/DESKJET-930C',
                            'time-at-completed': None,
                            'time-at-creation': 1239180119,
                            'time-at-processing': 1239180119})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [08/Apr/2009:10:41:44 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:41:44 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:41:44 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:44 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:44 +0200] Get-Jobs ipp://localhost/jobs/',
               'D [08/Apr/2009:10:41:44 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:44 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:41:44 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:41:44 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:44 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:44 +0200] Create-Printer-Subscription /',
               'D [08/Apr/2009:10:41:44 +0200] cupsdCreateSubscription(con=0x7f2e5c5b4940(7), uri="/")',
               'D [08/Apr/2009:10:41:44 +0200] pullmethod="ippget"',
               'D [08/Apr/2009:10:41:44 +0200] notify-lease-duration=86400',
               'D [08/Apr/2009:10:41:44 +0200] notify-time-interval=0',
               'D [08/Apr/2009:10:41:44 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [08/Apr/2009:10:41:44 +0200] Added subscription 3 for server',
               'I [08/Apr/2009:10:41:44 +0200] Saving subscriptions.conf...',
               'D [08/Apr/2009:10:41:44 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:44 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:41:45 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:41:45 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:45 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:45 +0200] Get-Notifications /',
               'D [08/Apr/2009:10:41:45 +0200] cupsdIsAuthorized: requesting-user-name="monkman"',
               'D [08/Apr/2009:10:41:45 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:45 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 7 POST /printers/DESKJET-930C HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] Print-Job ipp://localhost/printers/DESKJET-930C',
               'D [08/Apr/2009:10:41:59 +0200] add_job: requesting-user-name="monkman"',
               'D [08/Apr/2009:10:41:59 +0200] Adding default job-sheets values "none,none"...',
               'I [08/Apr/2009:10:41:59 +0200] [Job 2] Adding start banner page "none".',
               'I [08/Apr/2009:10:41:59 +0200] Saving subscriptions.conf...',
               'I [08/Apr/2009:10:41:59 +0200] [Job 2] Adding end banner page "none".',
               'I [08/Apr/2009:10:41:59 +0200] [Job 2] File of type application/postscript queued by "monkman".',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] hold_until=0',
               'I [08/Apr/2009:10:41:59 +0200] [Job 2] Queued on "DESKJET-930C" by "monkman".',
               'I [08/Apr/2009:10:41:59 +0200] Saving subscriptions.conf...',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] job-sheets=none,none',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] banner_page = 0',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[0]="DESKJET-930C"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[1]="2"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[2]="monkman"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[3]="Test Page"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[4]="1"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[5]="job-uuid=urn:uuid:f20942a7-3cc3-3999-48a3-6d3fdd816b11"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] argv[6]="/var/spool/cups/d00002-001"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[9]="SERVER_ADMIN=root@pc-ubuntu"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[12]="TZ=Europe/Berlin"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[13]="USER=root"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[16]="IPP_PORT=631"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[17]="CHARSET=utf-8"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[18]="LANG=de_DE.UTF8"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[19]="PPD=/etc/cups/ppd/DESKJET-930C.ppd"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[20]="RIP_MAX_CACHE=8m"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[22]="DEVICE_URI=hp:/usb/DeskJet_930C?serial=ES04D1D2VVJJ"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[23]="PRINTER=DESKJET-930C"',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] envp[24]="FINAL_CONTENT_TYPE=printer/DESKJET-930C"',
               'I [08/Apr/2009:10:41:59 +0200] [Job 2] Started filter /usr/lib/cups/filter/pstopdf (PID 6375)',
               'I [08/Apr/2009:10:41:59 +0200] [Job 2] Started filter /usr/lib/cups/filter/pdftopdf (PID 6376)',
               'I [08/Apr/2009:10:41:59 +0200] [Job 2] Started filter /usr/lib/cups/filter/foomatic-rip (PID 6377)',
               'I [08/Apr/2009:10:41:59 +0200] [Job 2] Started backend /usr/lib/cups/backend/hp (PID 6379)',
               'I [08/Apr/2009:10:41:59 +0200] Saving subscriptions.conf...',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] pstopdf argv[6] = 2 monkman Test Page 1 job-uuid=urn:uuid:f20942a7-3cc3-3999-48a3-6d3fdd816b11 /var/spool/cups/d00002-001',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] PPD: /etc/cups/ppd/DESKJET-930C.ppd',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Getting input from file',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] foomatic-rip version 4.0.0.195 running...',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Parsing PPD file ...',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option PageSize',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option ImageableArea',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option PaperDimension',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option ColorMode',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option BlackCorrect',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option Depletion',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option Passes',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Added option Font',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2]',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Parameter Summary',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] -----------------',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2]',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Spooler: cups',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Printer: DESKJET-930C',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Shell: /bin/bash',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] PPD file: /etc/cups/ppd/DESKJET-930C.ppd',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] ATTR file:',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Printer model: HP DeskJet 930C Foomatic/cdj550',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Job title: Test Page',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] File(s) to be printed:',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] <STDIN>',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2]',
               "D [08/Apr/2009:10:41:59 +0200] [Job 2] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               "D [08/Apr/2009:10:41:59 +0200] [Job 2] Pondering option 'job-uuid=urn:uuid:f20942a7-3cc3-3999-48a3-6d3fdd816b11'",
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Unknown option job-uuid=urn:uuid:f20942a7-3cc3-3999-48a3-6d3fdd816b11.',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2]',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] ================================================',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2]',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] File: <STDIN>',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2]',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] ================================================',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2]',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Resolution:',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Page size: A4',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Width: 595, height: 842, absolute margins: , , ,',
               'I [08/Apr/2009:10:41:59 +0200] Saving subscriptions.conf...',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Relative margins: 18, 36, 18, 36',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] PPD options: -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] PostScript to be injected:',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dPDFSETTINGS=/printer -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 - -',
               'D [08/Apr/2009:10:41:59 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] GPL Ghostscript 8.63: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] Get-Jobs ipp://localhost/jobs/',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] Get-Notifications /',
               'D [08/Apr/2009:10:41:59 +0200] cupsdIsAuthorized: requesting-user-name="monkman"',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] Get-Job-Attributes ipp://localhost/jobs/2',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] Get-Notifications /',
               'D [08/Apr/2009:10:41:59 +0200] cupsdIsAuthorized: requesting-user-name="monkman"',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Printers',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Classes',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Default',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Printers',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Classes',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] CUPS-Get-Default',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdCloseClient: 8',
               'D [08/Apr/2009:10:41:59 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:41:59 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:41:59 +0200] Get-Notifications /',
               'D [08/Apr/2009:10:41:59 +0200] cupsdIsAuthorized: requesting-user-name="monkman"',
               'D [08/Apr/2009:10:41:59 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:41:59 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:41:59 +0200] PID 6375 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Filetype: PDF',
               'D [08/Apr/2009:10:41:59 +0200] [Job 2] Storing temporary files in /var/spool/cups/tmp',
               'D [08/Apr/2009:10:41:59 +0200] PID 6376 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2] File contains 1 pages',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -r300x300 -sDEVICE=cdj550 -dBitsPerPixel=1 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dDepletion=0 -sOutputFile=-   /var/spool/cups/tmp/foomatic-mgy8bl',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2] Starting process "kid3" (generation 1)',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2] Starting process "kid4" (generation 2)',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2] JCL: \x1b%-12345X@PJL',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2] <job data>',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2]',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2] Starting process "renderer" (generation 2)',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2] renderer exited with status 255',
               'I [08/Apr/2009:10:42:00 +0200] Saving subscriptions.conf...',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2] Kid3 exit status: 3',
               'E [08/Apr/2009:10:42:00 +0200] PID 6377 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!',
               'D [08/Apr/2009:10:42:00 +0200] PID 6379 (/usr/lib/cups/backend/hp) exited with no errors.',
               'D [08/Apr/2009:10:42:00 +0200] [Job 2] File 0 is complete.',
               'E [08/Apr/2009:10:42:00 +0200] [Job 2] Job stopped due to filter errors.',
               'I [08/Apr/2009:10:42:00 +0200] Saving subscriptions.conf...',
               'I [08/Apr/2009:10:42:00 +0200] Saving subscriptions.conf...',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:00 +0200] Get-Jobs ipp://localhost/jobs/',
               'D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:00 +0200] Get-Notifications /',
               'D [08/Apr/2009:10:42:00 +0200] cupsdIsAuthorized: requesting-user-name="monkman"',
               'D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:00 +0200] Get-Notifications /',
               'D [08/Apr/2009:10:42:00 +0200] cupsdIsAuthorized: requesting-user-name="monkman"',
               'D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Printers',
               'D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Classes',
               'D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Default',
               'D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Printers',
               'D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:00 +0200] Get-Notifications /',
               'D [08/Apr/2009:10:42:00 +0200] cupsdIsAuthorized: requesting-user-name="monkman"',
               'D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Classes',
               'D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:42:00 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:00 +0200] CUPS-Get-Default',
               'D [08/Apr/2009:10:42:00 +0200] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:00 +0200] cupsdCloseClient: 8',
               'D [08/Apr/2009:10:42:01 +0200] [Job 2] Unloading...',
               'D [08/Apr/2009:10:42:07 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:42:07 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:07 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:07 +0200] Get-Job-Attributes ipp://localhost/jobs/2',
               'D [08/Apr/2009:10:42:07 +0200] [Job 2] Loading attributes...',
               'D [08/Apr/2009:10:42:07 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:07 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:42:07 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:42:07 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [08/Apr/2009:10:42:07 +0200] cupsdAuthorize: No authentication data provided.',
               'D [08/Apr/2009:10:42:07 +0200] Cancel-Subscription /',
               'D [08/Apr/2009:10:42:07 +0200] cupsdIsAuthorized: requesting-user-name="monkman"',
               'I [08/Apr/2009:10:42:07 +0200] Saving subscriptions.conf...',
               'D [08/Apr/2009:10:42:07 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [08/Apr/2009:10:42:07 +0200] cupsdCloseClient: 7',
               'D [08/Apr/2009:10:42:07 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [08/Apr/2009:10:42:07 +0200] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1',
               'D [08/Apr/2009:10:42:07 +0200] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
```

After some time i get a print out of it saying:

```
Unrecoverable error: rangecheck in .putdeviceprops
```

It used to work fine in 8.04, since i don't use it often i just realised the problems after updating to 8.10.

Thanks!!

---

### Post by bumanie on 2009-04-08
That looks fairly critical. Have you tried the HP self extracting installer? If not go [here]("http://hplipopensource.com/hplip-web/gethplip.html") and give it a try. If the installer doesn't work, it will usually tell what error it is getting, which in many cases are missing dependencies, but there can be other errors of course. If that doesn't work, put in a bug report to launchpad so that HP or a CUPS maintainer can have a look.

---

### Post by monkman on 2009-04-08
Thank you! That worked for me.

---

