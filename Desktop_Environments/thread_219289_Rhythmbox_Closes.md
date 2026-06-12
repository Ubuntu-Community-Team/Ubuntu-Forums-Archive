---
title: "Rhythmbox Closes"
date: 2006-07-19
forum: Desktop Environments
---

### Post by RexInTheCity on 2006-07-19
Rhythmbox was working fine last night, but I just got home and tried starting it from the Application menu. It comes up for a few seconds then closes. So I opened up a terminal and tried to start it from there.

$ rhythmbox
/home/banner/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:943: Unable to locate imag e file in pixmap_path: "focus_button.svg"
/home/banner/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:945: Background image opti ons specified without filename
/home/banner/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:1029: Unable to locate ima ge file in pixmap_path: "focus_button.svg"
/home/banner/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:1031: Background image opt ions specified without filename

(rhythmbox:29881): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `f ilename != NULL' failed

(rhythmbox:29881): Rhythmbox-WARNING **: Unable to load icon media-eject

(rhythmbox:29881): Rhythmbox-WARNING **: Unable to start mDNS browsing
The program 'rhythmbox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 4496 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Last night before I went to bed I went to [http://www.gnome-look.org/](http://www.gnome-look.org/) and got a new theme, icon set, and splash screen. I havn't had any problems with other programs not starting. So I went and switched to one of the themes that came with Ubuntu and Rhythmbox started working fine. Can anyone tell me what I need to do to get this all working together?

---

### Post by goobers on 2006-07-19
it looks to me like the theme you got is missing some images...

maybe you could copy the focus_button.svg file from another theme?

---

### Post by RexInTheCity on 2006-07-19
> **goobers said:**
> it looks to me like the theme you got is missing some images...

maybe you could copy the focus_button.svg file from another theme?

I figured that much, but none of the default Ubuntu themes have a file called focus_button.svg. Does anyone know what the button is suppose to look like or what other themes may have it?

---

### Post by Dubbayoo on 2006-07-19
I have had similiar issues with several apps. I bet if you restart it works, although that isn't really fixing it.

---

### Post by RexInTheCity on 2006-07-19
Rhythmbox just pulled a windows and magicaly started working lol

---

### Post by RexInTheCity on 2006-07-20
So, now it will sometimes start and sometimes wont. Does anyone know where I can get that file?

---

### Post by goobers on 2006-07-20
I did a search on the internet for you, but it yielded very few results... I think your best bet is to either make a dummy svg file (empty) and place it there, or download some more themes and check for the file,,,

---

