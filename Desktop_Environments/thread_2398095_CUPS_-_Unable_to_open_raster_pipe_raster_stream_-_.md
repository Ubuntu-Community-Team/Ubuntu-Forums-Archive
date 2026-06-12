---
title: "CUPS - Unable to open raster pipe raster stream - : Broken pipe"
date: 2018-08-07
forum: Desktop Environments
---

### Post by jtpaquet on 2018-08-07
[COLOR=#000000]I configured a Canon ML-1675 printer and I get a filter failed error.
[/COLOR][COLOR=#000000]

[/COLOR][ATTACH=CONFIG]280673[/ATTACH]



I already installed ghostscript and I downloaded the samsung drivers from their website: [https://support.hp.com/ca-fr/drivers/selfservice/samsung-ml-1675-laser-printer-series/19134532](https://support.hp.com/ca-fr/drivers/selfservice/samsung-ml-1675-laser-printer-series/19134532)


I copied the "raspertospl" file from /uld/x86_64 to /usr/lib/cups/filter.


[COLOR=#000000]Thank you


Here is my error log:

> 
[/COLOR]E [06/Aug/2018:16:41:23 -0400] [Job 5] Unable to open raster stream - : Broken pipeE [06/Aug/2018:16:41:31 -0400] [Job 5] Job stopped due to filter errors; please consult the error_log file for details.
D [06/Aug/2018:16:41:31 -0400] [Job 5] The following messages were recorded from 04:41:22 PM to 04:41:31 PM
D [06/Aug/2018:16:41:31 -0400] [Job 5] Adding start banner page "none".
D [06/Aug/2018:16:41:31 -0400] [Job 5] Adding end banner page "none".
D [06/Aug/2018:16:41:31 -0400] [Job 5] File of type application/pdf queued by "pi".
D [06/Aug/2018:16:41:31 -0400] [Job 5] hold_until=0
D [06/Aug/2018:16:41:31 -0400] [Job 5] Queued on "Samsung_ML-1670_Series" by "pi".
D [06/Aug/2018:16:41:31 -0400] [Job 5] time-at-processing=1533588082
D [06/Aug/2018:16:41:31 -0400] [Job 5] 3 filters for job:
D [06/Aug/2018:16:41:31 -0400] [Job 5] pdftopdf (application/pdf to application/vnd.cups-pdf, cost 66)
D [06/Aug/2018:16:41:31 -0400] [Job 5] gstoraster (application/vnd.cups-pdf to application/vnd.cups-raster, cost 99)
D [06/Aug/2018:16:41:31 -0400] [Job 5] rastertospl (application/vnd.cups-raster to printer/Samsung_ML-1670_Series, cost 0)
D [06/Aug/2018:16:41:31 -0400] [Job 5] job-sheets=none,none
D [06/Aug/2018:16:41:31 -0400] [Job 5] argv[0]="Samsung_ML-1670_Series"
D [06/Aug/2018:16:41:31 -0400] [Job 5] argv[1]="5"
D [06/Aug/2018:16:41:31 -0400] [Job 5] argv[2]="pi"
D [06/Aug/2018:16:41:31 -0400] [Job 5] argv[3]="Leafpad job #1"
D [06/Aug/2018:16:41:31 -0400] [Job 5] argv[4]="1"
D [06/Aug/2018:16:41:31 -0400] [Job 5] argv[5]="InputSlot=Auto Quality=600x600_Draft number-up=1 PageSize=Letter JCLEconomode=NONE MediaType=None JCLPowerSaveTime=min5 JCLDarkness=NORMAL job-uuid=urn:uuid:807a5b27-801c-3c70-69d7-09248ab4d2c5 job-originating-host-name=localhost date-time-at-creation= date-time-at-processing= time-at-creation=1533588082 time-at-processing=1533588082"
D [06/Aug/2018:16:41:31 -0400] [Job 5] argv[6]="/var/spool/cups/d00005-001"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[8]="HOME=/var/spool/cups/tmp"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[10]="SERVER_ADMIN=root@raspberrypi"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[11]="SOFTWARE=CUPS/2.2.1"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[13]="USER=root"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[14]="CUPS_MAX_MESSAGE=2047"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[17]="IPP_PORT=631"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[18]="CHARSET=utf-8"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[19]="LANG=en_CA.UTF-8"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[20]="PPD=/etc/cups/ppd/Samsung_ML-1670_Series.ppd"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[21]="RIP_MAX_CACHE=128m"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[22]="CONTENT_TYPE=application/pdf"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[23]="DEVICE_URI=usb://Samsung/ML-1670%20Series?serial=Z6EKBKDB601140R."
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[24]="PRINTER_INFO=Samsung ML-1670 Series"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[25]="PRINTER_LOCATION=Labo"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[26]="PRINTER=Samsung_ML-1670_Series"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[27]="PRINTER_STATE_REASONS=none"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[28]="CUPS_FILETYPE=document"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[29]="FINAL_CONTENT_TYPE=application/vnd.cups-raster"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[30]="AUTH_I****"
D [06/Aug/2018:16:41:31 -0400] [Job 5] Started filter /usr/lib/cups/filter/pdftopdf (PID 2641)
D [06/Aug/2018:16:41:31 -0400] [Job 5] Started filter /usr/lib/cups/filter/gstoraster (PID 2642)
D [06/Aug/2018:16:41:31 -0400] [Job 5] Started filter /usr/lib/cups/filter/rastertospl (PID 2643)
D [06/Aug/2018:16:41:31 -0400] [Job 5] Started backend /usr/lib/cups/backend/usb (PID 2644)
D [06/Aug/2018:16:41:31 -0400] [Job 5] execv failed: Exec format error
D [06/Aug/2018:16:41:31 -0400] [Job 5] PID 2643 (/usr/lib/cups/filter/rastertospl) stopped with status 108 (Exec format error)
D [06/Aug/2018:16:41:31 -0400] [Job 5] Hint: Try setting the LogLevel to "debug" to find out more.
D [06/Aug/2018:16:41:31 -0400] [Job 5] OUTFORMAT=\"(null)\", so output format will be CUPS/PWG Raster
D [06/Aug/2018:16:41:31 -0400] [Job 5] Loading USB quirks from \"/usr/share/cups/usb\".
D [06/Aug/2018:16:41:31 -0400] [Job 5] Loaded 132 quirks.
D [06/Aug/2018:16:41:31 -0400] [Job 5] Printing on printer with URI: usb://Samsung/ML-1670%20Series?serial=Z6EKBKDB601140R.
D [06/Aug/2018:16:41:31 -0400] [Job 5] pdftopdf: Last filter determined by the PPD: rastertospl; FINAL_CONTENT_TYPE: application/vnd.cups-raster => pdftopdf will not log pages in page_log.
D [06/Aug/2018:16:41:31 -0400] [Job 5] libusb_get_device_list=7
D [06/Aug/2018:16:41:31 -0400] [Job 5] STATE: +connecting-to-device
D [06/Aug/2018:16:41:31 -0400] [Job 5] PID 2641 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [06/Aug/2018:16:41:31 -0400] [Job 5] Color Manager: Calibration Mode/Off
D [06/Aug/2018:16:41:31 -0400] [Job 5] STATE: -connecting-to-device
D [06/Aug/2018:16:41:31 -0400] [Job 5] Printer found with device ID: MFG:Samsung;CMD:GDI,FWV,EXT;MDL:ML-1670 Series;CLS:PRINTER;STATUS:BUSY; Device URI: usb://Samsung/ML-1670%20Series?serial=Z6EKBKDB601140R.
D [06/Aug/2018:16:41:31 -0400] [Job 5] Device protocol: 2
D [06/Aug/2018:16:41:31 -0400] [Job 5] Calling FindDeviceById(cups-Samsung_ML-1670_Series)
D [06/Aug/2018:16:41:31 -0400] [Job 5] Sending data to printer.
D [06/Aug/2018:16:41:31 -0400] [Job 5] Sent 0 bytes...
D [06/Aug/2018:16:41:31 -0400] [Job 5] Found device /org/freedesktop/ColorManager/devices/cups_Samsung_ML_1670_Series
D [06/Aug/2018:16:41:31 -0400] [Job 5] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [06/Aug/2018:16:41:31 -0400] [Job 5] Calling FindDeviceById(cups-Samsung_ML-1670_Series)
D [06/Aug/2018:16:41:31 -0400] [Job 5] Found device /org/freedesktop/ColorManager/devices/cups_Samsung_ML_1670_Series
D [06/Aug/2018:16:41:31 -0400] [Job 5] Calling GetProfileForQualifiers(Gray.None.600dpi...)
D [06/Aug/2018:16:41:31 -0400] [Job 5] Failed to send: org.freedesktop.ColorManager.Device.NothingMatched:nothing matched expression \'Gray.None.600dpi,Gray.None.*,Gray.*.600dpi,Gray.*.*,*\'
D [06/Aug/2018:16:41:31 -0400] [Job 5] Failed to get profile filename for cups-Samsung_ML-1670_Series
D [06/Aug/2018:16:41:31 -0400] [Job 5] Color Manager: no profiles specified in PPD
D [06/Aug/2018:16:41:31 -0400] [Job 5] Color Manager: ICC Profile: None
D [06/Aug/2018:16:41:31 -0400] [Job 5] Ghostscript using Any-Part-of-Pixel method to fill paths.
D [06/Aug/2018:16:41:31 -0400] [Job 5] Ghostscript command line: gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -dNOMEDIAATTRS -sstdout=%stderr -sOutputFile=%stdout -sDEVICE=cups -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=0 -scupsPageSizeName=Letter -I/usr/share/cups/fonts -c \'<</.HWMargins[12.500000 12.500000 12.500000 12.500000] /Margins[0 0]>>setpagedevice\' -f -_
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[0]=\"CUPS_CACHEDIR=/var/cache/cups\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[1]=\"CUPS_DATADIR=/usr/share/cups\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[2]=\"CUPS_DOCROOT=/usr/share/cups/doc-root\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[3]=\"CUPS_FONTPATH=/usr/share/cups/fonts\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[4]=\"CUPS_REQUESTROOT=/var/spool/cups\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[5]=\"CUPS_SERVERBIN=/usr/lib/cups\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[6]=\"CUPS_SERVERROOT=/etc/cups\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[7]=\"CUPS_STATEDIR=/var/run/cups\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[8]=\"HOME=/var/spool/cups/tmp\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[9]=\"PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[10]=\"SERVER_ADMIN=root@raspberrypi\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[11]=\"SOFTWARE=CUPS/2.2.1\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[12]=\"TMPDIR=/var/spool/cups/tmp\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[13]=\"USER=root\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[14]=\"CUPS_MAX_MESSAGE=2047\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[15]=\"CUPS_SERVER=/var/run/cups/cups.sock\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[16]=\"CUPS_ENCRYPTION=IfRequested\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[17]=\"IPP_PORT=631\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[18]=\"CHARSET=utf-8\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[19]=\"LANG=en_CA.UTF-8\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[20]=\"PPD=/etc/cups/ppd/Samsung_ML-1670_Series.ppd\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[21]=\"RIP_MAX_CACHE=128m\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[22]=\"CONTENT_TYPE=application/pdf\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[23]=\"DEVICE_URI=usb://Samsung/ML-1670%20Series?serial=Z6EKBKDB601140R.\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[24]=\"PRINTER_INFO=Samsung ML-1670 Series\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[25]=\"PRINTER_LOCATION=Labo\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[26]=\"PRINTER=Samsung_ML-1670_Series\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[27]=\"PRINTER_STATE_REASONS=none\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[28]=\"CUPS_FILETYPE=document\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[29]=\"FINAL_CONTENT_TYPE=application/vnd.cups-raster\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] envp[30]=\"AUTH_INFO_REQUIRED=none\"
D [06/Aug/2018:16:41:31 -0400] [Job 5] Start rendering...
D [06/Aug/2018:16:41:31 -0400] [Job 5] Processing page 1...
D [06/Aug/2018:16:41:31 -0400] [Job 5] Waiting for read thread to exit...
D [06/Aug/2018:16:41:31 -0400] [Job 5] Error: /ioerror in --showpage--
D [06/Aug/2018:16:41:31 -0400] [Job 5] Operand stack:
D [06/Aug/2018:16:41:31 -0400] [Job 5] (/var/spool/cups/tmp/gs_0iFTlo)   --nostringval--   1   true
D [06/Aug/2018:16:41:31 -0400] [Job 5] Execution stack:
D [06/Aug/2018:16:41:31 -0400] [Job 5] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   2003   1   3   %oparray_pop   2002   1   3   %oparray_pop   1986   1   3   %oparray_pop   --nostringval--   --nostringval--   --nostringval--   2   1   1   --nostringval--   %for_pos_int_continue   --nostringval--   --nostringval--   1874   2   9   %oparray_pop   --nostringval--   --nostringval--
D [06/Aug/2018:16:41:31 -0400] [Job 5] Dictionary stack:
D [06/Aug/2018:16:41:31 -0400] [Job 5] --dict:1216/1684(ro)(G)--   --dict:1/20(G)--   --dict:83/200(L)--   --dict:83/200(L)--   --dict:135/256(ro)(G)--   --dict:291/300(ro)(G)--   --dict:32/32(L)--   --dict:6/9(L)--   --dict:23/40(L)--
D [06/Aug/2018:16:41:31 -0400] [Job 5] Current allocation mode is local
D [06/Aug/2018:16:41:31 -0400] [Job 5] Last OS error: Broken pipe
D [06/Aug/2018:16:41:31 -0400] [Job 5] GPL Ghostscript 9.20: Unrecoverable error, exit code 1
D [06/Aug/2018:16:41:31 -0400] [Job 5] Rendering completed
D [06/Aug/2018:16:41:31 -0400] [Job 5] PID 2642 (/usr/lib/cups/filter/gstoraster) stopped with status 1.
D [06/Aug/2018:16:41:31 -0400] [Job 5] Hint: Try setting the LogLevel to "debug" to find out more.
D [06/Aug/2018:16:41:31 -0400] [Job 5] Read thread still active, aborting the pending read...
D [06/Aug/2018:16:41:31 -0400] [Job 5] Resetting printer.
D [06/Aug/2018:16:41:31 -0400] [Job 5] PID 2644 (/usr/lib/cups/backend/usb) exited with no errors.
D [06/Aug/2018:16:41:31 -0400] [Job 5] End of messages
D [06/Aug/2018:16:41:31 -0400] [Job 5] printer-state=3(idle)
D [06/Aug/2018:16:41:31 -0400] [Job 5] printer-state-message="Rendering completed"
D [06/Aug/2018:16:41:31 -0400] [Job 5] printer-state-reasons=none
[COLOR=#000000][/COLOR]

---

