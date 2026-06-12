---
title: "How to set a program to use 'system tray' (like GAIM)?"
date: 2005-10-16
forum: Desktop Environments
---

### Post by veraction on 2005-10-16
So, I have this program, dcpp, which is a direct connect program, and I want to be able to have it 'minimize' to the sys tray, like how GAIM does.

Anyone know how I'd go about this?

I searched synaptic for dcpp and the only result was the program (I was thinking there might be a status-docklet plugin such as there is for beep-media-player)

---

### Post by jesseman on 2005-10-16
i use a program called AllTray

[http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)

its easy to install and use!

---

### Post by weblars on 2005-10-16
[Alltray]("http://alltray.sourceforge.net/") should do the job.

---

### Post by veraction on 2005-10-16
Ok, thanks a lot. it works great ;) wish I would've known about this earlier ;)

---

### Post by souled on 2005-10-16
I installed Alltray, but when I try and run it, I get this error:
```
/home/eric/.themes/Office/gtk-2.0/icons:10: Unable to locate image file in pixmap_path: "stock_bottom.png"
/home/eric/.themes/Office/gtk-2.0/icons:11: Unable to locate image file in pixmap_path: "stock_first.png"
/home/eric/.themes/Office/gtk-2.0/icons:12: Unable to locate image file in pixmap_path: "stock_last.png"
/home/eric/.themes/Office/gtk-2.0/icons:13: Unable to locate image file in pixmap_path: "stock_top.png"
/home/eric/.themes/Office/gtk-2.0/icons:14: Unable to locate image file in pixmap_path: "stock_left.png"
/home/eric/.themes/Office/gtk-2.0/icons:15: Unable to locate image file in pixmap_path: "stock_down.png"
/home/eric/.themes/Office/gtk-2.0/icons:16: Unable to locate image file in pixmap_path: "stock_right.png"
/home/eric/.themes/Office/gtk-2.0/icons:17: Unable to locate image file in pixmap_path: "stock_up.png"
/home/eric/.themes/Office/gtk-2.0/icons:18: Unable to locate image file in pixmap_path: "stock_cancel.png"
/home/eric/.themes/Office/gtk-2.0/icons:19: Unable to locate image file in pixmap_path: "stock_apply.png"
/home/eric/.themes/Office/gtk-2.0/icons:20: Unable to locate image file in pixmap_path: "stock_cancel.png"
/home/eric/.themes/Office/gtk-2.0/icons:21: Unable to locate image file in pixmap_path: "stock_ok.png"
/home/eric/.themes/Office/gtk-2.0/icons:22: Unable to locate image file in pixmap_path: "stock_apply.png"
/home/eric/.themes/Office/gtk-2.0/icons:23: Unable to locate image file in pixmap_path: "stock_refresh.png"
/home/eric/.themes/Office/gtk-2.0/icons:25: Unable to locate image file in pixmap_path: "stock_open.png"
/home/eric/.themes/Office/gtk-2.0/icons:26: Unable to locate image file in pixmap_path: "stock_find.png"
The program 'alltray' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAccess (attempt to access private resource denied)'.
  (Details: serial 535 error_code 10 request_code 33 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by veraction on 2005-10-16
All I did was download the .package file, then run:```
sudo sh alltray-0.62.x86.package
```. Then pressed Y to download files from web.

Then I could run alltray by just using the command ```
alltray
```.

And I make a little application launcher for convience & put it on my gnome panel

---

### Post by souled on 2005-10-16
Ok I installed it throught the package file this time, and I ran it. I saw the little window where it tells you to click on the window you want to be put in the tray. I clicked a window but nothing happened. Then I ran the program again and I get the same error message.

How can I remove alltray when I installed it using sh *package?

EDIT: Rebooted my computer and it works now.

---

