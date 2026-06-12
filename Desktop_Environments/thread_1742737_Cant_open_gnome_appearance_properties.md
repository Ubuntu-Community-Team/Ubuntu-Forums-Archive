---
title: "Cant open gnome appearance properties"
date: 2011-04-29
forum: Desktop Environments
---

### Post by karq on 2011-04-29
Hey!

I dont know why but I cant open the appearance properties anymore and here's the error:

```
kaarel@debian:~$ sudo gnome-appearance-properties
[sudo] password for kaarel: 

(gnome-appearance-properties:11272): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed

(gnome-appearance-properties:11272): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(gnome-appearance-properties:11272): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-appearance-properties:11272): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed

(gnome-appearance-properties:11272): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(gnome-appearance-properties:11272): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-appearance-properties:11272): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-appearance-properties:11272): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-appearance-properties:11272): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-appearance-properties:11272): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed
The program 'gnome-appearance-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2118 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
kaarel@debian:~$ gnome-appearance-properties --sync
The program 'gnome-appearance-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 693 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```


Hope someone can help me :)

---

### Post by Krytarik on 2011-04-29
Why do you run it with 'sudo' then!?

Aside from that you can screw up your "~/.ICEauthority" by running graphical apps with 'sudo' (see [here]("http://www.psychocats.net/ubuntu/graphicalsudo")), you would only change root's settings in this case.

Greetings.

---

### Post by xeno.by on 2011-06-10
I faced the same problem today and googled [a solution]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/386573") that did help me. Now I'm glad to share it with you:

> 
Mary Gardiner wrote on 2010-05-24: 	 #6 

I was told in private email that this behaviour is due to the /desktop/gnome/font_rendering/dpi key being an integer rather than a float.

You can do something like this to repair:

(find out existing value):
 $ gconftool-2 --get /desktop/gnome/font_rendering/dpi

(reset to float)
 $ gconftool-2 --set --type float /desktop/gnome/font_rendering/dpi [your value]

(unset entirely)
 $ gconftool-2 --unset /desktop/gnome/font_rendering/dpi


---

