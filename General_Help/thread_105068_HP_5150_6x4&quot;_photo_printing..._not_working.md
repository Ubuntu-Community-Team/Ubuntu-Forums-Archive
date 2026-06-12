---
title: "HP 5150 6x4&quot; photo printing... not working"
date: 2005-12-17
forum: General Help
---

### Post by alex-weej on 2005-12-17
Can print using A4 settings, letter, etc. fine, through GNOME-print.

If I choose 6x4 inch photo paper it just does nothing at all. No warnings, no errors.

Luckily I know sort of what I'm doing so I checked the CUPS error log and raised the log level to debug. God knows how "Mom and Pops" are supposed to do this but hey...

```
D [17/Dec/2005:19:41:35 +0000] ReadClient: 7 POST /printers/DeskJet-5150 HTTP/1.1
D [17/Dec/2005:19:41:35 +0000] print_job: auto-typing file...
D [17/Dec/2005:19:41:35 +0000] print_job: request file type is application/postscript.
D [17/Dec/2005:19:41:35 +0000] check_quotas: requesting-user-name = 'alex'
D [17/Dec/2005:19:41:35 +0000] print_job: requesting-user-name = 'alex'
D [17/Dec/2005:19:41:35 +0000] Adding default job-sheets values "none,none"...
I [17/Dec/2005:19:41:35 +0000] Adding start banner page "none" to job 73.
I [17/Dec/2005:19:41:35 +0000] Adding end banner page "none" to job 73.
I [17/Dec/2005:19:41:35 +0000] Job 73 queued on 'DeskJet-5150' by 'alex'.
D [17/Dec/2005:19:41:35 +0000] Job 73 hold_until = 0
D [17/Dec/2005:19:41:35 +0000] StartJob(73, 0x828b7a8)
D [17/Dec/2005:19:41:35 +0000] StartJob() id = 73, file = 0/1
D [17/Dec/2005:19:41:35 +0000] job-sheets=none,none
D [17/Dec/2005:19:41:35 +0000] banner_page = 0
D [17/Dec/2005:19:41:35 +0000] StartJob: argv = "DeskJet-5150","73","alex","","1","","/var/spool/cups/d00073-001"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[2]="USER=root"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[3]="CHARSET=utf-8"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[4]="LANG=en"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[5]="TZ=Europe/London"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[6]="PPD=/etc/cups/ppd/DeskJet-5150.ppd"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[11]="DEVICE_URI=hp:/usb/deskjet_5100?serial=MY41F4P10Q7A"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[12]="PRINTER=DeskJet-5150"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[15]="CUPS_SERVER=localhost"
D [17/Dec/2005:19:41:35 +0000] StartJob: envp[16]="IPP_PORT=631"
D [17/Dec/2005:19:41:35 +0000] StartJob: statusfds = [ 8 9 ]
D [17/Dec/2005:19:41:35 +0000] StartJob: filterfds[1] = [ 11 -1 ]
D [17/Dec/2005:19:41:35 +0000] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [17/Dec/2005:19:41:35 +0000] StartJob: filterfds[0] = [ 12 13 ]
D [17/Dec/2005:19:41:35 +0000] start_process("/usr/lib/cups/filter/pstops", 0xbf83cd60, 0xbf83c2d8, 11, 13, 9)
I [17/Dec/2005:19:41:35 +0000] Started filter /usr/lib/cups/filter/pstops (PID 9142) for job 73.
D [17/Dec/2005:19:41:35 +0000] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [17/Dec/2005:19:41:35 +0000] StartJob: filterfds[1] = [ 11 14 ]
D [17/Dec/2005:19:41:35 +0000] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbf83cd60, 0xbf83c2d8, 12, 14, 9)
I [17/Dec/2005:19:41:35 +0000] Started filter /usr/lib/cups/filter/foomatic-rip (PID 9143) for job 73.
D [17/Dec/2005:19:41:35 +0000] StartJob: backend = "/usr/lib/cups/backend/hp"
D [17/Dec/2005:19:41:35 +0000] StartJob: filterfds[0] = [ -1 12 ]
D [17/Dec/2005:19:41:35 +0000] start_process("/usr/lib/cups/backend/hp", 0xbf83cd60, 0xbf83c2d8, 11, 12, 9)
I [17/Dec/2005:19:41:35 +0000] Started backend /usr/lib/cups/backend/hp (PID 9144) for job 73.
D [17/Dec/2005:19:41:35 +0000] ProcessIPPRequest: 7 status_code=0
D [17/Dec/2005:19:41:35 +0000] [Job 73] perl: warning: Setting locale failed.
D [17/Dec/2005:19:41:35 +0000] [Job 73] perl: warning: Please check that your locale settings:
D [17/Dec/2005:19:41:35 +0000] [Job 73] LANGUAGE = (unset),
D [17/Dec/2005:19:41:35 +0000] [Job 73] LC_ALL = (unset),
D [17/Dec/2005:19:41:35 +0000] [Job 73] LANG = "en"
D [17/Dec/2005:19:41:35 +0000] [Job 73] are supported and installed on your system.
D [17/Dec/2005:19:41:35 +0000] [Job 73] perl: warning: Falling back to the standard locale ("C").
D [17/Dec/2005:19:41:36 +0000] [Job 73] Page = 595x842; 10,36 to 585,833
D [17/Dec/2005:19:41:36 +0000] [Job 73] slowcollate=0, slowduplex=0, sloworder=0
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%Creator: Gnome Print Version 2.12.1
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%CreationDate: D:20051217194134
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%LanguageLevel: 2
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%DocumentMedia: Regular 288 432 0 () ()
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%Orientation: Portrait
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%BoundingBox: 0 0 288 432
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%Pages: 1
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%PageOrder: Ascend
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%Title: 
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%DocumentSuppliedResources: procset pnome-print-procs-2.12.1
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%Requirements: numcopies(1)
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%EndComments
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%BeginDefaults
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%PageMedia: Regular
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%EndDefaults
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%BeginProlog
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%BeginResource: procset gnome-print-procs-2.12.1
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%EndResource
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%EndProlog
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%BeginSetup
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%EndSetup
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%Page: F-Spot/home/alex/Pictures/Img0095.jpg 1
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%Page: F-Spot/home/alex/Pictures/Img0095.jpg 1
D [17/Dec/2005:19:41:36 +0000] [Job 73] pw = 575.6, pl = 797.0
D [17/Dec/2005:19:41:36 +0000] [Job 73] PageLeft = 9.7, PageRight = 585.3
D [17/Dec/2005:19:41:36 +0000] [Job 73] PageTop = 833.0, PageBottom = 36.0
D [17/Dec/2005:19:41:36 +0000] [Job 73] PageWidth = 595.0, PageLength = 842.0
D [17/Dec/2005:19:41:36 +0000] [Job 73] 0 %%%%PageResources: (atend)
D [17/Dec/2005:19:41:37 +0000] ReadClient: 10 POST / HTTP/1.1
D [17/Dec/2005:19:41:37 +0000] ProcessIPPRequest: 10 status_code=1
D [17/Dec/2005:19:41:37 +0000] ReadClient: 10 POST / HTTP/1.1
D [17/Dec/2005:19:41:37 +0000] ProcessIPPRequest: 10 status_code=1
D [17/Dec/2005:19:41:37 +0000] ReadClient: 4 POST / HTTP/1.1
D [17/Dec/2005:19:41:37 +0000] ProcessIPPRequest: 4 status_code=0
D [17/Dec/2005:19:41:38 +0000] [Job 73] foomatic-rip version $Revision: 3.43.2.11 $ running...
D [17/Dec/2005:19:41:38 +0000] [Job 73] Parsing PPD file ...
D [17/Dec/2005:19:41:38 +0000] [Job 73] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option ColorSpace
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option Resolution
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option PageSize
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option PageRegion
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option Model
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option PrintoutMode
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option ImageableArea
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option PaperDimension
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option InputSlot
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option Duplex
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option Quality
D [17/Dec/2005:19:41:38 +0000] [Job 73] Added option Font
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] Parameter Summary
D [17/Dec/2005:19:41:38 +0000] [Job 73] -----------------
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] Spooler: cups
D [17/Dec/2005:19:41:38 +0000] [Job 73] Printer: DeskJet-5150
D [17/Dec/2005:19:41:38 +0000] [Job 73] PPD file: /etc/cups/ppd/DeskJet-5150.ppd
D [17/Dec/2005:19:41:38 +0000] [Job 73] Printer model: HP DeskJet 5150 Foomatic/hpijs (recommended)
D [17/Dec/2005:19:41:38 +0000] [Job 73] Job title: 
D [17/Dec/2005:19:41:38 +0000] [Job 73] File(s) to be printed: 
D [17/Dec/2005:19:41:38 +0000] [Job 73] <STDIN>
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] ================================================
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] File: <STDIN>
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] ================================================
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] Reading PostScript input ...
D [17/Dec/2005:19:41:38 +0000] [Job 73] --> This document is DSC-conforming!
D [17/Dec/2005:19:41:38 +0000] [Job 73] Job claims to be DSC-conforming, but "%%BeginProlog" was missing before first line with another "%%Begin..." comment (is this a TeX/LaTeX/dvips-generated PostScript file?). Assuming start of "Prolog" here.
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] -----------
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %%BeginProlog
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %%EndProlog
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] -----------
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %%BeginSetup
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %%BeginFeature: *PrintoutMode Normal
D [17/Dec/2005:19:41:38 +0000] [Job 73] Option: PrintoutMode=Normal --> Setting option
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %% FoomaticRIPOptionSetting: PrintoutMode=Normal
D [17/Dec/2005:19:41:38 +0000] [Job 73] Option: PrintoutMode=Normal --> Setting option
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %%BeginFeature: *InputSlot Default
D [17/Dec/2005:19:41:38 +0000] [Job 73] Option: InputSlot=Default --> Setting option
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %% FoomaticRIPOptionSetting: InputSlot=Default
D [17/Dec/2005:19:41:38 +0000] [Job 73] Option: InputSlot=Default --> Setting option
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %%BeginFeature: *Quality FromPrintoutMode
D [17/Dec/2005:19:41:38 +0000] [Job 73] Option: Quality=FromPrintoutMode --> Setting option
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %% FoomaticRIPOptionSetting: Quality=@PrintoutMode
D [17/Dec/2005:19:41:38 +0000] [Job 73] Option: Quality=FromPrintoutMode --> Setting option
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %%BeginFeature: *PageRegion A4
D [17/Dec/2005:19:41:38 +0000] [Job 73] Option: PageRegion=A4 --> Option will be set by PostScript interpreter
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %% FoomaticRIPOptionSetting: PageSize=A4
D [17/Dec/2005:19:41:38 +0000] [Job 73] Option: PageSize=A4 --> Setting option
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %%BeginFeature: *Duplex None
D [17/Dec/2005:19:41:38 +0000] [Job 73] Option: Duplex=None --> Setting option
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %% FoomaticRIPOptionSetting: Duplex=None
D [17/Dec/2005:19:41:38 +0000] [Job 73] Option: Duplex=None --> Setting option
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found: %%EndSetup
D [17/Dec/2005:19:41:38 +0000] [Job 73] Inserting PostScript code for CUPS' page accounting
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] -----------
D [17/Dec/2005:19:41:38 +0000] [Job 73] New page:  1 1
D [17/Dec/2005:19:41:38 +0000] [Job 73] Inserting option code into "PageSetup" section.
D [17/Dec/2005:19:41:38 +0000] [Job 73] No page header or page header not DSC-conforming
D [17/Dec/2005:19:41:38 +0000] [Job 73] Stopping search for page header options
D [17/Dec/2005:19:41:38 +0000] [Job 73] Found:
D [17/Dec/2005:19:41:38 +0000] [Job 73] 59574b5c5a4e5b594d59554a595549605a4c625c4e635b4e61574b60564a645a4e645c4f625a4d63
D [17/Dec/2005:19:41:38 +0000] [Job 73] --> Output goes directly to the renderer now.
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] Starting renderer
D [17/Dec/2005:19:41:38 +0000] [Job 73] JCL: <job data> 
D [17/Dec/2005:19:41:38 +0000] [Job 73] 
D [17/Dec/2005:19:41:38 +0000] [Job 73] renderer PID kid4=9147
D [17/Dec/2005:19:41:38 +0000] [Job 73] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5550" -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=- -
D [17/Dec/2005:19:41:38 +0000] [Job 73] perl: warning: Setting locale failed.
D [17/Dec/2005:19:41:38 +0000] [Job 73] perl: warning: Please check that your locale settings:
D [17/Dec/2005:19:41:38 +0000] [Job 73] LANGUAGE = (unset),
D [17/Dec/2005:19:41:38 +0000] [Job 73] LC_ALL = (unset),
D [17/Dec/2005:19:41:38 +0000] [Job 73] LANG = "en"
D [17/Dec/2005:19:41:38 +0000] [Job 73] are supported and installed on your system.
D [17/Dec/2005:19:41:38 +0000] [Job 73] perl: warning: Falling back to the standard locale ("C").
D [17/Dec/2005:19:41:38 +0000] [Job 73] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=deskjet 5550' '-dDEVICEWIDTHPOINTS=595' '-dDEVICEHEIGHTPOINTS=842' '-dDuplex=false' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7' '-dIjsUseOutputFD' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [17/Dec/2005:19:41:39 +0000] [Job 73] unable to read client data err=-2
D [17/Dec/2005:19:41:39 +0000] [Job 73] sh: line 1:  9149 Segmentation fault      gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=ijs' '-sIjsServer=hpijs' '-sDeviceManufacturer=HEWLETT-PACKARD' '-sDeviceModel=deskjet 5550' '-dDEVICEWIDTHPOINTS=595' '-dDEVICEHEIGHTPOINTS=842' '-dDuplex=false' '-r300' '-sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7' '-dIjsUseOutputFD' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [17/Dec/2005:19:41:39 +0000] [Job 73] renderer return value: 139
D [17/Dec/2005:19:41:39 +0000] [Job 73] renderer received signal: 139
D [17/Dec/2005:19:41:39 +0000] [Job 73] Process dying with "The renderer may have dumped core.", exit stat: 3
D [17/Dec/2005:19:41:39 +0000] [Job 73] error: Illegal seek (29)
D [17/Dec/2005:19:41:39 +0000] [Job 73] The renderer may have dumped core.
D [17/Dec/2005:19:41:40 +0000] ReadClient: 5 POST / HTTP/1.1
D [17/Dec/2005:19:41:40 +0000] ProcessIPPRequest: 5 status_code=0
D [17/Dec/2005:19:41:40 +0000] ReadClient: 5 POST / HTTP/1.1
D [17/Dec/2005:19:41:40 +0000] ProcessIPPRequest: 5 status_code=1
D [17/Dec/2005:19:41:40 +0000] ReadClient: 6 POST / HTTP/1.1
D [17/Dec/2005:19:41:40 +0000] ProcessIPPRequest: 6 status_code=0
D [17/Dec/2005:19:41:40 +0000] ReadClient: 6 POST / HTTP/1.1
D [17/Dec/2005:19:41:40 +0000] ProcessIPPRequest: 6 status_code=1
D [17/Dec/2005:19:41:40 +0000] [Job 73] tail process done writing data to STDOUT
D [17/Dec/2005:19:41:40 +0000] [Job 73] KID4 finished
D [17/Dec/2005:19:41:42 +0000] [Job 73] 0 %%%%PageTrailer
D [17/Dec/2005:19:41:42 +0000] [Job 73] 0 %%PageResources: procset gnome-print-procs-2.12.1
D [17/Dec/2005:19:41:42 +0000] [Job 73] 0 %%Trailer
D [17/Dec/2005:19:41:42 +0000] [Job 73] Saw Trailer!
D [17/Dec/2005:19:41:42 +0000] [Job 73] Saw EOF!
D [17/Dec/2005:19:41:42 +0000] [Job 73] 
D [17/Dec/2005:19:41:42 +0000] [Job 73] Closing renderer
D [17/Dec/2005:19:41:42 +0000] [Job 73] KID3 exited with status 3
D [17/Dec/2005:19:41:42 +0000] [Job 73] Renderer exit stat: 3
D [17/Dec/2005:19:41:42 +0000] [Job 73] Renderer process finished
D [17/Dec/2005:19:41:42 +0000] [Job 73] Killing process 9146 (KID3)
D [17/Dec/2005:19:41:42 +0000] [Job 73] Process dying with "Error closing renderer", exit stat: 3
D [17/Dec/2005:19:41:42 +0000] [Job 73] error: Illegal seek (29)
D [17/Dec/2005:19:41:42 +0000] [Job 73] Error closing renderer
E [17/Dec/2005:19:41:42 +0000] PID 9143 stopped with status 3!
```

What the f...

Why do I even have to *think* about this? :(

Any ideas, chaps? Cheers.

Alex

---

### Post by alex-weej on 2005-12-21
Top :(

---

### Post by bigzak on 2005-12-21
The problem is related to ghostscript - for some reason it is segfaulting while rendering the page.

Can you grab a similar log from a successful A4 print job? If you get the line starting foomatic-gswrapper, you can check what command line parameters change in the call to ghostscript. This might lead to a revelation moment (!) or at least open an avenue of investigation.

---

