---
title: "No 8 bit GLX pixmap format, disabling YV12 image format"
date: 2011-01-23
forum: Desktop Environments
---

### Post by Jim_Hope on 2011-01-23
Dear All,

I sometimes load into Ubuntu 10.10 and the graphics have all become extremely blocky. It also takes an age to load. I looked in .xsessions, and can see the following error:

Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
GLib.MissingIntPtrCtorException: GLib.Object subclass Do.Interface.ClassicWindow must provide a protected or public IntPtr ctor to support wrapping of native object handles.
  at GLib.ObjectManager.CreateObject (IntPtr raw) [0x00000] in <filename unknown>:0 
  at GLib.Object.GetObject (IntPtr o, Boolean owned_ref) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.styleset_cb (IntPtr widget, IntPtr previous_style) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.styleset_cb(IntPtr widget, IntPtr previous_style)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Do.Do.Main(System.String[] args)
Initializing nautilus-gdu extension
I/O warning : failed to load external entity "/home/xxxxx/.compiz/session/1041bafd72aa796ee129577927141270100000026120047"
Starting gtk-window-decorator

(nautilus:2813): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
/usr/bin/compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
** (nm-applet:2824): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2824): DEBUG: old state indicates that this was not a disconnect 0

I have looked in the forums, but am unable to find this error. Does anyone have a sense of what is going wrong, and what I might do?

cheers,

Jim.

---

