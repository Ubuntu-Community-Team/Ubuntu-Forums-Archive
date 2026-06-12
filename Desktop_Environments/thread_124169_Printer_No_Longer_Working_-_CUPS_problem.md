---
title: "Printer No Longer Working - CUPS problem?"
date: 2006-01-31
forum: Desktop Environments
---

### Post by reuben on 2006-01-31
My printer used to work, but I think a recent upgrade broke it. To try and fix it I completely uninstalled and reinstalled cups. Now when I try to set it up in KDE Printing Manager, I get the following output from CUPS (logging at debug level)...what's broken?


D [31/Jan/2006:18:44:58 -0800] [Job 1] Job title: KDE Print Test
D [31/Jan/2006:18:44:58 -0800] [Job 1] File(s) to be printed: 
D [31/Jan/2006:18:44:58 -0800] [Job 1] <STDIN>
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [31/Jan/2006:18:44:58 -0800] [Job 1] Pondering option 'multiple-document-handling=separate-documents-uncollated-copies'
D [31/Jan/2006:18:44:58 -0800] [Job 1] Unknown option multiple-document-handling=separate-documents-uncollated-copies.
D [31/Jan/2006:18:44:58 -0800] [Job 1] Pondering option 'orientation-requested=3'
D [31/Jan/2006:18:44:58 -0800] [Job 1] Unknown option orientation-requested=3.
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] ================================================
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] File: <STDIN>
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] ================================================
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] Reading PostScript input ...
D [31/Jan/2006:18:44:58 -0800] [Job 1] --> This document is DSC-conforming!
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] -----------
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%BeginProlog
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%EndProlog
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] -----------
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%BeginSetup
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%BeginFeature: *REt Medium
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: REt=Medium --> Setting option
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %% FoomaticRIPOptionSetting: REt=Medium
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: REt=Medium --> Setting option
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%BeginFeature: *TonerDensity 3
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: TonerDensity=3 --> Setting option
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %% FoomaticRIPOptionSetting: TonerDensity=3
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: TonerDensity=3 --> Setting option
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%BeginFeature: *InputSlot Default
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: InputSlot=Default --> Setting option
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %% FoomaticRIPOptionSetting: InputSlot=Default
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: InputSlot=Default --> Setting option
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%BeginFeature: *Copies 1
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: Copies=1 --> Setting option
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %% FoomaticRIPOptionSetting: Copies=1
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: Copies=1 --> Setting option
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%BeginFeature: *PageRegion Letter
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: PageRegion=Letter --> Option will be set by PostScript interpreter
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%BeginFeature: *Economode Off
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: Economode=Off --> Setting option
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %% FoomaticRIPOptionSetting: Economode=Off
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: Economode=Off --> Setting option
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%BeginFeature: *Resolution 300x300dpi
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: Resolution=300x300dpi --> Option will be set by PostScript interpreter
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%EndSetup
D [31/Jan/2006:18:44:58 -0800] [Job 1] Inserting PostScript code for CUPS' page accounting
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] -----------
D [31/Jan/2006:18:44:58 -0800] [Job 1] New page:  1 1
D [31/Jan/2006:18:44:58 -0800] [Job 1] Inserting option code into "PageSetup" section.
D [31/Jan/2006:18:44:58 -0800] [Job 1] No page header or page header not DSC-conforming
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found: %%BeginFeature: *HalftoningAlgorithm Standard
D [31/Jan/2006:18:44:58 -0800] [Job 1] Option: HalftoningAlgorithm=Standard --> Option will be set by PostScript interpreter
D [31/Jan/2006:18:44:58 -0800] [Job 1] Stopping search for page header options
D [31/Jan/2006:18:44:58 -0800] [Job 1] Found:
D [31/Jan/2006:18:44:58 -0800] [Job 1] 1 xResolution NUMBER             % xResolution
D [31/Jan/2006:18:44:58 -0800] [Job 1] --> Output goes directly to the renderer now.
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] Starting renderer
D [31/Jan/2006:18:44:58 -0800] [Job 1] JCL: -12345X@PJL
D [31/Jan/2006:18:44:58 -0800] [Job 1] @PJL SET MANUALFEED=OFF
D [31/Jan/2006:18:44:58 -0800] [Job 1] @PJL SET ECONOMODE=OFF
D [31/Jan/2006:18:44:58 -0800] [Job 1] @PJL SET COPIES=1
D [31/Jan/2006:18:44:58 -0800] [Job 1] @PJL SET RET=MEDIUM
D [31/Jan/2006:18:44:58 -0800] [Job 1] @PJL SET DENSITY=3
D [31/Jan/2006:18:44:58 -0800] [Job 1] <job data> 
D [31/Jan/2006:18:44:58 -0800] [Job 1] -12345X@PJL RESET
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] renderer PID kid4=12066
D [31/Jan/2006:18:44:58 -0800] [Job 1] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=ljet4 -sOutputFile=- - | perl -p -0033 -e " s/^&l\d+[aA]/$&/; " 
D [31/Jan/2006:18:44:58 -0800] [Job 1] 
D [31/Jan/2006:18:44:58 -0800] [Job 1] Closing renderer
D [31/Jan/2006:18:44:58 -0800] [Job 1] perl: warning: Setting locale failed.
D [31/Jan/2006:18:44:58 -0800] [Job 1] perl: warning: Please check that your locale settings:
D [31/Jan/2006:18:44:58 -0800] [Job 1] LANGUAGE = (unset),
D [31/Jan/2006:18:44:58 -0800] [Job 1] LC_ALL = (unset),
D [31/Jan/2006:18:44:58 -0800] [Job 1] LANG = "en_US"
D [31/Jan/2006:18:44:58 -0800] [Job 1] are supported and installed on your system.
D [31/Jan/2006:18:44:58 -0800] [Job 1] perl: warning: Falling back to the standard locale ("C").
D [31/Jan/2006:18:44:58 -0800] [Job 1] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dNOPAUSE' '-sDEVICE=ljet4' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [31/Jan/2006:18:44:58 -0800] [Job 1] sh: gs: command not found
D [31/Jan/2006:18:44:58 -0800] [Job 1] perl: warning: Setting locale failed.
D [31/Jan/2006:18:44:58 -0800] [Job 1] perl: warning: Please check that your locale settings:
D [31/Jan/2006:18:44:58 -0800] [Job 1] LANGUAGE = (unset),
D [31/Jan/2006:18:44:58 -0800] [Job 1] LC_ALL = (unset),
D [31/Jan/2006:18:44:58 -0800] [Job 1] LANG = "en_US"
D [31/Jan/2006:18:44:58 -0800] [Job 1] are supported and installed on your system.
D [31/Jan/2006:18:44:58 -0800] [Job 1] perl: warning: Falling back to the standard locale ("C").
D [31/Jan/2006:18:44:58 -0800] [Job 1] KID3 exited with status 0
D [31/Jan/2006:18:44:58 -0800] [Job 1] KID4 exited with status 9
D [31/Jan/2006:18:44:58 -0800] [Job 1] Renderer exit stat: 9
D [31/Jan/2006:18:44:58 -0800] [Job 1] Process dying with "error closing *main::STDOUT", exit stat: 9
D [31/Jan/2006:18:44:58 -0800] [Job 1] error: Broken pipe (32)
D [31/Jan/2006:18:44:58 -0800] [Job 1] error closing *main::STDOUT
D [31/Jan/2006:18:44:58 -0800] [Job 1] KID3 finished
D [31/Jan/2006:18:44:58 -0800] [Job 1] Renderer process finished
D [31/Jan/2006:18:44:58 -0800] [Job 1] Killing process 12065 (KID3)
D [31/Jan/2006:18:44:58 -0800] [Job 1] Process dying with "Error closing renderer", exit stat: 9
D [31/Jan/2006:18:44:58 -0800] [Job 1] error: Bad file descriptor (9)
D [31/Jan/2006:18:44:58 -0800] [Job 1] Error closing renderer
E [31/Jan/2006:18:44:58 -0800] PID 12063 stopped with status 9!
D [31/Jan/2006:18:44:58 -0800] UpdateJob: job 1, file 0 is complete.
D [31/Jan/2006:18:44:58 -0800] StopJob: id = 1, force = 0
I [31/Jan/2006:18:44:58 -0800] Saving printers.conf...
D [31/Jan/2006:18:44:58 -0800] StopJob: printer state is 5

