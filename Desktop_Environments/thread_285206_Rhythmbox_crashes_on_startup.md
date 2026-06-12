---
title: "Rhythmbox crashes on startup"
date: 2006-10-26
forum: Desktop Environments
---

### Post by Uolirod on 2006-10-26
Rhythmbox is crashing on startup.  The window opens for a moment and closes.  If I try to start in Xterm I receive this message:


```
(rhythmbox:5223): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `fi lename != NULL' failed

(rhythmbox:5223): Rhythmbox-WARNING **: Unable to load icon media-eject
The program 'rhythmbox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 7536 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

After looking around I'm thinking that I might install Rhythmbox 0.9.5 but I'm wondering if this error is indicative of something that will break the new version too.

---

### Post by skymt on 2006-10-26
How much free RAM and swap space do you have? If you don't know, post the output of the "free" command.

If you have lots of free memory, it's a bug in Rhythmbox (EDIT: or X) and you should update. If you don't, you need either more RAM or more swap space (preferably both).

(All this is assuming I read the error correctly.)

---

### Post by Uolirod on 2006-10-26
I don't know if this has something to do with it or is a symptom of the same problem but when I have beryl running the window frames keep flickering in and out.  This is what the output of free was.

```
~$ free
             total       used       free     shared    buffers     cached
Mem:       1036096     968156      67940          0      39704     654164
-/+ buffers/cache:     274288     761808
Swap:       987956      18944     969012

```

---

### Post by Uolirod on 2006-10-26
I don't know if this will make any sense to anyone but this keeps coming up when I start rhythmbox and beryl-manager.  Polycarbonate-dark is a theme I downloaded off Gnome-Look.org.

xmas@xmas-desktop:~$ beryl-manager
xmas@xmas-desktop:~$ /home/xmas/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:943: Unable to locate image file in pixmap_path: "focus_button.svg"
/home/xmas/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:945: Background image options specified without filename
/home/xmas/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:1029: Unable to locate image file in pixmap_path: "focus_button.svg"
/home/xmas/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:1031: Background image options specified without filename
XGL Present
Initiating splash
beryl-xgl: water: GL_ARB_fragment_program is missing

---

### Post by Uolirod on 2006-10-26
It appears there were two instances of emerald running. I don't know if that was causing the issues but they seem to have abated for now.  Rhythmbox and Beryl both seem to be functioning properly. Thanks.

---

### Post by skymt on 2006-10-26
It had nothing to do with free memory, but you're welcome anyway. I'm glad you fixed it. :)

---

