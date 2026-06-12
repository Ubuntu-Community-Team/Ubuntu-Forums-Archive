---
title: "KDE manager  crashes always and X not initialising, crashes instantly."
date: 2007-10-12
forum: Desktop Environments
---

### Post by Sachababs on 2007-10-12
Please help me. I  have to change the icon size of a theme back to what it was before but I can't access the theme manager because X crashes as does KDE manager or whatever it's called. I need a command to change icon size from the terminal, or some way of reverting X to run from defaults. Here is the debug info if it helps...


(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233398064 (LWP 5673)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb6d8bc3d in QImage::setPixel () from /usr/lib/libqt-mt.so.3
#7  0xb636aff6 in polyester::polyesterButton::genButtonPix ()
   from /usr/lib/kde3/kwin3_polyester.so
#8  0xb636f327 in polyester::polyesterButton::drawButton ()
   from /usr/lib/kde3/kwin3_polyester.so
#9  0xb6e6002c in QButton::paintEvent () from /usr/lib/libqt-mt.so.3
#10 0xb6df9a55 in QWidget::event () from /usr/lib/libqt-mt.so.3
#11 0xb6d59a60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#12 0xb6d5c42a in QApplication::notify () from /usr/lib/libqt-mt.so.3
#13 0xb752fce2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#14 0xb6cec25d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#15 0xb6cdacaa in QETWidget::translatePaintEvent ()
   from /usr/lib/libqt-mt.so.3
#16 0xb6ce904c in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#17 0xb6d00180 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#18 0xb6d74136 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#19 0xb6d5b587 in QApplication::enter_loop () from /usr/lib/libqt-mt.so.3
#20 0xb6f773e9 in QDialog::exec () from /usr/lib/libqt-mt.so.3
#21 0xb7f03438 in kdemain () from /usr/lib/libkdeinit_kcmshell.so
#22 0x080484c2 in ?? ()
#23 0x00000002 in ?? ()
#24 0xbfc53e64 in ?? ()
#25 0xbfc53dc8 in ?? ()
#26 0xb7dd7ff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#27 0xb7f227b0 in ?? () from /lib/ld-linux.so.2
#28 0xbfc53de0 in ?? ()
#29 0xbfc53e38 in ?? ()
#30 0xb7cb0ebc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
Backtrace stopped: frame did not save the PC

---

### Post by ovidiubar on 2007-10-12
On my laptop Kubuntu 7.10 beta blocks every time it gets to "starting the display manager". It gives me a black screen and my computer is dead. Same thing in Ubuntu 7.10 Gnome. I made an install of Kubuntu after opening it in safe graphics mode, but when I wanted to set my display to 1200x800 (the normal display on my computer, tested in Windows and Mandriva, for exemple), I got the same black screen and I have to press the button of the computer once again. Rebooting in recovery mode does not help much when you are just a normal computer user. Ok, I found the commands on the Internet and I tried sudo gedit /etc/x11/xorg.conf/etc/x11/xorg.conf, gksudo gedit /etc/X11/xorg.conf and five other commands (opening xorg with kwrite or nano or something else, I don't know). My opinion is that you have to be a computer passionate to like working in these conditions. If you are not, you'd like to have a gui to edit xorg and a command that make the computer go back to some safe settings. If the recovery would start ubuntu in safe graphics mode, for exemple, I'd be happy with it. I discovered linux by using Ubuntu 7.04 and I liked it very much (even I had to work without my mouse for a few days, because my mouse was not detected correcly and I had the same black screen problem when I wanted to change the display), but when the enthousiasm just don't live for ever, and when I saw that there are distributions that handle well this kind of problems, I found it a little bit strange. If Mandriva or PCLinux does not detect my display correctly, they keep the default 1024x748 when I try to change it with one that is not working, and a small distro like Puppy detects the display automatically.
 The point is that Ubuntu will loose many users if they will have to handle black screen and command-line problems. It's just an idea of mine.

---

