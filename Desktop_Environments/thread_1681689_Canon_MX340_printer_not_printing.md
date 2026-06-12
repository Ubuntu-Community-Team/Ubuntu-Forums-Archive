---
title: "Canon MX340 printer not printing"
date: 2011-02-04
forum: Desktop Environments
---

### Post by Cypher2 on 2011-02-04
Hello everyone,

I'm quite perplexed. Been using ubnutu gnome for a loooong time and my printer (Canon MX340) has been running just fine, configuration and usage.

I now switch to kde. configure my printer the same way i would under gnome and as soon as i send a job, it processes for about 3 seconds and just marks "stopped" under status. nothing goes through anymore!!

i've updated from 4.5 to 4.6 with backports and nothing is happening on there either.

im running maverick amd64 and using the i386 drivers (with dpkg -i --force-all) which are still recognized even under kde.

I have no clue on what to do anymore.. help would be much appreciated

Thanks

p.s.: the printer normally runs as wireless standalone (no samba/cups involvment whatsoever)

---

### Post by inobe on 2011-02-04
hi' did you install kubuntu desktop or is this pure kubuntu?

---

### Post by Cypher2 on 2011-02-05
It's a fresh install from kubuntu maverick 10.10 amd 64..

---

### Post by inobe on 2011-02-08
i checked previous posts and found your howto thread.

is your device recognized in the kde control module?

what did you do differently in kubuntu with that howto?

---

### Post by Cypher2 on 2011-02-08
That<s exactly what bothers me.. i've simplified the process eversince on gnome since most of my how-to was to show people how to configure the printer itself to prepare it for driver installation.

so basically it<s running as standalone with it's own IPv4 address on my network (wirelessly) and all I do is force the package install of the drivers I have (same ones used under gnome that were working without any issue).

after that, in the control module, it sets up fine, being recognized as MX340 (it's network name) with URI dnssd://MX340._printer._tcp.local/

I go through the process, label the location and then apply.

As soon as I try sending a test page print or whatever job, it processes for 3 seconds then marks @Stopped@ on status and just hangs there...

don't know what to do... I even upgraded to natty kubuntu in hopes the issue would resolve but nope!

Thanks for the reply btw :)


p.s.: I even have a debug i was able to log which doesn't show much of where the error emerges from...

---

