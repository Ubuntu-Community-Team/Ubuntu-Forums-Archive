---
title: "Programs Close Unexpectedly"
date: 2008-02-16
forum: Desktop Environments
---

### Post by ejs7597 on 2008-02-16
I have been running Ubuntu for about a year now, and have just recently been having problems with programs closing unexpectedly.  I notice it most with FireFox and Thunderbird, but that is only because that is what I use the most.  It seemed to happen most often, when I was scrolling with the wheel on my mouse, but it is also doing it at other times.  I tried a different mouse, just to be sure.  I even switched from a PS2 to a USB mouse.  Programs are still closing, but I still can't recall a program closing, when I wasn't doing something with the mouse.  They just close, like I pushed the Close button.  If I reopen FireFox, it does ask me if I want to start a new session, or resume the previous session, so it must be crashing.  It does this quite often.  I few minutes ago, I clicked on a button to download something, and FireFox just closed.  I opened it back up and pushed the resume button, and it works for a while again.   Any help or ideas would be appreciated. Thanks

---

### Post by aysiu on 2008-02-17
Try starting the programs from the terminal and see if there are any error messages that appear.

For example, instead of starting Firefox from a launcher icon, open [a terminal](http://www.psychocats.net/ubuntu/terminal) and type ```
firefox
``` When it closes unexpectedly, see if there are any error messages in the terminal.

My guess, though, if it has something to do with the mouse, is that something needs to be reconfigured in your /etc/X11/xorg.conf file.

---

### Post by ejs7597 on 2008-02-17
I finally got a program to give me an error when it crashed.  Konqueror crashed just like my other programs have been doing, they just close unexpectedly, and almost always without an error.  
Konqueror crashed and gave a signal 11 SIGSEGV.   The backtrace in the Konqueror error box showed the following:
[KCrash handler]
#6  0xb2b73c94 in ?? ()
#7  0xb5b76a9d in KJS::PropertyMap::mark () from /usr/lib/libkjs.so.1
#8  0xb5b76e0c in KJS::ObjectImp::mark () from /usr/lib/libkjs.so.1
#9  0xb5b76a68 in KJS::PropertyMap::mark () from /usr/lib/libkjs.so.1
#10 0xb5b76e0c in KJS::ObjectImp::mark () from /usr/lib/libkjs.so.1
#11 0xb5b76e4b in KJS::ObjectImp::mark () from /usr/lib/libkjs.so.1
#12 0xb5b76a68 in KJS::PropertyMap::mark () from /usr/lib/libkjs.so.1
#13 0xb5b76e0c in KJS::ObjectImp::mark () from /usr/lib/libkjs.so.1
#14 0xb5b76e4b in KJS::ObjectImp::mark () from /usr/lib/libkjs.so.1
#15 0xb5e42aee in ?? () from /usr/lib/libkhtml.so.4
#16 0xb5b7b5ae in ?? () from /usr/lib/libkjs.so.1
#17 0x08480c28 in ?? ()
#18 0x08d6edd8 in ?? ()
#19 0xb5b7b50b in ?? () from /usr/lib/libkjs.so.1
#20 0xb5bcb240 in ?? () from /usr/lib/libkjs.so.1
#21 0x0838c288 in ?? ()
#22 0xb5bcb880 in ?? () from /usr/lib/libkjs.so.1
#23 0xbfcb2d68 in ?? ()
#24 0xb5b7b658 in ?? () from /usr/lib/libkjs.so.1
#25 0x0838c288 in ?? ()
#26 0x08f57f4c in ?? ()
#27 0xbfcb2d48 in ?? ()
#28 0xb5bcb240 in ?? () from /usr/lib/libkjs.so.1
#29 0xbfcb2dc8 in ?? ()
#30 0xbfcb3624 in ?? ()
#31 0xbfcb2da8 in ?? ()
#32 0xb5b9dee0 in KJS::Reference::getValue () from /usr/lib/libkjs.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

I am not sure what any of the above means.  If anyone can fill me in, I would appreciate it. 
Thanks

---

### Post by ejs7597 on 2008-02-18
I do not get any errors when launching programs from Terminal either.

---

### Post by Luis_vxd on 2008-02-18
Hi

I'm having the same problem with pidgin. I started it from a terminal window as suggested and it gave an error when quitting:
**Segmentation fault (core dumped)**

No other program is having this behavior.

Thanks

---

### Post by ejs7597 on 2008-03-01
I ran the Memory test on the Ubuntu CD and found that one of my memory chips was bad.  I pulled it and the problem was fixed.

---

