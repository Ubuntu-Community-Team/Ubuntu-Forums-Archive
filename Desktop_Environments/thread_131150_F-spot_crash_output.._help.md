---
title: "F-spot crash output.. help?"
date: 2006-02-15
forum: Desktop Environments
---

### Post by kamaaina on 2006-02-15
I'm getting this result from f-spot
```

[SIZE="1"]blahblah@blah:~$ f-spot
Unable to find active server: Name 'org.gnome.FSpot' does not exist.

(f-spot:15972): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(f-spot:15972): Gdk-WARNING **: locale not supported by C library
Fontconfig error: "local.conf", line 20: no element found

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Widget:gtk_widget_show_all (intptr)
in <0x00017> Gtk.Widget:ShowAll ()
in <0x00f03> MainWindow:.ctor (.Db db)
in <0x00026> FSpot.Core:get_MainWindow ()
in <0x00010> FSpot.Core:Organize ()
in <0x003d8> Driver:Main (System.String[] args)
blahblah@blah:~$
[/SIZE]


```

The program opens up and dies immediately.  What could be causing this?
Thanks

---

### Post by krispyfi on 2006-02-19
me, too. :( 


```
foo@bar:~$ f-spot
Unable to find active server: Name 'org.gnome.FSpot' does not exist.

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Widget:gtk_widget_show_all (intptr)
in <0x00017> Gtk.Widget:ShowAll ()
in <0x00f03> MainWindow:.ctor (.Db db)
in <0x00026> FSpot.Core:get_MainWindow ()
in <0x00010> FSpot.Core:Organize ()
in <0x003d8> Driver:Main (System.String[] args)
```

---

### Post by krispyfi on 2006-02-20
bump..?

---