### Post by Cypher2 on 2011-02-08
this is the cups debug output through [http://localhost:631](http://localhost:631)

E [08/Feb/2011:12:34:15 -0500] [cups-deviced] PID 4379 (cnijnet) stopped with status 2!
E [08/Feb/2011:12:34:15 -0500] [cups-deviced] PID 4385 (cnijusb) stopped with status 2!
E [08/Feb/2011:12:35:27 -0500] [cups-deviced] PID 4420 (cnijusb) stopped with status 2!
E [08/Feb/2011:12:35:27 -0500] [cups-deviced] PID 4414 (cnijnet) stopped with status 2!
E [08/Feb/2011:12:36:01 -0500] [Job 1] No %%BoundingBox: comment in header!
E [08/Feb/2011:12:36:05 -0500] [Job 1] Job stopped due to filter errors; please consult the error_log file for details.
D [08/Feb/2011:12:36:05 -0500] [Job 1] The following messages were recorded from 12:36:01 to 12:36:05
D [08/Feb/2011:12:36:05 -0500] [Job 1] Adding start banner page "".
D [08/Feb/2011:12:36:05 -0500] [Job 1] Adding end banner page "".
D [08/Feb/2011:12:36:05 -0500] [Job 1] File of type application/postscript queued by "nathanel".
D [08/Feb/2011:12:36:05 -0500] [Job 1] hold_until=0
D [08/Feb/2011:12:36:05 -0500] [Job 1] Queued on "MX340_series" by "nathanel".
D [08/Feb/2011:12:36:05 -0500] [Job 1] job-sheets=,
D [08/Feb/2011:12:36:05 -0500] [Job 1] argv[0]="MX340_series"
D [08/Feb/2011:12:36:05 -0500] [Job 1] argv[1]="1"
D [08/Feb/2011:12:36:05 -0500] [Job 1] argv[2]="nathanel"
D [08/Feb/2011:12:36:05 -0500] [Job 1] argv[3]="Test Page"
D [08/Feb/2011:12:36:05 -0500] [Job 1] argv[4]="1"
D [08/Feb/2011:12:36:05 -0500] [Job 1] argv[5]="PageSize=Letter job-uuid=urn:uuid:72f3ed39-2256-3475-7bb4-5d1d118124b6 job-originating-host-name=localhost time-at-creation=1297186561 time-at-processing=1297186561 AP_D_InputSlot="
D [08/Feb/2011:12:36:05 -0500] [Job 1] argv[6]="/var/spool/cups/d00001-001"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[8]="HOME=/var/spool/cups/tmp"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[10]="SERVER_ADMIN=root@Mercury"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[11]="SOFTWARE=CUPS/1.4.5"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[13]="USER=root"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[16]="IPP_PORT=631"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[17]="CHARSET=utf-8"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[18]="LANG=en_CA.UTF-8"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[19]="PPD=/etc/cups/ppd/MX340_series.ppd"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[20]="RIP_MAX_CACHE=auto"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[21]="CONTENT_TYPE=application/postscript"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[22]="DEVICE_URI=dnssd://MX340._printer._tcp.local/"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[23]="PRINTER_INFO="
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[24]="PRINTER_LOCATION=Mercury"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[25]="PRINTER=MX340_series"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[26]="CUPS_FILETYPE=job-sheet"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[27]="FINAL_CONTENT_TYPE=printer/MX340_series"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[28]="AUTH_U****"
D [08/Feb/2011:12:36:05 -0500] [Job 1] envp[29]="AUTH_P****"
D [08/Feb/2011:12:36:05 -0500] [Job 1] Started filter /usr/lib/cups/filter/pstops (PID 4460)
D [08/Feb/2011:12:36:05 -0500] [Job 1] Started filter /usr/lib/cups/filter/pstocanonij (PID 4461)
D [08/Feb/2011:12:36:05 -0500] [Job 1] Started backend /usr/lib/cups/backend/dnssd (PID 4462)
D [08/Feb/2011:12:36:05 -0500] [Job 1] Resolving "MX340._printer._tcp.local"...
D [08/Feb/2011:12:36:05 -0500] [Job 1] STATE: +connecting-to-device
D [08/Feb/2011:12:36:05 -0500] [Job 1] Resolving "MX340", regtype="_printer._tcp", domain="local."...
D [08/Feb/2011:12:36:05 -0500] [Job 1] Resolved as "lpd://192.168.2.42:515/auto"...
D [08/Feb/2011:12:36:05 -0500] [Job 1] STATE: -connecting-to-device,offline-report
D [08/Feb/2011:12:36:05 -0500] [Job 1] Executing backend "/usr/lib/cups/backend/lpd"...
D [08/Feb/2011:12:36:05 -0500] [Job 1] STATE: +connecting-to-device
D [08/Feb/2011:12:36:05 -0500] [Job 1] Looking up "192.168.2.42"...
D [08/Feb/2011:12:36:05 -0500] [Job 1] Copying print data...
D [08/Feb/2011:12:36:05 -0500] [Job 1] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0x7f43ac0be098, use_bc=0, side_cb=0x7f43aa2de650)
D [08/Feb/2011:12:36:05 -0500] [Job 1] /usr/lib/cups/filter/pstocanonij: No such file or directory
D [08/Feb/2011:12:36:05 -0500] [Job 1] STATE: +connecting-to-device
D [08/Feb/2011:12:36:05 -0500] [Job 1] Looking up "192.168.2.42"...
D [08/Feb/2011:12:36:05 -0500] [Job 1] Connecting to 192.168.2.42:515 for printer auto
D [08/Feb/2011:12:36:05 -0500] [Job 1] Connecting to printer...
D [08/Feb/2011:12:36:05 -0500] [Job 1] Page = 612x792; 18,14 to 594,784
D [08/Feb/2011:12:36:05 -0500] [Job 1] slow_collate=0, slow_duplex=0, slow_order=0
D [08/Feb/2011:12:36:05 -0500] [Job 1] Before copy_comments - %!PS-Adobe-3.0
D [08/Feb/2011:12:36:05 -0500] [Job 1] %!PS-Adobe-3.0
D [08/Feb/2011:12:36:05 -0500] [Job 1] %%Title: PPR Test Page
D [08/Feb/2011:12:36:05 -0500] [Job 1] %%Pages: 1
D [08/Feb/2011:12:36:05 -0500] [Job 1] %%DocumentNeededResources: font Helvetica
D [08/Feb/2011:12:36:05 -0500] [Job 1] %%EndComments
D [08/Feb/2011:12:36:05 -0500] [Job 1] Before copy_prolog - %%BeginProlog
D [08/Feb/2011:12:36:05 -0500] [Job 1] Before copy_setup - %%BeginSetup
D [08/Feb/2011:12:36:05 -0500] [Job 1] Before page loop - %%Page: 1 1
D [08/Feb/2011:12:36:05 -0500] [Job 1] Copying page 1...
D [08/Feb/2011:12:36:05 -0500] [Job 1] pagew = 576.0, pagel = 769.3
D [08/Feb/2011:12:36:05 -0500] [Job 1] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [08/Feb/2011:12:36:05 -0500] [Job 1] PageLeft = 18.1, PageRight = 594.1
D [08/Feb/2011:12:36:05 -0500] [Job 1] PageTop = 783.5, PageBottom = 14.2
D [08/Feb/2011:12:36:05 -0500] [Job 1] PageWidth = 612.0, PageLength = 792.0
D [08/Feb/2011:12:36:05 -0500] [Job 1] STATE: -connecting-to-device
D [08/Feb/2011:12:36:05 -0500] [Job 1] Connected to printer...
D [08/Feb/2011:12:36:05 -0500] [Job 1] Connected to 192.168.2.42:515 (IPv4) (local port 1023)...
D [08/Feb/2011:12:36:05 -0500] [Job 1] hrDeviceDesc="Unknown"
D [08/Feb/2011:12:36:05 -0500] [Job 1] prtGeneralCurrentLocalization type is 0, expected 2!
D [08/Feb/2011:12:36:05 -0500] [Job 1] lpd_command 02 auto
D [08/Feb/2011:12:36:05 -0500] [Job 1] Sending command string (6 bytes)...
D [08/Feb/2011:12:36:05 -0500] [Job 1] Reading command status...
D [08/Feb/2011:12:36:05 -0500] [Job 1] lpd_command returning 0
D [08/Feb/2011:12:36:05 -0500] [Job 1] Control file is:
D [08/Feb/2011:12:36:05 -0500] [Job 1] HMercury
D [08/Feb/2011:12:36:05 -0500] [Job 1] Pnathanel
D [08/Feb/2011:12:36:05 -0500] [Job 1] JTest Page
D [08/Feb/2011:12:36:05 -0500] [Job 1] ldfA462Mercury
D [08/Feb/2011:12:36:05 -0500] [Job 1] UdfA462Mercury
D [08/Feb/2011:12:36:05 -0500] [Job 1] NTest Page
D [08/Feb/2011:12:36:05 -0500] [Job 1] lpd_command 02 71 cfA462Mercury
D [08/Feb/2011:12:36:05 -0500] [Job 1] Sending command string (18 bytes)...
D [08/Feb/2011:12:36:05 -0500] [Job 1] Reading command status...
D [08/Feb/2011:12:36:05 -0500] [Job 1] lpd_command returning 0
D [08/Feb/2011:12:36:05 -0500] [Job 1] Sending control file (71 bytes)
D [08/Feb/2011:12:36:05 -0500] [Job 1] Control file sent successfully
D [08/Feb/2011:12:36:05 -0500] [Job 1] lpd_command 03 0 dfA462Mercury
D [08/Feb/2011:12:36:05 -0500] [Job 1] Sending command string (17 bytes)...
D [08/Feb/2011:12:36:05 -0500] [Job 1] Reading command status...
D [08/Feb/2011:12:36:05 -0500] [Job 1] lpd_command returning 0
D [08/Feb/2011:12:36:05 -0500] [Job 1] Sending data file (0 bytes)
D [08/Feb/2011:12:36:05 -0500] [Job 1] Data file sent successfully
D [08/Feb/2011:12:36:05 -0500] [Job 1] End of messages
D [08/Feb/2011:12:36:05 -0500] [Job 1] printer-state=3(idle)
D [08/Feb/2011:12:36:05 -0500] [Job 1] printer-state-message="Data file sent successfully"
D [08/Feb/2011:12:36:05 -0500] [Job 1] printer-state-reasons=none
E [08/Feb/2011:12:43:16 -0500] [Job 2] No %%BoundingBox: comment in header!
E [08/Feb/2011:12:43:20 -0500] [Job 2] Job stopped due to filter errors; please consult the error_log file for details.
D [08/Feb/2011:12:43:20 -0500] [Job 2] The following messages were recorded from 12:43:16 to 12:43:20
D [08/Feb/2011:12:43:20 -0500] [Job 2] Adding start banner page "".
D [08/Feb/2011:12:43:20 -0500] [Job 2] Adding end banner page "".
D [08/Feb/2011:12:43:20 -0500] [Job 2] File of type application/postscript queued by "nathanel".
D [08/Feb/2011:12:43:20 -0500] [Job 2] hold_until=0
D [08/Feb/2011:12:43:20 -0500] [Job 2] Queued on "MX340_series" by "nathanel".
D [08/Feb/2011:12:43:20 -0500] [Job 2] job-sheets=,
D [08/Feb/2011:12:43:20 -0500] [Job 2] argv[0]="MX340_series"
D [08/Feb/2011:12:43:20 -0500] [Job 2] argv[1]="2"
D [08/Feb/2011:12:43:20 -0500] [Job 2] argv[2]="nathanel"
D [08/Feb/2011:12:43:20 -0500] [Job 2] argv[3]="Test Page"
D [08/Feb/2011:12:43:20 -0500] [Job 2] argv[4]="1"
D [08/Feb/2011:12:43:20 -0500] [Job 2] argv[5]="PageSize=Letter job-uuid=urn:uuid:aa6b11a6-f791-38c2-679c-b173d74d6f9d job-originating-host-name=localhost time-at-creation=1297186996 time-at-processing=1297186996 AP_D_InputSlot="
D [08/Feb/2011:12:43:20 -0500] [Job 2] argv[6]="/var/spool/cups/d00002-001"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[8]="HOME=/var/spool/cups/tmp"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[10]="SERVER_ADMIN=root@Mercury"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[11]="SOFTWARE=CUPS/1.4.5"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[13]="USER=root"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[16]="IPP_PORT=631"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[17]="CHARSET=utf-8"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[18]="LANG=en_CA.UTF-8"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[19]="PPD=/etc/cups/ppd/MX340_series.ppd"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[20]="RIP_MAX_CACHE=auto"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[21]="CONTENT_TYPE=application/postscript"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[22]="DEVICE_URI=dnssd://MX340._printer._tcp.local/"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[23]="PRINTER_INFO="
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[24]="PRINTER_LOCATION=Mercury"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[25]="PRINTER=MX340_series"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[26]="CUPS_FILETYPE=job-sheet"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[27]="FINAL_CONTENT_TYPE=printer/MX340_series"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[28]="AUTH_U****"
D [08/Feb/2011:12:43:20 -0500] [Job 2] envp[29]="AUTH_P****"
D [08/Feb/2011:12:43:20 -0500] [Job 2] Started filter /usr/lib/cups/filter/pstops (PID 4586)
D [08/Feb/2011:12:43:20 -0500] [Job 2] Started filter /usr/lib/cups/filter/pstocanonij (PID 4587)
D [08/Feb/2011:12:43:20 -0500] [Job 2] Started backend /usr/lib/cups/backend/dnssd (PID 4588)
D [08/Feb/2011:12:43:20 -0500] [Job 2] Page = 612x792; 18,14 to 594,784
D [08/Feb/2011:12:43:20 -0500] [Job 2] Resolving "MX340._printer._tcp.local"...
D [08/Feb/2011:12:43:20 -0500] [Job 2] /usr/lib/cups/filter/pstocanonij: No such file or directory
D [08/Feb/2011:12:43:20 -0500] [Job 2] STATE: +connecting-to-device
D [08/Feb/2011:12:43:20 -0500] [Job 2] Resolving "MX340", regtype="_printer._tcp", domain="local."...
D [08/Feb/2011:12:43:20 -0500] [Job 2] slow_collate=0, slow_duplex=0, slow_order=0
D [08/Feb/2011:12:43:20 -0500] [Job 2] Before copy_comments - %!PS-Adobe-3.0
D [08/Feb/2011:12:43:20 -0500] [Job 2] %!PS-Adobe-3.0
D [08/Feb/2011:12:43:20 -0500] [Job 2] %%Title: PPR Test Page
D [08/Feb/2011:12:43:20 -0500] [Job 2] %%Pages: 1
D [08/Feb/2011:12:43:20 -0500] [Job 2] %%DocumentNeededResources: font Helvetica
D [08/Feb/2011:12:43:20 -0500] [Job 2] %%EndComments
D [08/Feb/2011:12:43:20 -0500] [Job 2] Before copy_prolog - %%BeginProlog
D [08/Feb/2011:12:43:20 -0500] [Job 2] Before copy_setup - %%BeginSetup
D [08/Feb/2011:12:43:20 -0500] [Job 2] Before page loop - %%Page: 1 1
D [08/Feb/2011:12:43:20 -0500] [Job 2] Copying page 1...
D [08/Feb/2011:12:43:20 -0500] [Job 2] pagew = 576.0, pagel = 769.3
D [08/Feb/2011:12:43:20 -0500] [Job 2] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [08/Feb/2011:12:43:20 -0500] [Job 2] PageLeft = 18.1, PageRight = 594.1
D [08/Feb/2011:12:43:20 -0500] [Job 2] PageTop = 783.5, PageBottom = 14.2
D [08/Feb/2011:12:43:20 -0500] [Job 2] PageWidth = 612.0, PageLength = 792.0
D [08/Feb/2011:12:43:20 -0500] [Job 2] Resolved as "lpd://192.168.2.42:515/auto"...
D [08/Feb/2011:12:43:20 -0500] [Job 2] STATE: -connecting-to-device,offline-report
D [08/Feb/2011:12:43:20 -0500] [Job 2] Executing backend "/usr/lib/cups/backend/lpd"...
D [08/Feb/2011:12:43:20 -0500] [Job 2] STATE: +connecting-to-device
D [08/Feb/2011:12:43:20 -0500] [Job 2] Looking up "192.168.2.42"...
D [08/Feb/2011:12:43:20 -0500] [Job 2] Copying print data...
D [08/Feb/2011:12:43:20 -0500] [Job 2] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0x7f4523185098, use_bc=0, side_cb=0x7f45213f7650)
D [08/Feb/2011:12:43:20 -0500] [Job 2] STATE: +connecting-to-device
D [08/Feb/2011:12:43:20 -0500] [Job 2] Looking up "192.168.2.42"...
D [08/Feb/2011:12:43:20 -0500] [Job 2] Connecting to 192.168.2.42:515 for printer auto
D [08/Feb/2011:12:43:20 -0500] [Job 2] Connecting to printer...
D [08/Feb/2011:12:43:20 -0500] [Job 2] STATE: -connecting-to-device
D [08/Feb/2011:12:43:20 -0500] [Job 2] Connected to printer...
D [08/Feb/2011:12:43:20 -0500] [Job 2] Connected to 192.168.2.42:515 (IPv4) (local port 1023)...
D [08/Feb/2011:12:43:20 -0500] [Job 2] hrDeviceDesc="Unknown"
D [08/Feb/2011:12:43:20 -0500] [Job 2] prtGeneralCurrentLocalization type is 0, expected 2!
D [08/Feb/2011:12:43:20 -0500] [Job 2] lpd_command 02 auto
D [08/Feb/2011:12:43:20 -0500] [Job 2] Sending command string (6 bytes)...
D [08/Feb/2011:12:43:20 -0500] [Job 2] Reading command status...
D [08/Feb/2011:12:43:20 -0500] [Job 2] lpd_command returning 0
D [08/Feb/2011:12:43:20 -0500] [Job 2] Control file is:
D [08/Feb/2011:12:43:20 -0500] [Job 2] HMercury
D [08/Feb/2011:12:43:20 -0500] [Job 2] Pnathanel
D [08/Feb/2011:12:43:20 -0500] [Job 2] JTest Page
D [08/Feb/2011:12:43:20 -0500] [Job 2] ldfA588Mercury
D [08/Feb/2011:12:43:20 -0500] [Job 2] UdfA588Mercury
D [08/Feb/2011:12:43:20 -0500] [Job 2] NTest Page
D [08/Feb/2011:12:43:20 -0500] [Job 2] lpd_command 02 71 cfA588Mercury
D [08/Feb/2011:12:43:20 -0500] [Job 2] Sending command string (18 bytes)...
D [08/Feb/2011:12:43:20 -0500] [Job 2] Reading command status...
D [08/Feb/2011:12:43:20 -0500] [Job 2] lpd_command returning 0
D [08/Feb/2011:12:43:20 -0500] [Job 2] Sending control file (71 bytes)
D [08/Feb/2011:12:43:20 -0500] [Job 2] Control file sent successfully
D [08/Feb/2011:12:43:20 -0500] [Job 2] lpd_command 03 0 dfA588Mercury
D [08/Feb/2011:12:43:20 -0500] [Job 2] Sending command string (17 bytes)...
D [08/Feb/2011:12:43:20 -0500] [Job 2] Reading command status...
D [08/Feb/2011:12:43:20 -0500] [Job 2] lpd_command returning 0
D [08/Feb/2011:12:43:20 -0500] [Job 2] Sending data file (0 bytes)
D [08/Feb/2011:12:43:20 -0500] [Job 2] Data file sent successfully
D [08/Feb/2011:12:43:20 -0500] [Job 2] End of messages
D [08/Feb/2011:12:43:20 -0500] [Job 2] printer-state=3(idle)
D [08/Feb/2011:12:43:20 -0500] [Job 2] printer-state-message="Data file sent successfully"
D [08/Feb/2011:12:43:20 -0500] [Job 2] printer-state-reasons=none
E [08/Feb/2011:12:49:14 -0500] [Job 3] No %%BoundingBox: comment in header!
E [08/Feb/2011:12:49:14 -0500] [Job 3] Empty print file!
D [08/Feb/2011:12:49:14 -0500] [Job 3] The following messages were recorded from 12:49:13 to 12:49:14
D [08/Feb/2011:12:49:14 -0500] [Job 3] Adding start banner page "".
D [08/Feb/2011:12:49:14 -0500] [Job 3] Adding end banner page "".
D [08/Feb/2011:12:49:14 -0500] [Job 3] File of type application/postscript queued by "nathanel".
D [08/Feb/2011:12:49:14 -0500] [Job 3] hold_until=0
D [08/Feb/2011:12:49:14 -0500] [Job 3] Queued on "MX340_series" by "nathanel".
D [08/Feb/2011:12:49:14 -0500] [Job 3] job-sheets=,
D [08/Feb/2011:12:49:14 -0500] [Job 3] argv[0]="MX340_series"
D [08/Feb/2011:12:49:14 -0500] [Job 3] argv[1]="3"
D [08/Feb/2011:12:49:14 -0500] [Job 3] argv[2]="nathanel"
D [08/Feb/2011:12:49:14 -0500] [Job 3] argv[3]="Test Page"
D [08/Feb/2011:12:49:14 -0500] [Job 3] argv[4]="1"
D [08/Feb/2011:12:49:14 -0500] [Job 3] argv[5]="PageSize=Letter job-uuid=urn:uuid:4586f56b-f607-3f66-51c7-76f69bc7880c job-originating-host-name=localhost time-at-creation=1297187353 time-at-processing=1297187353 AP_D_InputSlot="
D [08/Feb/2011:12:49:14 -0500] [Job 3] argv[6]="/var/spool/cups/d00003-001"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[8]="HOME=/var/spool/cups/tmp"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[10]="SERVER_ADMIN=root@Mercury"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[11]="SOFTWARE=CUPS/1.4.5"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[13]="USER=root"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[16]="IPP_PORT=631"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[17]="CHARSET=utf-8"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[18]="LANG=en_CA.UTF-8"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[19]="PPD=/etc/cups/ppd/MX340_series.ppd"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[20]="RIP_MAX_CACHE=auto"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[21]="CONTENT_TYPE=application/postscript"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[22]="DEVICE_URI=ipp://MX340._printer._tcp.local/"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[23]="PRINTER_INFO="
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[24]="PRINTER_LOCATION=Mercury"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[25]="PRINTER=MX340_series"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[26]="CUPS_FILETYPE=job-sheet"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[27]="FINAL_CONTENT_TYPE=printer/MX340_series"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[28]="AUTH_U****"
D [08/Feb/2011:12:49:14 -0500] [Job 3] envp[29]="AUTH_P****"
D [08/Feb/2011:12:49:14 -0500] [Job 3] Started filter /usr/lib/cups/filter/pstops (PID 4813)
D [08/Feb/2011:12:49:14 -0500] [Job 3] Started filter /usr/lib/cups/filter/pstocanonij (PID 4814)
D [08/Feb/2011:12:49:14 -0500] [Job 3] Started backend /usr/lib/cups/backend/ipp (PID 4815)
D [08/Feb/2011:12:49:14 -0500] [Job 3] /usr/lib/cups/filter/pstocanonij: No such file or directory
D [08/Feb/2011:12:49:14 -0500] [Job 3] Resolving "MX340._printer._tcp.local"...
D [08/Feb/2011:12:49:14 -0500] [Job 3] STATE: +connecting-to-device
D [08/Feb/2011:12:49:14 -0500] [Job 3] Resolving "MX340", regtype="_printer._tcp", domain="local."...
D [08/Feb/2011:12:49:14 -0500] [Job 3] Page = 612x792; 18,14 to 594,784
D [08/Feb/2011:12:49:14 -0500] [Job 3] slow_collate=0, slow_duplex=0, slow_order=0
D [08/Feb/2011:12:49:14 -0500] [Job 3] Before copy_comments - %!PS-Adobe-3.0
D [08/Feb/2011:12:49:14 -0500] [Job 3] %!PS-Adobe-3.0
D [08/Feb/2011:12:49:14 -0500] [Job 3] %%Title: PPR Test Page
D [08/Feb/2011:12:49:14 -0500] [Job 3] %%Pages: 1
D [08/Feb/2011:12:49:14 -0500] [Job 3] %%DocumentNeededResources: font Helvetica
D [08/Feb/2011:12:49:14 -0500] [Job 3] %%EndComments
D [08/Feb/2011:12:49:14 -0500] [Job 3] Before copy_prolog - %%BeginProlog
D [08/Feb/2011:12:49:14 -0500] [Job 3] Before copy_setup - %%BeginSetup
D [08/Feb/2011:12:49:14 -0500] [Job 3] Before page loop - %%Page: 1 1
D [08/Feb/2011:12:49:14 -0500] [Job 3] Copying page 1...
D [08/Feb/2011:12:49:14 -0500] [Job 3] pagew = 576.0, pagel = 769.3
D [08/Feb/2011:12:49:14 -0500] [Job 3] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [08/Feb/2011:12:49:14 -0500] [Job 3] PageLeft = 18.1, PageRight = 594.1
D [08/Feb/2011:12:49:14 -0500] [Job 3] PageTop = 783.5, PageBottom = 14.2
D [08/Feb/2011:12:49:14 -0500] [Job 3] PageWidth = 612.0, PageLength = 792.0
D [08/Feb/2011:12:49:14 -0500] [Job 3] Resolved as "lpd://192.168.2.42:515/auto"...
D [08/Feb/2011:12:49:14 -0500] [Job 3] STATE: -connecting-to-device,offline-report
D [08/Feb/2011:12:49:14 -0500] [Job 3] STATE: +connecting-to-device
D [08/Feb/2011:12:49:14 -0500] [Job 3] Looking up "192.168.2.42"...
D [08/Feb/2011:12:49:14 -0500] [Job 3] Copying print data...
D [08/Feb/2011:12:49:14 -0500] [Job 3] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0x7fce3343b308, use_bc=0, side_cb=0x7fce31bd27c0)
D [08/Feb/2011:12:49:14 -0500] [Job 3] Backend returned status 1 (failed)
D [08/Feb/2011:12:49:14 -0500] [Job 3] End of messages
D [08/Feb/2011:12:49:14 -0500] [Job 3] printer-state=3(idle)
D [08/Feb/2011:12:49:14 -0500] [Job 3] printer-state-message="Empty print file!"
D [08/Feb/2011:12:49:14 -0500] [Job 3] printer-state-reasons=none
E [08/Feb/2011:12:49:31 -0500] [cups-deviced] PID 4821 (cnijnet) stopped with status 2!
E [08/Feb/2011:12:49:31 -0500] [cups-deviced] PID 4827 (cnijusb) stopped with status 2!
E [08/Feb/2011:12:51:59 -0500] [cups-deviced] PID 4876 (cnijnet) stopped with status 2!
E [08/Feb/2011:12:51:59 -0500] [cups-deviced] PID 4882 (cnijusb) stopped with status 2!

