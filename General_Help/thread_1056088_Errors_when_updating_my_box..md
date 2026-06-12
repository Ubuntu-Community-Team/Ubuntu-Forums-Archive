---
title: "Errors when updating my box."
date: 2009-01-31
forum: General Help
---

### Post by roadster3043 on 2009-01-31
Greetings.

Several days ago my Ubuntu 8.10 Intrepid Ibex started to give me the following error when updating it:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

When I run dpkg --configure -a I get the following error:

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

Any way of fixing it?

Thanks.

---

### Post by gettinoriginal on 2009-02-01
did you run it as??
```
sudo dpkg --configure -a
```

---

### Post by roadster3043 on 2009-02-02
Greetings.

Yes, I ran it with sudo.

---

### Post by lorna.s. on 2009-02-02
also similar issue in post below entitled  dpkg interrupted - right there with your suffering!

---

### Post by balaknair on 2009-02-02
Apparently dpkg is choking on some borked package.
Try the following commands in a terminal

*sudo dpkg -l | grep -v ^ii *

This will list any packages not installed correctly.
Then remove the faulty package wuth

*sudo dpkg --purge remove _faulty package_*

(Replace *_faulty package_* with the offending package.

Hope this helps.
All the best.

---

### Post by roadster3043 on 2009-02-10
Greetings.

Thanks for the help so far.

When I run the command sudo dpkg -l | grep -v ^ii I get the following list:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                 Description
+++-==========================================-=======================================-========================================================
rc  google-gadgets                             0.10.4-0~getdeb1                        Platform for running Google Gadgets on Linux
iF  gxine                                      0.5.903-2ubuntu2                        the xine video player, GTK+/Gnome user interface
rc  hunspell-en-us                             20070829-2ubuntu1                       English_american dictionary for hunspell
rc  language-support-writing-en                1:8.10+20080904                         Writing aids metapackage for English
rc  libavcodec-unstripped-51                   3:0.svn20080206-12ubuntu3+unstripped5   ffmpeg codec library
iU  libxine1                                   1.1.15-0ubuntu3.1                       the xine video/media player library, meta-package
iW  libxine1-bin                               1.1.15-0ubuntu3.1                       the xine video/media player library, binary files
iU  libxine1-console                           1.1.15-0ubuntu3.1                       libaa/libcaca/framebuffer/directfb related plugins for l
iU  libxine1-ffmpeg                            1.1.15-0ubuntu3.1                       MPEG-related plugins for libxine1
iU  libxine1-gnome                             1.1.15-0ubuntu3.1                       GNOME-related plugins for libxine1
iU  libxine1-misc-plugins                      1.1.15-0ubuntu3.1                       Input, audio output and post plugins for libxine1
iU  libxine1-x                                 1.1.15-0ubuntu3.1                       X desktop video output plugins for libxine1

```

---

### Post by balaknair on 2009-02-10
> **roadster3043 said:**
> Greetings.

Thanks for the help so far.

When I run the command sudo dpkg -l | grep -v ^ii I get the following list:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                 Description
+++-==========================================-=======================================-========================================================
rc  google-gadgets                             0.10.4-0~getdeb1                        Platform for running Google Gadgets on Linux
iF  gxine                                      0.5.903-2ubuntu2                        the xine video player, GTK+/Gnome user interface
rc  hunspell-en-us                             20070829-2ubuntu1                       English_american dictionary for hunspell
rc  language-support-writing-en                1:8.10+20080904                         Writing aids metapackage for English
rc  libavcodec-unstripped-51                   3:0.svn20080206-12ubuntu3+unstripped5   ffmpeg codec library
iU  libxine1                                   1.1.15-0ubuntu3.1                       the xine video/media player library, meta-package
iW  libxine1-bin                               1.1.15-0ubuntu3.1                       the xine video/media player library, binary files
iU  libxine1-console                           1.1.15-0ubuntu3.1                       libaa/libcaca/framebuffer/directfb related plugins for l
iU  libxine1-ffmpeg                            1.1.15-0ubuntu3.1                       MPEG-related plugins for libxine1
iU  libxine1-gnome                             1.1.15-0ubuntu3.1                       GNOME-related plugins for libxine1
iU  libxine1-misc-plugins                      1.1.15-0ubuntu3.1                       Input, audio output and post plugins for libxine1
iU  libxine1-x                                 1.1.15-0ubuntu3.1                       X desktop video output plugins for libxine1

```


Right, so now you know what packages are not properly installed. Use the command
```
sudo dpkg --purge remove _*faulty package*_
```

to remove these. You can reinstall them later if you please.

Example:
```
sudo dpkg --purge remove hunspell-en-us
```

will remove the package hunspell-en-us from your system, and after you have removed all the packages, you can reinstall them if you wish(they'll probably install properly this time around).

Hope this works for you. I've got exams going on, on a two hour break. I probably won't be able to get back online till the 17th. So I wish you luck. If you need more help I'll be back by the 18th.
Wish me luck for my exams, willya? :)

Bye for now.

---

