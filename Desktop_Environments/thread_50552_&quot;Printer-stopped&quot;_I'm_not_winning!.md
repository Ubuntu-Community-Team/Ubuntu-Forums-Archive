---
title: "&quot;Printer-stopped&quot; I'm not winning!"
date: 2005-07-20
forum: Desktop Environments
---

### Post by geofff on 2005-07-20
I cannot print to the shared printer on windows machine. I could yesterday and can't today. I haven't a clue what I've done.  

I have reset loglevel controls in /etc/cups/cupsd.conf to debug and produced the following from  /var/log/cups/error_log

[PHP]I [20/Jul/2005:21:05:56 +0100] Printer 'DeskJet-5740' started by 'root'.
D [20/Jul/2005:21:05:56 +0100] StartJob(130, 0x8097048)
D [20/Jul/2005:21:05:56 +0100] StartJob() id = 130, file = 0/1
D [20/Jul/2005:21:05:56 +0100] job-sheets=none,none
D [20/Jul/2005:21:05:56 +0100] banner_page = 0
D [20/Jul/2005:21:05:56 +0100] StartJob: argv = "DeskJet-5740","130","geoff","cpag1.sxw","1","","/var/spool/cups/d00130-001"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[2]="USER=root"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[3]="CHARSET=iso-8859-15"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[4]="LANG=en"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[5]="TZ=Europe/London"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[6]="PPD=/etc/cups/ppd/DeskJet-5740.ppd"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[11]="DEVICE_URI=smb://192.168.0.189/Linda Printer"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[12]="PRINTER=DeskJet-5740"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[15]="CUPS_SERVER=localhost"
D [20/Jul/2005:21:05:56 +0100] StartJob: envp[16]="IPP_PORT=631"
D [20/Jul/2005:21:05:56 +0100] StartJob: statusfds = [ 7 8 ]
D [20/Jul/2005:21:05:56 +0100] StartJob: filterfds[1] = [ 9 -1 ]
D [20/Jul/2005:21:05:56 +0100] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [20/Jul/2005:21:05:56 +0100] StartJob: filterfds[0] = [ 10 11 ]
D [20/Jul/2005:21:05:56 +0100] start_process("/usr/lib/cups/filter/pstops", 0xbfff0de0, 0xbfff0150, 9, 11, 8)
I [20/Jul/2005:21:05:56 +0100] Started filter /usr/lib/cups/filter/pstops (PID 3536) for job 130.
D [20/Jul/2005:21:05:56 +0100] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [20/Jul/2005:21:05:56 +0100] StartJob: filterfds[1] = [ 9 12 ]
D [20/Jul/2005:21:05:56 +0100] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbfff0de0, 0xbfff0150, 10, 12, 8)
I [20/Jul/2005:21:05:56 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 3537) for job 130.
D [20/Jul/2005:21:05:56 +0100] StartJob: backend = "/usr/lib/cups/backend/smb"
D [20/Jul/2005:21:05:56 +0100] StartJob: filterfds[0] = [ -1 10 ]
D [20/Jul/2005:21:05:56 +0100] start_process("/usr/lib/cups/backend/smb", 0xbfff0de0, 0xbfff0150, 9, 10, 8)
I [20/Jul/2005:21:05:56 +0100] Started backend /usr/lib/cups/backend/smb (PID 3538) for job 130.
D [20/Jul/2005:21:05:56 +0100] ProcessIPPRequest: 6 status_code=0
E [20/Jul/2005:21:05:56 +0100] PID 3538 stopped with status 22!
D [20/Jul/2005:21:05:56 +0100] [Job 130] perl: warning: Setting locale failed.
D [20/Jul/2005:21:05:56 +0100] [Job 130] perl: warning: Please check that your locale settings:
D [20/Jul/2005:21:05:56 +0100] [Job 130] LANGUAGE = (unset),
D [20/Jul/2005:21:05:56 +0100] [Job 130] LC_ALL = (unset),
D [20/Jul/2005:21:05:56 +0100] [Job 130] LANG = "en"
D [20/Jul/2005:21:05:56 +0100] [Job 130] are supported and installed on your system.
D [20/Jul/2005:21:05:56 +0100] [Job 130] perl: warning: Falling back to the standard locale ("C").
D [20/Jul/2005:21:05:56 +0100] [Job 130] /usr/lib/cups/backend/smb: No such file or directory
D [20/Jul/2005:21:05:56 +0100] ReadClient: 6 POST / HTTP/1.1
D [20/Jul/2005:21:05:56 +0100] ProcessIPPRequest: 6 status_code=1
D [20/Jul/2005:21:05:56 +0100] [Job 130] Page = 595x842; 10,36 to 585,833
D [20/Jul/2005:21:05:56 +0100] [Job 130] slowcollate=0, slowduplex=0, sloworder=0
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%BoundingBox: (atend)
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%Creator: OpenOffice.org 1.1.3
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%For: geoff
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%CreationDate: Wed Jul 20 21:02:28 2005
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%Title: cpag1.sxw
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%LanguageLevel: 3
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%DocumentData: Clean7Bit
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%Pages: (atend)
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%PageOrder: Ascend
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%EndComments
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%BeginProlog
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%BeginResource: procset PSPrint-Prolog 1.0 0
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%EndResource
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%EndProlog
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%BeginSetup
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%BeginResource: font NimbusRomNo9L-Regu
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%DocumentSuppliedResources: font NimbusRomNo9L-Regu
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%Title: NimbusRomNo9L-Regu
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%Version: 1.06
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%CreationDate: Sun Mar 27 19:14:25 2005
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%Creator: Dafydd Harries,,,
D [20/Jul/2005:21:05:56 +0100] [Job 130] 0 %%EndComments
D [20/Jul/2005:21:05:56 +0100] [Job 130] foomatic-rip version $Revision: 3.43.2.6 $ running...
D [20/Jul/2005:21:05:56 +0100] [Job 130] Parsing PPD file ...
D [20/Jul/2005:21:05:56 +0100] [Job 130] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [20/Jul/2005:21:05:56 +0100] [Job 130] Added option ColorSpace
D [20/Jul/2005:21:05:56 +0100] [Job 130] Added option Resolution
D [20/Jul/2005:21:05:56 +0100] [Job 130] Added option PageSize
D [20/Jul/2005:21:05:56 +0100] [Job 130] Added option PageRegion
D [20/Jul/2005:21:05:56 +0100] [Job 130] Added option Model
D [20/Jul/2005:21:05:56 +0100] [Job 130] Added option PrintoutMode
D [20/Jul/2005:21:05:57 +0100] [Job 130] Added option ImageableArea
D [20/Jul/2005:21:05:57 +0100] [Job 130] Added option PaperDimension
D [20/Jul/2005:21:05:57 +0100] [Job 130] Added option Duplex
D [20/Jul/2005:21:05:57 +0100] [Job 130] Added option Quality
D [20/Jul/2005:21:05:57 +0100] [Job 130] Added option Font
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] Parameter Summary
D [20/Jul/2005:21:05:57 +0100] [Job 130] -----------------
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] Spooler: cups
D [20/Jul/2005:21:05:57 +0100] [Job 130] Printer: DeskJet-5740
D [20/Jul/2005:21:05:57 +0100] [Job 130] PPD file: /etc/cups/ppd/DeskJet-5740.ppd
D [20/Jul/2005:21:05:57 +0100] [Job 130] Printer model: HP DeskJet 5740 Foomatic/hpijs (recommended)
D [20/Jul/2005:21:05:57 +0100] [Job 130] Job title: cpag1.sxw
D [20/Jul/2005:21:05:57 +0100] [Job 130] File(s) to be printed: 
D [20/Jul/2005:21:05:57 +0100] [Job 130] <STDIN>
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] ================================================
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] File: <STDIN>
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] ================================================
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] Reading PostScript input ...
D [20/Jul/2005:21:05:57 +0100] [Job 130] --> This document is DSC-conforming!
D [20/Jul/2005:21:05:57 +0100] [Job 130] Document created with OpenOffice.org 1.1.x
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] -----------
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%BeginProlog
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%EndProlog
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] -----------
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%BeginSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] Inserting PostScript code for CUPS' page accounting
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%BeginFeature: *PrintoutMode Normal
D [20/Jul/2005:21:05:57 +0100] [Job 130] Option: PrintoutMode=Normal --> Setting option
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [20/Jul/2005:21:05:57 +0100] [Job 130] Option: PrintoutMode=Normal --> Setting option
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%BeginFeature: *Quality FromPrintoutMode
D [20/Jul/2005:21:05:57 +0100] [Job 130] Option: Quality=FromPrintoutMode --> Setting option
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %% FoomaticRIPOptionSetting: Quality=@PrintoutMode
D [20/Jul/2005:21:05:57 +0100] [Job 130] Option: Quality=FromPrintoutMode --> Setting option
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%BeginFeature: *PageSize A4
D [20/Jul/2005:21:05:57 +0100] [Job 130] Option: PageSize=A4 --> Setting option
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %% FoomaticRIPOptionSetting: PageSize=A4
D [20/Jul/2005:21:05:57 +0100] [Job 130] Option: PageSize=A4 --> Setting option
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%BeginFeature: *Duplex None
D [20/Jul/2005:21:05:57 +0100] [Job 130] Option: Duplex=None --> Setting option
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %% FoomaticRIPOptionSetting: Duplex=None
D [20/Jul/2005:21:05:57 +0100] [Job 130] Option: Duplex=None --> Setting option
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%BeginResource: font OpenSymbolHGSet2
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%Creator: SunTypeTools-TT 1.0 gelf
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%EndResource
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%DocumentSuppliedResources: font NimbusRomNo9L-Regu
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%+ font OpenSymbolHGSet2
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%DocumentNeededResources: font Helvetica-Bold
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%+ font Helvetica
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%+ font Helvetica-Oblique
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%EndSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%Page: 1 1
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%Page: 1 1
D [20/Jul/2005:21:05:57 +0100] [Job 130] pw = 575.6, pl = 797.0
D [20/Jul/2005:21:05:57 +0100] [Job 130] PageLeft = 9.7, PageRight = 585.3
D [20/Jul/2005:21:05:57 +0100] [Job 130] PageTop = 833.0, PageBottom = 36.0
D [20/Jul/2005:21:05:57 +0100] [Job 130] PageWidth = 595.0, PageLength = 842.0
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%PageBoundingBox: 10 36 585 833
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%BeginPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%BeginFeature: *PageSize A4
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %% FoomaticRIPOptionSetting: PageSize=A4
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%EndFeature
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%EndPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%EndSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] -----------
D [20/Jul/2005:21:05:57 +0100] [Job 130] New page:  1 1
D [20/Jul/2005:21:05:57 +0100] [Job 130] Inserting option code into "PageSetup" section.
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%BeginPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%BeginFeature: *PageSize A4
D [20/Jul/2005:21:05:57 +0100] [Job 130] Option: PageSize=A4 --> Setting option
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %% FoomaticRIPOptionSetting: PageSize=A4
D [20/Jul/2005:21:05:57 +0100] [Job 130] Option: PageSize=A4 --> Setting option
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%EndPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] End of page header
D [20/Jul/2005:21:05:57 +0100] [Job 130] Stopping search for page header options
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found:
D [20/Jul/2005:21:05:57 +0100] [Job 130] 88 90 88 92 35 82 83 35 92 82 90 54 87 88 46 90 88 46 91 89 88 93 45 45 35 83 89
D [20/Jul/2005:21:05:57 +0100] [Job 130] --> Output goes directly to the renderer now.
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] Starting renderer
D [20/Jul/2005:21:05:57 +0100] [Job 130] JCL: <job data> 
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] renderer PID kid4=3545
D [20/Jul/2005:21:05:57 +0100] [Job 130] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5550" -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2 -dIjsUseOutputFD -sOutputFile=- -
D [20/Jul/2005:21:05:57 +0100] [Job 130] perl: warning: Setting locale failed.
D [20/Jul/2005:21:05:57 +0100] [Job 130] perl: warning: Please check that your locale settings:
D [20/Jul/2005:21:05:57 +0100] [Job 130] LANGUAGE = (unset),
D [20/Jul/2005:21:05:57 +0100] [Job 130] LC_ALL = (unset),
D [20/Jul/2005:21:05:57 +0100] [Job 130] LANG = "en"
D [20/Jul/2005:21:05:57 +0100] [Job 130] are supported and installed on your system.
D [20/Jul/2005:21:05:57 +0100] [Job 130] perl: warning: Falling back to the standard locale ("C").
D [20/Jul/2005:21:05:57 +0100] [Job 130] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=deskjet 5550' '-dDEVICEWIDTHPOINTS=595' '-dDEVICEHEIGHTPOINTS=842' '-dDuplex=false' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2' '-dIjsUseOutputFD' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%PageTrailer
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%Page: 2 2
D [20/Jul/2005:21:05:57 +0100] [Job 130] pw = 575.6, pl = 797.0
D [20/Jul/2005:21:05:57 +0100] [Job 130] PageLeft = 9.7, PageRight = 585.3
D [20/Jul/2005:21:05:57 +0100] [Job 130] PageTop = 833.0, PageBottom = 36.0
D [20/Jul/2005:21:05:57 +0100] [Job 130] PageWidth = 595.0, PageLength = 842.0
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%PageBoundingBox: 10 36 585 833
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%BeginPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%EndPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] -----------
D [20/Jul/2005:21:05:57 +0100] [Job 130] New page:  2 2
D [20/Jul/2005:21:05:57 +0100] [Job 130] Inserting option code into "PageSetup" section.
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found:
D [20/Jul/2005:21:05:57 +0100] [Job 130] %%Page: 2 2
D [20/Jul/2005:21:05:57 +0100] [Job 130] --> Output goes to the FIFO buffer now.
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%BeginPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%EndPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] End of page header
D [20/Jul/2005:21:05:57 +0100] [Job 130] Stopping search for page header options
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found:
D [20/Jul/2005:21:05:57 +0100] [Job 130] 616C2077657265206F6E6C7920636F6E6365726E656420776974682074686520736974756174696F
D [20/Jul/2005:21:05:57 +0100] [Job 130] --> Output goes directly to the renderer now.
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%PageTrailer
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%Page: 3 3
D [20/Jul/2005:21:05:57 +0100] [Job 130] pw = 575.6, pl = 797.0
D [20/Jul/2005:21:05:57 +0100] [Job 130] PageLeft = 9.7, PageRight = 585.3
D [20/Jul/2005:21:05:57 +0100] [Job 130] PageTop = 833.0, PageBottom = 36.0
D [20/Jul/2005:21:05:57 +0100] [Job 130] PageWidth = 595.0, PageLength = 842.0
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%PageBoundingBox: 10 36 585 833
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%BeginPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] 0 %%EndPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] -----------
D [20/Jul/2005:21:05:57 +0100] [Job 130] New page:  3 3
D [20/Jul/2005:21:05:57 +0100] [Job 130] Inserting option code into "PageSetup" section.
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found:
D [20/Jul/2005:21:05:57 +0100] [Job 130] %%Page: 3 3
D [20/Jul/2005:21:05:57 +0100] [Job 130] --> Output goes to the FIFO buffer now.
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%BeginPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found: %%EndPageSetup
D [20/Jul/2005:21:05:57 +0100] [Job 130] End of page header
D [20/Jul/2005:21:05:57 +0100] [Job 130] Stopping search for page header options
D [20/Jul/2005:21:05:57 +0100] [Job 130] Found:
D [20/Jul/2005:21:05:57 +0100] [Job 130] <4966204349532F343334382F3230303320697320636F72726563742C207468656E206120747769
D [20/Jul/2005:21:05:57 +0100] [Job 130] --> Output goes directly to the renderer now.
D [20/Jul/2005:21:05:57 +0100] [Job 130] 
D [20/Jul/2005:21:05:58 +0100] [Job 130] 0 %%PageTrailer
D [20/Jul/2005:21:05:58 +0100] [Job 130] 0 %%Trailer
D [20/Jul/2005:21:05:58 +0100] [Job 130] Saw Trailer!
D [20/Jul/2005:21:05:58 +0100] [Job 130] Saw EOF!
D [20/Jul/2005:21:05:58 +0100] [Job 130] 
D [20/Jul/2005:21:05:58 +0100] [Job 130] Closing renderer
D [20/Jul/2005:21:05:58 +0100] ReadClient: 6 POST / HTTP/1.1
D [20/Jul/2005:21:05:58 +0100] ProcessIPPRequest: 6 status_code=0
D [20/Jul/2005:21:05:58 +0100] ReadClient: 6 POST / HTTP/1.1
D [20/Jul/2005:21:05:58 +0100] ProcessIPPRequest: 6 status_code=1
D [20/Jul/2005:21:05:58 +0100] ReadClient: 6 POST / HTTP/1.1
D [20/Jul/2005:21:05:58 +0100] ProcessIPPRequest: 6 status_code=1
D [20/Jul/2005:21:05:58 +0100] [Job 130] Process dying with "error closing *main::STDOUT", exit stat: 9
D [20/Jul/2005:21:05:58 +0100] [Job 130] error closing *main::STDOUT
D [20/Jul/2005:21:05:58 +0100] [Job 130] KID4 exited with status 9
D [20/Jul/2005:21:05:58 +0100] [Job 130] Renderer exit stat: 9
D [20/Jul/2005:21:05:58 +0100] [Job 130] KID3 finished
D [20/Jul/2005:21:05:58 +0100] [Job 130] Renderer process finished
D [20/Jul/2005:21:05:58 +0100] [Job 130] Killing process 3544 (KID3)
D [20/Jul/2005:21:05:58 +0100] [Job 130] Process dying with "Error closing renderer", exit stat: 9
D [20/Jul/2005:21:05:58 +0100] [Job 130] Error closing renderer
E [20/Jul/2005:21:05:58 +0100] PID 3537 stopped with status 9!
D [20/Jul/2005:21:05:58 +0100] UpdateJob: job 130, file 0 is complete.
D [20/Jul/2005:21:05:58 +0100] StopJob: id = 130, force = 0
I [20/Jul/2005:21:05:58 +0100] Saving printers.conf...
D [20/Jul/2005:21:05:58 +0100] StopJob: printer state is 5[/PHP]

I'm aware I've got a problem with locales but now think my main problems may be with STDOUT and renderer whatever they are? I have used find but neither seems to exist anywhere on my system.

Can anyone help? Thanks

Geoff

---