---

### Post by inobe on 2011-02-08
cups is the problem here and it seems to start here

```
/usr/lib/cups/filter/pstocanonij: No such file or directory
```

navigate here

```
/usr/lib/cups/filter/
```

and look for 

```
pstocanonij
```

seems like the installation failed in some area.

edit: i don't think these files are being copied to the correct directories, considering in kde the directories may be a little different.

doe's this driver have an installer/ ?

---

### Post by Cypher2 on 2011-02-08
The file is present in the directory you suggested to look in.

there isn't any installer with the files and debs i have for all I know.

here is a new link to another website with linux driver packs (i386) containing an installer script. [http://software.canon-europe.com/download.asp](http://software.canon-europe.com/download.asp)

I think it only calls up dpkg and installs for the user...

---

### Post by inobe on 2011-02-08
the only other things i can think of...

during the install the permissions weren't granted for that directory.

that said, you ran the script, were you prompted for a password, did you just click the .sh file?

how do you feel about reinstalling the driver?

---

### Post by Cypher2 on 2011-02-08
Thing is I've never used the sh to run the install.. I've moved the packages into a single directory and just sudo dpkg -i --force-all.

I've used this method for almost a year now flawlessly... and all of a sudden it stops working.

I've reinstalled it many times since i have formated my system a good deal of times, and that's exactly what puzzles me, it just stopped working out of the blue.

---

### Post by Cypher2 on 2011-02-08
I've switched the dpkg -iG commad to -i --force-all in the script to see where it leads and even it can't detect the printer...

---

### Post by inobe on 2011-02-08
> **Cypher2 said:**
> Thing is I've never used the sh to run the install


do you think the previous install can be cleaned up enough to run the .sh file?

---

### Post by Cypher2 on 2011-02-08
I doubt... I'll just format back to kde maverick and see what gives with the .sh on --force-architecture... 

though what boggles me is that CUPS is identical on kubuntu and ubuntu.. the only variable is the printer-config system I guess..

---

### Post by Cypher2 on 2011-02-08
So here's the deal, I reset some settings on the printer, formated back to kubuntu maverick amd64 and it detects and runs the printer fine now as if nothing happened. GO FIGURE!

the notable difference is the protocol used to set the URI and is as follows:

cnijnet:/00-1E-8F-8E-78-B0 (using the mac address rather that ldpr or dnssd, weird no? since cnijnet was the protocol normally used before...)

thanks for your help :)

