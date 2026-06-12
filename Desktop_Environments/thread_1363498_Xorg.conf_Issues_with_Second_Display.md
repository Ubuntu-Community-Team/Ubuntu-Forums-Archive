---
title: "Xorg.conf Issues with Second Display"
date: 2009-12-24
forum: Desktop Environments
---

### Post by Crath on 2009-12-24
I am currently trying to get my IOGear USB to DVI external video card to display as a secondary monitor (part # GUC2020DW6).  I recently installed [libdlo]("http://libdlo.freedesktop.org/wiki/") and the tests ran successfully (drawing shapes on the external display). Then, I followed [this blog]("http://mulchman.org/blog/?p=21") and everything seemed successful. 

When starting up, stuff comes up on my netbook's monitor (GRUB and such) then more linux stuff shows up on the secondary external monitor, then goes back to netbook as it continues loading, then a window pops up on the netbook monitor saying there was an error loading my xorg conf file, yada yada. Here is a snapshot of the log file it gave me

[Top Half]("http://img259.imageshack.us/img259/704/1001780s.jpg") - [Bottom Half]("http://img710.imageshack.us/img710/4585/1001781z.jpg")

and here is the startup log:

[Top Half]("http://img694.imageshack.us/img694/2491/1001782.jpg") - [Bottom Half]("http://img200.imageshack.us/img200/1801/1001783p.jpg")

And here is what shows up on the secondary monitor.
[Window]("http://img683.imageshack.us/img683/49/1001784.jpg")

When I hit yes, it just loops back to this window, when i hit no, the secondary monitor freezes on this screen, and the netbook monitor loads everything as normal as if i didn't have a secondary display.

Here is my xorg.conf file: [Xorg.conf](http://pastie.org/755782)


Any suggestions would be highly appreciated. Thanks!

---

### Post by rob311 on 2010-01-25
Crath
I came across your post because we both have the same usb2dvi unit. I noticed line 40 in your Xorg.conf that reads DisplayLink Time should be commented out like this:

#######################################
#DisplayLink Time
#######################################

You're lucky though. I could not get the shape test to run successfuly. Good luck

---

