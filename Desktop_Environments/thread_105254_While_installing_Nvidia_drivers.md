---
title: "While installing Nvidia drivers"
date: 2005-12-18
forum: Desktop Environments
---

### Post by ToiletDuck on 2005-12-18
I get this.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--01:06:13--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--01:06:23--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384      181.31K/s

01:06:29 (180.92 KB/s) - `./andale32.exe' saved [198384/198384]

--01:06:29--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--01:06:39--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving twtelecom.dl.sourceforge.net... 207.250.4.12
Connecting to twtelecom.dl.sourceforge.net|207.250.4.12|:80... failed: Connection timed out.
Giving up.

--01:06:49--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--01:06:59--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--01:07:09--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20, 2001:620:0:1b::20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168,176 (164K) [application/octet-stream]

100%[====================================>] 168,176      142.27K/s

01:07:16 (141.84 KB/s) - `./arialb32.exe' saved [168176/168176]

--01:07:16--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)           => `./arial32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up nvidia-glx (1.0.7667-0ubuntu25.1) ...
Creating NVIDIA TLS links... done.

Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)


What is this msttcorefonts and how did i end up getting this while installing the drivers for my video card? 

Is there anyway to way to d/l these correctly or remove it so it will not pop up while installing other things?

Thanks

---

