---
title: "gfax crashing on lucid"
date: 2010-05-31
forum: Desktop Environments
---

### Post by awacs on 2010-05-31
Just upgraded from karmic to lucid, and installed gfax to talk to a hylafax server. gfax from the command line crashes with:

(/usr/lib/gfax/gfax.exe:6783): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.24.1/gobject/gtype.c:2706: You forgot to call g_type_init()

(/usr/lib/gfax/gfax.exe:6783): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(/usr/lib/gfax/gfax.exe:6783): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
[...]
=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

/usr/bin/gfax: line 37:  6783 Aborted                 mono /usr/lib/gfax/gfax.exe $@


Eh?

---

### Post by devzero on 2010-06-28
hi, 
did you get it running yet? 
If not I'll look again, because I fogot what I exactly did.
And there must be more than that lines.
Try create the /var/spool/gfax and give it the permission 777

---

### Post by Furry_Fighter_20x66 on 2010-06-28
Hi awacs:
I missed your original posting some weeks back or I would have posted.
devzero is correct. I had almost near identical errors and was banging my head trying to get it to work. But once I made that directory and set permissions to 777, everything worked fine.

---

### Post by FiReSTaRT on 2010-10-28
You guys are lucky.. It's a bloody mess on Maverick:
> Unhandled Exception: GLib.GException: Icon 'gtk-info' not present in theme
  at Gtk.IconTheme.LoadIcon (System.String icon_name, Int32 size, IconLookupFlags flags) [0x00000] in <filename unknown>:0 
  at gfax.G_ListView.AddColumnIcon (System.String iconname, Int32 col) [0x00000] in <filename unknown>:0 
  at gfax.Gfax..ctor (System.String fname, System.String[] args) [0x00000] in <filename unknown>:0 
  at gfax.gfax.Main (System.String[] args) [0x00000] in <filename unknown>:0
The error about /var/spool/gfax disappeared once I created the dir and did chmod 777, but this mess is still there.

---

