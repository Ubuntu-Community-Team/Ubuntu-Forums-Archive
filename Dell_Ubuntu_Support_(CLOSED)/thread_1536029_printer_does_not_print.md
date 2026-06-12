---
title: "printer does not print"
date: 2010-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bill56 on 2010-07-21
I have installed the lpr and cupswrapper drivers using the command line terminal for a Brother MFC8860DN printer in Ubuntu 10.04. The drivers are recognized and the printer is recognized, but the printer does not print. I ran a troubleshooting process and got the error log below.  I am a newbie that loves working with Ubuntu. The printer intallation is driving me crazy though. Please help. I hope the error log below can be understood by someone that can give me a solution.

Bill





D [21/Jul/2010:16:36:50 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:36:50 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [21/Jul/2010:16:36:50 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:36:50 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:50 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1
D [21/Jul/2010:16:36:50 -0400] Get-Jobs ipp://localhost/printers/
D [21/Jul/2010:16:36:50 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [21/Jul/2010:16:36:50 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:36:50 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [21/Jul/2010:16:36:50 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:36:50 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:50 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1
D [21/Jul/2010:16:36:50 -0400] Get-Jobs ipp://localhost/printers/
D [21/Jul/2010:16:36:50 -0400] [Job 1] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 1] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 2] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 2] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 3] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 3] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 5] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 5] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 6] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 6] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 7] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 7] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 8] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 8] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 9] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 9] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 10] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 10] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 11] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 11] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 12] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 12] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 13] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 13] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 14] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 14] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 15] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 15] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 16] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 16] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:50 -0400] [Job 17] Loading attributes...
E [21/Jul/2010:16:36:51 -0400] [Job 17] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:51 -0400] [Job 18] Loading attributes...
E [21/Jul/2010:16:36:51 -0400] [Job 18] Unable to queue job for destination "Brother-MFC-8860DN"!
D [21/Jul/2010:16:36:51 -0400] [Job 19] Loading attributes...
D [21/Jul/2010:16:36:51 -0400] [Job 20] Loading attributes...
D [21/Jul/2010:16:36:51 -0400] [Job 21] Loading attributes...
D [21/Jul/2010:16:36:51 -0400] [Job 22] Loading attributes...
D [21/Jul/2010:16:36:51 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [21/Jul/2010:16:36:51 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:36:51 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [21/Jul/2010:16:36:51 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:36:51 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:51 -0400] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1
D [21/Jul/2010:16:36:51 -0400] Create-Printer-Subscription /
D [21/Jul/2010:16:36:51 -0400] cupsdCreateSubscription(con=0x7fa19e125270(11), uri="/")
D [21/Jul/2010:16:36:51 -0400] pullmethod="ippget"
D [21/Jul/2010:16:36:51 -0400] notify-lease-duration=86400
D [21/Jul/2010:16:36:51 -0400] notify-time-interval=0
D [21/Jul/2010:16:36:51 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [21/Jul/2010:16:36:51 -0400] Added subscription 41 for server
D [21/Jul/2010:16:36:51 -0400] cupsdMarkDirty(-----S)
D [21/Jul/2010:16:36:51 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [21/Jul/2010:16:36:51 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:36:52 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [21/Jul/2010:16:36:52 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:36:52 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:52 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [21/Jul/2010:16:36:52 -0400] Get-Notifications /
D [21/Jul/2010:16:36:52 -0400] cupsdIsAuthorized: requesting-user-name="bill"
D [21/Jul/2010:16:36:52 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [21/Jul/2010:16:36:52 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 13 POST /printers/MFC8860DN HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 13 1.1 Print-Job 1
D [21/Jul/2010:16:36:57 -0400] Print-Job ipp://localhost/printers/MFC8860DN
D [21/Jul/2010:16:36:57 -0400] [Job ???] Auto-typing file...
I [21/Jul/2010:16:36:57 -0400] [Job ???] Request file type is application/vnd.cups-banner.
D [21/Jul/2010:16:36:57 -0400] cupsdMarkDirty(----J-)
D [21/Jul/2010:16:36:57 -0400] add_job: requesting-user-name="bill"
D [21/Jul/2010:16:36:57 -0400] Adding default job-sheets values "none,none"...
I [21/Jul/2010:16:36:57 -0400] [Job 23] Adding start banner page "none".
D [21/Jul/2010:16:36:57 -0400] cupsdMarkDirty(-----S)
D [21/Jul/2010:16:36:57 -0400] cupsdMarkDirty(----J-)
I [21/Jul/2010:16:36:57 -0400] [Job 23] Adding end banner page "none".
I [21/Jul/2010:16:36:57 -0400] [Job 23] File of type application/vnd.cups-banner queued by "bill".
D [21/Jul/2010:16:36:57 -0400] [Job 23] hold_until=0
I [21/Jul/2010:16:36:57 -0400] [Job 23] Queued on "MFC8860DN" by "bill".
D [21/Jul/2010:16:36:57 -0400] cupsdMarkDirty(----J-)
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdMarkDirty(-----S)
D [21/Jul/2010:16:36:57 -0400] [Job 23] job-sheets=none,none
D [21/Jul/2010:16:36:57 -0400] [Job 23] argv[0]="MFC8860DN"
D [21/Jul/2010:16:36:57 -0400] [Job 23] argv[1]="23"
D [21/Jul/2010:16:36:57 -0400] [Job 23] argv[2]="bill"
D [21/Jul/2010:16:36:57 -0400] [Job 23] argv[3]="Test Page"
D [21/Jul/2010:16:36:57 -0400] [Job 23] argv[4]="1"
D [21/Jul/2010:16:36:57 -0400] [Job 23] argv[5]="job-uuid=urn:uuid:31e99d3b-eb06-3f4d-5007-0413c034658a job-originating-host-name=localhost"
D [21/Jul/2010:16:36:57 -0400] [Job 23] argv[6]="/var/spool/cups/d00023-001"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[8]="HOME=/var/spool/cups/tmp"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[10]="SERVER_ADMIN=root@bill-desktop"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[11]="SOFTWARE=CUPS/1.4.3"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[13]="TZ=America/New_York"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[14]="USER=root"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[17]="IPP_PORT=631"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[18]="CHARSET=utf-8"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[19]="LANG=en_US.UTF-8"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[20]="PPD=/etc/cups/ppd/MFC8860DN.ppd"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[21]="RIP_MAX_CACHE=982326k"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[23]="DEVICE_URI=usb://Brother/MFC-8860DN"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[24]="PRINTER_INFO=MFC8860DN"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[25]="PRINTER_LOCATION="
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[26]="PRINTER=MFC8860DN"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[27]="CUPS_FILETYPE=document"
D [21/Jul/2010:16:36:57 -0400] [Job 23] envp[28]="FINAL_CONTENT_TYPE=printer/MFC8860DN"
I [21/Jul/2010:16:36:57 -0400] [Job 23] Started filter /usr/lib/cups/filter/bannertops (PID 1726)
I [21/Jul/2010:16:36:57 -0400] [Job 23] Started filter /usr/lib/cups/filter/pstopdf (PID 1727)
I [21/Jul/2010:16:36:57 -0400] [Job 23] Started filter /usr/lib/cups/filter/pdftopdf (PID 1728)
I [21/Jul/2010:16:36:57 -0400] [Job 23] Started filter /usr/lib/cups/filter/cpdftocps (PID 1729)
I [21/Jul/2010:16:36:57 -0400] [Job 23] Started filter /usr/lib/cups/filter/brlpdwrapperMFC8860DN (PID 1730)
I [21/Jul/2010:16:36:57 -0400] [Job 23] Started backend /usr/lib/cups/backend/usb (PID 1731)
D [21/Jul/2010:16:36:57 -0400] cupsdMarkDirty(-----S)
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/MFC8860DN) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] [Job 23] STATE: +connecting-to-device
D [21/Jul/2010:16:36:57 -0400] cupsdMarkDirty(-----S)
D [21/Jul/2010:16:36:57 -0400] [Job 23] load_banner(filename="/var/spool/cups/d00023-001")
D [21/Jul/2010:16:36:57 -0400] [Job 23] Printer using device file "/dev/usblp0"...
D [21/Jul/2010:16:36:57 -0400] [Job 23] STATE: -connecting-to-device
D [21/Jul/2010:16:36:57 -0400] [Job 23] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x7fc700e196a0)
D [21/Jul/2010:16:36:57 -0400] cupsdMarkDirty(-----S)
D [21/Jul/2010:16:36:57 -0400] [Job 23] pstopdf 5 args: 23 bill Test Page 1 job-uuid=urn:uuid:31e99d3b-eb06-3f4d-5007-0413c034658a job-originating-host-name=localhost
D [21/Jul/2010:16:36:57 -0400] [Job 23] PPD: /etc/cups/ppd/MFC8860DN.ppd
D [21/Jul/2010:16:36:57 -0400] [Job 23] Page = 595x842; 18,12 to 577,830
D [21/Jul/2010:16:36:57 -0400] [Job 23] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [21/Jul/2010:16:36:57 -0400] [Job 23] PNG image: 192x128x8, color_type=2 (RGB)
D [21/Jul/2010:16:36:57 -0400] PID 1726 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [21/Jul/2010:16:36:57 -0400] [Job 23] pdftops argv[5] = 23 bill Test Page 1 job-uuid=urn:uuid:31e99d3b-eb06-3f4d-5007-0413c034658a job-originating-host-name=localhost
D [21/Jul/2010:16:36:57 -0400] [Job 23] PPD: /etc/cups/ppd/MFC8860DN.ppd
D [21/Jul/2010:16:36:57 -0400] [Job 23] /usr/bin/pdftops supports '-origpagesizes': yes
D [21/Jul/2010:16:36:57 -0400] [Job 23] PostScript Level: 2
D [21/Jul/2010:16:36:57 -0400] [Job 23] Resolution: 600
D [21/Jul/2010:16:36:57 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [21/Jul/2010:16:36:57 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 17 1.1 Get-Notifications 1
D [21/Jul/2010:16:36:57 -0400] Get-Notifications /
D [21/Jul/2010:16:36:57 -0400] cupsdIsAuthorized: requesting-user-name="bill"
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 1.1 Get-Jobs 1
D [21/Jul/2010:16:36:57 -0400] Get-Jobs ipp://localhost/printers/
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [21/Jul/2010:16:36:57 -0400] cupsdCloseClient: 16
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [21/Jul/2010:16:36:57 -0400] cupsdCloseClient: 17
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [21/Jul/2010:16:36:57 -0400] Get-Notifications /
D [21/Jul/2010:16:36:57 -0400] cupsdIsAuthorized: requesting-user-name="bill"
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Printers
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Classes
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Default 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Default
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] [Job 23] Duplex: no
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] [Job 23] Page size: A4
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Printers
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] [Job 23] Resolution: 600
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Classes
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Default 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Default
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] [Job 23] Width: 595, height: 842, absolute margins: 18, 12, 577, 830
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Printers
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Classes
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Default 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Default
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] [Job 23] Page size: A4
D [21/Jul/2010:16:36:57 -0400] [Job 23] Relative margins: 18, 12, 18, 12
D [21/Jul/2010:16:36:57 -0400] [Job 23] PPD options: -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842
D [21/Jul/2010:16:36:57 -0400] [Job 23] PostScript to be injected:
D [21/Jul/2010:16:36:57 -0400] [Job 23] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -sOutputFile=-  -c .setpdfwrite -f -
D [21/Jul/2010:16:36:57 -0400] [Job 23] Width: 595, height: 842, absolute margins: 18, 12, 577, 830
D [21/Jul/2010:16:36:57 -0400] [Job 23] Relative margins: 18, 12, 18, 12
D [21/Jul/2010:16:36:57 -0400] [Job 23] PPD options: -level2 -origpagesizes
D [21/Jul/2010:16:36:57 -0400] [Job 23] PostScript to be injected:
D [21/Jul/2010:16:36:57 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 1.1 Create-Printer-Subscription 1
D [21/Jul/2010:16:36:57 -0400] Create-Printer-Subscription /
D [21/Jul/2010:16:36:57 -0400] cupsdCreateSubscription(con=0x7fa19e185f20(16), uri="/")
D [21/Jul/2010:16:36:57 -0400] pullmethod="ippget"
D [21/Jul/2010:16:36:57 -0400] notify-lease-duration=86400
D [21/Jul/2010:16:36:57 -0400] notify-time-interval=0
D [21/Jul/2010:16:36:57 -0400] cupsdAddSubscription(mask=1798f, dest=(nil)(), job=(nil)(0), uri="(null)")
D [21/Jul/2010:16:36:57 -0400] Added subscription 42 for server
D [21/Jul/2010:16:36:57 -0400] cupsdMarkDirty(-----S)
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Printers
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [21/Jul/2010:16:36:57 -0400] CUPS-Get-Printers
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [21/Jul/2010:16:36:57 -0400] Get-Printer-Attributes ipp://localhost/printers/MFC8860DN
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/MFC8860DN) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [21/Jul/2010:16:36:57 -0400] cupsdCloseClient: 17
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [21/Jul/2010:16:36:57 -0400] cupsdCloseClient: 16
D [21/Jul/2010:16:36:57 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 1.1 Get-Jobs 1
D [21/Jul/2010:16:36:57 -0400] Get-Jobs ipp://localhost/printers/
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [21/Jul/2010:16:36:57 -0400] Get-Printer-Attributes
D [21/Jul/2010:16:36:57 -0400] Get-Printer-Attributes client-error-not-found: The printer or class was not found.
D [21/Jul/2010:16:36:57 -0400] Returning IPP client-error-not-found for Get-Printer-Attributes () from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 19 1.1 Get-Job-Attributes 1
D [21/Jul/2010:16:36:57 -0400] Get-Job-Attributes ipp://localhost/jobs/23
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/23) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [21/Jul/2010:16:36:57 -0400] cupsdCloseClient: 19
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [21/Jul/2010:16:36:57 -0400] cupsdCloseClient: 16
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [21/Jul/2010:16:36:57 -0400] cupsdCloseClient: 17
D [21/Jul/2010:16:36:57 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 1.1 Get-Jobs 1
D [21/Jul/2010:16:36:57 -0400] Get-Jobs ipp://localhost/printers/
D [21/Jul/2010:16:36:57 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [21/Jul/2010:16:36:57 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [21/Jul/2010:16:36:57 -0400] cupsdCloseClient: 16
D [21/Jul/2010:16:36:58 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [21/Jul/2010:16:36:58 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [21/Jul/2010:16:36:58 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [21/Jul/2010:16:36:58 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:58 -0400] cupsdReadClient: 16 1.1 Get-Notifications 1
D [21/Jul/2010:16:36:58 -0400] Get-Notifications /
D [21/Jul/2010:16:36:58 -0400] cupsdIsAuthorized: requesting-user-name="bill"
D [21/Jul/2010:16:36:58 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [21/Jul/2010:16:36:58 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [21/Jul/2010:16:36:58 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [21/Jul/2010:16:36:58 -0400] cupsdCloseClient: 16
D [21/Jul/2010:16:36:58 -0400] PID 1727 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [21/Jul/2010:16:36:58 -0400] PID 1728 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [21/Jul/2010:16:36:58 -0400] [Job 23] Device copies: 1; device collate:
D [21/Jul/2010:16:36:58 -0400] [Job 23] Running /usr/bin/pdftops  -level2 -origpagesizes /tmp/pdftops.tfJPCs -
D [21/Jul/2010:16:36:58 -0400] [Job 23] Running pstops '23' 'bill' 'Test Page' '1' ' job-uuid=urn:uuid:31e99d3b-eb06-3f4d-5007-0413c034658a job-originating-host-name=localhost'
D [21/Jul/2010:16:36:58 -0400] [Job 23] Page = 595x842; 18,12 to 577,830
D [21/Jul/2010:16:36:58 -0400] [Job 23] slow_collate=0, slow_duplex=0, slow_order=0
D [21/Jul/2010:16:36:58 -0400] [Job 23] Before copy_comments - %!PS-Adobe-3.0
D [21/Jul/2010:16:36:58 -0400] [Job 23] %!PS-Adobe-3.0
D [21/Jul/2010:16:36:58 -0400] [Job 23] %%LanguageLevel: 2
D [21/Jul/2010:16:36:58 -0400] [Job 23] %%DocumentSuppliedResources: (atend)
D [21/Jul/2010:16:36:58 -0400] [Job 23] %%DocumentMedia: plain 595 842 0 () ()
D [21/Jul/2010:16:36:58 -0400] [Job 23] %%BoundingBox: 0 0 595 842
D [21/Jul/2010:16:36:58 -0400] [Job 23] %%Pages: 1
D [21/Jul/2010:16:36:58 -0400] [Job 23] %%EndComments
D [21/Jul/2010:16:36:58 -0400] [Job 23] Before copy_prolog - %%BeginDefaults
D [21/Jul/2010:16:36:58 -0400] [Job 23] Before copy_setup - %%BeginSetup
D [21/Jul/2010:16:36:58 -0400] [Job 23] Before page loop - %%Page: 1 1
D [21/Jul/2010:16:36:58 -0400] [Job 23] Copying page 1...
D [21/Jul/2010:16:36:58 -0400] [Job 23] pagew = 559.0, pagel = 818.0
D [21/Jul/2010:16:36:58 -0400] [Job 23] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [21/Jul/2010:16:36:58 -0400] [Job 23] PageLeft = 18.0, PageRight = 577.0
D [21/Jul/2010:16:36:58 -0400] [Job 23] PageTop = 830.0, PageBottom = 12.0
D [21/Jul/2010:16:36:58 -0400] [Job 23] PageWidth = 595.0, PageLength = 842.0
D [21/Jul/2010:16:36:58 -0400] [Job 23] Wrote 1 pages...
D [21/Jul/2010:16:36:58 -0400] PID 1729 (/usr/lib/cups/filter/cpdftocps) exited with no errors.
D [21/Jul/2010:16:36:59 -0400] [Job 23] /usr/local/Brother/lpd/rawtobr2: error while loading shared libraries: libbrcomplpr2.so: cannot open shared object file: No such file or directory
D [21/Jul/2010:16:36:59 -0400] PID 1730 (/usr/lib/cups/filter/brlpdwrapperMFC8860DN) exited with no errors.
D [21/Jul/2010:16:36:59 -0400] PID 1731 (/usr/lib/cups/backend/usb) exited with no errors.
D [21/Jul/2010:16:36:59 -0400] cupsdMarkDirty(-----S)
I [21/Jul/2010:16:36:59 -0400] [Job 23] Job completed.
D [21/Jul/2010:16:36:59 -0400] cupsdMarkDirty(----J-)
D [21/Jul/2010:16:36:59 -0400] cupsdMarkDirty(-----S)
D [21/Jul/2010:16:36:59 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [21/Jul/2010:16:36:59 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:36:59 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:59 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [21/Jul/2010:16:36:59 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 15 1.1 Get-Jobs 1
D [21/Jul/2010:16:36:59 -0400] Get-Jobs ipp://localhost/printers/
D [21/Jul/2010:16:36:59 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 16 1.1 Get-Notifications 1
D [21/Jul/2010:16:36:59 -0400] Get-Notifications /
D [21/Jul/2010:16:36:59 -0400] cupsdIsAuthorized: requesting-user-name="bill"
D [21/Jul/2010:16:36:59 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [21/Jul/2010:16:36:59 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:36:59 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 15 WAITING Closing on EOF
D [21/Jul/2010:16:36:59 -0400] cupsdCloseClient: 15
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [21/Jul/2010:16:36:59 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:36:59 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 17 1.1 Get-Notifications 1
D [21/Jul/2010:16:36:59 -0400] Get-Notifications /
D [21/Jul/2010:16:36:59 -0400] cupsdIsAuthorized: requesting-user-name="bill"
D [21/Jul/2010:16:36:59 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [21/Jul/2010:16:36:59 -0400] cupsdCloseClient: 16
D [21/Jul/2010:16:36:59 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [21/Jul/2010:16:36:59 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:36:59 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:59 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:59 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 11 1.1 Get-Notifications 1
D [21/Jul/2010:16:36:59 -0400] Get-Notifications /
D [21/Jul/2010:16:36:59 -0400] cupsdIsAuthorized: requesting-user-name="bill"
D [21/Jul/2010:16:36:59 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [21/Jul/2010:16:36:59 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1
D [21/Jul/2010:16:36:59 -0400] CUPS-Get-Printers
D [21/Jul/2010:16:36:59 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 15 1.1 Get-Printer-Attributes 1
D [21/Jul/2010:16:36:59 -0400] Get-Printer-Attributes ipp://bill-desktop:631/printers/MFC8860DN
D [21/Jul/2010:16:36:59 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://bill-desktop:631/printers/MFC8860DN) from localhost
D [21/Jul/2010:16:36:59 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:59 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:36:59 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1
D [21/Jul/2010:16:36:59 -0400] CUPS-Get-Classes
D [21/Jul/2010:16:36:59 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [21/Jul/2010:16:36:59 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [21/Jul/2010:16:36:59 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:36:59 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 18 1.1 CUPS-Get-Default 1
D [21/Jul/2010:16:36:59 -0400] CUPS-Get-Default
D [21/Jul/2010:16:36:59 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [21/Jul/2010:16:36:59 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:36:59 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [21/Jul/2010:16:36:59 -0400] cupsdCloseClient: 17
D [21/Jul/2010:16:37:00 -0400] [Job 23] Unloading...
D [21/Jul/2010:16:37:17 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [21/Jul/2010:16:37:17 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:37:17 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:37:17 -0400] cupsdReadClient: 11 1.1 Get-Job-Attributes 1
D [21/Jul/2010:16:37:17 -0400] Get-Job-Attributes ipp://localhost/jobs/23
D [21/Jul/2010:16:37:17 -0400] [Job 23] Loading attributes...
D [21/Jul/2010:16:37:17 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/23) from localhost
D [21/Jul/2010:16:37:17 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:37:17 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [21/Jul/2010:16:37:17 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:37:17 -0400] cupsdAuthorize: No authentication data provided.
D [21/Jul/2010:16:37:17 -0400] cupsdReadClient: 11 1.1 Cancel-Subscription 1
D [21/Jul/2010:16:37:17 -0400] Cancel-Subscription /
D [21/Jul/2010:16:37:17 -0400] cupsdIsAuthorized: requesting-user-name="bill"
D [21/Jul/2010:16:37:17 -0400] cupsdMarkDirty(-----S)
D [21/Jul/2010:16:37:17 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [21/Jul/2010:16:37:17 -0400] cupsdSetBusyState: Dirty files
D [21/Jul/2010:16:37:17 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [21/Jul/2010:16:37:17 -0400] cupsdReadClient: 16 GET /admin/log/error_log HTTP/1.1
D [21/Jul/2010:16:37:17 -0400] cupsdSetBusyState: Active clients and dirty files
D [21/Jul/2010:16:37:17 -0400] cupsdAuthorize: No authentication data provided.

---

### Post by quixote on 2010-07-23
Have you gotten into the cups admin pages?  Sometimes for some reason cups can think the printer is "not accepting jobs" for no reason.  You access it by opening a browser and in the url address bar typing: [http://localhost:631/](http://localhost:631/)

If it asks for an admin login, type "root" and your primary user password in ubuntu.  (At least that works for me.)

The printer should then be under the "printers" tab, and if it's red, there's your problem.  "Enable" and it'll work.

---

### Post by tkoco on 2010-07-24
> I have installed the lpr and cupswrapper drivers using the command line terminal for a Brother MFC8860DN printer in Ubuntu 10.04. The drivers are recognized and the printer is recognized, but the printer does not print. I ran a troubleshooting process and got the error log below.  I am a newbie that loves working with Ubuntu. The printer intallation is driving me crazy though. Please help. I hope the error log below can be understood by someone that can give me a solution.

Bill

D [21/Jul/2010:16:36:50 -0400] cupsdReadClient: 11 1.1 Get-Jobs 1
D [21/Jul/2010:16:36:50 -0400] Get-Jobs ipp://localhost/printers/
D [21/Jul/2010:16:36:50 -0400] [Job 1] Loading attributes...
E [21/Jul/2010:16:36:50 -0400] [Job 1] Unable to queue job for destination "Brother-MFC-8860DN"!

Note the destination shown above!


> D [21/Jul/2010:16:36:57 -0400] cupsdReadClient: 13 1.1 Print-Job 1
D [21/Jul/2010:16:36:57 -0400] Print-Job ipp://localhost/printers/MFC8860DN

Now look at the actual name of the print queue shown above!

In a nut shell, the print job has nowhere to go. The configuration is attempting to save the job to an non-existant location. Please check the printer configurations.;)

---

### Post by bill56 on 2010-07-28
I checked the localhost:631 web page and everything is fine there. Regarding the printer configuration file this is what I found:

The Brother solutions page states that a user should check the printer configuration in the /etc/printcap file for the following entry: :lp=/dev/usb/lp0:\. The printcap file, however, is not at the /etc/printcap location. My printcap file is to be found at the /etc/profile.d path on my Ubuntu 10.04 64 bit system and it does not contain the information as shown on the Brother printer solutions page. My printcap file contains the following information:

# This file was automatically generated by cupsd( from the
# /etc/cups/printers.conf file. All changes to this file
# will be lost.
MFC8860DN|MFC8860DN:rm=bill-desktop:rp=MFC8860DN:

The /etc/cups/printers.conf file mentioned above contains the following:

# Printer configuration file for CUPS v1.4.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<Printer MFC8860DN>
Info MFC8860DN
MakeModel Brother MFC8860DN for CUPS
DeviceURI usb:/dev/usb/lp0
State Idle
StateTime 1280260821
Type 8392724
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 0 brlpdwrapperMFC8860DN
Accepting Yes
Shared Yes
JobSheets classified classified
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option fitplot false
</Printer>

The Brother solutions page shows the following for a printcap configuration file in the /etc/printcap file for a printer USB connection:

printcap or printcap.local file (for USB connection)
$ cat /etc/printcap
DCP540CN:\
:mx=0:\
:sd=/var/spool/lpd/dcp540cn:\
:sh:\
:lp=/dev/usb/lp0:\
:if=/usr/local/Brother/Printer/dcp540cn/lpd/filterdcp540cn:

Is the problem that the configuration files are not where they are supposed to be as per the Brother solutions page? Or is it that the config files just have errors? Can anyone give me a step by step method to correct whatever the problem might be?

Bill

---

### Post by quixote on 2010-07-29
tkoco I think has the answer.  Your printer isn't being referred to correctly.  Somewhere, probably in System > Administration > Printing ?, the system has been told that the printer's name is "Brother-MFC-8860DN".  Somewhere else, the hardware is expecting the name "MFC8860DN".

If you go to System > Administration > Printing, right-click on the Brother printer and select "Properties" and then "Settings", what does it say under "device URI" exactly?

---

### Post by bill56 on 2010-07-31
Hi guys. I followed quixote's instructions and went from System > Administration > Printing, and checked on the printer properties of the printer. The "settings" list under "device URI" says: usb:/dev/usb/lp0.

The other "settings" for the printer are as follows: 

Under Description it says: MFC8860DN

Under Location it says absolutely nothing. It is blank.

Under make and model it says: Brother MFC8860DN for CUPS.

Let me know what you think.

---

### Post by quixote on 2010-08-01
It looks like the problem may be incorrect DEVICE_URI.  In that long list in your first post, it says: ```
DEVICE_URI=**usb://Brother/MFC-8860DN**"
```but the URI you have is usb:/dev/usb/lp0. Try changing it to the bolded bit exactly (it's case sensitive), and see whether that makes a difference. I don't think it matters that there's nothing under Location.  That. if I remember right, is just supposed to be a reminder as to where the printer is physically located.  Let's say you were in an office for instance, and it said "3rd floor Flintstones Building."

---

