---
title: "Having problems after trying to install openbox.."
date: 2006-01-08
forum: General Help
---

### Post by lleberg on 2006-01-08
FIrst of all, I'm absolute not blaming anyone, why would I..
i am looking for help, because i can't solve it, have looked into it a bit, but i haven't got that experience on ubuntu or linux.

I used this how-to, to try openbox! -> [General - How to use Openbox in GNOME and by itself.]("http://ubuntuforums.org/showthread.php?t=75471")
Now i do have some problems with it!
Lets start with booting..
I can log in graficly, but nothing starts, openbox does though, because i can windowskey-r to start a terminal (bound it myself), wich is opened in openbox. I start the gnome-panel to have some thing to click on.

If i run a ps aux, i have, among others, but this seems less usual.

```

lleberg  22036  0.0  0.1   7756  1948 ?        Ss   18:19   0:00 openbox restart
lleberg  22038  0.0  0.1   7760  1944 ?        Ss   18:19   0:00 openbox restart
lleberg  22040  0.0  0.1   7760  1932 ?        Ss   18:19   0:00 openbox restart
lleberg  22042  0.0  0.1   7756  1936 ?        Ss   18:19   0:00 openbox restart
lleberg  22044  0.0  0.1   7760  1940 ?        Ss   18:19   0:00 openbox restart
lleberg  22046  0.0  0.1   7756  1932 ?        Ss   18:19   0:00 openbox restart
lleberg  22048  0.0  0.1   7756  1936 ?        Ss   18:19   0:00 openbox restart
lleberg  22050  0.0  0.1   7760  1940 ?        Ss   18:19   0:00 openbox restart
lleberg  22052  0.0  0.1   7760  1932 ?        Ss   18:19   0:00 openbox restart
lleberg  22054  0.0  0.1   7756  1936 ?        Ss   18:19   0:00 openbox restart
lleberg  22056  0.0  0.1   7760  1936 ?        Ss   18:19   0:00 openbox restart
lleberg  22058  0.0  0.1   7756  1928 ?        Ss   18:19   0:00 openbox restart
lleberg  22060  0.0  0.1   7756  1932 ?        Ss   18:19   0:00 openbox restart
lleberg  22062  0.0  0.1   7760  1932 ?        Ss   18:19   0:00 openbox restart
lleberg  22063  0.0  0.0      0     0 ?        R    18:19   0:00 [gnome-session]
lleberg  22064  0.0  0.1   7760  1940 ?        Ss   18:19   0:00 openbox restart

```

The terminal running gnome-panel contained some errors, might be interesting.
```
lleberg@Margit:~$ gnome-panel

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data:  assertion `width > 0' failed

(gnome-window-properties:8901): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: asserti on `src != NULL' failed

(gnome-window-properties:8901): GLib-GObject-CRITICAL **: g_object_unref: assert ion `G_IS_OBJECT (object)' failed
/usr/lib/gnome-app-install/AppInstall.py:196: GtkWarning: gtk_accel_label_set_ac cel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NU LL' failed
  LaunchpadIntegration.add_items (widget, -1, False, True);

(synaptic:15974): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:15974): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:15974): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(services-admin:28166): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.
Warning: more than one line!
Warning: more than one line!
Warning: more than one line!
<and so on>

```

```
lleberg@Margit:~$ /etc/init.d/gdm start
 * Starting GNOME Display Manager...               [fail]
```

How do i.. undo all that has been done? ;)

Edit: "Undo, redo, or if you change your mind, you can redo what you last undid!" <- that takes me back to the days with.. some picturing-game i had when i was little.

---