---

### Post by inobe on 2011-02-08
> **Cypher2 said:**
> So here's the deal, I reset some settings on the printer, formated back to kubuntu maverick amd64 and it detects and runs the printer fine now as if nothing happened. GO FIGURE!

the notable difference is the protocol used to set the URI and is as follows:

cnijnet:/00-1E-8F-8E-78-B0 (using the mac address rather that ldpr or dnssd, weird no? since cnijnet was the protocol normally used before...)

thanks for your help :)

i could have been more help if i had that printer, we tried and you managed to to solve this, great news.


i use hp stuff, i like hp gui tools, the printer is detected out of the box and all the features work, not downing canon in any way, i just would like to see a little more from them then this.

---

### Post by vidtek on 2011-02-08
> **inobe said:**
> i could have been more help if i had that printer, we tried and you managed to to solve this, great news.


i use hp stuff, i like hp gui tools, the printer is detected out of the box and all the features work, not downing canon in any way, i just would like to see a little more from them then this.

I am using 64-bit 10.10 ubuntu KDE4. I have the MX340 printer along with a brother MFC885CW both on wireless.

The install for the MX340 me was very straightforward in the CUPS web interface, but I had to use the IP address, not MAC address.

The Brother was a totally different story.  Many hoops and files to load manually, but they both work fine now, even remote scanning and fax printing with the brother.

