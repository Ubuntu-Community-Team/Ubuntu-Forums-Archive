---
title: "compiz stop working in 8.10"
date: 2008-12-05
forum: General Help
---

### Post by Rodolfo Patricio on 2008-12-05
Please I need some help. I have Ubuntu installed in my Intel PentiumIV (2.4Ghz)
Version 8.10 (intrepid)
Kernel Linux 2.6.27-10-server
GNOME 2.24.1
Memory 10000.5 MiB

Since 6.10 I used first Beryl and changed to Compiz in version 7.10. Beryl and Compiz always worked remarkably well, with only very minor bugs.
Well, when I upgraded to Ubunto 8.10, Compiz stop working. I know this is not a bug in Compiz, since I left the old version which use to work before. I even update my Compiz version to 1:0.7.8-0ubuntu4.1 with no results.
If I try to start Compiz, all my windows and desktop disappear, remaining only the mouse and the desktop background. The keyboard also stops working. I know my computer is there because I can reach it by a remote shell, and, if I have some music, the music continues......

Under the comand lscpi I get
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

and under the script by Nick Bauermeister I get

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

I suspect a bug in my intel driver 
xserver-xorg-video-intel 2:2.4.1-1ubuntu10.1 
and tried to"downgrade" to the old driver (the one that comes with ubuntu 8.04) but I couldn't. 
Could any one help me? I attach here my xorg.conf

---