---

### Post by reuben on 2006-02-02
Anybody? This is really driving me nuts. 

Thanks

---

### Post by gamma on 2006-02-02
[https://lists.ubuntu.com/archives/ubuntu-users/2005-April/032142.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-April/032142.html)
Someone had this issue, and fixed it by reinstalling cupsys, try again and see if that fixes it for you. Make sure you sudo /etc/init.d/cupsys restart too.

---

### Post by reuben on 2006-02-02
Thanks, now it's working. 

I had reinstalled cupsys before, but did it once again -- this time I also installed libgnome2-perl (and all the crap it depends on), hpijs, and some extra foomatic crappola. Printing is sure a mess in linux...

---

### Post by apswartz on 2006-02-03
" Printing is sure a mess in linux..."

Not really. Maybe in Ubuntu. I run three boxes with Ubunu/Kubuntu and two with Mandrake. Never have printer problems in Mandrake. I'm not sure why that is.

---

### Post by mancho42 on 2006-04-29
I've been having some problems with CUPS in the Dapper Beta release, it all worked just fine with Breezy but in the Beta release the CUPS admin web page won't allow me to login to administer the setup, even as root! I cured most of the problems by hand editing the cupsd.conf file, local printing was fine then but it refused to print across the network.

It seems that in the Dapper Beta release the CUPS setup doesn't allocate a default printer, even when there is only one printer attached! I've worked around this by logging in after booting the computer and typing sudo lpoptions -d <printer name> followed by sudo /etc/init.d/cupsys restart in a terminal. Now all I have to do is to get those 2 commands issued during the boot process.

---

### Post by linuxfanatic1024 on 2006-05-12
[QUOTE=mancho42]I've been having some problems with CUPS in the Dapper Beta release, it all worked just fine with Breezy but in the Beta release the CUPS admin web page won't allow me to login to administer the setup, even as root! I cured most of the problems by hand editing the cupsd.conf file, local printing was fine then but it refused to print across the network.

It seems that in the Dapper Beta release the CUPS setup doesn't allocate a default printer, even when there is only one printer attached! I've worked around this by logging in after booting the computer and typing sudo lpoptions -d <printer name> followed by sudo /etc/init.d/cupsys restart in a terminal. Now all I have to do is to get those 2 commands issued during the boot process.[/QUOTE]
Just add those commands to /etc/init.d/bootmisc.sh just above the "exit 0" command.

---