Tony.

---

### Post by inobe on 2011-02-09
> **vidtek said:**
> I am using 64-bit 10.10 ubuntu KDE4. I have the MX340 printer along with a brother MFC885CW both on wireless.

The install for the MX340 me was very straightforward in the CUPS web interface, but I had to use the IP address, not MAC address.

The Brother was a totally different story.  Many hoops and files to load manually, but they both work fine now, even remote scanning and fax printing with the brother.

Tony.

tony, canon has probably the best cameras and printers in the world, i am just shocked that they aren't plug and play.

---

### Post by Cypher2 on 2011-02-09
Well my MP150 used to work out of the box. Could you please specify how did you config through the IP? I'm interested in knowing if i could script it. Also, like many other providers, the issue revolves around the lack of amd64 driver and build support... oh well. 

I'm eager to see if another clean install would make it go bonkers again or if my settings are the issue. Maybe disabling apple's bonjour service is what helped. I'll confirm that when i come back home from faculty.

Let's try figuring it out for the MX series as they seem to share similar configs :)

---

### Post by vidtek on 2011-02-09
> **Cypher2 said:**
> Well my MP150 used to work out of the box. Could you please specify how did you config through the IP? I'm interested in knowing if i could script it. Also, like many other providers, the issue revolves around the lack of amd64 driver and build support... oh well. 

I'm eager to see if another clean install would make it go bonkers again or if my settings are the issue. Maybe disabling apple's bonjour service is what helped. I'll confirm that when i come back home from faculty.

Let's try figuring it out for the MX series as they seem to share similar configs :)

c2-
Done so many things since, can't remember exactly what I did(silly old fart memory).

Doing a fresh install of 2.8 ultimate as it uses gnome and has most of the stuff I want, but am struggling with the LIRC 
installation which is eluding me at the moment....

When I get round to printers I'll make some notes on how it goes.

Tony

---

