---
title: "HP-PSC 2500 stopped working"
date: 2011-04-13
forum: Desktop Environments
---

### Post by bgvianyc on 2011-04-13
Hello,

I'm running Ubuntu 10.10, and my HP-PSC 2500 and have recently not been able to print over my wireless network to my HP-PSC 2500, I can't understand what the problem is since it used to work in the past. Below is the error log:

D [13/Apr/2011:06:25:20 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:20 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Apr/2011:06:25:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:20 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:20 -0400] cupsdReadClient: 13 1.1 Get-Jobs 1
D [13/Apr/2011:06:25:20 -0400] Get-Jobs ipp://localhost/printers/
D [13/Apr/2011:06:25:20 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Apr/2011:06:25:20 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:20 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Apr/2011:06:25:20 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:20 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:20 -0400] cupsdReadClient: 13 1.1 Get-Jobs 1
D [13/Apr/2011:06:25:20 -0400] Get-Jobs ipp://localhost/printers/
D [13/Apr/2011:06:25:20 -0400] [Job 1] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 2] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 3] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 4] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 5] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 6] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 7] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 8] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 9] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 10] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 11] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 12] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 13] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 14] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 15] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 16] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 17] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 18] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 19] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 20] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 21] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 22] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 23] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 24] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 25] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 26] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 27] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 28] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 29] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 30] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 31] Loading attributes...
D [13/Apr/2011:06:25:20 -0400] [Job 32] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 33] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 34] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 35] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 36] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 37] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 38] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 39] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 40] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 41] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 42] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 43] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 44] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 45] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 46] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 47] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 48] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 49] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 50] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 51] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 52] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 53] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 54] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 55] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 56] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 57] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 58] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] [Job 59] Loading attributes...
D [13/Apr/2011:06:25:21 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Apr/2011:06:25:21 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:21 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Apr/2011:06:25:21 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:21 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:21 -0400] cupsdReadClient: 13 1.1 Create-Printer-Subscription 1
D [13/Apr/2011:06:25:21 -0400] Create-Printer-Subscription /
D [13/Apr/2011:06:25:21 -0400] cupsdCreateSubscription(con=0x221d92f8(13), uri="/")
D [13/Apr/2011:06:25:21 -0400] pullmethod="ippget"
D [13/Apr/2011:06:25:21 -0400] notify-lease-duration=86400
D [13/Apr/2011:06:25:21 -0400] notify-time-interval=0
D [13/Apr/2011:06:25:21 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [13/Apr/2011:06:25:21 -0400] Added subscription 58 for server
D [13/Apr/2011:06:25:21 -0400] cupsdMarkDirty(-----S)
D [13/Apr/2011:06:25:21 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [13/Apr/2011:06:25:21 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:22 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Apr/2011:06:25:22 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:22 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:22 -0400] cupsdReadClient: 13 1.1 Get-Notifications 1
D [13/Apr/2011:06:25:22 -0400] Get-Notifications /
D [13/Apr/2011:06:25:22 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:22 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Apr/2011:06:25:22 -0400] cupsdSetBusyState: Dirty files
I [13/Apr/2011:06:25:25 -0400] Generating printcap /var/run/cups/printcap...
I [13/Apr/2011:06:25:25 -0400] Saving subscriptions.conf...
D [13/Apr/2011:06:25:25 -0400] cupsdSetBusyState: Not busy
D [13/Apr/2011:06:25:27 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 14 POST /printers/HP-PSC-2500 HTTP/1.1
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Active clients
D [13/Apr/2011:06:25:27 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 14 1.1 Print-Job 1
D [13/Apr/2011:06:25:27 -0400] Print-Job ipp://localhost/printers/HP-PSC-2500
D [13/Apr/2011:06:25:27 -0400] [Job ???] Auto-typing file...
I [13/Apr/2011:06:25:27 -0400] [Job ???] Request file type is application/vnd.cups-banner.
D [13/Apr/2011:06:25:27 -0400] cupsdMarkDirty(----J-)
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:27 -0400] add_job: requesting-user-name="barry"
D [13/Apr/2011:06:25:27 -0400] Adding default job-sheets values "none,none"...
I [13/Apr/2011:06:25:27 -0400] [Job 61] Adding start banner page "none".
D [13/Apr/2011:06:25:27 -0400] cupsdMarkDirty(-----S)
D [13/Apr/2011:06:25:27 -0400] cupsdMarkDirty(----J-)
I [13/Apr/2011:06:25:27 -0400] [Job 61] Adding end banner page "none".
I [13/Apr/2011:06:25:27 -0400] [Job 61] File of type application/vnd.cups-banner queued by "barry".
D [13/Apr/2011:06:25:27 -0400] [Job 61] hold_until=0
I [13/Apr/2011:06:25:27 -0400] [Job 61] Queued on "HP-PSC-2500" by "barry".
D [13/Apr/2011:06:25:27 -0400] cupsdMarkDirty(----J-)
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:27 -0400] cupsdMarkDirty(-----S)
D [13/Apr/2011:06:25:27 -0400] [Job 61] job-sheets=none,none
D [13/Apr/2011:06:25:27 -0400] [Job 61] argv[0]="HP-PSC-2500"
D [13/Apr/2011:06:25:27 -0400] [Job 61] argv[1]="61"
D [13/Apr/2011:06:25:27 -0400] [Job 61] argv[2]="barry"
D [13/Apr/2011:06:25:27 -0400] [Job 61] argv[3]="Test Page"
D [13/Apr/2011:06:25:27 -0400] [Job 61] argv[4]="1"
D [13/Apr/2011:06:25:27 -0400] [Job 61] argv[5]="job-uuid=urn:uuid:4c3f148d-7ae6-39bd-54e1-d8344266b08d job-originating-host-name=localhost"
D [13/Apr/2011:06:25:27 -0400] [Job 61] argv[6]="/var/spool/cups/d00061-001"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[8]="HOME=/var/spool/cups/tmp"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[10]="SERVER_ADMIN=root@barry-laptop"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[11]="SOFTWARE=CUPS/1.4.4"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[13]="USER=root"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[16]="IPP_PORT=631"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[17]="CHARSET=utf-8"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[18]="LANG=en_US.UTF-8"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[19]="PPD=/etc/cups/ppd/HP-PSC-2500.ppd"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[20]="RIP_MAX_CACHE=auto"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[22]="DEVICE_URI=hp:/net/psc_2500_series?ip=192.168.1.101"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[23]="PRINTER_INFO=HP PSC 2500"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[24]="PRINTER_LOCATION=Network"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[25]="PRINTER=HP-PSC-2500"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[26]="CUPS_FILETYPE=document"
D [13/Apr/2011:06:25:27 -0400] [Job 61] envp[27]="FINAL_CONTENT_TYPE=printer/HP-PSC-2500"
I [13/Apr/2011:06:25:27 -0400] [Job 61] Started filter /usr/lib/cups/filter/bannertops (PID 31803)
I [13/Apr/2011:06:25:27 -0400] [Job 61] Started filter /usr/lib/cups/filter/pstopdf (PID 31804)
I [13/Apr/2011:06:25:27 -0400] [Job 61] Started filter /usr/lib/cups/filter/pdftopdf (PID 31805)
I [13/Apr/2011:06:25:27 -0400] [Job 61] Started filter /usr/lib/cups/filter/foomatic-rip (PID 31806)
I [13/Apr/2011:06:25:27 -0400] [Job 61] Started backend /usr/lib/cups/backend/hp (PID 31807)
D [13/Apr/2011:06:25:27 -0400] cupsdMarkDirty(-----S)
D [13/Apr/2011:06:25:27 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-PSC-2500) from localhost
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:27 -0400] [Job 61] pstopdf 5 args: 61 barry Test Page 1 job-uuid=urn:uuid:4c3f148d-7ae6-39bd-54e1-d8344266b08d job-originating-host-name=localhost
D [13/Apr/2011:06:25:27 -0400] [Job 61] PPD: /etc/cups/ppd/HP-PSC-2500.ppd
D [13/Apr/2011:06:25:27 -0400] [Job 61] Getting input from file
D [13/Apr/2011:06:25:27 -0400] [Job 61] foomatic-rip version 4.0.5.223 running...
D [13/Apr/2011:06:25:27 -0400] [Job 61] Parsing PPD file ...
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option Resolution
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option PageSize
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option Model
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option PrintoutMode
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option InputSlot
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option Duplex
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option DryTime
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option Quality
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option ImageableArea
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option PaperDimension
D [13/Apr/2011:06:25:27 -0400] [Job 61] Added option Font
D [13/Apr/2011:06:25:27 -0400] [Job 61]
D [13/Apr/2011:06:25:27 -0400] [Job 61] Parameter Summary
D [13/Apr/2011:06:25:27 -0400] [Job 61] -----------------
D [13/Apr/2011:06:25:27 -0400] [Job 61]
D [13/Apr/2011:06:25:27 -0400] [Job 61] Spooler: cups
D [13/Apr/2011:06:25:27 -0400] [Job 61] Printer: HP-PSC-2500
D [13/Apr/2011:06:25:27 -0400] [Job 61] Shell: /bin/bash
D [13/Apr/2011:06:25:27 -0400] [Job 61] PPD file: /etc/cups/ppd/HP-PSC-2500.ppd
D [13/Apr/2011:06:25:27 -0400] [Job 61] ATTR file:
D [13/Apr/2011:06:25:27 -0400] [Job 61] Printer model: HP PSC 2500 Series hpijs, 3.10.6
D [13/Apr/2011:06:25:27 -0400] [Job 61] Job title: Test Page
D [13/Apr/2011:06:25:27 -0400] [Job 61] File(s) to be printed:
D [13/Apr/2011:06:25:27 -0400] [Job 61] <STDIN>
D [13/Apr/2011:06:25:27 -0400] [Job 61]
D [13/Apr/2011:06:25:27 -0400] [Job 61] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [13/Apr/2011:06:25:27 -0400] [Job 61] Printing system options:
D [13/Apr/2011:06:25:27 -0400] [Job 61] Pondering option 'job-uuid=urn:uuid:4c3f148d-7ae6-39bd-54e1-d8344266b08d'
D [13/Apr/2011:06:25:27 -0400] [Job 61] Unknown option job-uuid=urn:uuid:4c3f148d-7ae6-39bd-54e1-d8344266b08d.
D [13/Apr/2011:06:25:27 -0400] [Job 61] Pondering option 'job-originating-host-name=localhost'
D [13/Apr/2011:06:25:27 -0400] [Job 61] Unknown option job-originating-host-name=localhost.
D [13/Apr/2011:06:25:27 -0400] [Job 61] Options from the PPD file:
D [13/Apr/2011:06:25:27 -0400] [Job 61]
D [13/Apr/2011:06:25:27 -0400] [Job 61] ================================================
D [13/Apr/2011:06:25:27 -0400] [Job 61]
D [13/Apr/2011:06:25:27 -0400] [Job 61] File: <STDIN>
D [13/Apr/2011:06:25:27 -0400] [Job 61]
D [13/Apr/2011:06:25:27 -0400] [Job 61] ================================================
D [13/Apr/2011:06:25:27 -0400] [Job 61]
D [13/Apr/2011:06:25:27 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:27 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:27 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [13/Apr/2011:06:25:27 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 17 1.1 Get-Notifications 1
D [13/Apr/2011:06:25:27 -0400] Get-Notifications /
D [13/Apr/2011:06:25:27 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:27 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 18 1.1 Get-Jobs 1
D [13/Apr/2011:06:25:27 -0400] Get-Jobs ipp://localhost/printers/
D [13/Apr/2011:06:25:27 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 17 WAITING Closing on EOF
D [13/Apr/2011:06:25:27 -0400] cupsdCloseClient: 17
D [13/Apr/2011:06:25:27 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [13/Apr/2011:06:25:27 -0400] cupsdCloseClient: 18
D [13/Apr/2011:06:25:27 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:27 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [13/Apr/2011:06:25:27 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 18 1.1 Get-Notifications 1
D [13/Apr/2011:06:25:27 -0400] Get-Notifications /
D [13/Apr/2011:06:25:27 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:27 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [13/Apr/2011:06:25:27 -0400] CUPS-Get-Printers
D [13/Apr/2011:06:25:27 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:27 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:27 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [13/Apr/2011:06:25:27 -0400] Get-Job-Attributes ipp://localhost/jobs/61
D [13/Apr/2011:06:25:27 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/61) from localhost
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [13/Apr/2011:06:25:27 -0400] CUPS-Get-Classes
D [13/Apr/2011:06:25:27 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:27 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:27 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [13/Apr/2011:06:25:27 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [13/Apr/2011:06:25:27 -0400] CUPS-Get-Default
D [13/Apr/2011:06:25:27 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1
D [13/Apr/2011:06:25:27 -0400] Get-Printer-Attributes ipp://barry-laptop:631/printers/HP-PSC-2500
D [13/Apr/2011:06:25:27 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://barry-laptop:631/printers/HP-PSC-2500) from localhost
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [13/Apr/2011:06:25:27 -0400] cupsdCloseClient: 19
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:27 -0400] [Job 61] load_banner(filename="/var/spool/cups/d00061-001")
D [13/Apr/2011:06:25:27 -0400] [Job 61] Page = 612x792; 18,36 to 594,783
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:27 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 13 1.1 Get-Notifications 1
D [13/Apr/2011:06:25:27 -0400] Get-Notifications /
D [13/Apr/2011:06:25:27 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:27 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Apr/2011:06:25:27 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:27 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [13/Apr/2011:06:25:27 -0400] cupsdCloseClient: 18
D [13/Apr/2011:06:25:27 -0400] [Job 61] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [13/Apr/2011:06:25:27 -0400] [Job 61] PNG image: 192x128x8, color_type=2 (RGB)
D [13/Apr/2011:06:25:27 -0400] PID 31803 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [13/Apr/2011:06:25:27 -0400] [Job 61] Resolution: 600
D [13/Apr/2011:06:25:27 -0400] [Job 61] Page size: Letter
D [13/Apr/2011:06:25:27 -0400] [Job 61] Width: 612, height: 792, absolute margins: 18, 36, 594, 783
D [13/Apr/2011:06:25:27 -0400] [Job 61] Relative margins: 18, 36, 18, 9
D [13/Apr/2011:06:25:27 -0400] [Job 61] PPD options: -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [13/Apr/2011:06:25:27 -0400] [Job 61] PostScript to be injected:
D [13/Apr/2011:06:25:27 -0400] [Job 61] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [13/Apr/2011:06:25:29 -0400] PID 31804 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [13/Apr/2011:06:25:29 -0400] [Job 61] Filetype: PDF
D [13/Apr/2011:06:25:29 -0400] [Job 61] Storing temporary files in /var/spool/cups/tmp
D [13/Apr/2011:06:25:29 -0400] PID 31805 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [13/Apr/2011:06:25:29 -0400] [Job 61] File contains 1 pages
D [13/Apr/2011:06:25:29 -0400] [Job 61] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-rRntwq
D [13/Apr/2011:06:25:29 -0400] [Job 61] Starting process "kid3" (generation 1)
D [13/Apr/2011:06:25:29 -0400] [Job 61] Starting process "kid4" (generation 2)
D [13/Apr/2011:06:25:29 -0400] [Job 61] Starting process "renderer" (generation 2)
D [13/Apr/2011:06:25:29 -0400] [Job 61] JCL: %-12345X@PJL
D [13/Apr/2011:06:25:29 -0400] [Job 61] <job data>
D [13/Apr/2011:06:25:29 -0400] [Job 61]
D [13/Apr/2011:06:25:30 -0400] [Job 61] Segmentation fault
D [13/Apr/2011:06:25:30 -0400] [Job 61] GPL Ghostscript 8.71: Can't start ijs server "hpijs"
D [13/Apr/2011:06:25:30 -0400] [Job 61] renderer exited with status 1
D [13/Apr/2011:06:25:30 -0400] [Job 61] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
D [13/Apr/2011:06:25:30 -0400] PID 31806 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [13/Apr/2011:06:25:30 -0400] [Job 61] STATE: +connecting-to-device
D [13/Apr/2011:06:25:30 -0400] cupsdMarkDirty(-----S)
D [13/Apr/2011:06:25:30 -0400] [Job 61] STATE: -connecting-to-device
D [13/Apr/2011:06:25:30 -0400] [Job 61] STATE: -media-empty-error,media-jam-error,hplip.plugin-error,cover-open-error,toner-empty-error,other
D [13/Apr/2011:06:25:30 -0400] cupsdMarkDirty(-----S)
D [13/Apr/2011:06:25:30 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [13/Apr/2011:06:25:30 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [13/Apr/2011:06:25:30 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 18 1.1 Get-Notifications 1
D [13/Apr/2011:06:25:30 -0400] Get-Notifications /
D [13/Apr/2011:06:25:30 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:30 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 19 1.1 Get-Jobs 1
D [13/Apr/2011:06:25:30 -0400] Get-Jobs ipp://localhost/printers/
D [13/Apr/2011:06:25:30 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [13/Apr/2011:06:25:30 -0400] cupsdCloseClient: 19
D [13/Apr/2011:06:25:30 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [13/Apr/2011:06:25:30 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1
D [13/Apr/2011:06:25:30 -0400] Get-Notifications /
D [13/Apr/2011:06:25:30 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:30 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [13/Apr/2011:06:25:30 -0400] cupsdCloseClient: 19
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [13/Apr/2011:06:25:30 -0400] cupsdCloseClient: 18
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 13 1.1 Get-Notifications 1
D [13/Apr/2011:06:25:30 -0400] Get-Notifications /
D [13/Apr/2011:06:25:30 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:30 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [13/Apr/2011:06:25:30 -0400] CUPS-Get-Printers
D [13/Apr/2011:06:25:30 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [13/Apr/2011:06:25:30 -0400] CUPS-Get-Classes
D [13/Apr/2011:06:25:30 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [13/Apr/2011:06:25:30 -0400] CUPS-Get-Default
D [13/Apr/2011:06:25:30 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [13/Apr/2011:06:25:30 -0400] CUPS-Get-Printers
D [13/Apr/2011:06:25:30 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [13/Apr/2011:06:25:30 -0400] CUPS-Get-Classes
D [13/Apr/2011:06:25:30 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [13/Apr/2011:06:25:30 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:30 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [13/Apr/2011:06:25:30 -0400] CUPS-Get-Default
D [13/Apr/2011:06:25:30 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [13/Apr/2011:06:25:30 -0400] cupsdSetBusyState: Printing jobs and dirty files
I [13/Apr/2011:06:25:40 -0400] [Job 61] ready to print
D [13/Apr/2011:06:25:40 -0400] cupsdMarkDirty(-----S)
D [13/Apr/2011:06:25:41 -0400] PID 31807 (/usr/lib/cups/backend/hp) exited with no errors.
D [13/Apr/2011:06:25:41 -0400] cupsdMarkDirty(-----S)
E [13/Apr/2011:06:25:41 -0400] [Job 61] Job stopped due to filter errors; please consult the error_log file for details.
D [13/Apr/2011:06:25:41 -0400] cupsdMarkDirty(----J-)
D [13/Apr/2011:06:25:41 -0400] cupsdMarkDirty(-----S)
D [13/Apr/2011:06:25:41 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:41 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [13/Apr/2011:06:25:41 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 16 1.1 Get-Notifications 1
D [13/Apr/2011:06:25:41 -0400] Get-Notifications /
D [13/Apr/2011:06:25:41 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:41 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 18 1.1 Get-Jobs 1
D [13/Apr/2011:06:25:41 -0400] Get-Jobs ipp://localhost/printers/
D [13/Apr/2011:06:25:41 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [13/Apr/2011:06:25:41 -0400] cupsdCloseClient: 18
D [13/Apr/2011:06:25:41 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 18 1.1 Get-Notifications 1
D [13/Apr/2011:06:25:41 -0400] Get-Notifications /
D [13/Apr/2011:06:25:41 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:41 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [13/Apr/2011:06:25:41 -0400] cupsdCloseClient: 16
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1
D [13/Apr/2011:06:25:41 -0400] CUPS-Get-Printers
D [13/Apr/2011:06:25:41 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1
D [13/Apr/2011:06:25:41 -0400] CUPS-Get-Classes
D [13/Apr/2011:06:25:41 -0400] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 17 1.1 CUPS-Get-Default 1
D [13/Apr/2011:06:25:41 -0400] CUPS-Get-Default
D [13/Apr/2011:06:25:41 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Apr/2011:06:25:41 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 13 1.1 Get-Notifications 1
D [13/Apr/2011:06:25:41 -0400] Get-Notifications /
D [13/Apr/2011:06:25:41 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:41 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [13/Apr/2011:06:25:41 -0400] Get-Printer-Attributes ipp://barry-laptop:631/printers/HP-PSC-2500
D [13/Apr/2011:06:25:41 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://barry-laptop:631/printers/HP-PSC-2500) from localhost
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [13/Apr/2011:06:25:41 -0400] Get-Job-Attributes ipp://localhost/jobs/61
D [13/Apr/2011:06:25:41 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/61) from localhost
D [13/Apr/2011:06:25:41 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:41 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [13/Apr/2011:06:25:41 -0400] cupsdCloseClient: 18
D [13/Apr/2011:06:25:42 -0400] [Job 61] Unloading...
D [13/Apr/2011:06:25:48 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Apr/2011:06:25:48 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:48 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:48 -0400] cupsdReadClient: 13 1.1 Get-Job-Attributes 1
D [13/Apr/2011:06:25:48 -0400] Get-Job-Attributes ipp://localhost/jobs/61
D [13/Apr/2011:06:25:48 -0400] [Job 61] Loading attributes...
D [13/Apr/2011:06:25:48 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/61) from localhost
D [13/Apr/2011:06:25:48 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:48 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Apr/2011:06:25:48 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:48 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:48 -0400] cupsdReadClient: 13 1.1 Cancel-Subscription 1
D [13/Apr/2011:06:25:48 -0400] Cancel-Subscription /
D [13/Apr/2011:06:25:48 -0400] cupsdIsAuthorized: requesting-user-name="barry"
D [13/Apr/2011:06:25:48 -0400] cupsdMarkDirty(-----S)
D [13/Apr/2011:06:25:48 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [13/Apr/2011:06:25:48 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:48 -0400] cupsdReadClient: 13 PUT /admin/conf/cupsd.conf HTTP/1.1
D [13/Apr/2011:06:25:48 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:48 -0400] cupsdAuthorize: No authentication data provided.
D [13/Apr/2011:06:25:48 -0400] cupsdIsAuthorized: username=""
D [13/Apr/2011:06:25:48 -0400] cupsdSendHeader: 13 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [13/Apr/2011:06:25:48 -0400] cupsdCloseClient: 13
D [13/Apr/2011:06:25:48 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:48 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [13/Apr/2011:06:25:48 -0400] cupsdReadClient: 13 PUT /admin/conf/cupsd.conf HTTP/1.1
D [13/Apr/2011:06:25:48 -0400] cupsdSetBusyState: Active clients and dirty files
D [13/Apr/2011:06:25:48 -0400] cupsdAuthorize: Authorized as barry using PeerCred
D [13/Apr/2011:06:25:48 -0400] cupsdIsAuthorized: username="barry"
I [13/Apr/2011:06:25:48 -0400] Installing config file "/etc/cups/cupsd.conf"...
D [13/Apr/2011:06:25:48 -0400] cupsdSetBusyState: Dirty files
D [13/Apr/2011:06:25:48 -0400] cupsdCloseClient: 14
D [13/Apr/2011:06:25:48 -0400] cupsdCloseClient: 17
D [13/Apr/2011:06:25:48 -0400] cupsdCloseClient: 16
D [13/Apr/2011:06:25:48 -0400] cupsdCloseClient: 13
D [13/Apr/2011:06:25:48 -0400] cupsdDeregisterPrinter(p=0x221743c0(HP-PSC-2500), removeit=1)
I [13/Apr/2011:06:25:48 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [13/Apr/2011:06:25:48 -0400] Saving subscriptions.conf...
D [13/Apr/2011:06:25:48 -0400] cupsdSetBusyState: Not busy

---

