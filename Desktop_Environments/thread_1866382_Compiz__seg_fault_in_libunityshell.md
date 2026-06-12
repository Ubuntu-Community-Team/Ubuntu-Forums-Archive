---
title: "Compiz  seg fault in libunityshell"
date: 2011-10-21
forum: Desktop Environments
---

### Post by Siva Sankaran on 2011-10-21
[SIZE=2]**Background Information**[/SIZE]:
Pentium Dual Core E5400
Kernel Linux 2.6.38-11-generic
GNOME 2.32.1
I have upgraded to natty(11.04) from maverick a month ago with some errors like this 
```
The package "gconf2" failed to instal or upgrade
 .. .. . . . . 
. . . .
Processing was halted because there were too many errors
upgrade complete
The Upgrade has completed but there were errors during the upgrade process
``` Initially unity dash menu was not there. Afterwards I got it by this way[http://ubuntuforums.org/showpost.php?p=11246666&postcount=2](http://ubuntuforums.org/showpost.php?p=11246666&postcount=2)

Once there was a problem: Ubuntu software center cant open because of segmentation fault(It prompts when I tried from terminal). But from the next boot itself  software center can be launched as usual.
[SIZE=2]**Problem is**[/SIZE]:
 The applications which are running, desktop icons and top panel disappeared suddenly. And all appear again  in a fraction of second. They appear and disappear again and again very fast like blinking.[INDENT]1)  when I checked kernel log, it has this -> [http://paste.ubuntu.com/715137/](http://paste.ubuntu.com/715137/)
      Some folders are opened in nautilus and a text file opened in gedit. I am browsing    with firefox(7.0.1) and doing text chat in skype(beta version 2.2.0.35), while this happens. Whenever a (skype)pop up window alerting that a incoming text  in chat.

   The blink comes to end when closing some applications like nautilus and gedit. 

Finally I had only skype window the blink happens again and come to end after 4 or 5 time blinking.

2) This happens some time when clicking wherever on top panel. I have opened chrome with youtube and firefox(2 windows). This time kernel log reads with slight difference look here [http://paste.ubuntu.com/715147/](http://paste.ubuntu.com/715147/) Here note the error is in **[B]libsigc-2.0.so.0.0.0**[/B]  in previous case it is **libunityshell.so**
[/INDENT][INDENT]3)Another case here error in **libX11.so.6.3.0**
[/INDENT]```
Oct 20 11:01:09 workstation kernel: [ 6574.156821] compiz[2512]:  segfault at 1 ip 00843ed8 sp bfde62f0 error 6 in  libX11.so.6.3.0[817000+116000]
```[INDENT]The above log is repated many times
4)One another case [http://paste.ubuntu.com/715157/](http://paste.ubuntu.com/715157/)
It says something like "**Hangcheck timer elapsed... GPU hung**". This log exactly from the blinking begins. Because I watched carefully before the blinking.Here error in [B]i965_dri.so 
[/B][/INDENT][SIZE=2]**My Question**[/SIZE]:
      1) Shall I Uninstall compiz now ?
      2) I dont know deep technical details enough to report the segmentation fault
          how to fix it ?
      3)if I upgrade to Oneric, Will the problem be solved ?

---

