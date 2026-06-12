---
title: "Keyboard Stopped Working"
date: 2007-12-10
forum: Desktop Environments
---

### Post by unix4linux on 2007-12-10
Hello,

I was on the browser (firefox) when suddenly my keyboard lost the number lock light and stopped working.  I could not switch to VT because keyboard was not responding.

I had to use the mouse to log out of X.  Now, when I log out and the login screen comes back, the keyboard works fine.  I looked at my xorg.conf by switching to a VT and everything was fine.  I even copied a previous revision from my repository just to make sure it wasn't something I missed and still no keyboard.

In VT mode, the keyboard works fine as well as in my login screen of X.  Once it does log me in after I enter my credentials, the keyboard stops working.  It is a PS/2 keyboard and I run a USB mouse.

I looked at other postings; it was suggested to enable/disable my legacy support for USB which I did but keyboard still doesn't work.  It was also suggested that I unplug my USB mouse and restart without the USB mouse but still no keyboard.  I also even tried the acpi=off during boot and still no keyboard.

Why would the keyboard work anywhere else except after X loads?  Any suggestions?

I am actually running Kubuntu 7.10 Gutsy.  Keep in mind that I HAVE NOT done any upgrades and this installation has been running fine for a month.  The computer was on the entire time and never restarted until I encountered this problem.  2.6.22-14 is the only kernal I have installed and running.

Thanks in advance

---

### Post by unix4linux on 2007-12-11
Anyone have anything I can try?

---

