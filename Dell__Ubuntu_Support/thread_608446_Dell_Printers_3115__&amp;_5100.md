---
title: "Dell Printers 3115  &amp; 5100"
date: 2007-11-10
forum: Dell  Ubuntu Support
---

### Post by mptpro on 2007-11-10
Hello I just switched from Windows and one of the few things still baffeling me is connecting to my Dell Printers.

I have a 3115cn laser network printer

and a

5100 printer.

I have searched these forums, dell forums and called dell tech support to no avail.

Anyone have any help locating drivers for these printer or a workaround?

thanks.

using Ubuntu 7.1

---

### Post by linuxwizard on 2007-11-10
Both printers should work. classified as Mostly Works.

This shows that drivers are on printer cd.
[http://www.openprinting.org/show_printer.cgi?recnum=Dell-3115cn_AIO](http://www.openprinting.org/show_printer.cgi?recnum=Dell-3115cn_AIO)

This shows you need the  PostScript driver.
[http://www.openprinting.org/show_printer.cgi?recnum=Dell-5100CN](http://www.openprinting.org/show_printer.cgi?recnum=Dell-5100CN)

Dell printers are not very well supported in Linux and most does not work. They are made by Lexmark which does not support Linux.

---

### Post by mptpro on 2007-11-10
Thank you.

It says that the driver is on the cd,  However, I found no .deb packages, and Dell web site they list only suse and RH for linux, no mention of debian or ubuntu (even though dell sell ubuntu linux!)

If anyone knows how to install these, I would appreciate it!

thanks again for the links!

---

### Post by nailbnny on 2007-11-15
I got our networked 3115cn to print by using a German/Dutch(?) .ppd that I found using google.  It works, but some of the menu options are in a non-English language.  Forgive me if someone finds this a bit spammy!

Hope this helps:
(Copy this into a file named dl3115cn.ppd)

```

*PPD-Adobe: "4.3"
*% Adobe Systems PostScript(R) Printer Description File
*% Copyright 1987-1996 Adobe Systems Incorporated.
*% All Rights Reserved.
*% Permission is granted for redistribution of this file as
*% long as this copyright notice is intact and the contents
*% of the file is not altered in any way from its original form.
*% End of Copyright statement
*FileVersion: "1.0"
*FormatVersion: "4.3"
*LanguageEncoding: ISOLatin1
*LanguageVersion: Dutch
*Manufacturer: "Dell"
*PCFileName: "DL3115CN.PPD"
*Product: "(MFP Laser 3115cn)"
*PSVersion: "(3015.103) 1"
*ShortNickName: "Dell MFP Laser 3115cn PS"
*ModelName: "Dell MFP Laser 3115cn v3015.103 PS"
*NickName: "Dell MFP Laser 3115cn v3015.103 PS"

*% === Options and Constraints =========
*OpenGroup: InstallableOptions/Opties ge<EF>nstalleerd
*OpenUI *InstalledMemory/Geheugencapaciteit: PickOne
*DefaultInstalledMemory: 128Meg
*InstalledMemory 128Meg/Standaard 128 MB: ""
*InstalledMemory 384Meg/384 MB: ""
*InstalledMemory 640Meg/640 MB: ""
*InstalledMemory 1152Meg/1152 MB: ""
*?InstalledMemory: "
    save
    (Unknown) currentsystemparams /RamSize get
    dup 134217728 eq{exch pop (128Meg) exch}if
    dup 402653184 eq{exch pop (384Meg) exch}if
    dup 671088640 eq{exch pop (640Meg) exch}if
    dup 1207959552 eq{exch pop (1152Meg) exch}if
    pop = flush
    restore
"
*End
*CloseUI: *InstalledMemory

*OpenUI *Option1/Papierladeconfiguratie: PickOne
*DefaultOption1: None
*Option1 None/Niet aanwezig: ""
*Option1 1TrayModule/2-Lademodule: ""
*?Option1: "
    save
    currentpagedevice /InputAttributes get dup null eq
    { pop (Unknown) }
    { 1 known
        { (1TrayModule) }{(None)} ifelse
    } ifelse = flush
    restore
"
*End
*CloseUI: *Option1

*OpenUI *Option2/Opslagapparaat: PickOne
*DefaultOption2: None
*Option2 None/Niet aanwezig: ""
*Option2 RAMDisk/RAM-schijf: ""
*?Option2: "
  save
  /FXProcs /ProcSet resourcestatus {
    pop pop /FXProcs /ProcSet findresource /currentstorage get exec
    {(RAMDisk)}{(None)} ifelse
  } {(Unknown)} ifelse = flush
  restore
"
*End
*CloseUI: *Option2

*OpenUI *Option3/Dubbelzijdige module: Boolean
*DefaultOption3: False
*Option3 False/Niet aanwezig: ""
*Option3 True/Aanwezig: ""
*?Option3: "
    save
    currentpagedevice
    /Duplex known {(True)}{(False)} ifelse = flush
    restore
"
*End
*CloseUI: *Option3

*CloseGroup: InstallableOptions

*% ==== UIConstraints ===============
*% ==== OptionTray vs InputSlot ====
*UIConstraints: *Option1 None *InputSlot 2ndTray
*UIConstraints: *InputSlot 2ndTray *Option1 None

*% ==== OptionTray vs SlipSheetTray ====
*UIConstraints: *Option1 None *DLSlipSheetTray 2ndTray
*UIConstraints: *DLSlipSheetTray 2ndTray *Option1 None

*% ==== OptionDuplex vs Duplex ====
*UIConstraints: *Option3 False *Duplex DuplexNoTumble
*UIConstraints: *Option3 False *Duplex DuplexTumble
*UIConstraints: *Duplex DuplexNoTumble *Option3 False
*UIConstraints: *Duplex DuplexTumble *Option3 False

*% ==== StorageDevice vs Collate ====
*UIConstraints: *Option2 None *Collate True
*UIConstraints: *Collate True *Option2 None

*% ==== PageSize vs InputSlot ====
*UIConstraints: *PageSize Env10 *InputSlot 1stTray
*UIConstraints: *PageSize Env10 *InputSlot 2ndTray
*UIConstraints: *PageSize Env10 *ManualFeed False
*UIConstraints: *PageSize EnvMonarch *InputSlot 1stTray
*UIConstraints: *PageSize EnvMonarch *InputSlot 2ndTray
*UIConstraints: *PageSize EnvMonarch *ManualFeed False
*UIConstraints: *PageSize EnvC5 *InputSlot 1stTray
*UIConstraints: *PageSize EnvC5 *InputSlot 2ndTray
*UIConstraints: *PageSize EnvC5 *ManualFeed False
*UIConstraints: *PageSize EnvDL *InputSlot 1stTray
*UIConstraints: *PageSize EnvDL *InputSlot 2ndTray
*UIConstraints: *PageSize EnvDL *ManualFeed False
*UIConstraints: *PageRegion Env10 *InputSlot 1stTray
*UIConstraints: *PageRegion Env10 *InputSlot 2ndTray
*UIConstraints: *PageRegion Env10 *ManualFeed False
*UIConstraints: *PageRegion EnvMonarch *InputSlot 1stTray
*UIConstraints: *PageRegion EnvMonarch *InputSlot 2ndTray
*UIConstraints: *PageRegion EnvMonarch *ManualFeed False
*UIConstraints: *PageRegion EnvC5 *InputSlot 1stTray
*UIConstraints: *PageRegion EnvC5 *InputSlot 2ndTray
*UIConstraints: *PageRegion EnvC5 *ManualFeed False
*UIConstraints: *PageRegion EnvDL *InputSlot 1stTray
*UIConstraints: *PageRegion EnvDL *InputSlot 2ndTray
*UIConstraints: *PageRegion EnvDL *ManualFeed False
*UIConstraints: *InputSlot 1stTray *PageSize Env10
*UIConstraints: *InputSlot 2ndTray *PageSize Env10
*UIConstraints: *ManualFeed False *PageSize Env10
*UIConstraints: *InputSlot 1stTray *PageSize EnvMonarch
*UIConstraints: *InputSlot 2ndTray *PageSize EnvMonarch
*UIConstraints: *ManualFeed False *PageSize EnvMonarch
*UIConstraints: *InputSlot 1stTray *PageSize EnvC5
*UIConstraints: *InputSlot 2ndTray *PageSize EnvC5
*UIConstraints: *ManualFeed False *PageSize EnvC5
*UIConstraints: *InputSlot 1stTray *PageSize EnvDL
*UIConstraints: *InputSlot 2ndTray *PageSize EnvDL
*UIConstraints: *ManualFeed False *PageSize EnvDL
*UIConstraints: *InputSlot 1stTray *PageRegion Env10
*UIConstraints: *InputSlot 2ndTray *PageRegion Env10
*UIConstraints: *ManualFeed False *PageRegion Env10
*UIConstraints: *InputSlot 1stTray *PageRegion EnvMonarch
*UIConstraints: *InputSlot 2ndTray *PageRegion EnvMonarch
*UIConstraints: *ManualFeed False *PageRegion EnvMonarch
*UIConstraints: *InputSlot 1stTray *PageRegion EnvC5
*UIConstraints: *InputSlot 2ndTray *PageRegion EnvC5
*UIConstraints: *ManualFeed False *PageRegion EnvC5
*UIConstraints: *InputSlot 1stTray *PageRegion EnvDL
*UIConstraints: *InputSlot 2ndTray *PageRegion EnvDL
*UIConstraints: *ManualFeed False *PageRegion EnvDL

*% ==== PageSize vs Duplex ====
*UIConstraints: *PageSize Env10 *Duplex DuplexNoTumble
*UIConstraints: *PageSize Env10 *Duplex DuplexTumble
*UIConstraints: *PageSize EnvMonarch *Duplex DuplexNoTumble
*UIConstraints: *PageSize EnvMonarch *Duplex DuplexTumble
*UIConstraints: *PageSize EnvC5 *Duplex DuplexNoTumble
*UIConstraints: *PageSize EnvC5 *Duplex DuplexTumble
*UIConstraints: *PageSize EnvDL *Duplex DuplexNoTumble
*UIConstraints: *PageSize EnvDL *Duplex DuplexTumble
*UIConstraints: *PageRegion Env10 *Duplex DuplexNoTumble
*UIConstraints: *PageRegion Env10 *Duplex DuplexTumble
*UIConstraints: *PageRegion EnvMonarch *Duplex DuplexNoTumble
*UIConstraints: *PageRegion EnvMonarch *Duplex DuplexTumble
*UIConstraints: *PageRegion EnvC5 *Duplex DuplexNoTumble
*UIConstraints: *PageRegion EnvC5 *Duplex DuplexTumble
*UIConstraints: *PageRegion EnvDL *Duplex DuplexNoTumble
*UIConstraints: *PageRegion EnvDL *Duplex DuplexTumble
*UIConstraints: *Duplex DuplexNoTumble *PageSize Env10
*UIConstraints: *Duplex DuplexTumble *PageSize Env10
*UIConstraints: *Duplex DuplexNoTumble *PageSize EnvMonarch
*UIConstraints: *Duplex DuplexTumble *PageSize EnvMonarch
*UIConstraints: *Duplex DuplexNoTumble *PageSize EnvC5
*UIConstraints: *Duplex DuplexTumble *PageSize EnvC5
*UIConstraints: *Duplex DuplexNoTumble *PageSize EnvDL
*UIConstraints: *Duplex DuplexTumble *PageSize EnvDL
*UIConstraints: *Duplex DuplexNoTumble *PageRegion Env10
*UIConstraints: *Duplex DuplexTumble *PageRegion Env10
*UIConstraints: *Duplex DuplexNoTumble *PageRegion EnvMonarch
*UIConstraints: *Duplex DuplexTumble *PageRegion EnvMonarch
*UIConstraints: *Duplex DuplexNoTumble *PageRegion EnvC5
*UIConstraints: *Duplex DuplexTumble *PageRegion EnvC5
*UIConstraints: *Duplex DuplexNoTumble *PageRegion EnvDL
*UIConstraints: *Duplex DuplexTumble *PageRegion EnvDL

*% ==== PageSize vs SlipSheetTray ====
*UIConstraints: *PageSize Env10 *DLSlipSheetTray 1stTray
*UIConstraints: *PageSize Env10 *DLSlipSheetTray 2ndTray
*UIConstraints: *PageSize Env10 *DLSlipSheetTray AutoTray
*UIConstraints: *PageSize EnvMonarch *DLSlipSheetTray 1stTray
*UIConstraints: *PageSize EnvMonarch *DLSlipSheetTray 2ndTray
*UIConstraints: *PageSize EnvMonarch *DLSlipSheetTray AutoTray
*UIConstraints: *PageSize EnvC5 *DLSlipSheetTray 1stTray
*UIConstraints: *PageSize EnvC5 *DLSlipSheetTray 2ndTray
*UIConstraints: *PageSize EnvC5 *DLSlipSheetTray AutoTray
*UIConstraints: *PageSize EnvDL *DLSlipSheetTray 1stTray
*UIConstraints: *PageSize EnvDL *DLSlipSheetTray 2ndTray
*UIConstraints: *PageSize EnvDL *DLSlipSheetTray AutoTray
*UIConstraints: *PageRegion Env10 *DLSlipSheetTray 1stTray
*UIConstraints: *PageRegion Env10 *DLSlipSheetTray 2ndTray
*UIConstraints: *PageRegion Env10 *DLSlipSheetTray AutoTray
*UIConstraints: *PageRegion EnvMonarch *DLSlipSheetTray 1stTray
*UIConstraints: *PageRegion EnvMonarch *DLSlipSheetTray 2ndTray
*UIConstraints: *PageRegion EnvMonarch *DLSlipSheetTray AutoTray
*UIConstraints: *PageRegion EnvC5 *DLSlipSheetTray 1stTray
*UIConstraints: *PageRegion EnvC5 *DLSlipSheetTray 2ndTray
*UIConstraints: *PageRegion EnvC5 *DLSlipSheetTray AutoTray
*UIConstraints: *PageRegion EnvDL *DLSlipSheetTray 1stTray
*UIConstraints: *PageRegion EnvDL *DLSlipSheetTray 2ndTray
*UIConstraints: *PageRegion EnvDL *DLSlipSheetTray AutoTray
*UIConstraints: *DLSlipSheetTray 1stTray *PageSize Env10
*UIConstraints: *DLSlipSheetTray 2ndTray *PageSize Env10
*UIConstraints: *DLSlipSheetTray AutoTray *PageSize Env10
*UIConstraints: *DLSlipSheetTray 1stTray *PageSize EnvMonarch
*UIConstraints: *DLSlipSheetTray 2ndTray *PageSize EnvMonarch
*UIConstraints: *DLSlipSheetTray AutoTray *PageSize EnvMonarch
*UIConstraints: *DLSlipSheetTray 1stTray *PageSize EnvC5
*UIConstraints: *DLSlipSheetTray 2ndTray *PageSize EnvC5
*UIConstraints: *DLSlipSheetTray AutoTray *PageSize EnvC5
*UIConstraints: *DLSlipSheetTray 1stTray *PageSize EnvDL
*UIConstraints: *DLSlipSheetTray 2ndTray *PageSize EnvDL
*UIConstraints: *DLSlipSheetTray AutoTray *PageSize EnvDL
*UIConstraints: *DLSlipSheetTray 1stTray *PageRegion Env10
*UIConstraints: *DLSlipSheetTray 2ndTray *PageRegion Env10
*UIConstraints: *DLSlipSheetTray AutoTray *PageRegion Env10
*UIConstraints: *DLSlipSheetTray 1stTray *PageRegion EnvMonarch
*UIConstraints: *DLSlipSheetTray 2ndTray *PageRegion EnvMonarch
*UIConstraints: *DLSlipSheetTray AutoTray *PageRegion EnvMonarch
*UIConstraints: *DLSlipSheetTray 1stTray *PageRegion EnvC5
*UIConstraints: *DLSlipSheetTray 2ndTray *PageRegion EnvC5
*UIConstraints: *DLSlipSheetTray AutoTray *PageRegion EnvC5
*UIConstraints: *DLSlipSheetTray 1stTray *PageRegion EnvDL
*UIConstraints: *DLSlipSheetTray 2ndTray *PageRegion EnvDL
*UIConstraints: *DLSlipSheetTray AutoTray *PageRegion EnvDL

*% ==== PageSize vs MediaType ====
*UIConstraints: *PageSize Env10 *MediaType Stationary
*UIConstraints: *PageSize Env10 *MediaType StationaryBack
*UIConstraints: *PageSize Env10 *MediaType FinePaper
*UIConstraints: *PageSize Env10 *MediaType FinePaperBack
*UIConstraints: *PageSize Env10 *MediaType Transparency
*UIConstraints: *PageSize Env10 *MediaType LabelPaper
*UIConstraints: *PageSize EnvMonarch *MediaType Stationary
*UIConstraints: *PageSize EnvMonarch *MediaType StationaryBack
*UIConstraints: *PageSize EnvMonarch *MediaType FinePaper
*UIConstraints: *PageSize EnvMonarch *MediaType FinePaperBack
*UIConstraints: *PageSize EnvMonarch *MediaType Transparency
*UIConstraints: *PageSize EnvMonarch *MediaType LabelPaper
*UIConstraints: *PageSize EnvC5 *MediaType Stationary
*UIConstraints: *PageSize EnvC5 *MediaType StationaryBack
*UIConstraints: *PageSize EnvC5 *MediaType FinePaper
*UIConstraints: *PageSize EnvC5 *MediaType FinePaperBack
*UIConstraints: *PageSize EnvC5 *MediaType Transparency
*UIConstraints: *PageSize EnvC5 *MediaType LabelPaper
*UIConstraints: *PageSize EnvDL *MediaType Stationary
*UIConstraints: *PageSize EnvDL *MediaType StationaryBack
*UIConstraints: *PageSize EnvDL *MediaType FinePaper
*UIConstraints: *PageSize EnvDL *MediaType FinePaperBack
*UIConstraints: *PageSize EnvDL *MediaType Transparency
*UIConstraints: *PageSize EnvDL *MediaType LabelPaper
*UIConstraints: *PageRegion Env10 *MediaType Stationary
*UIConstraints: *PageRegion Env10 *MediaType StationaryBack
*UIConstraints: *PageRegion Env10 *MediaType FinePaper
*UIConstraints: *PageRegion Env10 *MediaType FinePaperBack
*UIConstraints: *PageRegion Env10 *MediaType Transparency
*UIConstraints: *PageRegion Env10 *MediaType LabelPaper
*UIConstraints: *PageRegion EnvMonarch *MediaType Stationary
*UIConstraints: *PageRegion EnvMonarch *MediaType StationaryBack
*UIConstraints: *PageRegion EnvMonarch *MediaType FinePaper
*UIConstraints: *PageRegion EnvMonarch *MediaType FinePaperBack
*UIConstraints: *PageRegion EnvMonarch *MediaType Transparency
*UIConstraints: *PageRegion EnvMonarch *MediaType LabelPaper
*UIConstraints: *PageRegion EnvC5 *MediaType Stationary
*UIConstraints: *PageRegion EnvC5 *MediaType StationaryBack
*UIConstraints: *PageRegion EnvC5 *MediaType FinePaper
*UIConstraints: *PageRegion EnvC5 *MediaType FinePaperBack
*UIConstraints: *PageRegion EnvC5 *MediaType Transparency
*UIConstraints: *PageRegion EnvC5 *MediaType LabelPaper
*UIConstraints: *PageRegion EnvDL *MediaType Stationary
*UIConstraints: *PageRegion EnvDL *MediaType StationaryBack
*UIConstraints: *PageRegion EnvDL *MediaType FinePaper
*UIConstraints: *PageRegion EnvDL *MediaType FinePaperBack
*UIConstraints: *PageRegion EnvDL *MediaType Transparency
*UIConstraints: *PageRegion EnvDL *MediaType LabelPaper
*UIConstraints: *MediaType Stationary *PageSize Env10
*UIConstraints: *MediaType StationaryBack *PageSize Env10
*UIConstraints: *MediaType FinePaper *PageSize Env10
*UIConstraints: *MediaType FinePaperBack *PageSize Env10
*UIConstraints: *MediaType Transparency *PageSize Env10
*UIConstraints: *MediaType LabelPaper *PageSize Env10
*UIConstraints: *MediaType Stationary *PageSize EnvMonarch
*UIConstraints: *MediaType StationaryBack *PageSize EnvMonarch
*UIConstraints: *MediaType FinePaper *PageSize EnvMonarch
*UIConstraints: *MediaType FinePaperBack *PageSize EnvMonarch
*UIConstraints: *MediaType Transparency *PageSize EnvMonarch
*UIConstraints: *MediaType LabelPaper *PageSize EnvMonarch
*UIConstraints: *MediaType Stationary *PageSize EnvC5
*UIConstraints: *MediaType StationaryBack *PageSize EnvC5
*UIConstraints: *MediaType FinePaper *PageSize EnvC5
*UIConstraints: *MediaType FinePaperBack *PageSize EnvC5
*UIConstraints: *MediaType Transparency *PageSize EnvC5
*UIConstraints: *MediaType LabelPaper *PageSize EnvC5
*UIConstraints: *MediaType Stationary *PageSize EnvDL
*UIConstraints: *MediaType StationaryBack *PageSize EnvDL
*UIConstraints: *MediaType FinePaper *PageSize EnvDL
*UIConstraints: *MediaType FinePaperBack *PageSize EnvDL
*UIConstraints: *MediaType Transparency *PageSize EnvDL
*UIConstraints: *MediaType LabelPaper *PageSize EnvDL
*UIConstraints: *MediaType Stationary *PageRegion Env10
*UIConstraints: *MediaType StationaryBack *PageRegion Env10
*UIConstraints: *MediaType FinePaper *PageRegion Env10
*UIConstraints: *MediaType FinePaperBack *PageRegion Env10
*UIConstraints: *MediaType Transparency *PageRegion Env10
*UIConstraints: *MediaType LabelPaper *PageRegion Env10
*UIConstraints: *MediaType Stationary *PageRegion EnvMonarch
*UIConstraints: *MediaType StationaryBack *PageRegion EnvMonarch
*UIConstraints: *MediaType FinePaper *PageRegion EnvMonarch
*UIConstraints: *MediaType FinePaperBack *PageRegion EnvMonarch
*UIConstraints: *MediaType Transparency *PageRegion EnvMonarch
*UIConstraints: *MediaType LabelPaper *PageRegion EnvMonarch
*UIConstraints: *MediaType Stationary *PageRegion EnvC5
*UIConstraints: *MediaType StationaryBack *PageRegion EnvC5
*UIConstraints: *MediaType FinePaper *PageRegion EnvC5
*UIConstraints: *MediaType FinePaperBack *PageRegion EnvC5
*UIConstraints: *MediaType Transparency *PageRegion EnvC5
*UIConstraints: *MediaType LabelPaper *PageRegion EnvC5
*UIConstraints: *MediaType Stationary *PageRegion EnvDL
*UIConstraints: *MediaType StationaryBack *PageRegion EnvDL
*UIConstraints: *MediaType FinePaper *PageRegion EnvDL
*UIConstraints: *MediaType FinePaperBack *PageRegion EnvDL
*UIConstraints: *MediaType Transparency *PageRegion EnvDL
*UIConstraints: *MediaType LabelPaper *PageRegion EnvDL

*% ==== SlipSheetTray vs InputSlot ====
*UIConstraints: *DLSlipSheetTray 1stTray *InputSlot 1stTray
*UIConstraints: *DLSlipSheetTray 1stTray *InputSlot 2ndTray
*UIConstraints: *DLSlipSheetTray 2ndTray *InputSlot 1stTray
*UIConstraints: *DLSlipSheetTray 2ndTray *InputSlot 2ndTray
*UIConstraints: *DLSlipSheetTray AutoTray *InputSlot 1stTray
*UIConstraints: *DLSlipSheetTray AutoTray *InputSlot 2ndTray
*UIConstraints: *InputSlot 1stTray *DLSlipSheetTray 1stTray
*UIConstraints: *InputSlot 2ndTray *DLSlipSheetTray 1stTray
*UIConstraints: *InputSlot 1stTray *DLSlipSheetTray 2ndTray
*UIConstraints: *InputSlot 2ndTray *DLSlipSheetTray 2ndTray
*UIConstraints: *InputSlot 1stTray *DLSlipSheetTray AutoTray
*UIConstraints: *InputSlot 2ndTray *DLSlipSheetTray AutoTray

*% ==== SlipSheetTray vs MediaType ====
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType Stationary
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType StationaryBack
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType FinePaper
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType FinePaperBack
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType ThickPaper
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType ThickPaperBack
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType ThickPaper2
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType ThickPaper2Back
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType LabelPaper
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType CoatingPaper2
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType CoatingPaper2Back
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType CoatingPaper3
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType CoatingPaper3Back
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType Envelope
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType Stationary
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType StationaryBack
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType FinePaper
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType FinePaperBack
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType ThickPaper
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType ThickPaperBack
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType ThickPaper2
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType ThickPaper2Back
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType LabelPaper
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType CoatingPaper2
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType CoatingPaper2Back
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType CoatingPaper3
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType CoatingPaper3Back
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType Envelope
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType Stationary
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType StationaryBack
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType FinePaper
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType FinePaperBack
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType ThickPaper
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType ThickPaperBack
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType ThickPaper2
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType ThickPaper2Back
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType LabelPaper
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType CoatingPaper2
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType CoatingPaper2Back
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType CoatingPaper3
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType CoatingPaper3Back
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType Envelope
*UIConstraints: *MediaType Stationary *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType StationaryBack *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType FinePaper *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType FinePaperBack *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType ThickPaper *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType ThickPaperBack *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType ThickPaper2 *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType ThickPaper2Back *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType LabelPaper *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType CoatingPaper2 *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType CoatingPaper2Back *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType CoatingPaper3 *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType CoatingPaper3Back *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType Envelope *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType Stationary *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType StationaryBack *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType FinePaper *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType FinePaperBack *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType ThickPaper *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType ThickPaperBack *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType ThickPaper2 *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType ThickPaper2Back *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType LabelPaper *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType CoatingPaper2 *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType CoatingPaper2Back *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType CoatingPaper3 *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType CoatingPaper3Back *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType Envelope *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType Stationary *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType StationaryBack *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType FinePaper *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType FinePaperBack *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType ThickPaper *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType ThickPaperBack *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType ThickPaper2 *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType ThickPaper2Back *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType LabelPaper *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType CoatingPaper2 *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType CoatingPaper2Back *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType CoatingPaper3 *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType CoatingPaper3Back *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType Envelope *DLSlipSheetTray AutoTray

*% ==== SlipSheetTray vs Duplex ====
*UIConstraints: *DLSlipSheetTray 1stTray *Duplex DuplexNoTumble
*UIConstraints: *DLSlipSheetTray 1stTray *Duplex DuplexTumble
*UIConstraints: *DLSlipSheetTray 2ndTray *Duplex DuplexNoTumble
*UIConstraints: *DLSlipSheetTray 2ndTray *Duplex DuplexTumble
*UIConstraints: *DLSlipSheetTray AutoTray *Duplex DuplexNoTumble
*UIConstraints: *DLSlipSheetTray AutoTray *Duplex DuplexTumble
*UIConstraints: *Duplex DuplexNoTumble *DLSlipSheetTray 1stTray
*UIConstraints: *Duplex DuplexTumble *DLSlipSheetTray 1stTray
*UIConstraints: *Duplex DuplexNoTumble *DLSlipSheetTray 2ndTray
*UIConstraints: *Duplex DuplexTumble *DLSlipSheetTray 2ndTray
*UIConstraints: *Duplex DuplexNoTumble *DLSlipSheetTray AutoTray
*UIConstraints: *Duplex DuplexTumble *DLSlipSheetTray AutoTray

*% ==== InputSlot vs MediaType ====
*UIConstraints: *InputSlot 1stTray *MediaType Stationary
*UIConstraints: *InputSlot 1stTray *MediaType StationaryBack
*UIConstraints: *InputSlot 1stTray *MediaType FinePaper
*UIConstraints: *InputSlot 1stTray *MediaType FinePaperBack
*UIConstraints: *InputSlot 1stTray *MediaType ThickPaper
*UIConstraints: *InputSlot 1stTray *MediaType ThickPaperBack
*UIConstraints: *InputSlot 1stTray *MediaType ThickPaper2
*UIConstraints: *InputSlot 1stTray *MediaType ThickPaper2Back
*UIConstraints: *InputSlot 1stTray *MediaType Transparency
*UIConstraints: *InputSlot 1stTray *MediaType LabelPaper
*UIConstraints: *InputSlot 1stTray *MediaType CoatingPaper2
*UIConstraints: *InputSlot 1stTray *MediaType CoatingPaper2Back
*UIConstraints: *InputSlot 1stTray *MediaType CoatingPaper3
*UIConstraints: *InputSlot 1stTray *MediaType CoatingPaper3Back
*UIConstraints: *InputSlot 1stTray *MediaType Envelope
*UIConstraints: *InputSlot 2ndTray *MediaType Stationary
*UIConstraints: *InputSlot 2ndTray *MediaType StationaryBack
*UIConstraints: *InputSlot 2ndTray *MediaType FinePaper
*UIConstraints: *InputSlot 2ndTray *MediaType FinePaperBack
*UIConstraints: *InputSlot 2ndTray *MediaType ThickPaper
*UIConstraints: *InputSlot 2ndTray *MediaType ThickPaperBack
*UIConstraints: *InputSlot 2ndTray *MediaType ThickPaper2
*UIConstraints: *InputSlot 2ndTray *MediaType ThickPaper2Back
*UIConstraints: *InputSlot 2ndTray *MediaType Transparency
*UIConstraints: *InputSlot 2ndTray *MediaType LabelPaper
*UIConstraints: *InputSlot 2ndTray *MediaType CoatingPaper2
*UIConstraints: *InputSlot 2ndTray *MediaType CoatingPaper2Back
*UIConstraints: *InputSlot 2ndTray *MediaType CoatingPaper3
*UIConstraints: *InputSlot 2ndTray *MediaType CoatingPaper3Back
*UIConstraints: *InputSlot 2ndTray *MediaType Envelope
*UIConstraints: *ManualFeed False *MediaType StationaryBack
*UIConstraints: *ManualFeed False *MediaType FinePaperBack
*UIConstraints: *ManualFeed False *MediaType ThickPaperBack
*UIConstraints: *ManualFeed False *MediaType ThickPaper2
*UIConstraints: *ManualFeed False *MediaType ThickPaper2Back
*UIConstraints: *ManualFeed False *MediaType Transparency
*UIConstraints: *ManualFeed False *MediaType LabelPaper
*UIConstraints: *ManualFeed False *MediaType CoatingPaper2
*UIConstraints: *ManualFeed False *MediaType CoatingPaper2Back
*UIConstraints: *ManualFeed False *MediaType CoatingPaper3
*UIConstraints: *ManualFeed False *MediaType CoatingPaper3Back
*UIConstraints: *ManualFeed False *MediaType Envelope
*UIConstraints: *MediaType Stationary *InputSlot 1stTray
*UIConstraints: *MediaType StationaryBack *InputSlot 1stTray
*UIConstraints: *MediaType FinePaper *InputSlot 1stTray
*UIConstraints: *MediaType FinePaperBack *InputSlot 1stTray
*UIConstraints: *MediaType ThickPaper *InputSlot 1stTray
*UIConstraints: *MediaType ThickPaperBack *InputSlot 1stTray
*UIConstraints: *MediaType ThickPaper2 *InputSlot 1stTray
*UIConstraints: *MediaType ThickPaper2Back *InputSlot 1stTray
*UIConstraints: *MediaType Transparency *InputSlot 1stTray
*UIConstraints: *MediaType LabelPaper *InputSlot 1stTray
*UIConstraints: *MediaType CoatingPaper2 *InputSlot 1stTray
*UIConstraints: *MediaType CoatingPaper2Back *InputSlot 1stTray
*UIConstraints: *MediaType CoatingPaper3 *InputSlot 1stTray
*UIConstraints: *MediaType CoatingPaper3Back *InputSlot 1stTray
*UIConstraints: *MediaType Envelope *InputSlot 1stTray
*UIConstraints: *MediaType Stationary *InputSlot 2ndTray
*UIConstraints: *MediaType StationaryBack *InputSlot 2ndTray
*UIConstraints: *MediaType FinePaper *InputSlot 2ndTray
*UIConstraints: *MediaType FinePaperBack *InputSlot 2ndTray
*UIConstraints: *MediaType ThickPaper *InputSlot 2ndTray
*UIConstraints: *MediaType ThickPaperBack *InputSlot 2ndTray
*UIConstraints: *MediaType ThickPaper2 *InputSlot 2ndTray
*UIConstraints: *MediaType ThickPaper2Back *InputSlot 2ndTray
*UIConstraints: *MediaType Transparency *InputSlot 2ndTray
*UIConstraints: *MediaType LabelPaper *InputSlot 2ndTray
*UIConstraints: *MediaType CoatingPaper2 *InputSlot 2ndTray
*UIConstraints: *MediaType CoatingPaper2Back *InputSlot 2ndTray
*UIConstraints: *MediaType CoatingPaper3 *InputSlot 2ndTray
*UIConstraints: *MediaType CoatingPaper3Back *InputSlot 2ndTray
*UIConstraints: *MediaType Envelope *InputSlot 2ndTray
*UIConstraints: *MediaType StationaryBack *ManualFeed False
*UIConstraints: *MediaType FinePaperBack *ManualFeed False
*UIConstraints: *MediaType ThickPaperBack *ManualFeed False
*UIConstraints: *MediaType ThickPaper2 *ManualFeed False
*UIConstraints: *MediaType ThickPaper2Back *ManualFeed False
*UIConstraints: *MediaType Transparency *ManualFeed False
*UIConstraints: *MediaType LabelPaper *ManualFeed False
*UIConstraints: *MediaType CoatingPaper2 *ManualFeed False
*UIConstraints: *MediaType CoatingPaper2Back *ManualFeed False
*UIConstraints: *MediaType CoatingPaper3 *ManualFeed False
*UIConstraints: *MediaType CoatingPaper3Back *ManualFeed False
*UIConstraints: *MediaType Envelope *ManualFeed False

*% ==== Duplex vs MediaType ====
*UIConstraints: *Duplex DuplexNoTumble *MediaType StationaryBack
*UIConstraints: *Duplex DuplexNoTumble *MediaType FinePaperBack
*UIConstraints: *Duplex DuplexNoTumble *MediaType ThickPaperBack
*UIConstraints: *Duplex DuplexNoTumble *MediaType ThickPaper2
*UIConstraints: *Duplex DuplexNoTumble *MediaType ThickPaper2Back
*UIConstraints: *Duplex DuplexNoTumble *MediaType Transparency
*UIConstraints: *Duplex DuplexNoTumble *MediaType LabelPaper
*UIConstraints: *Duplex DuplexNoTumble *MediaType CoatingPaper2Back
*UIConstraints: *Duplex DuplexNoTumble *MediaType CoatingPaper3
*UIConstraints: *Duplex DuplexNoTumble *MediaType CoatingPaper3Back
*UIConstraints: *Duplex DuplexNoTumble *MediaType Envelope
*UIConstraints: *Duplex DuplexTumble *MediaType StationaryBack
*UIConstraints: *Duplex DuplexTumble *MediaType FinePaperBack
*UIConstraints: *Duplex DuplexTumble *MediaType ThickPaperBack
*UIConstraints: *Duplex DuplexTumble *MediaType ThickPaper2
*UIConstraints: *Duplex DuplexTumble *MediaType ThickPaper2Back
*UIConstraints: *Duplex DuplexTumble *MediaType Transparency
*UIConstraints: *Duplex DuplexTumble *MediaType LabelPaper
*UIConstraints: *Duplex DuplexTumble *MediaType CoatingPaper2Back
*UIConstraints: *Duplex DuplexTumble *MediaType CoatingPaper3
*UIConstraints: *Duplex DuplexTumble *MediaType CoatingPaper3Back
*UIConstraints: *Duplex DuplexTumble *MediaType Envelope
*UIConstraints: *MediaType StationaryBack *Duplex DuplexNoTumble
*UIConstraints: *MediaType FinePaperBack *Duplex DuplexNoTumble
*UIConstraints: *MediaType ThickPaperBack *Duplex DuplexNoTumble
*UIConstraints: *MediaType ThickPaper2 *Duplex DuplexNoTumble
*UIConstraints: *MediaType ThickPaper2Back *Duplex DuplexNoTumble
*UIConstraints: *MediaType Transparency *Duplex DuplexNoTumble
*UIConstraints: *MediaType LabelPaper *Duplex DuplexNoTumble
*UIConstraints: *MediaType CoatingPaper2Back *Duplex DuplexNoTumble
*UIConstraints: *MediaType CoatingPaper3 *Duplex DuplexNoTumble
*UIConstraints: *MediaType CoatingPaper3Back *Duplex DuplexNoTumble
*UIConstraints: *MediaType Envelope *Duplex DuplexNoTumble
*UIConstraints: *MediaType StationaryBack *Duplex DuplexTumble
*UIConstraints: *MediaType FinePaperBack *Duplex DuplexTumble
*UIConstraints: *MediaType ThickPaperBack *Duplex DuplexTumble
*UIConstraints: *MediaType ThickPaper2 *Duplex DuplexTumble
*UIConstraints: *MediaType ThickPaper2Back *Duplex DuplexTumble
*UIConstraints: *MediaType Transparency *Duplex DuplexTumble
*UIConstraints: *MediaType LabelPaper *Duplex DuplexTumble
*UIConstraints: *MediaType CoatingPaper2Back *Duplex DuplexTumble
*UIConstraints: *MediaType CoatingPaper3 *Duplex DuplexTumble
*UIConstraints: *MediaType CoatingPaper3Back *Duplex DuplexTumble
*UIConstraints: *MediaType Envelope *Duplex DuplexTumble

*% ==== LeadingEdge vs PageSize ====
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize A4
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize A5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize B5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize Letter
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize FanFoldGermanLegal
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize Legal
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize Executive
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize Env10
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize EnvC5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize EnvMonarch
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize EnvDL
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion A4
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion A5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion B5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion Letter
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion FanFoldGermanLegal
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion Legal
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion Executive
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion Env10
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion EnvC5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion EnvMonarch
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion EnvDL
*UIConstraints: *PageSize A4 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize A5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize B5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize Letter *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize FanFoldGermanLegal *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize Legal *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize Executive *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize Env10 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize EnvC5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize EnvMonarch *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize EnvDL *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion A4 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion A5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion B5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion Letter *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion FanFoldGermanLegal *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion Legal *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion Executive *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion Env10 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion EnvC5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion EnvMonarch *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion EnvDL *DLMSILeadingEdge LongEdge

*% ==== Device Capabilities ===============
*LanguageLevel: "3"
*Protocols: TBCP
*1284Modes Parallel: Compat Nibble ECP
*1284DeviceID: "MFG:Dell;CMD:PJL,RASTER,DOWNLOAD,PCLXL,PCL,POSTSCRIPT;MDL:MFP Laser 3115cn;DES:Dell MFP Laser 3115cn;CLS:PRINTER;"
*FreeVM: "11140352"
*VMOption 128Meg/Standaard 128 MB: "11140352"
*VMOption 384Meg/384 MB: "11140352"
*VMOption 640Meg/640 MB: "11140352"
*VMOption 1152Meg/1152 MB: "11140352"

*ColorDevice: True
*DefaultColorSpace: CMYK
*VariablePaperSize: True
*LandscapeOrientation: Plus90
*TTRasterizer: Type42
*?TTRasterizer: "
save
    42 /FontType resourcestatus
    {pop pop (Type42)}{(No Type42)} ifelse = flush
restore
"
*End
*FileSystem: True
*?FileSystem: "
  save false
   (%disk?%)
   { currentdevparams dup /Writeable known
      { /Writeable get {pop true} if }  { pop } ifelse
    } 10 string /IODevice resourceforall
    {(True)}{(False)} ifelse = flush
 restore
"
*End

*Throughput: "30"
*Password: "()"
*ExitServer: "
 count 0 eq
 { false } { true exch startjob } ifelse
 not {
     (WARNING: Cannot modify initial VM.) =
     (Missing or invalid password.) =
     (Please contact the author of this software.) = flush quit
     } if
"
*End
*Reset: "
 count 0 eq
 { false } { true exch startjob } ifelse
 not {
    (WARNING: Cannot reset printer.) =
    (Missing or invalid password.) =
    (Please contact the author of this software.) = flush quit
    } if
 systemdict /quit get exec
 (WARNING : Printer Reset Failed.) = flush
"
*End

*DefaultResolution: 600dpi
*?Resolution: "
save
    currentpagedevice /HWResolution get dup aload pop eq
    {0 get cvi 9 string cvs print}
    {aload pop exch cvi 9 string cvs print (x) print cvi 9 string cvs 
print}
    ifelse (dpi) =
restore
"
*End
*AccurateScreensSupport: True
*SuggestedJobTimeout: "0"
*SuggestedWaitTimeout: "300"
*PrintPSErrors: True


*% Halftone Information ===============
*DefaultHalftoneType: 5
*ScreenFreq: "141.0"
*ScreenAngle: "45.0"
*DefaultScreenProc: Dot
*ScreenProc Dot: "{180 mul cos exch 180 mul cos add 2 div} bind"
*ScreenProc Line: "{ pop }"
*ScreenProc Ellipse: "{ dup 5 mul 8 div mul exch dup mul exch add sqrt 1 
exch sub }"
*DefaultTransfer: Null
*Transfer Null: "{ }"
*Transfer Null.Inverse: "{ 1 exch sub }"


*% InputSlot Information ================
*RequiresPageRegion 1stTray: True
*RequiresPageRegion 2ndTray: True

*OpenUI *InputSlot/Papierinvoer: PickOne
*OrderDependency: 50.0 AnySetup *InputSlot
*DefaultInputSlot: 1stTray
*InputSlot 1stTray/Lade 1: "
  3 dict begin
  /MediaPosition 0 def
  /DeferredMediaSelection true def
  /TraySwitch false def
  currentdict end setpagedevice
"
*End
*InputSlot 2ndTray/Lade 2: "
  3 dict begin
  /MediaPosition 1 def
  /DeferredMediaSelection true def
  /TraySwitch false def
  currentdict end setpagedevice
"
*End
*?InputSlot: "
"
*End
*CloseUI: *InputSlot


*OpenUI *ManualFeed/MPF:  Boolean
*OrderDependency: 30.0 AnySetup *ManualFeed
*DefaultManualFeed: False
*ManualFeed True: "
  1 dict dup /ManualFeed true put setpagedevice
"
*End
*ManualFeed False: "
  1 dict dup /ManualFeed false put setpagedevice
"
*End
*?ManualFeed: "
  save
    currentpagedevice /ManualFeed known
    {currentpagedevice /ManualFeed get {(True)}{(False)}ifelse}
    {(False)} ifelse = flush
  restore
"
*End
*CloseUI: *ManualFeed

*OpenUI *Duplex/2-zijdig afdrukken:  PickOne
*OrderDependency: 110.0 AnySetup *Duplex
*DefaultDuplex: None
*Duplex None/1-zijdig afdrukken: "
    1 dict
    dup /Duplex false put
    setpagedevice
"
*End
*Duplex DuplexNoTumble/Naar Lange zijde draaien: "
    2 dict dup /Duplex true put
    dup /Tumble false put setpagedevice
"
*End
*Duplex DuplexTumble/Naar Korte zijde draaien: "
    2 dict dup /Duplex true put
    dup /Tumble true put setpagedevice
"
*End
*?Duplex: "
save
   currentpagedevice /Duplex known
   { currentpagedevice /Duplex get
       { currentpagedevice /Tumble get
          {(DuplexTumble)}{(DuplexNoTumble)}ifelse
       }
       { (None) } ifelse
   }
   { (None)}
   ifelse = flush
restore
"
*End
*CloseUI: *Duplex


*% Paper Handling ===================
*OpenUI *PageSize: PickOne
*OrderDependency: 60.0 AnySetup *PageSize
*DefaultPageSize: A4
*PageSize A4/A4: "
    6 dict dup /PageSize [595 842] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize A5/A5: "
    6 dict dup /PageSize [420 595] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize B5/B5: "
    6 dict dup /PageSize [516 729] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize Letter/Letter (21,59 x 27,94 cm): "
    6 dict dup /PageSize [612 792] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize FanFoldGermanLegal/Folio (21,59 x 33,02 cm): "
    6 dict dup /PageSize [612 936] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize Legal/Legal (21,59 x 35,56 cm): "
    6 dict dup /PageSize [612 1008] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize Executive/Executive (18,42x 26,67 cm): "
    6 dict dup /PageSize [522 756] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize Env10/Envelop #10: "
    6 dict dup /PageSize [297 684] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize EnvMonarch/Monarch: "
    6 dict dup /PageSize [279 540] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize EnvC5/C5: "
    6 dict dup /PageSize [459 649] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize EnvDL/DL: "
    6 dict dup /PageSize [312 624] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*?PageSize: "
  save
   currentpagedevice /PageSize get aload pop
   2 copy gt {exch} if
   (Unknown)
   11 dict
   dup [595 842] (A4) put
   dup [420 595] (A5) put
   dup [516 729] (B5) put
   dup [612 792] (Letter) put
   dup [612 936] (FanFoldGermanLegal) put
   dup [612 1008] (Legal) put
   dup [522 756] (Executive) put
   dup [297 684] (Env10) put
   dup [279 540] (EnvMonarch) put
   dup [459 649] (EnvC5) put
   dup [312 624] (EnvDL) put
   { exch aload pop 4 index sub abs 5 le exch
   5 index sub abs 5 le and
      {exch pop exit} {pop} ifelse
   } bind forall
   = flush pop pop
   restore
"
*End
*CloseUI: *PageSize

*OpenUI *PageRegion:  PickOne
*OrderDependency: 80.0 AnySetup *PageRegion
*DefaultPageRegion: A4
*PageRegion A4/A4: "
    6 dict dup /PageSize [595 842] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion A5/A5: "
    6 dict dup /PageSize [420 595] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion B5/B5: "
    6 dict dup /PageSize [516 729] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion Letter/Letter (21,59 x 27,94 cm): "
    6 dict dup /PageSize [612 792] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion FanFoldGermanLegal/Folio (21,59 x 33,02 cm): "
    6 dict dup /PageSize [612 936] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion Legal/Legal (21,59 x 35,56 cm): "
    6 dict dup /PageSize [612 1008] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion Executive/Executive (18,42x 26,67 cm): "
    6 dict dup /PageSize [522 756] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion Env10/Envelop #10: "
    6 dict dup /PageSize [297 684] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion EnvMonarch/Monarch: "
    6 dict dup /PageSize [279 540] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion EnvC5/C5: "
    6 dict dup /PageSize [459 649] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion EnvDL/DL: "
    6 dict dup /PageSize [312 624] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false 
put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*CloseUI: *PageRegion

*% The following entries provide information about specific paper keywords.
*DefaultImageableArea: A4
*ImageableArea A4/A4: "11.62 11.62 583.38 830.38 "
*ImageableArea A5/A5: "11.62 11.62 408.38 583.38 "
*ImageableArea B5/B5: "11.62 11.62 504.38 717.38 "
*ImageableArea Letter/Letter (21,59 x 27,94 cm): "11.62 11.62 600.38 
780.38 "
*ImageableArea FanFoldGermanLegal/Folio (21,59 x 33,02 cm): "11.62 11.62 
600.38 924.38 "
*ImageableArea Legal/Legal (21,59 x 35,56 cm): "11.62 11.62 600.38 
996.38 "
*ImageableArea Executive/Executive (18,42x 26,67 cm): "11.62 11.62 
510.38 744.38 "
*ImageableArea Env10/Envelop #10: "11.62 11.62 285.38 672.38 "
*ImageableArea EnvMonarch/Monarch: "11.62 11.62 267.38 528.38 "
*ImageableArea EnvC5/C5: "11.62 11.62 447.38 637.38 "
*ImageableArea EnvDL/DL: "11.62 17.29 300.38 606.71 "
*?ImageableArea: "
save
   3 dict begin
   /cvp { (                ) cvs print ( ) print } bind def
   /upperright {10000 mul floor 10000 div} bind def
   /lowerleft {10000 mul ceiling 10000 div} bind def
   newpath clippath pathbbox
   4 -2 roll exch 2 {lowerleft cvp} repeat
   exch 2 {upperright cvp} repeat (\n) print flush
   end
restore
"
*End

*% These provide the physical dimensions of the paper (by keyword)
*DefaultPaperDimension: A4
*PaperDimension A4/A4: "595 842"
*PaperDimension A5/A5: "420 595"
*PaperDimension B5/B5: "516 729"
*PaperDimension Letter/Letter (21,59 x 27,94 cm): "612 792"
*PaperDimension FanFoldGermanLegal/Folio (21,59 x 33,02 cm): "612 936"
*PaperDimension Legal/Legal (21,59 x 35,56 cm): "612 1008"
*PaperDimension Executive/Executive (18,42x 26,67 cm): "522 756"
*PaperDimension Env10/Envelop #10: "297 684"
*PaperDimension EnvMonarch/Monarch: "279 540"
*PaperDimension EnvC5/C5: "459 649"
*PaperDimension EnvDL/DL: "312 624"

*% Custom Page Sizes ===================
*% min: 216 pts x 277 pts   (76.2mm * 98mm)
*% max: 624 pts x 1008 pts  (8.66 inch * 14.00 inch)
*HWMargins: 11 11 11 11
*LeadingEdge Short: ""
*DefaultLeadingEdge: Short
*MaxMediaWidth: "624"
*MaxMediaHeight: "1008"
*NonUIOrderDependency: 80.0 AnySetup *CustomPageSize
*CustomPageSize True: "
4 dict dup /LeadingEdge null put
dup /MediaClass null put currentpagedevice
dup /MediaPosition get null eq
{/Policies 2 copy known
  {get /PageSize 2 copy known
    {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} 
if}
    {pop pop} ifelse
  }{pop pop} ifelse
}{pop} ifelse setpagedevice
userdict /4.3PPDCompliant known
    {userdict /4.3PPDCompliant get } {false} ifelse
{ % From Print Managers complying with 4.3 PPD Spec.
  pop pop pop % discard orientation & offsets
  3 dict begin
    /PageSize [
      4 -2 roll
    ] def
  /ImagingBBox null def
  currentdict end setpagedevice
}{ % From Print Managers not complying with 4.3 PPD Spec.
  pop pop pop % discard orientation & offsets
  3 dict begin
    /PageSize [
      4 -2 roll exch
    ] def
  /ImagingBBox null def
  currentdict end setpagedevice
} ifelse
"
*End
*ParamCustomPageSize Height:       1 points 277 1008
*ParamCustomPageSize Width:        2 points 216 624
*ParamCustomPageSize WidthOffset:  3 points 0 0
*ParamCustomPageSize HeightOffset: 4 points 0 0
*ParamCustomPageSize Orientation:  5 int 1 1

*OpenGroup: Graphics/Afdrukkwaliteit/Kleur.
*% ColorMode Information ===================
*OpenUI *DLColorMode/Uitvoerkleur:PickOne
*OrderDependency: 20.0 AnySetup *DLColorMode
*DefaultDLColorMode: Color
*DLColorMode Color/Kleur: "
  1 dict dup /ProcessColorModel /DeviceCMYK put setpagedevice
"
*End
*DLColorMode Black/Zwart: "
  1 dict dup /ProcessColorModel /DeviceGray put setpagedevice
"
*End
*?DLColorMode: "
save
  currentpagedevice /ProcessColorModel get
  cvn /DeviceGray eq {(Black)}{(Color)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLColorMode

*% OutputMode Information ===================
*OpenUI *DLOutputMode/Afdrukmodus:PickOne
*OrderDependency: 10.0 AnySetup *DLOutputMode
*DefaultDLOutputMode: HighSpeed
*DLOutputMode HighSpeed/Hoge snelheid: "
    2 dict dup /HWResolution [600 600] put
    dup 2 dict dup /Type 26 put dup /ValuesPerColorComponent 2 put
    /DeviceRenderingInfo exch put
    setpagedevice
"
*End
*DLOutputMode HighQuality/Hoge kwaliteit: "
    2 dict dup /HWResolution [600 600] put
    dup 2 dict dup /Type 26 put dup /ValuesPerColorComponent 16 put
    /DeviceRenderingInfo exch put
    setpagedevice
"
*End
*?DLOutputMode: "
"
*End
*CloseUI: *DLOutputMode

*% Brightness Information ==========================
*OpenUI *DLBrightness/Helderheid: PickOne
*OrderDependency: 26.0 AnySetup *DLBrightness
*DefaultDLBrightness: Normal
*DLBrightness Bright5/Helderder (+5): "1 dict dup 2 dict dup/Type 26 put 
dup/Brightness 5
put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Bright4/Helderder (+4): "1 dict dup 2 dict dup/Type 26 put 
dup/Brightness 4
put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Bright3/Helderder (+3): "1 dict dup 2 dict dup/Type 26 put 
dup/Brightness 3
put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Bright2/Helderder (+2): "1 dict dup 2 dict dup/Type 26 put 
dup/Brightness 2
put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Bright1/Helderder (+1): "1 dict dup 2 dict dup/Type 26 put 
dup/Brightness 1
put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Normal/Normaal: "
    1 dict dup 2 dict dup/Type 26 put dup/Brightness 0 put
    /DeviceRenderingInfo exch put setpagedevice
"
*End
*DLBrightness Dark1/Donkerder (-1): "1 dict dup 2 dict dup/Type 26 put 
dup/Brightness -1
put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Dark2/Donkerder (-2): "1 dict dup 2 dict dup/Type 26 put 
dup/Brightness -2
put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Dark3/Donkerder (-3): "1 dict dup 2 dict dup/Type 26 put 
dup/Brightness -3
put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Dark4/Donkerder (-4): "1 dict dup 2 dict dup/Type 26 put 
dup/Brightness -4
put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Dark5/Donkerder (-5): "1 dict dup 2 dict dup/Type 26 put 
dup/Brightness -5
put/DeviceRenderingInfo exch put setpagedevice"
*?DLBrightness: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /Brightness get
      11 dict
      dup 5 (Bright5) put
      dup 4 (Bright4) put
      dup 3 (Bright3) put
      dup 2 (Bright2) put
      dup 1 (Bright1) put
      dup 0 (Normal) put
      dup -1 (Dark1) put
      dup -2 (Dark2) put
      dup -3 (Dark3) put
      dup -4 (Dark4) put
      dup -5 (Dark5) put
      exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLBrightness

*% RGB Color Correction Information ==========================
*OpenUI *DLRGBImageType/Beeldtype: PickOne
*OrderDependency: 25.0 AnySetup *DLRGBImageType
*DefaultDLRGBImageType: sRGB
*DLRGBImageType sRGB/Normaal: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 2 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBImageType Presentation/Zakelijke grafieken: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 4 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBImageType Photo/Foto: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 1 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBImageType Standard/Tekst: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 3 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBImageType Off/Uit: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 0 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLRGBImageType: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /RGBCorrection get
      [(Off)(Photo)(sRGB)(Standard)(Presentation)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLRGBImageType

*% EngineScreen Information ===================
*OpenUI *DLEngineScreen/Scherm:  PickOne
*OrderDependency: 27.0 AnySetup *DLEngineScreen
*DefaultDLEngineScreen: Auto
*DLEngineScreen Auto/Auto:  "
  1 dict dup
  /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put dup /EngineScreen 2 put put
  dup /PostRenderingEnhance true put setpagedevice
"
*End
*DLEngineScreen Screen1/Fijnheid:  "
  1 dict dup
  /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put dup /EngineScreen 0 put put
  dup /PostRenderingEnhance true put setpagedevice
"
*End
*DLEngineScreen Screen2/Standaard:  "
  1 dict dup
  /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put dup /EngineScreen 1 put put
  dup /PostRenderingEnhance true put setpagedevice
"
*End
*DLEngineScreen Screen3/Gradatie:  "
  1 dict dup
  /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put dup /EngineScreen 3 put put
  dup /PostRenderingEnhance true put setpagedevice
"
*End
*?DLEngineScreen: "
save
  currentpagedevice /PostRenderingEnhanceDetails 2 copy known {
    get dup /Type get 32 eq {
      /EngineScreen get [(Screen1) (Screen2) (Auto) (Screen3)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLEngineScreen
*CloseGroup: Graphics

*OpenGroup: ColorAdjustment/Kleurinstelling
*OpenUI *DLRGBCorrection/RGB-kleurcorrectie: PickOne
*OrderDependency: 27.0 AnySetup *DLRGBCorrection
*DefaultDLRGBCorrection: None
*DLRGBCorrection None/Geen: ""
*DLRGBCorrection Perceptual/Perceptueel: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 10 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBCorrection Saturation/Verzadiging: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 11 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBCorrection RelativeC/Relatieve colorimetrie: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 12 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBCorrection AbsoluteC/Absolute colorimetrie: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 13 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLRGBCorrection: "
% TBD
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /RGBCorrection get
      10 dict
      dup 10 (Perceptual) put
      dup 11 (Saturation) put
      dup 12 (RelativeC) put
      dup 13 (AbsoluteC) put
      exch 2 copy known {get} {pop pop (None)} ifelse
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLRGBCorrection

*OpenUI *DLRGBInputProfile/RGB-profiel: PickOne
*OrderDependency: 28.0 AnySetup *DLRGBInputProfile
*DefaultDLRGBInputProfile: SRGB
*DLRGBInputProfile SRGB/sRGB: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBSpace 0 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBInputProfile AdobeRGB/Adobe RGB (1998): "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBSpace 1 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLRGBInputProfile: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /RGBSpace get 
      [(SRGB) (AdobeRGB)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLRGBInputProfile

*OpenUI *DLRGBBCorrection/RGB-gammacorrectie: PickOne
*OrderDependency: 26.0 AnySetup *DLRGBBCorrection
*DefaultDLRGBBCorrection: Dark
*DLRGBBCorrection Lightest/1.0: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 1 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBBCorrection Light/1.4: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 2 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBBCorrection Standard/1.8: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 3 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBBCorrection Dark/2.2: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 4 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBBCorrection Darkest/2.6: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 5 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBBCorrection Off/Uit: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 0 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLRGBBCorrection: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /GammaCorrection get
      [(Off) (Lightest) (Light) (Standard) (Dark) (Darkest)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLRGBBCorrection

*OpenUI *DLColorTemperature/RGB-kleurtemperatuur: PickOne
*OrderDependency: 30.0 AnySetup *DLColorTemperature
*DefaultDLColorTemperature: TemperatureD65
*DLColorTemperature TemperatureD50/5000K (D50): "
  1 dict dup
  2 dict dup /Type 26 put dup /WhitePoint 0 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLColorTemperature TemperatureD65/6500K (D65): "
  1 dict dup
  2 dict dup /Type 26 put dup /WhitePoint 1 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLColorTemperature Temperature9300K/9.300K: "
  1 dict dup
  2 dict dup /Type 26 put dup /WhitePoint 2 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLColorTemperature: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /WhitePoint get 
      [(TemperatureD50) (TemperatureD65) (Temperature9300K)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLColorTemperature

*% Gray Balance Information ===================
*OpenUI *DLGrayBalance/Gegarandeerd grijs: Boolean
*OrderDependency: 28.0 AnySetup *DLGrayBalance
*DefaultDLGrayBalance: True
*DLGrayBalance False/Uit: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBToK 0 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLGrayBalance True/Aan:  "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBToK 1 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLGrayBalance: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /RGBToK get
      [(False) (True) (Unknown) (Unknown)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLGrayBalance
*CloseGroup: ColorAdjustment

*OpenGroup: AdvancedMedia/Mediaverwerking
*% LeadingEdge ===============
*OpenUI *DLMSILeadingEdge/MPF-richting:  PickOne
*OrderDependency: 100.0 AnySetup *DLMSILeadingEdge
*DefaultDLMSILeadingEdge: ShortEdge
*DLMSILeadingEdge LongEdge/Liggend: "
  currentpagedevice /ManualFeed get {
    1 dict dup /LeadingEdge 1 put setpagedevice
  } if
"
*End
*DLMSILeadingEdge ShortEdge/Staand: "
  currentpagedevice /ManualFeed get {
    1 dict dup /LeadingEdge 0 put setpagedevice
  } if
"
*End
*?DLMSILeadingEdge: "
  save
    currentpagedevice /LeadingEdge get dup null eq
    {pop (ShortEdge)}
    {[(ShortEdge)(LongEdge)(Unknown)(Unknown)] exch get} ifelse = flush
  restore
"
*End
*CloseUI: *DLMSILeadingEdge

*% Collate ===============
*OpenUI *Collate/Sorteren: Boolean
*OrderDependency: 15.0 AnySetup *Collate
*DefaultCollate: False
*Collate False/Uit: "
        1  dict dup /Collate false put setpagedevice"
*End
*Collate True/Aan: "
        1  dict dup /Collate true put setpagedevice"
*End
*?Collate: "
  save
    currentpagedevice /Collate get
    {(True)} {(False)} ifelse
    = flush
  restore
"
*End
*CloseUI: *Collate

*% MediaType ===============
*OpenUI *MediaType/Papiersoort (MPF):  PickOne
*OrderDependency: 90.0 AnySetup *MediaType
*DefaultMediaType: Default
*MediaType Default/Printerinstellingen gebruiken: ""
*MediaType Stationary/Normaal: "1 dict dup /MediaClass (stationary) put 
setpagedevice"
*MediaType StationaryBack/Normaal (zijde 2): "1 dict dup /MediaClass 
(stationary side2) put
setpagedevice"
*MediaType FinePaper/Normaal dik: "1 dict dup /MediaClass (fine) put 
setpagedevice"
*MediaType FinePaperBack/Normaal dik (zijde 2): "1 dict dup /MediaClass 
(fine side2) put
setpagedevice"
*MediaType ThickPaper/Voorbladen  (106-163g/m2): "1 dict dup /MediaClass 
(thick1) put
setpagedevice"
*MediaType ThickPaperBack/Voorbladen (zijde 2): "1 dict dup /MediaClass 
(thick1 side2) put
setpagedevice"
*MediaType ThickPaper2/Voorbladen dik (164-216g/m2): "1 dict dup 
/MediaClass (thick2) put
setpagedevice"
*MediaType ThickPaper2Back/Voorbladen dik (zijde 2): "1 dict dup 
/MediaClass (thick2 side2) put
setpagedevice"
*MediaType Transparency/Transparant: "1 dict dup /MediaClass 
(transparency) put setpagedevice"
*MediaType LabelPaper/Etiket: "1 dict dup /MediaClass (label) put 
setpagedevice"
*MediaType CoatingPaper2/Gecoat   (106-163g/m2): "1 dict dup /MediaClass 
(coating2) put
setpagedevice"
*MediaType CoatingPaper2Back/Gecoat (zijde 2): "1 dict dup /MediaClass 
(coating2 side2) put
setpagedevice"
*MediaType CoatingPaper3/Gecoat dik (164-216g/m2): "1 dict dup 
/MediaClass (coating3) put
setpagedevice"
*MediaType CoatingPaper3Back/Gecoat dik (zijde 2): "1 dict dup 
/MediaClass (coating3 side2) put
setpagedevice"
*MediaType Envelope/Envelop: "1 dict dup /MediaClass (envelope) put 
setpagedevice"
*?MediaType: "
save
    currentpagedevice /MediaClass get dup null eq {pop (Default)}
    {dup (stationary) eq {pop (Stationary)}
     {dup (stationary side2) eq {pop (StationaryBack)}
      {dup (fine) eq {pop (FinePaper)}
       {dup (fine side2) eq {pop (FinePaperBack)}
          {dup (thickpaper1) eq{pop (ThickPaper)}
           {dup (thickpaper1 side2) eq{pop (ThickPaperBack)}
            {dup (thickpaper2) eq {pop (ThickPaper2)}
             {dup (thickpaper2 side2) eq {pop (ThickPaper2Back)}
              {dup (transparency) eq {pop (Transparency)}
               {dup (label) eq {pop (LabelPaper)}
                {dup (coating2) eq {pop (CoatingPaper2)}
                 {dup (coating2 side2) eq {pop (CoatingPaper2Back)}
                  {dup (coating3) eq {pop (CoatingPaper3)}
                   {dup (coating3 side2) eq {pop (CoatingPaper3Back)}
                        {dup (envelope) eq {pop (Envelope)}
                         {(Unknown)} ifelse
                        } ifelse
                   } ifelse
                  } ifelse
                 } ifelse
                } ifelse
               } ifelse
              } ifelse
             } ifelse
            } ifelse
           } ifelse
          } ifelse
       } ifelse
      } ifelse
     } ifelse
    } ifelse
   = flush
restore
"
*End
*CloseUI: *MediaType

*% SlipSheetTray Information ===================
*OpenUI *DLSlipSheetTray/Scheidingen invoeren vanaf:  PickOne
*OrderDependency: 120.0 AnySetup *DLSlipSheetTray
*DefaultDLSlipSheetTray: OFF
*DLSlipSheetTray OFF/Geen:  "1 dict dup /SlipSheet 0 put setpagedevice "
*DLSlipSheetTray AutoTray/Auto: "
    2 dict dup dup /SlipSheet 4 put
    /SlipSheetDetails 2 dict dup /AutoTraySelect 1 put dup /Type 1 put
    put setpagedevice "
*End
*DLSlipSheetTray 1stTray/Lade 1: "
    2 dict dup dup /SlipSheet 4 put
    /SlipSheetDetails 3 dict dup /AutoTraySelect 0 put
    dup /Type 1 put dup
    /SheetTray 0 put put setpagedevice "
*End
*DLSlipSheetTray 2ndTray/Lade 2: "
    2 dict dup dup /SlipSheet 4 put
    /SlipSheetDetails 3 dict dup /AutoTraySelect 0 put
    dup /Type 1 put dup
    /SheetTray 1 put put setpagedevice "
*End
*?DLSlipSheetTray: "
"
*End
*CloseUI: *DLSlipSheetTray

*OpenUI *DLSlipSheetPrint/Afdrukken op scheidingen:  Boolean
*OrderDependency: 119.0 AnySetup *DLSlipSheetPrint
*DefaultDLSlipSheetPrint: False
*DLSlipSheetPrint False/Blanco scheidingen: "
"
*End
*DLSlipSheetPrint True/Afgedrukte scheidingen: "
  /FXProcs /ProcSet resourcestatus {
    /FXProcs /ProcSet findresource /slipcopy get exec
  } if pop pop
"
*End
*?DLSlipSheetPrint: "
"
*End
*CloseUI: *DLSlipSheetPrint


*% SPS ===============
*OpenUI *DLSubPaperSelection/Vervangende lade: PickOne
*OrderDependency: 40.0 AnySetup *DLSubPaperSelection
*DefaultDLSubPaperSelection: SMH
*DLSubPaperSelection Policy0/Printerinstellingen gebruiken: "
"
*End
*DLSubPaperSelection Policy2/Bericht weergeven: "
  2 dict dup /Policies 1 dict dup /PageSize 1 put put
  dup /DeferredMediaSelection true put setpagedevice
"
*End
*DLSubPaperSelection Policy3/Gebruik eerst volgende formaat (inpassen): "
  2 dict dup /Policies 1 dict dup /PageSize 3 put put
  dup /DeferredMediaSelection false put setpagedevice
"
*End
*DLSubPaperSelection Policy5/Gebruik eerst volgende formaat (geen zoom): "
  2 dict dup /Policies 1 dict dup /PageSize 5 put put
  dup /DeferredMediaSelection false put setpagedevice
"
*End
*DLSubPaperSelection Policy4/Gebruik groter formaat (inpassen): "
  2 dict dup /Policies 1 dict dup /PageSize 4 put put
  dup /DeferredMediaSelection false put setpagedevice
"
*End
*DLSubPaperSelection Policy6/Gebruik groter formaat (geen zoom): "
  2 dict dup /Policies 1 dict dup /PageSize 6 put put
  dup /DeferredMediaSelection false put setpagedevice
"
*End
*DLSubPaperSelection SMH/Invoer van MPF: "
  2 dict dup /Policies 1 dict dup /PageSize 2 put put
  dup /DeferredMediaSelection true put setpagedevice
"
*End
*?DLSubPaperSelection: "
  save
  [(Policy0)(Policy2)(SMH)(Policy3)(Policy4)(Policy5)(Policy6)(Unknown)]
  currentpagedevice /Policies get /PageSize get get = flush
  restore
"
*End
*CloseUI: *DLSubPaperSelection

*OpenUI *DLCustomPageSizeCorrection/Automatische papierrichting aanpassen: Boolean
*OrderDependency: 1.0 Prolog *DLCustomPageSizeCorrection
*DefaultDLCustomPageSizeCorrection: True
*DLCustomPageSizeCorrection False/Uit: "userdict /4.3PPDCompliant true put"
*DLCustomPageSizeCorrection True/Aan: "userdict /4.3PPDCompliant false put"
*?DLCustomPageSizeCorrection: "
    save
    (Unknown)
    userdict /4.3PPDCompliant known
        {userdict /4.3PPDCompliant get
            {pop (False) }{pop (True)} ifelse
        } if
        = flush
    restore
"
*End
*CloseUI: *DLCustomPageSizeCorrection
*CloseGroup: AdvancedMedia

*OpenGroup: PrinterFunction/Specifieke printeropties
*OpenUI *Smoothing/Afbeeldingverbetering: Boolean
*OrderDependency: 180.0 AnySetup *Smoothing
*DefaultSmoothing: True
*Smoothing False/Uit: "
  2 dict dup /PostRenderingEnhance true put
  dup /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put
  dup /REValue 0 put
  put setpagedevice
"
*End
*Smoothing True/Aan: "
  2 dict dup /PostRenderingEnhance true put
  dup /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put
  dup /REValue 1 put
  put setpagedevice
"
*End
*?Smoothing: "
  save
    currentpagedevice /PostRenderingEnhance 2 copy known {
      get {
        currentpagedevice /PostRenderingEnhanceDetails 2 copy known
          { get dup /Type get 32 eq {
             /REValue get 1 eq
             {(True)}{(False)}ifelse
             }
             {pop (Unknown)} ifelse
          }
          { pop pop (Unknown)} ifelse
      }{(False)} ifelse
    }{(Unknown)}ifelse
    = flush
  restore
"
*End
*CloseUI: *Smoothing

*% TonerSaver Information ===================
*OpenUI *DLTonerSaver/Conceptmodus:  Boolean
*OrderDependency: 29.0 AnySetup *DLTonerSaver
*DefaultDLTonerSaver: False
*DLTonerSaver False/Uit: "1 dict dup /PostRenderingEnhanceDetails 2 dict 
dup /Type 32 put dup
/TonerSaver 0 put put setpagedevice"
*DLTonerSaver True/Aan:  "1 dict dup /PostRenderingEnhanceDetails 2 dict 
dup /Type 32 put dup
/TonerSaver 1 put put setpagedevice"
*?DLTonerSaver: "
save
  currentpagedevice /PostRenderingEnhanceDetails 2 copy known {
    get dup /Type get 32 eq {
      /TonerSaver get 1 eq
      {(True)}{(False)}ifelse
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLTonerSaver

*% Color Control ===============
*OpenUI *DLColorAjst/Kleurtransformatie: Boolean
*OrderDependency: 20.0 AnySetup *DLColorAjst
*DefaultDLColorAjst: False
*DLColorAjst False/Uit: "
    1 dict dup /UseCIEColor false put setpagedevice
"
*End
*DLColorAjst True/Aan: "
    1 dict dup /UseCIEColor true put setpagedevice
"
*End
*?DLColorAjst: "
    save
    currentpagedevice /UseCIEColor get
    {(True)}{(False)} ifelse = flush
    restore
"
*End
*CloseUI: *DLColorAjst

*OpenUI *DLSaveBlankSheet/Blanco pagina's overslaan: Boolean
*OrderDependency: 40.0 AnySetup *DLSaveBlankSheet
*DefaultDLSaveBlankSheet: False
*DLSaveBlankSheet False/Uit: ""
*DLSaveBlankSheet True/Aan: "
  /FXProcs /ProcSet resourcestatus {
    /FXProcs /ProcSet findresource /skippage get exec
  } if pop pop
"
*End
*?DLSaveBlankSheet: "
"
*End
*CloseUI: *DLSaveBlankSheet

*OpenUI *DLHalftoneMode/Halftoon schermvergrendeling: Boolean
*OrderDependency: 40.0 AnySetup *DLHalftoneMode
*DefaultDLHalftoneMode: True
*DLHalftoneMode False/Uit: "
    <</HalftoneMode 0>>setuserparams
"
*End
*DLHalftoneMode True/Aan: "
    <</HalftoneMode 1>>setuserparams
"
*End
*?DLHalftoneMode: "
  save
    [(True)(False)]
    currentuserparams
    /HalftoneMode get get = flush
  restore
"
*End
*CloseUI: *DLHalftoneMode

*OpenUI *DLMonochromePriority/Prioriteit voor het afdrukken van zwart/witdocumenten: Boolean
*OrderDependency: 145.0 AnySetup *DLMonochromePriority
*DefaultDLMonochromePriority: False
*DLMonochromePriority False/Uit: "
/Custom /ProcSet resourcestatus
 { pop pop /Custom /ProcSet findresource dup /setprocessmode known
   {/setprocessmode get 1 exch exec}{pop} ifelse
 }if
"
*End
*DLMonochromePriority True/Aan: "
/Custom /ProcSet resourcestatus
 { pop pop /Custom /ProcSet findresource dup /setprocessmode known
   {/setprocessmode get 0 exch exec}{pop} ifelse
 }if
"
*End
*?DLMonochromePriority: "
save
 /Custom /ProcSet resourcestatus
 { pop pop /Custom /ProcSet findresource dup /currentprocessmode known
   {/currentprocessmode get exec 0 eq {(True)}{(False)} ifelse}{pop 
(Unknown)} ifelse
 }if
 = flush
restore
"
*End
*CloseUI: *DLMonochromePriority

*CloseGroup: PrinterFunction

*% Font Information =====================

*FCacheSize 128Meg: 1258291
*FCacheSize 384Meg: 1258291
*FCacheSize 640Meg: 1258291
*FCacheSize 1152Meg: 1258291

*DefaultFont: Courier

*Font AlbertusMT-Italic: Standard "(001.000)" Standard ROM
*Font AlbertusMT-Light: Standard "(001.000)" Standard ROM
*Font AlbertusMT: Standard "(001.000)" Standard ROM
*Font AntiqueOlive-Bold: Standard "(501.009)" ExtendedRoman ROM
*Font AntiqueOlive-Compact: Standard "(501.008)" ExtendedRoman ROM
*Font AntiqueOlive-Italic: Standard "(501.010)" Standard ROM
*Font AntiqueOlive-Roman: Standard "(501.008)" ExtendedRoman ROM
*Font AntiqueOliveCE-Bold: Win1250 "(501.009)" ExtendedRoman ROM
*Font AntiqueOliveCE-Compact: Win1250 "(501.008)" ExtendedRoman ROM
*Font AntiqueOliveCE-Italic: Win1250 "(501.010)" ExtendedRoman ROM
*Font AntiqueOliveCE-Roman: Win1250 "(501.008)" ExtendedRoman ROM
*Font Apple-Chancery: Standard "(001.001)" ExtendedRoman ROM
*Font Apple-ChanceryCE: Win1250 "(001.001)" ExtendedRoman ROM
*Font Arial-BoldItalicMT: Standard "(501.009)" ExtendedRoman ROM
*Font Arial-BoldMT: Standard "(501.009)" ExtendedRoman ROM
*Font Arial-ItalicMT: Standard "(501.012)" ExtendedRoman ROM
*Font ArialCE-Bold: Win1250 "(501.009)" ExtendedRoman ROM
*Font ArialCE-BoldItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font ArialCE-Italic: Win1250 "(501.012)" ExtendedRoman ROM
*Font ArialCE: Win1250 "(501.009)" ExtendedRoman ROM
*Font ArialMT: Standard "(501.009)" ExtendedRoman ROM
*Font AvantGarde-Book: Standard "(501.009)" ExtendedRoman ROM
*Font AvantGarde-BookOblique: Standard "(501.009)" ExtendedRoman ROM
*Font AvantGarde-Demi: Standard "(501.010)" ExtendedRoman ROM
*Font AvantGarde-DemiOblique: Standard "(501.010)" ExtendedRoman ROM
*Font AvantGardeCE-Book: Win1250 "(501.009)" ExtendedRoman ROM
*Font AvantGardeCE-BookOblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font AvantGardeCE-Demi: Win1250 "(501.010)" ExtendedRoman ROM
*Font AvantGardeCE-DemiOblique: Win1250 "(501.010)" ExtendedRoman ROM
*Font Bodoni-Bold: Standard "(501.006)" ExtendedRoman ROM
*Font Bodoni-BoldItalic: Standard "(501.007)" ExtendedRoman ROM
*Font Bodoni-Italic: Standard "(501.007)" ExtendedRoman ROM
*Font Bodoni-Poster: Standard "(501.009)" ExtendedRoman ROM
*Font Bodoni-PosterCompressed: Standard "(501.007)" ExtendedRoman ROM
*Font Bodoni: Standard "(501.008)" ExtendedRoman ROM
*Font BodoniCE-Bold: Win1250 "(501.006)" ExtendedRoman ROM
*Font BodoniCE-BoldItalic: Win1250 "(501.007)" ExtendedRoman ROM
*Font BodoniCE-Italic: Win1250 "(501.007)" ExtendedRoman ROM
*Font BodoniCE-Poster: Win1250 "(501.009)" ExtendedRoman ROM
*Font BodoniCE-PosterCompressed: Win1250 "(501.007)" ExtendedRoman ROM
*Font BodoniCE: Win1250 "(501.008)" ExtendedRoman ROM
*Font Bookman-Demi: Standard "(501.007)" ExtendedRoman ROM
*Font Bookman-DemiItalic: Standard "(501.008)" ExtendedRoman ROM
*Font Bookman-Light: Standard "(501.006)" ExtendedRoman ROM
*Font Bookman-LightItalic: Standard "(501.007)" ExtendedRoman ROM
*Font BookmanCE-Demi: Win1250 "(501.007)" ExtendedRoman ROM
*Font BookmanCE-DemiItalic: Win1250 "(501.008)" ExtendedRoman ROM
*Font BookmanCE-Light: Win1250 "(501.006)" ExtendedRoman ROM
*Font BookmanCE-LightItalic: Win1250 "(501.007)" ExtendedRoman ROM
*Font Carta: Special "(001.001)" Special ROM
*Font Chicago: Standard "(501.011)" ExtendedRoman ROM
*Font ChicagoCE: Win1250 "(501.011)" ExtendedRoman ROM
*Font Clarendon-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font Clarendon-Light: Standard "(501.009)" ExtendedRoman ROM
*Font Clarendon: Standard "(501.009)" ExtendedRoman ROM
*Font ClarendonCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font ClarendonCE-Light: Win1250 "(501.009)" ExtendedRoman ROM
*Font ClarendonCE: Win1250 "(501.009)" ExtendedRoman ROM
*Font CooperBlack-Italic: Standard "(001.003)" Standard ROM
*Font CooperBlack: Standard "(001.003)" Standard ROM
*Font Copperplate-ThirtyThreeBC: Standard "(001.002)" Standard ROM
*Font Copperplate-ThirtyTwoBC: Standard "(001.002)" Standard ROM
*Font Coronet-Regular: Standard "(001.000)" ExtendedRoman ROM
*Font CoronetCE-Regular: Win1250 "(001.000)" ExtendedRoman ROM
*Font Courier-Bold: Standard "(501.010)" ExtendedRoman ROM
*Font Courier-BoldOblique: Standard "(501.010)" ExtendedRoman ROM
*Font Courier-Oblique: Standard "(501.010)" ExtendedRoman ROM
*Font Courier: Standard "(501.010)" ExtendedRoman ROM
*Font CourierCE-Bold: Win1250 "(501.010)" ExtendedRoman ROM
*Font CourierCE-BoldOblique: Win1250 "(501.010)" ExtendedRoman ROM
*Font CourierCE-Oblique: Win1250 "(501.010)" ExtendedRoman ROM
*Font CourierCE: Win1250 "(501.010)" ExtendedRoman ROM
*Font Eurostile-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font Eurostile-BoldExtendedTwo: Standard "(501.008)" ExtendedRoman ROM
*Font Eurostile-ExtendedTwo: Standard "(501.010)" ExtendedRoman ROM
*Font Eurostile: Standard "(501.008)" ExtendedRoman ROM
*Font EurostileCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font EurostileCE-BoldExtendedTwo: Win1250 "(501.008)" ExtendedRoman ROM
*Font EurostileCE-ExtendedTwo: Win1250 "(501.010)" ExtendedRoman ROM
*Font EurostileCE: Win1250 "(501.008)" ExtendedRoman ROM
*Font Geneva: Standard "(501.007)" ExtendedRoman ROM
*Font GenevaCE: Win1250 "(501.007)" ExtendedRoman ROM
*Font GillSans-Bold: Standard "(501.007)" ExtendedRoman ROM
*Font GillSans-BoldCondensed: Standard "(501.006)" ExtendedRoman ROM
*Font GillSans-BoldItalic: Standard "(501.008)" ExtendedRoman ROM
*Font GillSans-Condensed: Standard "(501.007)" ExtendedRoman ROM
*Font GillSans-ExtraBold: Standard "(501.008)" ExtendedRoman ROM
*Font GillSans-Italic: Standard "(501.008)" ExtendedRoman ROM
*Font GillSans-Light: Standard "(501.009)" ExtendedRoman ROM
*Font GillSans-LightItalic: Standard "(501.009)" ExtendedRoman ROM
*Font GillSans: Standard "(501.009)" ExtendedRoman ROM
*Font GillSansCE-Bold: Win1250 "(501.007)" ExtendedRoman ROM
*Font GillSansCE-BoldCondensed: Win1250 "(501.006)" ExtendedRoman ROM
*Font GillSansCE-BoldItalic: Win1250 "(501.008)" ExtendedRoman ROM
*Font GillSansCE-Condensed: Win1250 "(501.007)" ExtendedRoman ROM
*Font GillSansCE-ExtraBold: Win1250 "(501.008)" ExtendedRoman ROM
*Font GillSansCE-Italic: Win1250 "(501.008)" ExtendedRoman ROM
*Font GillSansCE-Light: Win1250 "(501.009)" ExtendedRoman ROM
*Font GillSansCE-LightItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font GillSansCE-Roman: Win1250 "(501.009)" ExtendedRoman ROM
*Font Goudy-Bold: Standard "(001.002)" Standard ROM
*Font Goudy-BoldItalic: Standard "(001.002)" Standard ROM
*Font Goudy-ExtraBold: Standard "(001.001)" Standard ROM
*Font Goudy-Italic: Standard "(001.002)" Standard ROM
*Font Goudy: Standard "(001.003)" Standard ROM
*Font Helvetica-Bold: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-BoldOblique: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-Condensed-Bold: Standard "(501.009)" ExtendedRoman ROM
*Font Helvetica-Condensed-BoldObl: Standard "(501.009)" ExtendedRoman ROM
*Font Helvetica-Condensed-Oblique: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-Condensed: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-Narrow-Bold: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-Narrow-Oblique: Standard "(501.008)" ExtendedRoman ROM
*Font Helvetica-Narrow: Standard "(501.008)" ExtendedRoman ROM
*Font Helvetica-Oblique: Standard "(501.008)" ExtendedRoman ROM
*Font Helvetica: Standard "(501.008)" ExtendedRoman ROM
*Font HelveticaCE-Bold: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-BoldOblique: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-Cond: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-CondBold: Win1250 "(501.009)" ExtendedRoman ROM
*Font HelveticaCE-CondBoldObl: Win1250 "(501.009)" ExtendedRoman ROM
*Font HelveticaCE-CondObl: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-Narrow: Win1250 "(501.008)" ExtendedRoman ROM
*Font HelveticaCE-NarrowBold: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-NarrowBoldOblique: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-NarrowOblique: Win1250 "(501.008)" ExtendedRoman ROM
*Font HelveticaCE-Oblique: Win1250 "(501.008)" ExtendedRoman ROM
*Font HelveticaCE: Win1250 "(501.008)" ExtendedRoman ROM
*Font HoeflerText-Black: Standard "(501.008)" ExtendedRoman ROM
*Font HoeflerText-BlackItalic: Standard "(501.009)" ExtendedRoman ROM
*Font HoeflerText-Italic: Standard "(501.010)" ExtendedRoman ROM
*Font HoeflerText-Ornaments: Special "(001.001)" Special ROM
*Font HoeflerText-Regular: Standard "(501.009)" ExtendedRoman ROM
*Font HoeflerTextCE-Black: Win1250 "(501.008)" ExtendedRoman ROM
*Font HoeflerTextCE-BlackItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font HoeflerTextCE-Italic: Win1250 "(501.010)" ExtendedRoman ROM
*Font HoeflerTextCE-Regular: Win1250 "(501.009)" ExtendedRoman ROM
*Font JoannaMT-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font JoannaMT-BoldItalic: Standard "(501.008)" ExtendedRoman ROM
*Font JoannaMT-Italic: Standard "(501.008)" ExtendedRoman ROM
*Font JoannaMT: Standard "(501.009)" ExtendedRoman ROM
*Font JoannaMTCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font JoannaMTCE-BoldItalic: Win1250 "(501.008)" ExtendedRoman ROM
*Font JoannaMTCE-Italic: Win1250 "(501.008)" ExtendedRoman ROM
*Font JoannaMTCE: Win1250 "(501.009)" ExtendedRoman ROM
*Font LetterGothic-Bold: Standard "(501.010)" ExtendedRoman ROM
*Font LetterGothic-BoldSlanted: Standard "(501.010)" ExtendedRoman ROM
*Font LetterGothic-Slanted: Standard "(501.010)" ExtendedRoman ROM
*Font LetterGothic: Standard "(501.009)" ExtendedRoman ROM
*Font LetterGothicCE-Bold: Win1250 "(501.010)" ExtendedRoman ROM
*Font LetterGothicCE-BoldSlanted: Win1250 "(501.010)" ExtendedRoman ROM
*Font LetterGothicCE-Slanted: Win1250 "(501.010)" ExtendedRoman ROM
*Font LetterGothicCE: Win1250 "(501.009)" ExtendedRoman ROM
*Font LubalinGraph-Book: Standard "(501.009)" ExtendedRoman ROM
*Font LubalinGraph-BookOblique: Standard "(501.009)" ExtendedRoman ROM
*Font LubalinGraph-Demi: Standard "(501.009)" ExtendedRoman ROM
*Font LubalinGraph-DemiOblique: Standard "(501.009)" ExtendedRoman ROM
*Font LubalinGraphCE-Book: Win1250 "(501.009)" ExtendedRoman ROM
*Font LubalinGraphCE-BookOblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font LubalinGraphCE-Demi: Win1250 "(501.009)" ExtendedRoman ROM
*Font LubalinGraphCE-DemiOblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font Marigold: Standard "(001.000)" Standard ROM
*Font MonaLisa-Recut: Standard "(001.000)" Standard ROM
*Font Monaco: Standard "(501.012)" ExtendedRoman ROM
*Font MonacoCE: Win1250 "(501.012)" ExtendedRoman ROM
*Font NewCenturySchlbk-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(501.009)" ExtendedRoman ROM
*Font NewCenturySchlbk-Italic: Standard "(501.011)" ExtendedRoman ROM
*Font NewCenturySchlbk-Roman: Standard "(501.008)" ExtendedRoman ROM
*Font NewCenturySchlbkCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font NewCenturySchlbkCE-BoldItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font NewCenturySchlbkCE-Italic: Win1250 "(501.011)" ExtendedRoman ROM
*Font NewCenturySchlbkCE-Roman: Win1250 "(501.008)" ExtendedRoman ROM
*Font NewYork: Standard "(501.013)" ExtendedRoman ROM
*Font NewYorkCE: Win1250 "(501.013)" ExtendedRoman ROM
*Font Optima-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font Optima-BoldItalic: Standard "(501.009)" ExtendedRoman ROM
*Font Optima-Italic: Standard "(501.010)" ExtendedRoman ROM
*Font Optima: Standard "(501.010)" ExtendedRoman ROM
*Font OptimaCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font OptimaCE-BoldItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font OptimaCE-Italic: Win1250 "(501.010)" ExtendedRoman ROM
*Font OptimaCE-Roman: Win1250 "(501.010)" ExtendedRoman ROM
*Font Oxford: Standard "(001.000)" Standard ROM
*Font Palatino-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font Palatino-BoldItalic: Standard "(501.007)" ExtendedRoman ROM
*Font Palatino-Italic: Standard "(501.008)" ExtendedRoman ROM
*Font Palatino-Roman: Standard "(501.006)" ExtendedRoman ROM
*Font PalatinoCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font PalatinoCE-BoldItalic: Win1250 "(501.007)" ExtendedRoman ROM
*Font PalatinoCE-Italic: Win1250 "(501.008)" ExtendedRoman ROM
*Font PalatinoCE-Roman: Win1250 "(501.006)" ExtendedRoman ROM
*Font StempelGaramond-Bold: Standard "(501.007)" ExtendedRoman ROM
*Font StempelGaramond-BoldItalic: Standard "(501.012)" ExtendedRoman ROM
*Font StempelGaramond-Italic: Standard "(501.009)" ExtendedRoman ROM
*Font StempelGaramond-Roman: Standard "(501.011)" ExtendedRoman ROM
*Font StempelGaramondCE-Bold: Win1250 "(501.007)" ExtendedRoman ROM
*Font StempelGaramondCE-BoldItalic: Win1250 "(501.012)" ExtendedRoman ROM
*Font StempelGaramondCE-Italic: Win1250 "(501.009)" ExtendedRoman ROM
*Font StempelGaramondCE-Roman: Win1250 "(501.011)" ExtendedRoman ROM
*Font Symbol: Special "(001.008)" Special ROM
*Font Tekton: Standard "(001.001)" Standard ROM
*Font Times-Bold: Standard "(501.009)" ExtendedRoman ROM
*Font Times-BoldItalic: Standard "(501.009)" ExtendedRoman ROM
*Font Times-Italic: Standard "(501.010)" ExtendedRoman ROM
*Font Times-Roman: Standard "(501.010)" ExtendedRoman ROM
*Font TimesCE-Bold: Win1250 "(501.009)" ExtendedRoman ROM
*Font TimesCE-BoldItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font TimesCE-Italic: Win1250 "(501.010)" ExtendedRoman ROM
*Font TimesCE-Roman: Win1250 "(501.010)" ExtendedRoman ROM
*Font TimesNewRomanCE-Bold: Win1250 "(501.009)" ExtendedRoman ROM
*Font TimesNewRomanCE-BoldItalic: Win1250 "(501.011)" ExtendedRoman ROM
*Font TimesNewRomanCE-Italic: Win1250 "(501.011)" ExtendedRoman ROM
*Font TimesNewRomanCE: Win1250 "(501.010)" ExtendedRoman ROM
*Font TimesNewRomanPS-BoldItalicMT: Standard "(501.011)" ExtendedRoman ROM
*Font TimesNewRomanPS-BoldMT: Standard "(501.009)" ExtendedRoman ROM
*Font TimesNewRomanPS-ItalicMT: Standard "(501.011)" ExtendedRoman ROM
*Font TimesNewRomanPSMT: Standard "(501.010)" ExtendedRoman ROM
*Font Univers-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font Univers-BoldExt: Standard "(501.010)" ExtendedRoman ROM
*Font Univers-BoldExtObl: Standard "(501.010)" ExtendedRoman ROM
*Font Univers-BoldOblique: Standard "(501.008)" ExtendedRoman ROM
*Font Univers-Condensed: Standard "(501.011)" ExtendedRoman ROM
*Font Univers-CondensedBold: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-CondensedBoldOblique: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-CondensedOblique: Standard "(501.011)" ExtendedRoman ROM
*Font Univers-Extended: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-ExtendedObl: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-Light: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-LightOblique: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-Oblique: Standard "(501.009)" ExtendedRoman ROM
*Font Univers: Standard "(501.009)" ExtendedRoman ROM
*Font UniversCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font UniversCE-BoldExt: Win1250 "(501.010)" ExtendedRoman ROM
*Font UniversCE-BoldExtObl: Win1250 "(501.010)" ExtendedRoman ROM
*Font UniversCE-BoldOblique: Win1250 "(501.008)" ExtendedRoman ROM
*Font UniversCE-Condensed: Win1250 "(501.011)" ExtendedRoman ROM
*Font UniversCE-CondensedBold: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-CondensedBoldOblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-CondensedOblique: Win1250 "(501.011)" ExtendedRoman ROM
*Font UniversCE-Extended: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-ExtendedObl: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-Light: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-LightOblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-Medium: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-Oblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font Wingdings-Regular: Special "(001.001)" Special ROM
*Font ZapfChancery-MediumItalic: Standard "(002.000)" ExtendedRoman ROM
*Font ZapfChanceryCE-MediumItalic: Win1250 "(002.000)" ExtendedRoman ROM
*Font ZapfDingbats: Special "(001.005S)" Special ROM
*?FontQuery: "
 save
   { count 1 gt
      { exch dup 127 string cvs (/)
        print print (:) print
        /Font resourcestatus {pop pop (Yes)} {(No)} ifelse =
      } { exit } ifelse
   } bind loop
   (*) = flush
 restore
"
*End

*?FontList: "
save
  (*) {cvn ==} 128 string /Font resourceforall
  (*) = flush
restore
"
*End

*% Printer Messages (verbatim from printer):
*Message: "%%[ exitserver: permanent state may be changed ]%%"
*Message: "%%[ Flushing: rest of job (to end-of-file) will be ignored 
]%%"
*Message: "\FontName\ not found, using Courier"

*% Status (format: %%[ status: <one of these> ] %%)
*Status: "busy"
*Status: "idle"
*Status: "initializing"
*Status: "PrinterError"
*Status: "PrinterError: belt error"
*Status: "PrinterError: belt life over"
*Status: "PrinterError: belt out"
*Status: "PrinterError: cover open"
*Status: "PrinterError: disk full"
*Status: "PrinterError: download error"
*Status: "PrinterError: error"
*Status: "PrinterError: fuser error"
*Status: "PrinterError: fuser life over"
*Status: "PrinterError: fuser out"
*Status: "PrinterError: memory full"
*Status: "PrinterError: no paper"
*Status: "PrinterError: no paper tray"
*Status: "PrinterError: NVRAM malfunction"
*Status: "PrinterError: paper jam"
*Status: "PrinterError: paper size mismatch"
*Status: "PrinterError: service call"
*Status: "PrinterError: toner error"
*Status: "PrinterError: toner life over"
*Status: "PrinterError: toner out"
*Status: "PrinterError: toner over"

*% Input Sources (format: %%[ status: <stat>; source: <one of these> ]%%)
*Source: "Parallel"
*Source: "USB"
*Source: "EtherTalk"

*% Printer Error (format: %%[ PrinterError: <one of these> ]%%)
*PrinterError: "belt error"
*PrinterError: "belt life over"
*PrinterError: "belt out"
*PrinterError: "cover open"
*PrinterError: "disk full"
*PrinterError: "download error"
*PrinterError: "error"
*PrinterError: "fuser error"
*PrinterError: "fuser life over"
*PrinterError: "fuser out"
*PrinterError: "memory full"
*PrinterError: "no paper"
*PrinterError: "no paper tray"
*PrinterError: "NVRAM malfunction"
*PrinterError: "paper jam"
*PrinterError: "paper size mismatch"
*PrinterError: "service call"
*PrinterError: "toner error"
*PrinterError: "toner life over"
*PrinterError: "toner out"
*PrinterError: "toner over"

*% Color Separation Information =====================
*%*DefaultGuaranteedMaxSeparations: 1
*%*GuaranteedMaxSeparations 4: ""
*%*GuaranteedMaxSeparations 3: ""
*%*GuaranteedMaxSeparations 2: ""
*%*GuaranteedMaxSeparations 1: ""
*%*?GuaranteedMaxSeparations: "
*%    currentpagedevice /MaxSeparations get ="
*%*End

*% Produced using PPDTool 2.3's BLDPPD43.PS file
*% Last Edit Date: 2006-03-08
*% end of PPD file

```

---

### Post by gmork123 on 2008-02-14
I downloaded the suse package from the Dell support site (08-Driver_Filter_for_Unix_Linux), converted the .rpm in that zip file with alien, and installed that package.

That package installed a /usr/share/cups/model/Dell/Dell_3115cn_MFP.ppd which I could use in the normal printer install wizard from Ubuntu. 

Now printing seems to work fine from my workstation.

greetings. Wessel

---

### Post by mptpro on 2008-03-25
Thanks nailbnny that worked!

gmork123, any chance you could send me the file you compiled?

my email is mptpro -at- gmail


thanks!

---

### Post by mini_g on 2008-04-09
Here's the where the package that's noted in the Dell website that's on the CD: */cdrom/Linux/Dell-MFP-Laser-3115cn-1.0-1.noarch.rpm* (I converted it to a tarball and attached it.)
What it has in it is the Printer Description File and two foomatic instruction files.

It inserts the following files:
/usr/share/cups/model/Dell/Dell_3115cn_MFP.ppd
/usr/share/foomatic/db/source/opt/ppd-Dell-MFP_Laser_3115cn-InputSlot.xml
/usr/share/foomatic/db/source/printer/Dell-MFP_Laser_3115cn.xml

Also, if you go to */cdrom/Users_Guide/**your language**/Frame.html*  you can access an enhanced HTML version of the manual.

And last but not least, here's the English version of nailbnny's ppd:
```
*PPD-Adobe: "4.3"
*% Adobe Systems PostScript(R) Printer Description File
*% Copyright 1987-1996 Adobe Systems Incorporated.
*% All Rights Reserved.
*% Permission is granted for redistribution of this file as
*% long as this copyright notice is intact and the contents
*% of the file is not altered in any way from its original form.
*% End of Copyright statement
*FileVersion: "1.0"
*FormatVersion: "4.3"
*LanguageEncoding: UTF-8
*LanguageVersion: English
*Manufacturer: "Dell"
*PCFileName: "DL3115CN.PPD"
*Product: "(MFP Laser 3115cn)"
*PSVersion: "(3015.103) 1"
*ShortNickName: "Dell MFP Laser 3115cn PS"
*ModelName: "Dell MFP Laser 3115cn"
*NickName: "Dell MFP Laser 3115cn v3015.103 PS"
*cupsVersion: 1.1

*% === Options and Constraints =========
*OpenGroup: InstallableOptions/Options Installed
*OpenUI *InstalledMemory/Memory Capacity: PickOne
*DefaultInstalledMemory: 1152Meg
*InstalledMemory 128Meg/Standard 128MB: ""
*InstalledMemory 384Meg/384MB: ""
*InstalledMemory 640Meg/640MB: ""
*InstalledMemory 1152Meg/1152MB: ""
*?InstalledMemory: "
    save
    (Unknown) currentsystemparams /RamSize get
    dup 134217728 eq{exch pop (128Meg) exch}if
    dup 402653184 eq{exch pop (384Meg) exch}if
    dup 671088640 eq{exch pop (640Meg) exch}if
    dup 1207959552 eq{exch pop (1152Meg) exch}if
    pop = flush
    restore
"
*End
*CloseUI: *InstalledMemory

*OpenUI *Option1/Paper Tray Configuration: PickOne
*DefaultOption1: 1TrayModule
*Option1 None/Not Available: ""
*Option1 1TrayModule/2-Tray Module: ""
*?Option1: "
    save
    currentpagedevice /InputAttributes get dup null eq
    { pop (Unknown) }
    { 1 known
        { (1TrayModule) }{(None)} ifelse
    } ifelse = flush
    restore
"
*End
*CloseUI: *Option1

*OpenUI *Option2/Storage Device: PickOne
*DefaultOption2: RAMDisk
*Option2 None/Not Available: ""
*Option2 RAMDisk/RAM Disk: ""
*?Option2: "
  save
  /FXProcs /ProcSet resourcestatus {
    pop pop /FXProcs /ProcSet findresource /currentstorage get exec
    {(RAMDisk)}{(None)} ifelse
  } {(Unknown)} ifelse = flush
  restore
"
*End
*CloseUI: *Option2

*OpenUI *Option3/Duplexer: Boolean
*DefaultOption3: True
*Option3 False/Not Available: ""
*Option3 True/Available: ""
*?Option3: "
	save
	currentpagedevice
	/Duplex known {(True)}{(False)} ifelse = flush
	restore
"
*End
*CloseUI: *Option3

*CloseGroup: InstallableOptions

*% ==== UIConstraints ===============
*% ==== OptionTray vs InputSlot ====
*UIConstraints: *Option1 None *InputSlot 2ndTray
*UIConstraints: *InputSlot 2ndTray *Option1 None

*% ==== OptionTray vs SlipSheetTray ====
*UIConstraints: *Option1 None *DLSlipSheetTray 2ndTray
*UIConstraints: *DLSlipSheetTray 2ndTray *Option1 None

*% ==== OptionDuplex vs Duplex ====
*UIConstraints: *Option3 False *Duplex DuplexNoTumble
*UIConstraints: *Option3 False *Duplex DuplexTumble
*UIConstraints: *Duplex DuplexNoTumble *Option3 False
*UIConstraints: *Duplex DuplexTumble *Option3 False

*% ==== StorageDevice vs Collate ====
*UIConstraints: *Option2 None *Collate True
*UIConstraints: *Collate True *Option2 None

*% ==== PageSize vs InputSlot ====
*UIConstraints: *PageSize Env10 *InputSlot 1stTray
*UIConstraints: *PageSize Env10 *InputSlot 2ndTray
*UIConstraints: *PageSize EnvMonarch *InputSlot 1stTray
*UIConstraints: *PageSize EnvMonarch *InputSlot 2ndTray
*UIConstraints: *PageSize EnvC5 *InputSlot 1stTray
*UIConstraints: *PageSize EnvC5 *InputSlot 2ndTray
*UIConstraints: *PageSize EnvDL *InputSlot 1stTray
*UIConstraints: *PageSize EnvDL *InputSlot 2ndTray
*UIConstraints: *PageRegion Env10 *InputSlot 1stTray
*UIConstraints: *PageRegion Env10 *InputSlot 2ndTray
*UIConstraints: *PageRegion EnvMonarch *InputSlot 1stTray
*UIConstraints: *PageRegion EnvMonarch *InputSlot 2ndTray
*UIConstraints: *PageRegion EnvC5 *InputSlot 1stTray
*UIConstraints: *PageRegion EnvC5 *InputSlot 2ndTray
*UIConstraints: *PageRegion EnvDL *InputSlot 1stTray
*UIConstraints: *PageRegion EnvDL *InputSlot 2ndTray
*UIConstraints: *InputSlot 1stTray *PageSize Env10
*UIConstraints: *InputSlot 2ndTray *PageSize Env10
*UIConstraints: *InputSlot 1stTray *PageSize EnvMonarch
*UIConstraints: *InputSlot 2ndTray *PageSize EnvMonarch
*UIConstraints: *InputSlot 1stTray *PageSize EnvC5
*UIConstraints: *InputSlot 2ndTray *PageSize EnvC5
*UIConstraints: *InputSlot 1stTray *PageSize EnvDL
*UIConstraints: *InputSlot 2ndTray *PageSize EnvDL
*UIConstraints: *InputSlot 1stTray *PageRegion Env10
*UIConstraints: *InputSlot 2ndTray *PageRegion Env10
*UIConstraints: *InputSlot 1stTray *PageRegion EnvMonarch
*UIConstraints: *InputSlot 2ndTray *PageRegion EnvMonarch
*UIConstraints: *InputSlot 1stTray *PageRegion EnvC5
*UIConstraints: *InputSlot 2ndTray *PageRegion EnvC5
*UIConstraints: *InputSlot 1stTray *PageRegion EnvDL
*UIConstraints: *InputSlot 2ndTray *PageRegion EnvDL

*% ==== PageSize vs Duplex ====
*UIConstraints: *PageSize Env10 *Duplex DuplexNoTumble
*UIConstraints: *PageSize Env10 *Duplex DuplexTumble
*UIConstraints: *PageSize EnvMonarch *Duplex DuplexNoTumble
*UIConstraints: *PageSize EnvMonarch *Duplex DuplexTumble
*UIConstraints: *PageSize EnvC5 *Duplex DuplexNoTumble
*UIConstraints: *PageSize EnvC5 *Duplex DuplexTumble
*UIConstraints: *PageSize EnvDL *Duplex DuplexNoTumble
*UIConstraints: *PageSize EnvDL *Duplex DuplexTumble
*UIConstraints: *PageRegion Env10 *Duplex DuplexNoTumble
*UIConstraints: *PageRegion Env10 *Duplex DuplexTumble
*UIConstraints: *PageRegion EnvMonarch *Duplex DuplexNoTumble
*UIConstraints: *PageRegion EnvMonarch *Duplex DuplexTumble
*UIConstraints: *PageRegion EnvC5 *Duplex DuplexNoTumble
*UIConstraints: *PageRegion EnvC5 *Duplex DuplexTumble
*UIConstraints: *PageRegion EnvDL *Duplex DuplexNoTumble
*UIConstraints: *PageRegion EnvDL *Duplex DuplexTumble
*UIConstraints: *Duplex DuplexNoTumble *PageSize Env10
*UIConstraints: *Duplex DuplexTumble *PageSize Env10
*UIConstraints: *Duplex DuplexNoTumble *PageSize EnvMonarch
*UIConstraints: *Duplex DuplexTumble *PageSize EnvMonarch
*UIConstraints: *Duplex DuplexNoTumble *PageSize EnvC5
*UIConstraints: *Duplex DuplexTumble *PageSize EnvC5
*UIConstraints: *Duplex DuplexNoTumble *PageSize EnvDL
*UIConstraints: *Duplex DuplexTumble *PageSize EnvDL
*UIConstraints: *Duplex DuplexNoTumble *PageRegion Env10
*UIConstraints: *Duplex DuplexTumble *PageRegion Env10
*UIConstraints: *Duplex DuplexNoTumble *PageRegion EnvMonarch
*UIConstraints: *Duplex DuplexTumble *PageRegion EnvMonarch
*UIConstraints: *Duplex DuplexNoTumble *PageRegion EnvC5
*UIConstraints: *Duplex DuplexTumble *PageRegion EnvC5
*UIConstraints: *Duplex DuplexNoTumble *PageRegion EnvDL
*UIConstraints: *Duplex DuplexTumble *PageRegion EnvDL

*% ==== PageSize vs SlipSheetTray ====
*UIConstraints: *PageSize Env10 *DLSlipSheetTray 1stTray
*UIConstraints: *PageSize Env10 *DLSlipSheetTray 2ndTray
*UIConstraints: *PageSize Env10 *DLSlipSheetTray AutoTray
*UIConstraints: *PageSize EnvMonarch *DLSlipSheetTray 1stTray
*UIConstraints: *PageSize EnvMonarch *DLSlipSheetTray 2ndTray
*UIConstraints: *PageSize EnvMonarch *DLSlipSheetTray AutoTray
*UIConstraints: *PageSize EnvC5 *DLSlipSheetTray 1stTray
*UIConstraints: *PageSize EnvC5 *DLSlipSheetTray 2ndTray
*UIConstraints: *PageSize EnvC5 *DLSlipSheetTray AutoTray
*UIConstraints: *PageSize EnvDL *DLSlipSheetTray 1stTray
*UIConstraints: *PageSize EnvDL *DLSlipSheetTray 2ndTray
*UIConstraints: *PageSize EnvDL *DLSlipSheetTray AutoTray
*UIConstraints: *PageRegion Env10 *DLSlipSheetTray 1stTray
*UIConstraints: *PageRegion Env10 *DLSlipSheetTray 2ndTray
*UIConstraints: *PageRegion Env10 *DLSlipSheetTray AutoTray
*UIConstraints: *PageRegion EnvMonarch *DLSlipSheetTray 1stTray
*UIConstraints: *PageRegion EnvMonarch *DLSlipSheetTray 2ndTray
*UIConstraints: *PageRegion EnvMonarch *DLSlipSheetTray AutoTray
*UIConstraints: *PageRegion EnvC5 *DLSlipSheetTray 1stTray
*UIConstraints: *PageRegion EnvC5 *DLSlipSheetTray 2ndTray
*UIConstraints: *PageRegion EnvC5 *DLSlipSheetTray AutoTray
*UIConstraints: *PageRegion EnvDL *DLSlipSheetTray 1stTray
*UIConstraints: *PageRegion EnvDL *DLSlipSheetTray 2ndTray
*UIConstraints: *PageRegion EnvDL *DLSlipSheetTray AutoTray
*UIConstraints: *DLSlipSheetTray 1stTray *PageSize Env10
*UIConstraints: *DLSlipSheetTray 2ndTray *PageSize Env10
*UIConstraints: *DLSlipSheetTray AutoTray *PageSize Env10
*UIConstraints: *DLSlipSheetTray 1stTray *PageSize EnvMonarch
*UIConstraints: *DLSlipSheetTray 2ndTray *PageSize EnvMonarch
*UIConstraints: *DLSlipSheetTray AutoTray *PageSize EnvMonarch
*UIConstraints: *DLSlipSheetTray 1stTray *PageSize EnvC5
*UIConstraints: *DLSlipSheetTray 2ndTray *PageSize EnvC5
*UIConstraints: *DLSlipSheetTray AutoTray *PageSize EnvC5
*UIConstraints: *DLSlipSheetTray 1stTray *PageSize EnvDL
*UIConstraints: *DLSlipSheetTray 2ndTray *PageSize EnvDL
*UIConstraints: *DLSlipSheetTray AutoTray *PageSize EnvDL
*UIConstraints: *DLSlipSheetTray 1stTray *PageRegion Env10
*UIConstraints: *DLSlipSheetTray 2ndTray *PageRegion Env10
*UIConstraints: *DLSlipSheetTray AutoTray *PageRegion Env10
*UIConstraints: *DLSlipSheetTray 1stTray *PageRegion EnvMonarch
*UIConstraints: *DLSlipSheetTray 2ndTray *PageRegion EnvMonarch
*UIConstraints: *DLSlipSheetTray AutoTray *PageRegion EnvMonarch
*UIConstraints: *DLSlipSheetTray 1stTray *PageRegion EnvC5
*UIConstraints: *DLSlipSheetTray 2ndTray *PageRegion EnvC5
*UIConstraints: *DLSlipSheetTray AutoTray *PageRegion EnvC5
*UIConstraints: *DLSlipSheetTray 1stTray *PageRegion EnvDL
*UIConstraints: *DLSlipSheetTray 2ndTray *PageRegion EnvDL
*UIConstraints: *DLSlipSheetTray AutoTray *PageRegion EnvDL

*% ==== PageSize vs MediaType ====
*UIConstraints: *PageSize Env10 *MediaType Stationary
*UIConstraints: *PageSize Env10 *MediaType StationaryBack
*UIConstraints: *PageSize Env10 *MediaType FinePaper
*UIConstraints: *PageSize Env10 *MediaType FinePaperBack
*UIConstraints: *PageSize Env10 *MediaType Transparency
*UIConstraints: *PageSize Env10 *MediaType LabelPaper
*UIConstraints: *PageSize EnvMonarch *MediaType Stationary
*UIConstraints: *PageSize EnvMonarch *MediaType StationaryBack
*UIConstraints: *PageSize EnvMonarch *MediaType FinePaper
*UIConstraints: *PageSize EnvMonarch *MediaType FinePaperBack
*UIConstraints: *PageSize EnvMonarch *MediaType Transparency
*UIConstraints: *PageSize EnvMonarch *MediaType LabelPaper
*UIConstraints: *PageSize EnvC5 *MediaType Stationary
*UIConstraints: *PageSize EnvC5 *MediaType StationaryBack
*UIConstraints: *PageSize EnvC5 *MediaType FinePaper
*UIConstraints: *PageSize EnvC5 *MediaType FinePaperBack
*UIConstraints: *PageSize EnvC5 *MediaType Transparency
*UIConstraints: *PageSize EnvC5 *MediaType LabelPaper
*UIConstraints: *PageSize EnvDL *MediaType Stationary
*UIConstraints: *PageSize EnvDL *MediaType StationaryBack
*UIConstraints: *PageSize EnvDL *MediaType FinePaper
*UIConstraints: *PageSize EnvDL *MediaType FinePaperBack
*UIConstraints: *PageSize EnvDL *MediaType Transparency
*UIConstraints: *PageSize EnvDL *MediaType LabelPaper
*UIConstraints: *PageRegion Env10 *MediaType Stationary
*UIConstraints: *PageRegion Env10 *MediaType StationaryBack
*UIConstraints: *PageRegion Env10 *MediaType FinePaper
*UIConstraints: *PageRegion Env10 *MediaType FinePaperBack
*UIConstraints: *PageRegion Env10 *MediaType Transparency
*UIConstraints: *PageRegion Env10 *MediaType LabelPaper
*UIConstraints: *PageRegion EnvMonarch *MediaType Stationary
*UIConstraints: *PageRegion EnvMonarch *MediaType StationaryBack
*UIConstraints: *PageRegion EnvMonarch *MediaType FinePaper
*UIConstraints: *PageRegion EnvMonarch *MediaType FinePaperBack
*UIConstraints: *PageRegion EnvMonarch *MediaType Transparency
*UIConstraints: *PageRegion EnvMonarch *MediaType LabelPaper
*UIConstraints: *PageRegion EnvC5 *MediaType Stationary
*UIConstraints: *PageRegion EnvC5 *MediaType StationaryBack
*UIConstraints: *PageRegion EnvC5 *MediaType FinePaper
*UIConstraints: *PageRegion EnvC5 *MediaType FinePaperBack
*UIConstraints: *PageRegion EnvC5 *MediaType Transparency
*UIConstraints: *PageRegion EnvC5 *MediaType LabelPaper
*UIConstraints: *PageRegion EnvDL *MediaType Stationary
*UIConstraints: *PageRegion EnvDL *MediaType StationaryBack
*UIConstraints: *PageRegion EnvDL *MediaType FinePaper
*UIConstraints: *PageRegion EnvDL *MediaType FinePaperBack
*UIConstraints: *PageRegion EnvDL *MediaType Transparency
*UIConstraints: *PageRegion EnvDL *MediaType LabelPaper
*UIConstraints: *MediaType Stationary *PageSize Env10
*UIConstraints: *MediaType StationaryBack *PageSize Env10
*UIConstraints: *MediaType FinePaper *PageSize Env10
*UIConstraints: *MediaType FinePaperBack *PageSize Env10
*UIConstraints: *MediaType Transparency *PageSize Env10
*UIConstraints: *MediaType LabelPaper *PageSize Env10
*UIConstraints: *MediaType Stationary *PageSize EnvMonarch
*UIConstraints: *MediaType StationaryBack *PageSize EnvMonarch
*UIConstraints: *MediaType FinePaper *PageSize EnvMonarch
*UIConstraints: *MediaType FinePaperBack *PageSize EnvMonarch
*UIConstraints: *MediaType Transparency *PageSize EnvMonarch
*UIConstraints: *MediaType LabelPaper *PageSize EnvMonarch
*UIConstraints: *MediaType Stationary *PageSize EnvC5
*UIConstraints: *MediaType StationaryBack *PageSize EnvC5
*UIConstraints: *MediaType FinePaper *PageSize EnvC5
*UIConstraints: *MediaType FinePaperBack *PageSize EnvC5
*UIConstraints: *MediaType Transparency *PageSize EnvC5
*UIConstraints: *MediaType LabelPaper *PageSize EnvC5
*UIConstraints: *MediaType Stationary *PageSize EnvDL
*UIConstraints: *MediaType StationaryBack *PageSize EnvDL
*UIConstraints: *MediaType FinePaper *PageSize EnvDL
*UIConstraints: *MediaType FinePaperBack *PageSize EnvDL
*UIConstraints: *MediaType Transparency *PageSize EnvDL
*UIConstraints: *MediaType LabelPaper *PageSize EnvDL
*UIConstraints: *MediaType Stationary *PageRegion Env10
*UIConstraints: *MediaType StationaryBack *PageRegion Env10
*UIConstraints: *MediaType FinePaper *PageRegion Env10
*UIConstraints: *MediaType FinePaperBack *PageRegion Env10
*UIConstraints: *MediaType Transparency *PageRegion Env10
*UIConstraints: *MediaType LabelPaper *PageRegion Env10
*UIConstraints: *MediaType Stationary *PageRegion EnvMonarch
*UIConstraints: *MediaType StationaryBack *PageRegion EnvMonarch
*UIConstraints: *MediaType FinePaper *PageRegion EnvMonarch
*UIConstraints: *MediaType FinePaperBack *PageRegion EnvMonarch
*UIConstraints: *MediaType Transparency *PageRegion EnvMonarch
*UIConstraints: *MediaType LabelPaper *PageRegion EnvMonarch
*UIConstraints: *MediaType Stationary *PageRegion EnvC5
*UIConstraints: *MediaType StationaryBack *PageRegion EnvC5
*UIConstraints: *MediaType FinePaper *PageRegion EnvC5
*UIConstraints: *MediaType FinePaperBack *PageRegion EnvC5
*UIConstraints: *MediaType Transparency *PageRegion EnvC5
*UIConstraints: *MediaType LabelPaper *PageRegion EnvC5
*UIConstraints: *MediaType Stationary *PageRegion EnvDL
*UIConstraints: *MediaType StationaryBack *PageRegion EnvDL
*UIConstraints: *MediaType FinePaper *PageRegion EnvDL
*UIConstraints: *MediaType FinePaperBack *PageRegion EnvDL
*UIConstraints: *MediaType Transparency *PageRegion EnvDL
*UIConstraints: *MediaType LabelPaper *PageRegion EnvDL

*% ==== SlipSheetTray vs InputSlot ====
*UIConstraints: *DLSlipSheetTray 1stTray *InputSlot 1stTray
*UIConstraints: *DLSlipSheetTray 1stTray *InputSlot 2ndTray
*UIConstraints: *DLSlipSheetTray 2ndTray *InputSlot 1stTray
*UIConstraints: *DLSlipSheetTray 2ndTray *InputSlot 2ndTray
*UIConstraints: *DLSlipSheetTray AutoTray *InputSlot 1stTray
*UIConstraints: *DLSlipSheetTray AutoTray *InputSlot 2ndTray
*UIConstraints: *InputSlot 1stTray *DLSlipSheetTray 1stTray
*UIConstraints: *InputSlot 2ndTray *DLSlipSheetTray 1stTray
*UIConstraints: *InputSlot 1stTray *DLSlipSheetTray 2ndTray
*UIConstraints: *InputSlot 2ndTray *DLSlipSheetTray 2ndTray
*UIConstraints: *InputSlot 1stTray *DLSlipSheetTray AutoTray
*UIConstraints: *InputSlot 2ndTray *DLSlipSheetTray AutoTray

*% ==== SlipSheetTray vs MediaType ====
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType Stationary
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType StationaryBack
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType FinePaper
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType FinePaperBack
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType ThickPaper
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType ThickPaperBack
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType ThickPaper2
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType ThickPaper2Back
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType LabelPaper
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType CoatingPaper2
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType CoatingPaper2Back
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType CoatingPaper3
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType CoatingPaper3Back
*UIConstraints: *DLSlipSheetTray 1stTray *MediaType Envelope
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType Stationary
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType StationaryBack
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType FinePaper
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType FinePaperBack
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType ThickPaper
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType ThickPaperBack
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType ThickPaper2
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType ThickPaper2Back
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType LabelPaper
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType CoatingPaper2
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType CoatingPaper2Back
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType CoatingPaper3
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType CoatingPaper3Back
*UIConstraints: *DLSlipSheetTray 2ndTray *MediaType Envelope
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType Stationary
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType StationaryBack
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType FinePaper
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType FinePaperBack
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType ThickPaper
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType ThickPaperBack
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType ThickPaper2
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType ThickPaper2Back
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType LabelPaper
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType CoatingPaper2
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType CoatingPaper2Back
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType CoatingPaper3
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType CoatingPaper3Back
*UIConstraints: *DLSlipSheetTray AutoTray *MediaType Envelope
*UIConstraints: *MediaType Stationary *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType StationaryBack *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType FinePaper *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType FinePaperBack *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType ThickPaper *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType ThickPaperBack *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType ThickPaper2 *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType ThickPaper2Back *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType LabelPaper *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType CoatingPaper2 *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType CoatingPaper2Back *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType CoatingPaper3 *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType CoatingPaper3Back *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType Envelope *DLSlipSheetTray 1stTray
*UIConstraints: *MediaType Stationary *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType StationaryBack *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType FinePaper *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType FinePaperBack *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType ThickPaper *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType ThickPaperBack *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType ThickPaper2 *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType ThickPaper2Back *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType LabelPaper *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType CoatingPaper2 *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType CoatingPaper2Back *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType CoatingPaper3 *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType CoatingPaper3Back *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType Envelope *DLSlipSheetTray 2ndTray
*UIConstraints: *MediaType Stationary *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType StationaryBack *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType FinePaper *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType FinePaperBack *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType ThickPaper *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType ThickPaperBack *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType ThickPaper2 *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType ThickPaper2Back *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType LabelPaper *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType CoatingPaper2 *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType CoatingPaper2Back *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType CoatingPaper3 *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType CoatingPaper3Back *DLSlipSheetTray AutoTray
*UIConstraints: *MediaType Envelope *DLSlipSheetTray AutoTray

*% ==== SlipSheetTray vs Duplex ====
*UIConstraints: *DLSlipSheetTray 1stTray *Duplex DuplexNoTumble
*UIConstraints: *DLSlipSheetTray 1stTray *Duplex DuplexTumble
*UIConstraints: *DLSlipSheetTray 2ndTray *Duplex DuplexNoTumble
*UIConstraints: *DLSlipSheetTray 2ndTray *Duplex DuplexTumble
*UIConstraints: *DLSlipSheetTray AutoTray *Duplex DuplexNoTumble
*UIConstraints: *DLSlipSheetTray AutoTray *Duplex DuplexTumble
*UIConstraints: *Duplex DuplexNoTumble *DLSlipSheetTray 1stTray
*UIConstraints: *Duplex DuplexTumble *DLSlipSheetTray 1stTray
*UIConstraints: *Duplex DuplexNoTumble *DLSlipSheetTray 2ndTray
*UIConstraints: *Duplex DuplexTumble *DLSlipSheetTray 2ndTray
*UIConstraints: *Duplex DuplexNoTumble *DLSlipSheetTray AutoTray
*UIConstraints: *Duplex DuplexTumble *DLSlipSheetTray AutoTray

*% ==== InputSlot vs MediaType ====
*UIConstraints: *InputSlot 1stTray *MediaType Stationary
*UIConstraints: *InputSlot 1stTray *MediaType StationaryBack
*UIConstraints: *InputSlot 1stTray *MediaType FinePaper
*UIConstraints: *InputSlot 1stTray *MediaType FinePaperBack
*UIConstraints: *InputSlot 1stTray *MediaType ThickPaper
*UIConstraints: *InputSlot 1stTray *MediaType ThickPaperBack
*UIConstraints: *InputSlot 1stTray *MediaType ThickPaper2
*UIConstraints: *InputSlot 1stTray *MediaType ThickPaper2Back
*UIConstraints: *InputSlot 1stTray *MediaType Transparency
*UIConstraints: *InputSlot 1stTray *MediaType LabelPaper
*UIConstraints: *InputSlot 1stTray *MediaType CoatingPaper2
*UIConstraints: *InputSlot 1stTray *MediaType CoatingPaper2Back
*UIConstraints: *InputSlot 1stTray *MediaType CoatingPaper3
*UIConstraints: *InputSlot 1stTray *MediaType CoatingPaper3Back
*UIConstraints: *InputSlot 1stTray *MediaType Envelope
*UIConstraints: *InputSlot 2ndTray *MediaType Stationary
*UIConstraints: *InputSlot 2ndTray *MediaType StationaryBack
*UIConstraints: *InputSlot 2ndTray *MediaType FinePaper
*UIConstraints: *InputSlot 2ndTray *MediaType FinePaperBack
*UIConstraints: *InputSlot 2ndTray *MediaType ThickPaper
*UIConstraints: *InputSlot 2ndTray *MediaType ThickPaperBack
*UIConstraints: *InputSlot 2ndTray *MediaType ThickPaper2
*UIConstraints: *InputSlot 2ndTray *MediaType ThickPaper2Back
*UIConstraints: *InputSlot 2ndTray *MediaType Transparency
*UIConstraints: *InputSlot 2ndTray *MediaType LabelPaper
*UIConstraints: *InputSlot 2ndTray *MediaType CoatingPaper2
*UIConstraints: *InputSlot 2ndTray *MediaType CoatingPaper2Back
*UIConstraints: *InputSlot 2ndTray *MediaType CoatingPaper3
*UIConstraints: *InputSlot 2ndTray *MediaType CoatingPaper3Back
*UIConstraints: *InputSlot 2ndTray *MediaType Envelope
*UIConstraints: *MediaType Stationary *InputSlot 1stTray
*UIConstraints: *MediaType StationaryBack *InputSlot 1stTray
*UIConstraints: *MediaType FinePaper *InputSlot 1stTray
*UIConstraints: *MediaType FinePaperBack *InputSlot 1stTray
*UIConstraints: *MediaType ThickPaper *InputSlot 1stTray
*UIConstraints: *MediaType ThickPaperBack *InputSlot 1stTray
*UIConstraints: *MediaType ThickPaper2 *InputSlot 1stTray
*UIConstraints: *MediaType ThickPaper2Back *InputSlot 1stTray
*UIConstraints: *MediaType Transparency *InputSlot 1stTray
*UIConstraints: *MediaType LabelPaper *InputSlot 1stTray
*UIConstraints: *MediaType CoatingPaper2 *InputSlot 1stTray
*UIConstraints: *MediaType CoatingPaper2Back *InputSlot 1stTray
*UIConstraints: *MediaType CoatingPaper3 *InputSlot 1stTray
*UIConstraints: *MediaType CoatingPaper3Back *InputSlot 1stTray
*UIConstraints: *MediaType Envelope *InputSlot 1stTray
*UIConstraints: *MediaType Stationary *InputSlot 2ndTray
*UIConstraints: *MediaType StationaryBack *InputSlot 2ndTray
*UIConstraints: *MediaType FinePaper *InputSlot 2ndTray
*UIConstraints: *MediaType FinePaperBack *InputSlot 2ndTray
*UIConstraints: *MediaType ThickPaper *InputSlot 2ndTray
*UIConstraints: *MediaType ThickPaperBack *InputSlot 2ndTray
*UIConstraints: *MediaType ThickPaper2 *InputSlot 2ndTray
*UIConstraints: *MediaType ThickPaper2Back *InputSlot 2ndTray
*UIConstraints: *MediaType Transparency *InputSlot 2ndTray
*UIConstraints: *MediaType LabelPaper *InputSlot 2ndTray
*UIConstraints: *MediaType CoatingPaper2 *InputSlot 2ndTray
*UIConstraints: *MediaType CoatingPaper2Back *InputSlot 2ndTray
*UIConstraints: *MediaType CoatingPaper3 *InputSlot 2ndTray
*UIConstraints: *MediaType CoatingPaper3Back *InputSlot 2ndTray
*UIConstraints: *MediaType Envelope *InputSlot 2ndTray

*% ==== Duplex vs MediaType ====
*UIConstraints: *Duplex DuplexNoTumble *MediaType StationaryBack
*UIConstraints: *Duplex DuplexNoTumble *MediaType FinePaperBack
*UIConstraints: *Duplex DuplexNoTumble *MediaType ThickPaperBack
*UIConstraints: *Duplex DuplexNoTumble *MediaType ThickPaper2
*UIConstraints: *Duplex DuplexNoTumble *MediaType ThickPaper2Back
*UIConstraints: *Duplex DuplexNoTumble *MediaType Transparency
*UIConstraints: *Duplex DuplexNoTumble *MediaType LabelPaper
*UIConstraints: *Duplex DuplexNoTumble *MediaType CoatingPaper2Back
*UIConstraints: *Duplex DuplexNoTumble *MediaType CoatingPaper3
*UIConstraints: *Duplex DuplexNoTumble *MediaType CoatingPaper3Back
*UIConstraints: *Duplex DuplexNoTumble *MediaType Envelope
*UIConstraints: *Duplex DuplexTumble *MediaType StationaryBack
*UIConstraints: *Duplex DuplexTumble *MediaType FinePaperBack
*UIConstraints: *Duplex DuplexTumble *MediaType ThickPaperBack
*UIConstraints: *Duplex DuplexTumble *MediaType ThickPaper2
*UIConstraints: *Duplex DuplexTumble *MediaType ThickPaper2Back
*UIConstraints: *Duplex DuplexTumble *MediaType Transparency
*UIConstraints: *Duplex DuplexTumble *MediaType LabelPaper
*UIConstraints: *Duplex DuplexTumble *MediaType CoatingPaper2Back
*UIConstraints: *Duplex DuplexTumble *MediaType CoatingPaper3
*UIConstraints: *Duplex DuplexTumble *MediaType CoatingPaper3Back
*UIConstraints: *Duplex DuplexTumble *MediaType Envelope
*UIConstraints: *MediaType StationaryBack *Duplex DuplexNoTumble
*UIConstraints: *MediaType FinePaperBack *Duplex DuplexNoTumble
*UIConstraints: *MediaType ThickPaperBack *Duplex DuplexNoTumble
*UIConstraints: *MediaType ThickPaper2 *Duplex DuplexNoTumble
*UIConstraints: *MediaType ThickPaper2Back *Duplex DuplexNoTumble
*UIConstraints: *MediaType Transparency *Duplex DuplexNoTumble
*UIConstraints: *MediaType LabelPaper *Duplex DuplexNoTumble
*UIConstraints: *MediaType CoatingPaper2Back *Duplex DuplexNoTumble
*UIConstraints: *MediaType CoatingPaper3 *Duplex DuplexNoTumble
*UIConstraints: *MediaType CoatingPaper3Back *Duplex DuplexNoTumble
*UIConstraints: *MediaType Envelope *Duplex DuplexNoTumble
*UIConstraints: *MediaType StationaryBack *Duplex DuplexTumble
*UIConstraints: *MediaType FinePaperBack *Duplex DuplexTumble
*UIConstraints: *MediaType ThickPaperBack *Duplex DuplexTumble
*UIConstraints: *MediaType ThickPaper2 *Duplex DuplexTumble
*UIConstraints: *MediaType ThickPaper2Back *Duplex DuplexTumble
*UIConstraints: *MediaType Transparency *Duplex DuplexTumble
*UIConstraints: *MediaType LabelPaper *Duplex DuplexTumble
*UIConstraints: *MediaType CoatingPaper2Back *Duplex DuplexTumble
*UIConstraints: *MediaType CoatingPaper3 *Duplex DuplexTumble
*UIConstraints: *MediaType CoatingPaper3Back *Duplex DuplexTumble
*UIConstraints: *MediaType Envelope *Duplex DuplexTumble

*% ==== LeadingEdge vs PageSize ====
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize A4
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize A4
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize A5
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize A5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize B5
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize B5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize Letter
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize Letter
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize FanFoldGermanLegal
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize FanFoldGermanLegal
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize Legal
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize Legal
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize Executive
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize Executive
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize Env10
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize Env10
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize EnvC5
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize EnvC5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize EnvMonarch
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize EnvMonarch
*UIConstraints: *DLMSILeadingEdge LongEdge *PageSize EnvDL
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageSize EnvDL
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion A4
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion A4
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion A5
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion A5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion B5
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion B5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion Letter
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion Letter
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion FanFoldGermanLegal
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion FanFoldGermanLegal
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion Legal
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion Legal
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion Executive
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion Executive
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion Env10
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion Env10
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion EnvC5
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion EnvC5
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion EnvMonarch
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion EnvMonarch
*UIConstraints: *DLMSILeadingEdge LongEdge *PageRegion EnvDL
*UIConstraints: *DLMSILeadingEdge LongEdgeR *PageRegion EnvDL
*UIConstraints: *PageSize A4 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize A4 *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageSize A5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize A5 *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageSize B5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize B5 *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageSize Letter *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize Letter *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageSize FanFoldGermanLegal *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize FanFoldGermanLegal *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageSize Legal *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize Legal *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageSize Executive *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize Executive *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageSize Env10 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize Env10 *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageSize EnvC5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize EnvC5 *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageSize EnvMonarch *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize EnvMonarch *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageSize EnvDL *DLMSILeadingEdge LongEdge
*UIConstraints: *PageSize EnvDL *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion A4 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion A4 *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion A5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion A5 *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion B5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion B5 *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion Letter *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion Letter *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion FanFoldGermanLegal *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion FanFoldGermanLegal *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion Legal *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion Legal *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion Executive *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion Executive *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion Env10 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion Env10 *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion EnvC5 *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion EnvC5 *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion EnvMonarch *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion EnvMonarch *DLMSILeadingEdge LongEdgeR
*UIConstraints: *PageRegion EnvDL *DLMSILeadingEdge LongEdge
*UIConstraints: *PageRegion EnvDL *DLMSILeadingEdge LongEdgeR

*% ==== SecurityPrint ====
*UIConstraints: *Option2 None *DLSecurityPrint Security
*UIConstraints: *DLSecurityPrint Security *Option2 None
*UIConstraints: *DLSecurityPrint Security *DLSecurityUserID None
*UIConstraints: *DLSecurityUserID None *DLSecurityPrint Security
*UIConstraints: *DLSecurityPrint Security *DLSecurityJobName None
*UIConstraints: *DLSecurityJobName None *DLSecurityPrint Security

*UIConstraints: *DLSecurityPrint Off *DLSecurityUserID User1
*UIConstraints: *DLSecurityPrint Off *DLSecurityUserID User2
*UIConstraints: *DLSecurityPrint Off *DLSecurityUserID User3
*UIConstraints: *DLSecurityPrint Off *DLSecurityUserID User4
*UIConstraints: *DLSecurityPrint Off *DLSecurityUserID User5
*UIConstraints: *DLSecurityUserID User1 *DLSecurityPrint Off
*UIConstraints: *DLSecurityUserID User2 *DLSecurityPrint Off
*UIConstraints: *DLSecurityUserID User3 *DLSecurityPrint Off
*UIConstraints: *DLSecurityUserID User4 *DLSecurityPrint Off
*UIConstraints: *DLSecurityUserID User5 *DLSecurityPrint Off
*UIConstraints: *DLSecurityPrint Off *DLSecurityPasswd Passwd1
*UIConstraints: *DLSecurityPrint Off *DLSecurityPasswd Passwd2
*UIConstraints: *DLSecurityPrint Off *DLSecurityPasswd Passwd3
*UIConstraints: *DLSecurityPrint Off *DLSecurityPasswd Passwd4
*UIConstraints: *DLSecurityPrint Off *DLSecurityPasswd Passwd5
*UIConstraints: *DLSecurityPasswd Passwd1 *DLSecurityPrint Off
*UIConstraints: *DLSecurityPasswd Passwd2 *DLSecurityPrint Off
*UIConstraints: *DLSecurityPasswd Passwd3 *DLSecurityPrint Off
*UIConstraints: *DLSecurityPasswd Passwd4 *DLSecurityPrint Off
*UIConstraints: *DLSecurityPasswd Passwd5 *DLSecurityPrint Off
*UIConstraints: *DLSecurityPrint Off *DLSecurityJobName Document1
*UIConstraints: *DLSecurityPrint Off *DLSecurityJobName Document2
*UIConstraints: *DLSecurityPrint Off *DLSecurityJobName Document3
*UIConstraints: *DLSecurityPrint Off *DLSecurityJobName Document4
*UIConstraints: *DLSecurityPrint Off *DLSecurityJobName Document5
*UIConstraints: *DLSecurityJobName Document1 *DLSecurityPrint Off
*UIConstraints: *DLSecurityJobName Document2 *DLSecurityPrint Off
*UIConstraints: *DLSecurityJobName Document3 *DLSecurityPrint Off
*UIConstraints: *DLSecurityJobName Document4 *DLSecurityPrint Off
*UIConstraints: *DLSecurityJobName Document5 *DLSecurityPrint Off

*% JCL Information ================
*JCLBegin: "<1B>%-12345X"
*JCLToPSInterpreter: "@PJL COMMENT ===This PJL was generated by the <22>Secure Print<22> PPD for the CUPS===<0A>@PJL ENTER LANGUAGE=POSTSCRIPT<0A>"
*JCLEnd: "<04>"

*JCLOpenUI *DLSecurityPrint/Job Type: PickOne
*OrderDependency: 20.0 JCLSetup *DLSecurityPrint
*DefaultDLSecurityPrint: Off
*DLSecurityPrint Off/Normal Print: ""
*DLSecurityPrint Security/Secure Print: "@PJL SET HOLD=STORE<0A>"
*JCLCloseUI: *DLSecurityPrint		

*JCLOpenUI *DLSecurityUserID/User ID: PickOne
*OrderDependency: 21.0 JCLSetup *DLSecurityUserID
*DefaultDLSecurityUserID: None
*DLSecurityUserID None/-: ""
*DLSecurityUserID User1/User 1: "@PJL SET USERNAME=<22>User 1<22><0A>"
*DLSecurityUserID User2/User 2: "@PJL SET USERNAME=<22>User 2<22><0A>"
*DLSecurityUserID User3/User 3: "@PJL SET USERNAME=<22>User 3<22><0A>"
*DLSecurityUserID User4/User 4: "@PJL SET USERNAME=<22>User 4<22><0A>"
*DLSecurityUserID User5/User 5: "@PJL SET USERNAME=<22>User 5<22><0A>"
*JCLCloseUI: *DLSecurityUserID		

*JCLOpenUI *DLSecurityPasswd/Password: PickOne
*OrderDependency: 22.0 JCLSetup *DLSecurityPasswd
*DefaultDLSecurityPasswd: None
*DLSecurityPasswd None/-: ""
*DLSecurityPasswd Passwd1/1947: "@PJL SET HOLDTYPE=PRIVATE<0A>@PJL SET HOLDKEY=<22>QV9HQA==<22><0A>"
*DLSecurityPasswd Passwd2/3729: "@PJL SET HOLDTYPE=PRIVATE<0A>@PJL SET HOLDKEY=<22>Q1FBTg==<22><0A>"
*DLSecurityPasswd Passwd3/4197: "@PJL SET HOLDTYPE=PRIVATE<0A>@PJL SET HOLDKEY=<22>RFdKQA==<22><0A>"
*DLSecurityPasswd Passwd4/6835: "@PJL SET HOLDTYPE=PRIVATE<0A>@PJL SET HOLDKEY=<22>Rl5AQg==<22><0A>"
*DLSecurityPasswd Passwd5/9284: "@PJL SET HOLDTYPE=PRIVATE<0A>@PJL SET HOLDKEY=<22>SVRLQw==<22><0A>"
*JCLCloseUI: *DLSecurityPasswd		

*JCLOpenUI *DLSecurityJobName/Document Name: PickOne
*OrderDependency: 23.0 JCLSetup *DLSecurityJobName
*DefaultDLSecurityJobName: None
*DLSecurityJobName None/-: ""
*DLSecurityJobName Document1/Document 1: "@PJL SET JOBNAME=<22>Document 1<22><0A>"
*DLSecurityJobName Document2/Document 2: "@PJL SET JOBNAME=<22>Document 2<22><0A>"
*DLSecurityJobName Document3/Document 3: "@PJL SET JOBNAME=<22>Document 3<22><0A>"
*DLSecurityJobName Document4/Document 4: "@PJL SET JOBNAME=<22>Document 4<22><0A>"
*DLSecurityJobName Document5/Document 5: "@PJL SET JOBNAME=<22>Document 5<22><0A>"
*JCLCloseUI: *DLSecurityJobName		

*% ==== Device Capabilities ===============
*LanguageLevel: "3"
*Protocols: TBCP
*1284Modes Parallel: Compat Nibble ECP
*1284DeviceID: "MFG:Dell;CMD:PJL,RASTER,DOWNLOAD,PCLXL,PCL,POSTSCRIPT;MDL:MFP Laser 3115cn;DES:Dell MFP Laser 3115cn;CLS:PRINTER;"

*FreeVM: "11140352"
*VMOption 128Meg/Standard 128MB: "11140352"
*VMOption 384Meg/384MB: "11140352"
*VMOption 640Meg/640MB: "11140352"
*VMOption 1152Meg/1152MB: "11140352"

*ColorDevice: True
*DefaultColorSpace: CMYK
*VariablePaperSize: True
*LandscapeOrientation: Plus90
*TTRasterizer: Type42
*?TTRasterizer: "
save
    42 /FontType resourcestatus
    {pop pop (Type42)}{(No Type42)} ifelse = flush
restore
"
*End
*FileSystem: True
*?FileSystem: "
  save false
   (%disk?%)
   { currentdevparams dup /Writeable known
      { /Writeable get {pop true} if }  { pop } ifelse
    } 10 string /IODevice resourceforall
    {(True)}{(False)} ifelse = flush
 restore
"
*End

*Throughput: "30"
*Password: "()"
*ExitServer: "
 count 0 eq
 { false } { true exch startjob } ifelse
 not {
     (WARNING: Cannot modify initial VM.) =
     (Missing or invalid password.) =
     (Please contact the author of this software.) = flush quit
     } if
"
*End
*Reset: "
 count 0 eq
 { false } { true exch startjob } ifelse
 not {
    (WARNING: Cannot reset printer.) =
    (Missing or invalid password.) =
    (Please contact the author of this software.) = flush quit
    } if
 systemdict /quit get exec
 (WARNING : Printer Reset Failed.) = flush
"
*End

*DefaultResolution: 600dpi
*?Resolution: "
save
    currentpagedevice /HWResolution get dup aload pop eq
    {0 get cvi 9 string cvs print}
    {aload pop exch cvi 9 string cvs print (x) print cvi 9 string cvs print}
    ifelse (dpi) =
restore
"
*End
*AccurateScreensSupport: True
*SuggestedJobTimeout: "0"
*SuggestedWaitTimeout: "300"
*PrintPSErrors: True


*% Halftone Information ===============
*DefaultHalftoneType: 5
*ScreenFreq: "141.0"
*ScreenAngle: "45.0"
*DefaultScreenProc: Dot
*ScreenProc Dot: "{180 mul cos exch 180 mul cos add 2 div} bind"
*ScreenProc Line: "{ pop }"
*ScreenProc Ellipse: "{ dup 5 mul 8 div mul exch dup mul exch add sqrt 1 exch sub }"
*DefaultTransfer: Null
*Transfer Null: "{ }"
*Transfer Null.Inverse: "{ 1 exch sub }"


*% InputSlot Information ================
*RequiresPageRegion 1stTray: True
*RequiresPageRegion 2ndTray: True
*RequiresPageRegion BypassTray: True

*OpenUI *InputSlot/Paper Source: PickOne
*OrderDependency: 50.0 AnySetup *InputSlot
*DefaultInputSlot: AutoSelect
*InputSlot AutoSelect/Auto Select: ""
*InputSlot 1stTray/Tray 1: "
  3 dict begin
  /MediaPosition 0 def
  /DeferredMediaSelection true def
  /TraySwitch false def
  currentdict end setpagedevice
"
*End
*InputSlot 2ndTray/Tray 2: "
  3 dict begin
  /MediaPosition 1 def
  /DeferredMediaSelection true def
  /TraySwitch false def
  currentdict end setpagedevice
"
*End
*InputSlot BypassTray/MPF: "
  1 dict dup /ManualFeed true put setpagedevice
"
*End
*?InputSlot: "
"
*End
*CloseUI: *InputSlot

*OpenUI *Duplex/2 Sided Print:  PickOne
*OrderDependency: 110.0 AnySetup *Duplex
*DefaultDuplex: None
*Duplex None/1 Sided Print: "
    1 dict
    dup /Duplex false put
    setpagedevice
"
*End
*Duplex DuplexNoTumble/Flip on Long Edge: "
    2 dict dup /Duplex true put
    dup /Tumble false put setpagedevice
"
*End
*Duplex DuplexTumble/Flip on Short Edge: "
    2 dict dup /Duplex true put
    dup /Tumble true put setpagedevice
"
*End
*?Duplex: "
save
   currentpagedevice /Duplex known
   { currentpagedevice /Duplex get
       { currentpagedevice /Tumble get
          {(DuplexTumble)}{(DuplexNoTumble)}ifelse
       }
       { (None) } ifelse
   }
   { (None)}
   ifelse = flush
restore
"
*End
*CloseUI: *Duplex


*% Paper Handling ===================
*OpenUI *PageSize: PickOne
*OrderDependency: 60.0 AnySetup *PageSize
*DefaultPageSize: Letter
*PageSize A4/A4: "
    6 dict dup /PageSize [595 842] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize A5/A5: "
    6 dict dup /PageSize [420 595] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize B5/B5: "
    6 dict dup /PageSize [516 729] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize Letter/Letter (8.5 x 11 in): "
    6 dict dup /PageSize [612 792] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize FanFoldGermanLegal/Folio (8.5 x 13 in): "
    6 dict dup /PageSize [612 936] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize Legal/Legal (8.5 x 14 in): "
    6 dict dup /PageSize [612 1008] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize Executive/Executive (7.25 x 10.5 in): "
    6 dict dup /PageSize [522 756] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize Env10/Envelope #10: "
    6 dict dup /PageSize [297 684] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize EnvMonarch/Monarch: "
    6 dict dup /PageSize [279 540] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize EnvC5/C5: "
    6 dict dup /PageSize [459 649] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageSize EnvDL/DL: "
    6 dict dup /PageSize [312 624] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*?PageSize: "
  save
   currentpagedevice /PageSize get aload pop
   2 copy gt {exch} if
   (Unknown)
   11 dict
   dup [595 842] (A4) put
   dup [420 595] (A5) put
   dup [516 729] (B5) put
   dup [612 792] (Letter) put
   dup [612 936] (FanFoldGermanLegal) put
   dup [612 1008] (Legal) put
   dup [522 756] (Executive) put
   dup [297 684] (Env10) put
   dup [279 540] (EnvMonarch) put
   dup [459 649] (EnvC5) put
   dup [312 624] (EnvDL) put
   { exch aload pop 4 index sub abs 5 le exch
   5 index sub abs 5 le and
      {exch pop exit} {pop} ifelse
   } bind forall
   = flush pop pop
   restore
"
*End
*CloseUI: *PageSize

*OpenUI *PageRegion:  PickOne
*OrderDependency: 80.0 AnySetup *PageRegion
*DefaultPageRegion: Letter
*PageRegion A4/A4: "
    6 dict dup /PageSize [595 842] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion A5/A5: "
    6 dict dup /PageSize [420 595] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion B5/B5: "
    6 dict dup /PageSize [516 729] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion Letter/Letter (8.5 x 11 in): "
    6 dict dup /PageSize [612 792] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion FanFoldGermanLegal/Folio (8.5 x 13 in): "
    6 dict dup /PageSize [612 936] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion Legal/Legal (8.5 x 14 in): "
    6 dict dup /PageSize [612 1008] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion Executive/Executive (7.25 x 10.5 in): "
    6 dict dup /PageSize [522 756] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion Env10/Envelope #10: "
    6 dict dup /PageSize [297 684] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion EnvMonarch/Monarch: "
    6 dict dup /PageSize [279 540] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion EnvC5/C5: "
    6 dict dup /PageSize [459 649] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*PageRegion EnvDL/DL: "
    6 dict dup /PageSize [312 624] put dup /ImagingBBox null put
    dup /LeadingEdge null put
    dup /MediaClass null put currentpagedevice
    dup /MediaPosition get null eq
    {/Policies 2 copy known
      {get /PageSize 2 copy known
        {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
        {pop pop} ifelse
      }{pop pop} ifelse
    }{pop} ifelse setpagedevice
"
*End
*CloseUI: *PageRegion

*% The following entries provide information about specific paper keywords.
*DefaultImageableArea: Letter
*ImageableArea A4/A4: "11.62 11.62 583.38 830.38 "
*ImageableArea A5/A5: "11.62 11.62 408.38 583.38 "
*ImageableArea B5/B5: "11.62 11.62 504.38 717.38 "
*ImageableArea Letter/Letter (8.5 x 11 in): "11.62 11.62 600.38 780.38 "
*ImageableArea FanFoldGermanLegal/Folio (8.5 x 13 in): "11.62 11.62 600.38 924.38 "
*ImageableArea Legal/Legal (8.5 x 14 in): "11.62 11.62 600.38 996.38 "
*ImageableArea Executive/Executive (7.25 x 10.5 in): "11.62 11.62 510.38 744.38 "
*ImageableArea Env10/Envelope #10: "11.62 11.62 285.38 672.38 "
*ImageableArea EnvMonarch/Monarch: "11.62 11.62 267.38 528.38 "
*ImageableArea EnvC5/C5: "11.62 11.62 447.38 637.38 "
*ImageableArea EnvDL/DL: "11.62 17.29 300.38 606.71 "
*?ImageableArea: "
save
   3 dict begin
   /cvp { (                ) cvs print ( ) print } bind def
   /upperright {10000 mul floor 10000 div} bind def
   /lowerleft {10000 mul ceiling 10000 div} bind def
   newpath clippath pathbbox
   4 -2 roll exch 2 {lowerleft cvp} repeat
   exch 2 {upperright cvp} repeat (\n) print flush
   end
restore
"
*End

*% These provide the physical dimensions of the paper (by keyword)
*DefaultPaperDimension: Letter
*PaperDimension A4/A4: "595 842"
*PaperDimension A5/A5: "420 595"
*PaperDimension B5/B5: "516 729"
*PaperDimension Letter/Letter (8.5 x 11 in): "612 792"
*PaperDimension FanFoldGermanLegal/Folio (8.5 x 13 in): "612 936"
*PaperDimension Legal/Legal (8.5 x 14 in): "612 1008"
*PaperDimension Executive/Executive (7.25 x 10.5 in): "522 756"
*PaperDimension Env10/Envelope #10: "297 684"
*PaperDimension EnvMonarch/Monarch: "279 540"
*PaperDimension EnvC5/C5: "459 649"
*PaperDimension EnvDL/DL: "312 624"

*% Custom Page Sizes ===================
*% min: 216 pts x 277 pts   (76.2mm * 98mm)
*% max: 624 pts x 1008 pts  (8.66 inch * 14.00 inch)
*HWMargins: 11 11 11 11
*LeadingEdge Short: ""
*DefaultLeadingEdge: Short
*MaxMediaWidth: "624"
*MaxMediaHeight: "1008"
*NonUIOrderDependency: 80.0 AnySetup *CustomPageSize
*CustomPageSize True: "
4 dict dup /LeadingEdge null put
dup /MediaClass null put currentpagedevice
dup /MediaPosition get null eq
{/Policies 2 copy known
  {get /PageSize 2 copy known
    {get dup 3 ge exch 6 le and {dup /DeferredMediaSelection false put} if}
    {pop pop} ifelse
  }{pop pop} ifelse
}{pop} ifelse setpagedevice
userdict /4.3PPDCompliant known
    {userdict /4.3PPDCompliant get } {false} ifelse
{ % From Print Managers complying with 4.3 PPD Spec.
  pop pop pop % discard orientation & offsets
  3 dict begin
    /PageSize [
      4 -2 roll
    ] def
  /ImagingBBox null def
  currentdict end setpagedevice
}{ % From Print Managers not complying with 4.3 PPD Spec.
  pop pop pop % discard orientation & offsets
  3 dict begin
    /PageSize [
      4 -2 roll exch
    ] def
  /ImagingBBox null def
  currentdict end setpagedevice
} ifelse
"
*End
*ParamCustomPageSize Height:       1 points 277 1008
*ParamCustomPageSize Width:        2 points 216 624
*ParamCustomPageSize WidthOffset:  3 points 0 0
*ParamCustomPageSize HeightOffset: 4 points 0 0
*ParamCustomPageSize Orientation:  5 int 1 1

*OpenGroup: Graphics/Print Quality/Color
*% ColorMode Information ===================
*OpenUI *DLColorMode/Output Color:PickOne
*OrderDependency: 20.0 AnySetup *DLColorMode
*DefaultDLColorMode: Color
*DLColorMode Color/Color: "
  1 dict dup /ProcessColorModel /DeviceCMYK put setpagedevice
"
*End
*DLColorMode Black/Black: "
  1 dict dup /ProcessColorModel /DeviceGray put setpagedevice
"
*End
*?DLColorMode: "
save
  currentpagedevice /ProcessColorModel get
  cvn /DeviceGray eq {(Black)}{(Color)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLColorMode

*% OutputMode Information ===================
*OpenUI *DLOutputMode/Print Mode:PickOne
*OrderDependency: 10.0 AnySetup *DLOutputMode
*DefaultDLOutputMode: HighSpeed
*DLOutputMode HighSpeed/High Speed: "
    2 dict dup /HWResolution [600 600] put
    dup 2 dict dup /Type 26 put dup /ValuesPerColorComponent 2 put
    /DeviceRenderingInfo exch put
    setpagedevice
"
*End
*DLOutputMode HighQuality/High Quality: "
    2 dict dup /HWResolution [600 600] put
    dup 2 dict dup /Type 26 put dup /ValuesPerColorComponent 16 put
    /DeviceRenderingInfo exch put
    setpagedevice
"
*End
*?DLOutputMode: "
"
*End
*CloseUI: *DLOutputMode

*% Brightness Information ==========================
*OpenUI *DLBrightness/Brightness: PickOne
*OrderDependency: 26.0 AnySetup *DLBrightness
*DefaultDLBrightness: Normal
*DLBrightness Bright5/Brighter (+5): "1 dict dup 2 dict dup/Type 26 put dup/Brightness 5 put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Bright4/Brighter (+4): "1 dict dup 2 dict dup/Type 26 put dup/Brightness 4 put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Bright3/Brighter (+3): "1 dict dup 2 dict dup/Type 26 put dup/Brightness 3 put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Bright2/Brighter (+2): "1 dict dup 2 dict dup/Type 26 put dup/Brightness 2 put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Bright1/Brighter (+1): "1 dict dup 2 dict dup/Type 26 put dup/Brightness 1 put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Normal/Normal: "
    1 dict dup 2 dict dup/Type 26 put dup/Brightness 0 put
    /DeviceRenderingInfo exch put setpagedevice
"
*End
*DLBrightness Dark1/Darker (-1): "1 dict dup 2 dict dup/Type 26 put dup/Brightness -1 put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Dark2/Darker (-2): "1 dict dup 2 dict dup/Type 26 put dup/Brightness -2 put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Dark3/Darker (-3): "1 dict dup 2 dict dup/Type 26 put dup/Brightness -3 put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Dark4/Darker (-4): "1 dict dup 2 dict dup/Type 26 put dup/Brightness -4 put/DeviceRenderingInfo exch put setpagedevice"
*DLBrightness Dark5/Darker (-5): "1 dict dup 2 dict dup/Type 26 put dup/Brightness -5 put/DeviceRenderingInfo exch put setpagedevice"
*?DLBrightness: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /Brightness get
      11 dict
      dup 5 (Bright5) put
      dup 4 (Bright4) put
      dup 3 (Bright3) put
      dup 2 (Bright2) put
      dup 1 (Bright1) put
      dup 0 (Normal) put
      dup -1 (Dark1) put
      dup -2 (Dark2) put
      dup -3 (Dark3) put
      dup -4 (Dark4) put
      dup -5 (Dark5) put
      exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLBrightness

*% RGB Color Correction Information ==========================
*OpenUI *DLRGBImageType/Image Type: PickOne
*OrderDependency: 25.0 AnySetup *DLRGBImageType
*DefaultDLRGBImageType: sRGB
*DLRGBImageType sRGB/Normal: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 2 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBImageType Presentation/Business Graphics: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 4 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBImageType Photo/Photo: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 1 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBImageType Standard/Text: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 3 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBImageType Off/Off: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 0 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLRGBImageType: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /RGBCorrection get
      [(Off)(Photo)(sRGB)(Standard)(Presentation)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLRGBImageType

*% EngineScreen Information ===================
*OpenUI *DLEngineScreen/Screen:  PickOne
*OrderDependency: 27.0 AnySetup *DLEngineScreen
*DefaultDLEngineScreen: Auto
*DLEngineScreen Auto/Auto:  "
  1 dict dup
  /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put dup /EngineScreen 2 put put
  dup /PostRenderingEnhance true put setpagedevice
"
*End
*DLEngineScreen Screen1/Fineness:  "
  1 dict dup
  /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put dup /EngineScreen 0 put put
  dup /PostRenderingEnhance true put setpagedevice
"
*End
*DLEngineScreen Screen2/Standard:  "
  1 dict dup
  /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put dup /EngineScreen 1 put put
  dup /PostRenderingEnhance true put setpagedevice
"
*End
*DLEngineScreen Screen3/Gradation:  "
  1 dict dup
  /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put dup /EngineScreen 3 put put
  dup /PostRenderingEnhance true put setpagedevice
"
*End
*?DLEngineScreen: "
save
  currentpagedevice /PostRenderingEnhanceDetails 2 copy known {
    get dup /Type get 32 eq {
      /EngineScreen get [(Screen1) (Screen2) (Auto) (Screen3)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLEngineScreen

*OpenUI *DLColorBalanceAdjustment/Adjust Color Balance: Boolean
*OrderDependency: 40.0 AnySetup *DLColorBalanceAdjustment
*DefaultDLColorBalanceAdjustment: False
*DLColorBalanceAdjustment False/Off: "false/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorBalanceAdjustment True/On: "true/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorBalanceAdjustment
*CloseGroup: Graphics

*OpenGroup: ColorAdjustment/Color Adjustment
*OpenUI *DLRGBCorrection/RGB Color Correction: PickOne
*OrderDependency: 27.0 AnySetup *DLRGBCorrection
*DefaultDLRGBCorrection: None
*DLRGBCorrection None/None: ""
*DLRGBCorrection Perceptual/Perceptual: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 10 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBCorrection Saturation/Saturation: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 11 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBCorrection RelativeC/Relative Colorimetric: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 12 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBCorrection AbsoluteC/Absolute Colorimetric: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBCorrection 13 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLRGBCorrection: "
% TBD
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /RGBCorrection get
      10 dict
      dup 10 (Perceptual) put
      dup 11 (Saturation) put
      dup 12 (RelativeC) put
      dup 13 (AbsoluteC) put
      exch 2 copy known {get} {pop pop (None)} ifelse
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLRGBCorrection

*OpenUI *DLRGBInputProfile/RGB Profile: PickOne
*OrderDependency: 28.0 AnySetup *DLRGBInputProfile
*DefaultDLRGBInputProfile: SRGB
*DLRGBInputProfile SRGB/sRGB: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBSpace 0 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBInputProfile AdobeRGB/Adobe RGB (1998): "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBSpace 1 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLRGBInputProfile: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /RGBSpace get 
      [(SRGB) (AdobeRGB)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLRGBInputProfile

*OpenUI *DLRGBBCorrection/RGB Gamma Correction: PickOne
*OrderDependency: 26.0 AnySetup *DLRGBBCorrection
*DefaultDLRGBBCorrection: Standard
*DLRGBBCorrection Lightest/1.0: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 1 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBBCorrection Light/1.4: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 2 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBBCorrection Standard/1.8: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 3 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBBCorrection Dark/2.2: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 4 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBBCorrection Darkest/2.6: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 5 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLRGBBCorrection Off/Off: "
  1 dict dup
  2 dict dup /Type 26 put dup /GammaCorrection 0 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLRGBBCorrection: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /GammaCorrection get
      [(Off) (Lightest) (Light) (Standard) (Dark) (Darkest)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLRGBBCorrection

*OpenUI *DLColorTemperature/RGB Color Temperature: PickOne
*OrderDependency: 30.0 AnySetup *DLColorTemperature
*DefaultDLColorTemperature: TemperatureD65
*DLColorTemperature TemperatureD50/5000K (D50): "
  1 dict dup
  2 dict dup /Type 26 put dup /WhitePoint 0 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLColorTemperature TemperatureD65/6500K (D65): "
  1 dict dup
  2 dict dup /Type 26 put dup /WhitePoint 1 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLColorTemperature Temperature9300K/9300K: "
  1 dict dup
  2 dict dup /Type 26 put dup /WhitePoint 2 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLColorTemperature: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /WhitePoint get 
      [(TemperatureD50) (TemperatureD65) (Temperature9300K)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLColorTemperature

*% Gray Balance Information ===================
*OpenUI *DLGrayBalance/Gray Guaranteed: Boolean
*OrderDependency: 28.0 AnySetup *DLGrayBalance
*DefaultDLGrayBalance: True
*DLGrayBalance False/Off: "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBToK 0 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*DLGrayBalance True/On:  "
  1 dict dup
  2 dict dup /Type 26 put dup /RGBToK 1 put
  /DeviceRenderingInfo exch put
  setpagedevice
"
*End
*?DLGrayBalance: "
save
  currentpagedevice /DeviceRenderingInfo 2 copy known {
    get dup /Type get 26 eq {
      /RGBToK get
      [(False) (True) (Unknown) (Unknown)] exch get
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLGrayBalance
*CloseGroup: ColorAdjustment

*OpenGroup: DLColorBalanceGroupC/Color Balance C

*OpenUI *DLColorDensityCyanLow/Low Density (C): PickOne
*OrderDependency: 41.0 AnySetup *DLColorDensityCyanLow
*DefaultDLColorDensityCyanLow: 0
*DLColorDensityCyanLow +3/Darker (+3): "/Cyan/Low 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanLow +2/Darker (+2): "/Cyan/Low 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanLow +1/Darker (+1): "/Cyan/Low 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanLow 0/Normal: "/Cyan/Low 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanLow -1/Lighter (-1): "/Cyan/Low -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanLow -2/Lighter (-2): "/Cyan/Low -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanLow -3/Lighter (-3): "/Cyan/Low -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityCyanLow

*OpenUI *DLColorDensityCyanMid/Medium Density (C): PickOne
*OrderDependency: 42.0 AnySetup *DLColorDensityCyanMid
*DefaultDLColorDensityCyanMid: 0
*DLColorDensityCyanMid +3/Darker (+3): "/Cyan/Middle 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanMid +2/Darker (+2): "/Cyan/Middle 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanMid +1/Darker (+1): "/Cyan/Middle 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanMid 0/Normal: "/Cyan/Middle 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanMid -1/Lighter (-1): "/Cyan/Middle -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanMid -2/Lighter (-2): "/Cyan/Middle -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanMid -3/Lighter (-3): "/Cyan/Middle -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityCyanMid

*OpenUI *DLColorDensityCyanHigh/High Density (C): PickOne
*OrderDependency: 43.0 AnySetup *DLColorDensityCyanHigh
*DefaultDLColorDensityCyanHigh: 0
*DLColorDensityCyanHigh +3/Darker (+3): "/Cyan/High 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanHigh +2/Darker (+2): "/Cyan/High 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanHigh +1/Darker (+1): "/Cyan/High 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanHigh 0/Normal: "/Cyan/High 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanHigh -1/Lighter (-1): "/Cyan/High -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanHigh -2/Lighter (-2): "/Cyan/High -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityCyanHigh -3/Lighter (-3): "/Cyan/High -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityCyanHigh

*CloseGroup: DLColorBalanceGroupC
*OpenGroup: DLColorBalanceGroupM/Color Balance M
*OpenUI *DLColorDensityMagentaLow/Low Density (M): PickOne
*OrderDependency: 44.0 AnySetup *DLColorDensityMagentaLow
*DefaultDLColorDensityMagentaLow: 0
*DLColorDensityMagentaLow +3/Darker (+3): "/Magenta/Low 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaLow +2/Darker (+2): "/Magenta/Low 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaLow +1/Darker (+1): "/Magenta/Low 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaLow 0/Normal: "/Magenta/Low 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaLow -1/Lighter (-1): "/Magenta/Low -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaLow -2/Lighter (-2): "/Magenta/Low -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaLow -3/Lighter (-3): "/Magenta/Low -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityMagentaLow

*OpenUI *DLColorDensityMagentaMid/Medium Density (M): PickOne
*OrderDependency: 45.0 AnySetup *DLColorDensityMagentaMid
*DefaultDLColorDensityMagentaMid: 0
*DLColorDensityMagentaMid +3/Darker (+3): "/Magenta/Middle 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaMid +2/Darker (+2): "/Magenta/Middle 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaMid +1/Darker (+1): "/Magenta/Middle 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaMid 0/Normal: "/Magenta/Middle 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaMid -1/Lighter (-1): "/Magenta/Middle -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaMid -2/Lighter (-2): "/Magenta/Middle -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaMid -3/Lighter (-3): "/Magenta/Middle -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityMagentaMid

*OpenUI *DLColorDensityMagentaHigh/High Density (M): PickOne
*OrderDependency: 46.0 AnySetup *DLColorDensityMagentaHigh
*DefaultDLColorDensityMagentaHigh: 0
*DLColorDensityMagentaHigh +3/Darker (+3): "/Magenta/High 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaHigh +2/Darker (+2): "/Magenta/High 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaHigh +1/Darker (+1): "/Magenta/High 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaHigh 0/Normal: "/Magenta/High 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaHigh -1/Lighter (-1): "/Magenta/High -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaHigh -2/Lighter (-2): "/Magenta/High -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityMagentaHigh -3/Lighter (-3): "/Magenta/High -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityMagentaHigh

*CloseGroup: DLColorBalanceGroupM
*OpenGroup: DLColorBalanceGroupY/Color Balance Y
*OpenUI *DLColorDensityYellowLow/Low Density (Y): PickOne
*OrderDependency: 47.0 AnySetup *DLColorDensityYellowLow
*DefaultDLColorDensityYellowLow: 0
*DLColorDensityYellowLow +3/Darker (+3): "/Yellow/Low 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowLow +2/Darker (+2): "/Yellow/Low 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowLow +1/Darker (+1): "/Yellow/Low 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowLow 0/Normal: "/Yellow/Low 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowLow -1/Lighter (-1): "/Yellow/Low -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowLow -2/Lighter (-2): "/Yellow/Low -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowLow -3/Lighter (-3): "/Yellow/Low -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityYellowLow

*OpenUI *DLColorDensityYellowMid/Medium Density (Y): PickOne
*OrderDependency: 48.0 AnySetup *DLColorDensityYellowMid
*DefaultDLColorDensityYellowMid: 0
*DLColorDensityYellowMid +3/Darker (+3): "/Yellow/Middle 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowMid +2/Darker (+2): "/Yellow/Middle 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowMid +1/Darker (+1): "/Yellow/Middle 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowMid 0/Normal: "/Yellow/Middle 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowMid -1/Lighter (-1): "/Yellow/Middle -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowMid -2/Lighter (-2): "/Yellow/Middle -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowMid -3/Lighter (-3): "/Yellow/Middle -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityYellowMid

*OpenUI *DLColorDensityYellowHigh/High Density (Y): PickOne
*OrderDependency: 49.0 AnySetup *DLColorDensityYellowHigh
*DefaultDLColorDensityYellowHigh: 0
*DLColorDensityYellowHigh +3/Darker (+3): "/Yellow/High 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowHigh +2/Darker (+2): "/Yellow/High 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowHigh +1/Darker (+1): "/Yellow/High 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowHigh 0/Normal: "/Yellow/High 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowHigh -1/Lighter (-1): "/Yellow/High -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowHigh -2/Lighter (-2): "/Yellow/High -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityYellowHigh -3/Lighter (-3): "/Yellow/High -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityYellowHigh

*CloseGroup: DLColorBalanceGroupY
*OpenGroup: DLColorBalanceGroupK/Color Balance K
*OpenUI *DLColorDensityBlackLow/Low Density (K): PickOne
*OrderDependency: 50.0 AnySetup *DLColorDensityBlackLow
*DefaultDLColorDensityBlackLow: 0
*DLColorDensityBlackLow +3/Darker (+3): "/Black/Low 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackLow +2/Darker (+2): "/Black/Low 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackLow +1/Darker (+1): "/Black/Low 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackLow 0/Normal: "/Black/Low 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackLow -1/Lighter (-1): "/Black/Low -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackLow -2/Lighter (-2): "/Black/Low -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackLow -3/Lighter (-3): "/Black/Low -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityBlackLow

*OpenUI *DLColorDensityBlackMid/Medium Density (K): PickOne
*OrderDependency: 51.0 AnySetup *DLColorDensityBlackMid
*DefaultDLColorDensityBlackMid: 0
*DLColorDensityBlackMid +3/Darker (+3): "/Black/Middle 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackMid +2/Darker (+2): "/Black/Middle 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackMid +1/Darker (+1): "/Black/Middle 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackMid 0/Normal: "/Black/Middle 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackMid -1/Lighter (-1): "/Black/Middle -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackMid -2/Lighter (-2): "/Black/Middle -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackMid -3/Lighter (-3): "/Black/Middle -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityBlackMid

*OpenUI *DLColorDensityBlackHigh/High Density (K): PickOne
*OrderDependency: 52.0 AnySetup *DLColorDensityBlackHigh
*DefaultDLColorDensityBlackHigh: 0
*DLColorDensityBlackHigh +3/Darker (+3): "/Black/High 3/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackHigh +2/Darker (+2): "/Black/High 2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackHigh +1/Darker (+1): "/Black/High 1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackHigh 0/Normal: "/Black/High 0/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackHigh -1/Lighter (-1): "/Black/High -1/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackHigh -2/Lighter (-2): "/Black/High -2/Custom/ProcSet findresource/setcolorbalance get exec"
*DLColorDensityBlackHigh -3/Lighter (-3): "/Black/High -3/Custom/ProcSet findresource/setcolorbalance get exec"
*CloseUI: *DLColorDensityBlackHigh

*CloseGroup: DLColorBalanceGroupK

*OpenGroup: AdvancedMedia/Media Handling
*% LeadingEdge ===============
*OpenUI *DLMSILeadingEdge/MPF Orientation:  PickOne
*OrderDependency: 100.0 AnySetup *DLMSILeadingEdge
*DefaultDLMSILeadingEdge: ShortEdge
*DLMSILeadingEdge LongEdge/Landscape: "
  currentpagedevice /ManualFeed get {
    1 dict dup /LeadingEdge 1 put setpagedevice
  } if
"
*End
*DLMSILeadingEdge LongEdgeR/Landscape (Rotated): "
  currentpagedevice /ManualFeed get {
    1 dict dup /LeadingEdge 3 put setpagedevice
  } if
"
*End
*DLMSILeadingEdge ShortEdge/Portrait: "
  currentpagedevice /ManualFeed get {
    1 dict dup /LeadingEdge 0 put setpagedevice
  } if
"
*End
*DLMSILeadingEdge ShortEdgeR/Portrait (Rotated): "
  currentpagedevice /ManualFeed get {
    1 dict dup /LeadingEdge 2 put setpagedevice
  } if
"
*End
*?DLMSILeadingEdge: "
  save
    currentpagedevice /LeadingEdge get dup null eq
    {pop (ShortEdge)}
    {[(ShortEdge)(LongEdge)(ShortEdgeR)(LongEdgeR)] exch get} ifelse = flush
  restore
"
*End
*CloseUI: *DLMSILeadingEdge

*% Collate ===============
*OpenUI *Collate/Collate: Boolean
*OrderDependency: 15.0 AnySetup *Collate
*DefaultCollate: False
*Collate False/Off: "
        1  dict dup /Collate false put setpagedevice"
*End
*Collate True/On: "
        1  dict dup /Collate true put setpagedevice"
*End
*?Collate: "
  save
    currentpagedevice /Collate get
    {(True)} {(False)} ifelse
    = flush
  restore
"
*End
*CloseUI: *Collate

*% MediaType ===============
*OpenUI *MediaType/Paper Type (MPF):  PickOne
*OrderDependency: 90.0 AnySetup *MediaType
*DefaultMediaType: Default
*MediaType Default/Use Printer Settings: ""
*MediaType Stationary/Plain: "1 dict dup /MediaClass (stationary) put setpagedevice"
*MediaType StationaryBack/Plain - Side 2: "1 dict dup /MediaClass (stationary side2) put setpagedevice"
*MediaType FinePaper/Plain Thick: "1 dict dup /MediaClass (fine) put setpagedevice"
*MediaType FinePaperBack/Plain Thick - Side 2: "1 dict dup /MediaClass (fine side2) put setpagedevice"
*MediaType ThickPaper/Covers  (106-163g/m2): "1 dict dup /MediaClass (thick1) put setpagedevice"
*MediaType ThickPaperBack/Covers - Side 2: "1 dict dup /MediaClass (thick1 side2) put setpagedevice"
*MediaType ThickPaper2/Covers Thick  (164-216g/m2): "1 dict dup /MediaClass (thick2) put setpagedevice"
*MediaType ThickPaper2Back/Covers Thick - Side 2: "1 dict dup /MediaClass (thick2 side2) put setpagedevice"
*MediaType Transparency/Transparency: "1 dict dup /MediaClass (transparency) put setpagedevice"
*MediaType LabelPaper/Label: "1 dict dup /MediaClass (label) put setpagedevice"
*MediaType CoatingPaper2/Coated  (106-163g/m2): "1 dict dup /MediaClass (coating2) put setpagedevice"
*MediaType CoatingPaper2Back/Coated - Side 2: "1 dict dup /MediaClass (coating2 side2) put setpagedevice"
*MediaType CoatingPaper3/Coated Thick  (164-216g/m2): "1 dict dup /MediaClass (coating3) put setpagedevice"
*MediaType CoatingPaper3Back/Coated Thick - Side 2: "1 dict dup /MediaClass (coating3 side2) put setpagedevice"
*MediaType Envelope/Envelope: "1 dict dup /MediaClass (envelope) put setpagedevice"
*?MediaType: "
save
    currentpagedevice /MediaClass get dup null eq {pop (Default)}
    {dup (stationary) eq {pop (Stationary)}
     {dup (stationary side2) eq {pop (StationaryBack)}
      {dup (fine) eq {pop (FinePaper)}
       {dup (fine side2) eq {pop (FinePaperBack)}
          {dup (thickpaper1) eq{pop (ThickPaper)}
           {dup (thickpaper1 side2) eq{pop (ThickPaperBack)}
            {dup (thickpaper2) eq {pop (ThickPaper2)}
             {dup (thickpaper2 side2) eq {pop (ThickPaper2Back)}
              {dup (transparency) eq {pop (Transparency)}
               {dup (label) eq {pop (LabelPaper)}
                {dup (coating2) eq {pop (CoatingPaper2)}
                 {dup (coating2 side2) eq {pop (CoatingPaper2Back)}
                  {dup (coating3) eq {pop (CoatingPaper3)}
                   {dup (coating3 side2) eq {pop (CoatingPaper3Back)}
                        {dup (envelope) eq {pop (Envelope)}
                         {(Unknown)} ifelse
                        } ifelse
                   } ifelse
                  } ifelse
                 } ifelse
                } ifelse
               } ifelse
              } ifelse
             } ifelse
            } ifelse
           } ifelse
          } ifelse
       } ifelse
      } ifelse
     } ifelse
    } ifelse
   = flush
restore
"
*End
*CloseUI: *MediaType

*% SlipSheetTray Information ===================
*OpenUI *DLSlipSheetTray/Feed Separators from:  PickOne
*OrderDependency: 120.0 AnySetup *DLSlipSheetTray
*DefaultDLSlipSheetTray: OFF
*DLSlipSheetTray OFF/None:  "1 dict dup /SlipSheet 0 put setpagedevice "
*DLSlipSheetTray AutoTray/Auto: "
    2 dict dup dup /SlipSheet 4 put
    /SlipSheetDetails 2 dict dup /AutoTraySelect 1 put dup /Type 1 put
    put setpagedevice "
*End
*DLSlipSheetTray 1stTray/Tray 1: "
    2 dict dup dup /SlipSheet 4 put
    /SlipSheetDetails 3 dict dup /AutoTraySelect 0 put
    dup /Type 1 put dup
    /SheetTray 0 put put setpagedevice "
*End
*DLSlipSheetTray 2ndTray/Tray 2: "
    2 dict dup dup /SlipSheet 4 put
    /SlipSheetDetails 3 dict dup /AutoTraySelect 0 put
    dup /Type 1 put dup
    /SheetTray 1 put put setpagedevice "
*End
*?DLSlipSheetTray: "
"
*End
*CloseUI: *DLSlipSheetTray

*OpenUI *DLSlipSheetPrint/Print on Separators:  Boolean
*OrderDependency: 119.0 AnySetup *DLSlipSheetPrint
*DefaultDLSlipSheetPrint: False
*DLSlipSheetPrint False/Blank Separators: "
"
*End
*DLSlipSheetPrint True/Printed Separators: "
  /FXProcs /ProcSet resourcestatus {
    /FXProcs /ProcSet findresource /slipcopy get exec
  } if pop pop
"
*End
*?DLSlipSheetPrint: "
"
*End
*CloseUI: *DLSlipSheetPrint


*% SPS ===============
*OpenUI *DLSubPaperSelection/Substitute Tray: PickOne
*OrderDependency: 40.0 AnySetup *DLSubPaperSelection
*DefaultDLSubPaperSelection: SMH
*DLSubPaperSelection Policy0/Use Printer Settings: "
"
*End
*DLSubPaperSelection Policy2/Display Message: "
  2 dict dup /Policies 1 dict dup /PageSize 1 put put
  dup /DeferredMediaSelection true put setpagedevice
"
*End
*DLSubPaperSelection Policy3/Use Nearest Size (Adjust to Fit): "
  2 dict dup /Policies 1 dict dup /PageSize 3 put put
  dup /DeferredMediaSelection false put setpagedevice
"
*End
*DLSubPaperSelection Policy5/Use Nearest Size (No Zoom): "
  2 dict dup /Policies 1 dict dup /PageSize 5 put put
  dup /DeferredMediaSelection false put setpagedevice
"
*End
*DLSubPaperSelection Policy4/Use Larger Size (Adjust to Fit): "
  2 dict dup /Policies 1 dict dup /PageSize 4 put put
  dup /DeferredMediaSelection false put setpagedevice
"
*End
*DLSubPaperSelection Policy6/Use Larger Size (No Zoom): "
  2 dict dup /Policies 1 dict dup /PageSize 6 put put
  dup /DeferredMediaSelection false put setpagedevice
"
*End
*DLSubPaperSelection SMH/Feed from MPF: "
  2 dict dup /Policies 1 dict dup /PageSize 2 put put
  dup /DeferredMediaSelection true put setpagedevice
"
*End
*?DLSubPaperSelection: "
  save
  [(Policy0)(Policy2)(SMH)(Policy3)(Policy4)(Policy5)(Policy6)(Unknown)]
  currentpagedevice /Policies get /PageSize get get = flush
  restore
"
*End
*CloseUI: *DLSubPaperSelection

*OpenUI *DLCustomPageSizeCorrection/Custom Paper Auto Orientation: Boolean
*OrderDependency: 1.0 Prolog *DLCustomPageSizeCorrection
*DefaultDLCustomPageSizeCorrection: True
*DLCustomPageSizeCorrection False/Off: "userdict /4.3PPDCompliant true put"
*DLCustomPageSizeCorrection True/On: "userdict /4.3PPDCompliant false put"
*?DLCustomPageSizeCorrection: "
    save
    (Unknown)
    userdict /4.3PPDCompliant known
        {userdict /4.3PPDCompliant get
            {pop (False) }{pop (True)} ifelse
        } if
        = flush
    restore
"
*End
*CloseUI: *DLCustomPageSizeCorrection
*CloseGroup: AdvancedMedia

*OpenGroup: PrinterFunction/Printer Specific Options
*OpenUI *Smoothing/Image Enhancement: Boolean
*OrderDependency: 180.0 AnySetup *Smoothing
*DefaultSmoothing: True
*Smoothing False/Off: "
  2 dict dup /PostRenderingEnhance true put
  dup /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put
  dup /REValue 0 put
  put setpagedevice
"
*End
*Smoothing True/On: "
  2 dict dup /PostRenderingEnhance true put
  dup /PostRenderingEnhanceDetails 2 dict
  dup /Type 32 put
  dup /REValue 1 put
  put setpagedevice
"
*End
*?Smoothing: "
  save
    currentpagedevice /PostRenderingEnhance 2 copy known {
      get {
        currentpagedevice /PostRenderingEnhanceDetails 2 copy known
          { get dup /Type get 32 eq {
             /REValue get 1 eq
             {(True)}{(False)}ifelse
             }
             {pop (Unknown)} ifelse
          }
          { pop pop (Unknown)} ifelse
      }{(False)} ifelse
    }{(Unknown)}ifelse
    = flush
  restore
"
*End
*CloseUI: *Smoothing

*% TonerSaver Information ===================
*OpenUI *DLTonerSaver/Draft Mode:  Boolean
*OrderDependency: 29.0 AnySetup *DLTonerSaver
*DefaultDLTonerSaver: False
*DLTonerSaver False/Off: "1 dict dup /PostRenderingEnhanceDetails 2 dict dup /Type 32 put dup /TonerSaver 0 put put setpagedevice"
*DLTonerSaver True/On:  "1 dict dup /PostRenderingEnhanceDetails 2 dict dup /Type 32 put dup /TonerSaver 1 put put setpagedevice"
*?DLTonerSaver: "
save
  currentpagedevice /PostRenderingEnhanceDetails 2 copy known {
    get dup /Type get 32 eq {
      /TonerSaver get 1 eq
      {(True)}{(False)}ifelse
    }
    {pop (Unknown)} ifelse
  }
  {pop pop (Unknown)} ifelse
  = flush
restore
"
*End
*CloseUI: *DLTonerSaver

*% Color Control ===============
*OpenUI *DLColorAjst/Color Transformation: Boolean
*OrderDependency: 20.0 AnySetup *DLColorAjst
*DefaultDLColorAjst: False
*DLColorAjst False/Off: "
    1 dict dup /UseCIEColor false put setpagedevice
"
*End
*DLColorAjst True/On: "
    1 dict dup /UseCIEColor true put setpagedevice
"
*End
*?DLColorAjst: "
    save
    currentpagedevice /UseCIEColor get
    {(True)}{(False)} ifelse = flush
    restore
"
*End
*CloseUI: *DLColorAjst

*OpenUI *DLSaveBlankSheet/Skip Blank Pages: Boolean
*OrderDependency: 40.0 AnySetup *DLSaveBlankSheet
*DefaultDLSaveBlankSheet: False
*DLSaveBlankSheet False/Off: ""
*DLSaveBlankSheet True/On: "
  /FXProcs /ProcSet resourcestatus {
    /FXProcs /ProcSet findresource /skippage get exec
  } if pop pop
"
*End
*?DLSaveBlankSheet: "
"
*End
*CloseUI: *DLSaveBlankSheet

*OpenUI *DLHalftoneMode/Halftone Screen Lock: Boolean
*OrderDependency: 40.0 AnySetup *DLHalftoneMode
*DefaultDLHalftoneMode: True
*DLHalftoneMode False/Off: "
    <</HalftoneMode 0>>setuserparams
"
*End
*DLHalftoneMode True/On: "
    <</HalftoneMode 1>>setuserparams
"
*End
*?DLHalftoneMode: "
  save
    [(True)(False)]
    currentuserparams
    /HalftoneMode get get = flush
  restore
"
*End
*CloseUI: *DLHalftoneMode

*OpenUI *DLMonochromePriority/Priority to print of monochrome documents: Boolean
*OrderDependency: 145.0 AnySetup *DLMonochromePriority
*DefaultDLMonochromePriority: False
*DLMonochromePriority False/Off: "
/Custom /ProcSet resourcestatus
 { pop pop /Custom /ProcSet findresource dup /setprocessmode known
   {/setprocessmode get 1 exch exec}{pop} ifelse
 }if
"
*End
*DLMonochromePriority True/On: "
/Custom /ProcSet resourcestatus
 { pop pop /Custom /ProcSet findresource dup /setprocessmode known
   {/setprocessmode get 0 exch exec}{pop} ifelse
 }if
"
*End
*?DLMonochromePriority: "
save
 /Custom /ProcSet resourcestatus
 { pop pop /Custom /ProcSet findresource dup /currentprocessmode known
   {/currentprocessmode get exec 0 eq {(True)}{(False)} ifelse}{pop (Unknown)} ifelse
 }if
 = flush
restore
"
*End
*CloseUI: *DLMonochromePriority

*CloseGroup: PrinterFunction

*% Font Information =====================

*FCacheSize 128Meg: 1258291
*FCacheSize 384Meg: 1258291
*FCacheSize 640Meg: 1258291
*FCacheSize 1152Meg: 1258291

*DefaultFont: Courier

*Font AlbertusMT-Italic: Standard "(001.000)" Standard ROM
*Font AlbertusMT-Light: Standard "(001.000)" Standard ROM
*Font AlbertusMT: Standard "(001.000)" Standard ROM
*Font AntiqueOlive-Bold: Standard "(501.009)" ExtendedRoman ROM
*Font AntiqueOlive-Compact: Standard "(501.008)" ExtendedRoman ROM
*Font AntiqueOlive-Italic: Standard "(501.010)" Standard ROM
*Font AntiqueOlive-Roman: Standard "(501.008)" ExtendedRoman ROM
*Font AntiqueOliveCE-Bold: Win1250 "(501.009)" ExtendedRoman ROM
*Font AntiqueOliveCE-Compact: Win1250 "(501.008)" ExtendedRoman ROM
*Font AntiqueOliveCE-Italic: Win1250 "(501.010)" ExtendedRoman ROM
*Font AntiqueOliveCE-Roman: Win1250 "(501.008)" ExtendedRoman ROM
*Font Apple-Chancery: Standard "(001.001)" ExtendedRoman ROM
*Font Apple-ChanceryCE: Win1250 "(001.001)" ExtendedRoman ROM
*Font Arial-BoldItalicMT: Standard "(501.009)" ExtendedRoman ROM
*Font Arial-BoldMT: Standard "(501.009)" ExtendedRoman ROM
*Font Arial-ItalicMT: Standard "(501.012)" ExtendedRoman ROM
*Font ArialCE-Bold: Win1250 "(501.009)" ExtendedRoman ROM
*Font ArialCE-BoldItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font ArialCE-Italic: Win1250 "(501.012)" ExtendedRoman ROM
*Font ArialCE: Win1250 "(501.009)" ExtendedRoman ROM
*Font ArialMT: Standard "(501.009)" ExtendedRoman ROM
*Font AvantGarde-Book: Standard "(501.009)" ExtendedRoman ROM
*Font AvantGarde-BookOblique: Standard "(501.009)" ExtendedRoman ROM
*Font AvantGarde-Demi: Standard "(501.010)" ExtendedRoman ROM
*Font AvantGarde-DemiOblique: Standard "(501.010)" ExtendedRoman ROM
*Font AvantGardeCE-Book: Win1250 "(501.009)" ExtendedRoman ROM
*Font AvantGardeCE-BookOblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font AvantGardeCE-Demi: Win1250 "(501.010)" ExtendedRoman ROM
*Font AvantGardeCE-DemiOblique: Win1250 "(501.010)" ExtendedRoman ROM
*Font Bodoni-Bold: Standard "(501.006)" ExtendedRoman ROM
*Font Bodoni-BoldItalic: Standard "(501.007)" ExtendedRoman ROM
*Font Bodoni-Italic: Standard "(501.007)" ExtendedRoman ROM
*Font Bodoni-Poster: Standard "(501.009)" ExtendedRoman ROM
*Font Bodoni-PosterCompressed: Standard "(501.007)" ExtendedRoman ROM
*Font Bodoni: Standard "(501.008)" ExtendedRoman ROM
*Font BodoniCE-Bold: Win1250 "(501.006)" ExtendedRoman ROM
*Font BodoniCE-BoldItalic: Win1250 "(501.007)" ExtendedRoman ROM
*Font BodoniCE-Italic: Win1250 "(501.007)" ExtendedRoman ROM
*Font BodoniCE-Poster: Win1250 "(501.009)" ExtendedRoman ROM
*Font BodoniCE-PosterCompressed: Win1250 "(501.007)" ExtendedRoman ROM
*Font BodoniCE: Win1250 "(501.008)" ExtendedRoman ROM
*Font Bookman-Demi: Standard "(501.007)" ExtendedRoman ROM
*Font Bookman-DemiItalic: Standard "(501.008)" ExtendedRoman ROM
*Font Bookman-Light: Standard "(501.006)" ExtendedRoman ROM
*Font Bookman-LightItalic: Standard "(501.007)" ExtendedRoman ROM
*Font BookmanCE-Demi: Win1250 "(501.007)" ExtendedRoman ROM
*Font BookmanCE-DemiItalic: Win1250 "(501.008)" ExtendedRoman ROM
*Font BookmanCE-Light: Win1250 "(501.006)" ExtendedRoman ROM
*Font BookmanCE-LightItalic: Win1250 "(501.007)" ExtendedRoman ROM
*Font Carta: Special "(001.001)" Special ROM
*Font Chicago: Standard "(501.011)" ExtendedRoman ROM
*Font ChicagoCE: Win1250 "(501.011)" ExtendedRoman ROM
*Font Clarendon-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font Clarendon-Light: Standard "(501.009)" ExtendedRoman ROM
*Font Clarendon: Standard "(501.009)" ExtendedRoman ROM
*Font ClarendonCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font ClarendonCE-Light: Win1250 "(501.009)" ExtendedRoman ROM
*Font ClarendonCE: Win1250 "(501.009)" ExtendedRoman ROM
*Font CooperBlack-Italic: Standard "(001.003)" Standard ROM
*Font CooperBlack: Standard "(001.003)" Standard ROM
*Font Copperplate-ThirtyThreeBC: Standard "(001.002)" Standard ROM
*Font Copperplate-ThirtyTwoBC: Standard "(001.002)" Standard ROM
*Font Coronet-Regular: Standard "(001.000)" ExtendedRoman ROM
*Font CoronetCE-Regular: Win1250 "(001.000)" ExtendedRoman ROM
*Font Courier-Bold: Standard "(501.010)" ExtendedRoman ROM
*Font Courier-BoldOblique: Standard "(501.010)" ExtendedRoman ROM
*Font Courier-Oblique: Standard "(501.010)" ExtendedRoman ROM
*Font Courier: Standard "(501.010)" ExtendedRoman ROM
*Font CourierCE-Bold: Win1250 "(501.010)" ExtendedRoman ROM
*Font CourierCE-BoldOblique: Win1250 "(501.010)" ExtendedRoman ROM
*Font CourierCE-Oblique: Win1250 "(501.010)" ExtendedRoman ROM
*Font CourierCE: Win1250 "(501.010)" ExtendedRoman ROM
*Font Eurostile-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font Eurostile-BoldExtendedTwo: Standard "(501.008)" ExtendedRoman ROM
*Font Eurostile-ExtendedTwo: Standard "(501.010)" ExtendedRoman ROM
*Font Eurostile: Standard "(501.008)" ExtendedRoman ROM
*Font EurostileCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font EurostileCE-BoldExtendedTwo: Win1250 "(501.008)" ExtendedRoman ROM
*Font EurostileCE-ExtendedTwo: Win1250 "(501.010)" ExtendedRoman ROM
*Font EurostileCE: Win1250 "(501.008)" ExtendedRoman ROM
*Font Geneva: Standard "(501.007)" ExtendedRoman ROM
*Font GenevaCE: Win1250 "(501.007)" ExtendedRoman ROM
*Font GillSans-Bold: Standard "(501.007)" ExtendedRoman ROM
*Font GillSans-BoldCondensed: Standard "(501.006)" ExtendedRoman ROM
*Font GillSans-BoldItalic: Standard "(501.008)" ExtendedRoman ROM
*Font GillSans-Condensed: Standard "(501.007)" ExtendedRoman ROM
*Font GillSans-ExtraBold: Standard "(501.008)" ExtendedRoman ROM
*Font GillSans-Italic: Standard "(501.008)" ExtendedRoman ROM
*Font GillSans-Light: Standard "(501.009)" ExtendedRoman ROM
*Font GillSans-LightItalic: Standard "(501.009)" ExtendedRoman ROM
*Font GillSans: Standard "(501.009)" ExtendedRoman ROM
*Font GillSansCE-Bold: Win1250 "(501.007)" ExtendedRoman ROM
*Font GillSansCE-BoldCondensed: Win1250 "(501.006)" ExtendedRoman ROM
*Font GillSansCE-BoldItalic: Win1250 "(501.008)" ExtendedRoman ROM
*Font GillSansCE-Condensed: Win1250 "(501.007)" ExtendedRoman ROM
*Font GillSansCE-ExtraBold: Win1250 "(501.008)" ExtendedRoman ROM
*Font GillSansCE-Italic: Win1250 "(501.008)" ExtendedRoman ROM
*Font GillSansCE-Light: Win1250 "(501.009)" ExtendedRoman ROM
*Font GillSansCE-LightItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font GillSansCE-Roman: Win1250 "(501.009)" ExtendedRoman ROM
*Font Goudy-Bold: Standard "(001.002)" Standard ROM
*Font Goudy-BoldItalic: Standard "(001.002)" Standard ROM
*Font Goudy-ExtraBold: Standard "(001.001)" Standard ROM
*Font Goudy-Italic: Standard "(001.002)" Standard ROM
*Font Goudy: Standard "(001.003)" Standard ROM
*Font Helvetica-Bold: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-BoldOblique: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-Condensed-Bold: Standard "(501.009)" ExtendedRoman ROM
*Font Helvetica-Condensed-BoldObl: Standard "(501.009)" ExtendedRoman ROM
*Font Helvetica-Condensed-Oblique: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-Condensed: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-Narrow-Bold: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-Narrow-BoldOblique: Standard "(501.010)" ExtendedRoman ROM
*Font Helvetica-Narrow-Oblique: Standard "(501.008)" ExtendedRoman ROM
*Font Helvetica-Narrow: Standard "(501.008)" ExtendedRoman ROM
*Font Helvetica-Oblique: Standard "(501.008)" ExtendedRoman ROM
*Font Helvetica: Standard "(501.008)" ExtendedRoman ROM
*Font HelveticaCE-Bold: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-BoldOblique: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-Cond: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-CondBold: Win1250 "(501.009)" ExtendedRoman ROM
*Font HelveticaCE-CondBoldObl: Win1250 "(501.009)" ExtendedRoman ROM
*Font HelveticaCE-CondObl: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-Narrow: Win1250 "(501.008)" ExtendedRoman ROM
*Font HelveticaCE-NarrowBold: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-NarrowBoldOblique: Win1250 "(501.010)" ExtendedRoman ROM
*Font HelveticaCE-NarrowOblique: Win1250 "(501.008)" ExtendedRoman ROM
*Font HelveticaCE-Oblique: Win1250 "(501.008)" ExtendedRoman ROM
*Font HelveticaCE: Win1250 "(501.008)" ExtendedRoman ROM
*Font HoeflerText-Black: Standard "(501.008)" ExtendedRoman ROM
*Font HoeflerText-BlackItalic: Standard "(501.009)" ExtendedRoman ROM
*Font HoeflerText-Italic: Standard "(501.010)" ExtendedRoman ROM
*Font HoeflerText-Ornaments: Special "(001.001)" Special ROM
*Font HoeflerText-Regular: Standard "(501.009)" ExtendedRoman ROM
*Font HoeflerTextCE-Black: Win1250 "(501.008)" ExtendedRoman ROM
*Font HoeflerTextCE-BlackItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font HoeflerTextCE-Italic: Win1250 "(501.010)" ExtendedRoman ROM
*Font HoeflerTextCE-Regular: Win1250 "(501.009)" ExtendedRoman ROM
*Font JoannaMT-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font JoannaMT-BoldItalic: Standard "(501.008)" ExtendedRoman ROM
*Font JoannaMT-Italic: Standard "(501.008)" ExtendedRoman ROM
*Font JoannaMT: Standard "(501.009)" ExtendedRoman ROM
*Font JoannaMTCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font JoannaMTCE-BoldItalic: Win1250 "(501.008)" ExtendedRoman ROM
*Font JoannaMTCE-Italic: Win1250 "(501.008)" ExtendedRoman ROM
*Font JoannaMTCE: Win1250 "(501.009)" ExtendedRoman ROM
*Font LetterGothic-Bold: Standard "(501.010)" ExtendedRoman ROM
*Font LetterGothic-BoldSlanted: Standard "(501.010)" ExtendedRoman ROM
*Font LetterGothic-Slanted: Standard "(501.010)" ExtendedRoman ROM
*Font LetterGothic: Standard "(501.009)" ExtendedRoman ROM
*Font LetterGothicCE-Bold: Win1250 "(501.010)" ExtendedRoman ROM
*Font LetterGothicCE-BoldSlanted: Win1250 "(501.010)" ExtendedRoman ROM
*Font LetterGothicCE-Slanted: Win1250 "(501.010)" ExtendedRoman ROM
*Font LetterGothicCE: Win1250 "(501.009)" ExtendedRoman ROM
*Font LubalinGraph-Book: Standard "(501.009)" ExtendedRoman ROM
*Font LubalinGraph-BookOblique: Standard "(501.009)" ExtendedRoman ROM
*Font LubalinGraph-Demi: Standard "(501.009)" ExtendedRoman ROM
*Font LubalinGraph-DemiOblique: Standard "(501.009)" ExtendedRoman ROM
*Font LubalinGraphCE-Book: Win1250 "(501.009)" ExtendedRoman ROM
*Font LubalinGraphCE-BookOblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font LubalinGraphCE-Demi: Win1250 "(501.009)" ExtendedRoman ROM
*Font LubalinGraphCE-DemiOblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font Marigold: Standard "(001.000)" Standard ROM
*Font MonaLisa-Recut: Standard "(001.000)" Standard ROM
*Font Monaco: Standard "(501.012)" ExtendedRoman ROM
*Font MonacoCE: Win1250 "(501.012)" ExtendedRoman ROM
*Font NewCenturySchlbk-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font NewCenturySchlbk-BoldItalic: Standard "(501.009)" ExtendedRoman ROM
*Font NewCenturySchlbk-Italic: Standard "(501.011)" ExtendedRoman ROM
*Font NewCenturySchlbk-Roman: Standard "(501.008)" ExtendedRoman ROM
*Font NewCenturySchlbkCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font NewCenturySchlbkCE-BoldItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font NewCenturySchlbkCE-Italic: Win1250 "(501.011)" ExtendedRoman ROM
*Font NewCenturySchlbkCE-Roman: Win1250 "(501.008)" ExtendedRoman ROM
*Font NewYork: Standard "(501.013)" ExtendedRoman ROM
*Font NewYorkCE: Win1250 "(501.013)" ExtendedRoman ROM
*Font Optima-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font Optima-BoldItalic: Standard "(501.009)" ExtendedRoman ROM
*Font Optima-Italic: Standard "(501.010)" ExtendedRoman ROM
*Font Optima: Standard "(501.010)" ExtendedRoman ROM
*Font OptimaCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font OptimaCE-BoldItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font OptimaCE-Italic: Win1250 "(501.010)" ExtendedRoman ROM
*Font OptimaCE-Roman: Win1250 "(501.010)" ExtendedRoman ROM
*Font Oxford: Standard "(001.000)" Standard ROM
*Font Palatino-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font Palatino-BoldItalic: Standard "(501.007)" ExtendedRoman ROM
*Font Palatino-Italic: Standard "(501.008)" ExtendedRoman ROM
*Font Palatino-Roman: Standard "(501.006)" ExtendedRoman ROM
*Font PalatinoCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font PalatinoCE-BoldItalic: Win1250 "(501.007)" ExtendedRoman ROM
*Font PalatinoCE-Italic: Win1250 "(501.008)" ExtendedRoman ROM
*Font PalatinoCE-Roman: Win1250 "(501.006)" ExtendedRoman ROM
*Font StempelGaramond-Bold: Standard "(501.007)" ExtendedRoman ROM
*Font StempelGaramond-BoldItalic: Standard "(501.012)" ExtendedRoman ROM
*Font StempelGaramond-Italic: Standard "(501.009)" ExtendedRoman ROM
*Font StempelGaramond-Roman: Standard "(501.011)" ExtendedRoman ROM
*Font StempelGaramondCE-Bold: Win1250 "(501.007)" ExtendedRoman ROM
*Font StempelGaramondCE-BoldItalic: Win1250 "(501.012)" ExtendedRoman ROM
*Font StempelGaramondCE-Italic: Win1250 "(501.009)" ExtendedRoman ROM
*Font StempelGaramondCE-Roman: Win1250 "(501.011)" ExtendedRoman ROM
*Font Symbol: Special "(001.008)" Special ROM
*Font Tekton: Standard "(001.001)" Standard ROM
*Font Times-Bold: Standard "(501.009)" ExtendedRoman ROM
*Font Times-BoldItalic: Standard "(501.009)" ExtendedRoman ROM
*Font Times-Italic: Standard "(501.010)" ExtendedRoman ROM
*Font Times-Roman: Standard "(501.010)" ExtendedRoman ROM
*Font TimesCE-Bold: Win1250 "(501.009)" ExtendedRoman ROM
*Font TimesCE-BoldItalic: Win1250 "(501.009)" ExtendedRoman ROM
*Font TimesCE-Italic: Win1250 "(501.010)" ExtendedRoman ROM
*Font TimesCE-Roman: Win1250 "(501.010)" ExtendedRoman ROM
*Font TimesNewRomanCE-Bold: Win1250 "(501.009)" ExtendedRoman ROM
*Font TimesNewRomanCE-BoldItalic: Win1250 "(501.011)" ExtendedRoman ROM
*Font TimesNewRomanCE-Italic: Win1250 "(501.011)" ExtendedRoman ROM
*Font TimesNewRomanCE: Win1250 "(501.010)" ExtendedRoman ROM
*Font TimesNewRomanPS-BoldItalicMT: Standard "(501.011)" ExtendedRoman ROM
*Font TimesNewRomanPS-BoldMT: Standard "(501.009)" ExtendedRoman ROM
*Font TimesNewRomanPS-ItalicMT: Standard "(501.011)" ExtendedRoman ROM
*Font TimesNewRomanPSMT: Standard "(501.010)" ExtendedRoman ROM
*Font Univers-Bold: Standard "(501.008)" ExtendedRoman ROM
*Font Univers-BoldExt: Standard "(501.010)" ExtendedRoman ROM
*Font Univers-BoldExtObl: Standard "(501.010)" ExtendedRoman ROM
*Font Univers-BoldOblique: Standard "(501.008)" ExtendedRoman ROM
*Font Univers-Condensed: Standard "(501.011)" ExtendedRoman ROM
*Font Univers-CondensedBold: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-CondensedBoldOblique: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-CondensedOblique: Standard "(501.011)" ExtendedRoman ROM
*Font Univers-Extended: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-ExtendedObl: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-Light: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-LightOblique: Standard "(501.009)" ExtendedRoman ROM
*Font Univers-Oblique: Standard "(501.009)" ExtendedRoman ROM
*Font Univers: Standard "(501.009)" ExtendedRoman ROM
*Font UniversCE-Bold: Win1250 "(501.008)" ExtendedRoman ROM
*Font UniversCE-BoldExt: Win1250 "(501.010)" ExtendedRoman ROM
*Font UniversCE-BoldExtObl: Win1250 "(501.010)" ExtendedRoman ROM
*Font UniversCE-BoldOblique: Win1250 "(501.008)" ExtendedRoman ROM
*Font UniversCE-Condensed: Win1250 "(501.011)" ExtendedRoman ROM
*Font UniversCE-CondensedBold: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-CondensedBoldOblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-CondensedOblique: Win1250 "(501.011)" ExtendedRoman ROM
*Font UniversCE-Extended: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-ExtendedObl: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-Light: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-LightOblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-Medium: Win1250 "(501.009)" ExtendedRoman ROM
*Font UniversCE-Oblique: Win1250 "(501.009)" ExtendedRoman ROM
*Font Wingdings-Regular: Special "(001.001)" Special ROM
*Font ZapfChancery-MediumItalic: Standard "(002.000)" ExtendedRoman ROM
*Font ZapfChanceryCE-MediumItalic: Win1250 "(002.000)" ExtendedRoman ROM
*Font ZapfDingbats: Special "(001.005S)" Special ROM
*?FontQuery: "
 save
   { count 1 gt
      { exch dup 127 string cvs (/)
        print print (:) print
        /Font resourcestatus {pop pop (Yes)} {(No)} ifelse =
      } { exit } ifelse
   } bind loop
   (*) = flush
 restore
"
*End

*?FontList: "
save
  (*) {cvn ==} 128 string /Font resourceforall
  (*) = flush
restore
"
*End

*% Printer Messages (verbatim from printer):
*Message: "%%[ exitserver: permanent state may be changed ]%%"
*Message: "%%[ Flushing: rest of job (to end-of-file) will be ignored ]%%"
*Message: "\FontName\ not found, using Courier"

*% Status (format: %%[ status: <one of these> ] %%)
*Status: "busy"
*Status: "idle"
*Status: "initializing"
*Status: "PrinterError"
*Status: "PrinterError: belt error"
*Status: "PrinterError: belt life over"
*Status: "PrinterError: belt out"
*Status: "PrinterError: cover open"
*Status: "PrinterError: disk full"
*Status: "PrinterError: download error"
*Status: "PrinterError: error"
*Status: "PrinterError: fuser error"
*Status: "PrinterError: fuser life over"
*Status: "PrinterError: fuser out"
*Status: "PrinterError: memory full"
*Status: "PrinterError: no paper"
*Status: "PrinterError: no paper tray"
*Status: "PrinterError: NVRAM malfunction"
*Status: "PrinterError: paper jam"
*Status: "PrinterError: paper size mismatch"
*Status: "PrinterError: service call"
*Status: "PrinterError: toner error"
*Status: "PrinterError: toner life over"
*Status: "PrinterError: toner out"
*Status: "PrinterError: toner over"

*% Input Sources (format: %%[ status: <stat>; source: <one of these> ]%% )
*Source: "Parallel"
*Source: "USB"
*Source: "EtherTalk"

*% Printer Error (format: %%[ PrinterError: <one of these> ]%%)
*PrinterError: "belt error"
*PrinterError: "belt life over"
*PrinterError: "belt out"
*PrinterError: "cover open"
*PrinterError: "disk full"
*PrinterError: "download error"
*PrinterError: "error"
*PrinterError: "fuser error"
*PrinterError: "fuser life over"
*PrinterError: "fuser out"
*PrinterError: "memory full"
*PrinterError: "no paper"
*PrinterError: "no paper tray"
*PrinterError: "NVRAM malfunction"
*PrinterError: "paper jam"
*PrinterError: "paper size mismatch"
*PrinterError: "service call"
*PrinterError: "toner error"
*PrinterError: "toner life over"
*PrinterError: "toner out"
*PrinterError: "toner over"

*% Color Separation Information =====================
*%*DefaultGuaranteedMaxSeparations: 1
*%*GuaranteedMaxSeparations 4: ""
*%*GuaranteedMaxSeparations 3: ""
*%*GuaranteedMaxSeparations 2: ""
*%*GuaranteedMaxSeparations 1: ""
*%*?GuaranteedMaxSeparations: "
*%    currentpagedevice /MaxSeparations get ="
*%*End

*% Produced using PPDTool 2.3's BLDPPD43.PS file
*% Last Edit Date: 2006-03-08
*% end of PPD file
```

---

