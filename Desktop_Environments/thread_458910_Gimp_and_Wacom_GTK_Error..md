---
title: "Gimp and Wacom GTK Error."
date: 2007-05-30
forum: Desktop Environments
---

### Post by eldaria on 2007-05-30
I have a bit of an odd error, I have tried to Google for a solution but without any luck.

I use Gimp in Kubuntu 7.04 with a Wacom Table.
I was plesently suprised that the tablet worked without me having to manually install the Wacom drivers like in Dapper and Edgy.

However when I try to configure the tablet in Gimp I get trouble.
I go to File->Preferences->Input Devices->Confidure Extended Input Devises....

I get the Overview, where I can see the Axes and Keys tabs, but as soon as I select anything from the drop down list, the tabs go blank and  can no longer configure anything.

To find out if there where any debug stuff I tried to start Gimp from a terminal.
And this is what I got as soon as it goes blank:

```

(gimp:17637): Gtk-CRITICAL **: gtk_scrolled_window_add: assertion `bin->child ==NULL' failed

(gimp:17637): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(gimp:17637): Gdk-CRITICAL **: gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(gimp:17637): Gdk-CRITICAL **: gdk_window_set_background: assertion `GDK_IS_WINDOW (window)' failed

(gimp:17637): Gtk-CRITICAL **: gtk_scrolled_window_add: assertion `bin->child ==NULL' failed

(gimp:17637): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(gimp:17637): Gdk-CRITICAL **: gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(gimp:17637): Gdk-CRITICAL **: gdk_window_set_background: assertion `GDK_IS_WINDOW (window)' failed

```

Anybody have an Idea?

---

### Post by wadubois on 2007-06-09
FWIW, I'm having the exact same error.  Unfortunately, I haven't found anything on this either.  I did discover that it does the same thing in Inkscape (with the exact same results) so at this point I'm thinking that it's a GTK/GDK error. <sigh>

 I'll post back here if I come up with anything.

At least the tablet still works, but it is a bit unnerving.

 - w

---

### Post by P_Badger on 2007-06-09
I've always had the same issue, unfortunately, including the same issue in Inkscape. I'd plotz if anybody can tell me anything about it, as I've also not been able to find anything on it.

---

### Post by eldaria on 2007-06-09
Well I suppose we could report it as a bug on Launchpad, but I'm not sure how to do that.
Or what to put there.

Are you guys all using Kubuntu, or also Ubuntu..
I'm using Kubuntu, and Gimp is a Gnome application, so I don't know if it could be related to that.

---

### Post by wadubois on 2007-06-26
Actually, I'm using Kubuntu mostly.  But, since I still have Gnome installed (from an earlier time) and I had the same thought you did I flipped over to Gnome for a bit to test that theory.  

Bottom line, no change.  The options still disappear under Gnome.

I'm still thinking it's a library issue.  If i have time tonight I'll investigate a little more before filing a bug report.

 - w

---

