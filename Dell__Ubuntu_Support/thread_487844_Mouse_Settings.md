---
title: "Mouse Settings"
date: 2007-06-29
forum: Dell  Ubuntu Support
---

### Post by likegiraffes on 2007-06-29
I just got a new Dell with Ubuntu pre-installed, and I love it!  Seriously, its awesome.

The only problem is the weird touchpad mouse thing.  My last laptop was a Thinkpad, with a trackpoint, and I was used to it.  I'm getting used to moving the mouse around, but I keep clicking on things by accident.

Is there anyway to turn off the ability to click by tapping on the mouse-moving-thing, and only allow clicking with the buttons?

I found the 'mouse preferences' section, but it only allows you to change from right-handed to left-handed.

I'd really appreciate it if anyone knew how to do this!  If I close one more window by accident...  x.x

---

### Post by kgr132 on 2007-06-29
"...The easiest way is to edit /etc/X11/xorg.conf by adding the following line to the Input Devices section for the touchpad:
Option "MaxTapTime" 0"
Per this thread on the Dell web site: [http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=9556](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=9556)

Also, you can get fancier following advice here:
[http://ubuntuforums.org/showthread.php?t=417573&highlight=touchpad](http://ubuntuforums.org/showthread.php?t=417573&highlight=touchpad)
and here:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

---

### Post by likegiraffes on 2007-06-29
Thank you so much!  Its been driving me insane.  xD

---

### Post by likegiraffes on 2007-06-29
How do you edit the xorg.conf?

It says its a read only file and won't let me save changes.  =/

I'm really really new at this, so its probably obvious, but help me out anyway?  =D

---

### Post by mysticrider92 on 2007-06-29
Just open a terminal (Applications>Accessories>Terminal) and type: sudo gedit /etc/X11/xorg.conf. Type in your password and it will open a text editor with the file in read/write mode. Just be careful not to edit the wrong thing in this file, it is importent in displaying the graphical part of Linux.

---

### Post by dixelpixel on 2007-07-02
I have a Dell laptop too, hence the same problem.

When I open Xorg.conf I just see a blank page, no text whatsoever. What is going wrong here?

Thanks for all help :)

dxpx

---

### Post by avik on 2007-07-02
> Xorg.conf

It's /etc/X11/xorg.conf.  Case matters.

---

### Post by dixelpixel on 2007-07-07
OK, thanks for pointing that out, a bit clumsy of me when I wrote the post.

However, I have been using the correct case all along inn Terminal. And yes, the text file that is opened using the commands described so far in the thread is still completely blank.

What is going wrong here?

All help is appreciated. :KS

Thanks
..dxpx..

---

### Post by gcsoares on 2007-07-07
you know how to tab-complete???         when you are writing something in the terminal, like a file name, you just need to write the beginning and then press "tab", it will complete the address...       it is usefull when you are not sure how to write some command...           
you can select a text and click with the midle button of the mouse, try to select:
sudo gedit /etc/X11/xorg.conf
and click with the scroll...

---

### Post by pbaumgar on 2007-07-07
open a terminal, type:

cd /etc/X11

then type:

ls

do you see a file called xorg.conf?

Then to edit it, type:

sudo gedit xorg.conf

---

### Post by dixelpixel on 2007-07-07
Amazing!

Well, not sure I completely understood everything here, but at least that really annoying problem is solved.

Thanks! :KS

..dxp...

---

