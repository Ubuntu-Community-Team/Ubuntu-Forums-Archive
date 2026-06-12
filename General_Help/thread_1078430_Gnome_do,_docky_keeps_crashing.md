---
title: "Gnome do, docky keeps crashing"
date: 2009-02-23
forum: General Help
---

### Post by Depressed Man on 2009-02-23
vforviktor@vendetta-laptop:~$ gnome-do
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.IO.DirectoryNotFoundException: Directory '/home/vforviktor/.local/share/Trash/files' not found.
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String pattern, FileAttributes mask, FileAttributes attrs) [0x00000] 
  at System.IO.Directory.GetFiles (System.String path, System.String pattern) [0x00000] 
  at System.IO.Directory.GetFiles (System.String path) [0x00000] 
  at Docky.Interface.TrashDockItem.GetSurfacePixbuf () [0x00000] 
  at Docky.Interface.BaseDockItem.MakeIconSurface (Cairo.Surface similar) [0x00000] 
  at Docky.Interface.BaseDockItem.GetIconSurface (Cairo.Surface similar) [0x00000] 
  at Docky.Interface.DockArea.DrawIcon (Cairo.Context cr, Int32 icon) [0x00000] 
  at Docky.Interface.DockArea.DrawIcons (Cairo.Context cr) [0x00000] 
  at Docky.Interface.DockArea.DrawDrock (Cairo.Context cr) [0x00000] 
  at Docky.Interface.DockArea.OnExposeEvent (Gdk.EventExpose evnt) [0x00000] 
  at Gtk.Widget.exposeevent_cb (IntPtr widget, IntPtr evnt) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.exposeevent_cb(IntPtr widget, IntPtr evnt)
   at Gtk.Widget.exposeevent_cb(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Do.Do.Main(System.String[] args)
Cairo.Context: called from finalization thread, programmer is missing a call to Dispose
Cairo.Context: called from finalization thread, programmer is missing a call to Dispose


Could it be because I removed cairo-dock? But that only removed the data and cairo-dock itself?

Edit: Might be linked to this bug..

[https://bugs.launchpad.net/do/+bug/323453/+viewstatus](https://bugs.launchpad.net/do/+bug/323453/+viewstatus)

Edit2:Yup, if I put something in the trash it works now.

---

### Post by makisupa123 on 2009-02-23
Two things:

1.  Do you meet either of the 2 conditions specified in the bug report?

2.  Have you tried launching gnome-do without the Docky theme?  (I realize you might be a little hosed right now since you can't change preferences). 

Does your trash exist the location specified?  What are the permissions on it?


Just noticed your edit.  My bad...


Glad its working.

---

