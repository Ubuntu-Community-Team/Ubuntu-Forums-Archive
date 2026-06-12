---
title: "Mono problem with Autopanog.exe, after Breezy upgrade."
date: 2005-10-22
forum: Desktop Environments
---

### Post by kblood on 2005-10-22
Hello there,

I recently upgraded to Breezy, and now I can't run Autopano SIFT anymore. It starts, but after loading the images, when you click on Compute, it crashes out, with this error:

```
Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in (unmanaged) 0xb67701d1
in <0x00004> (wrapper managed-to-native) System.Drawing.GDIPlus:GdipGetImageGraphicsContext (intptr,intptr&)
in <0x00057> System.Drawing.Graphics:FromImage (System.Drawing.Image)
in <0x00186> DisplayImage:ScaleWithin (int)
in <0x0011f> Autopanog:GenerateKeypointForImage (Gtk.TreeModel,Gtk.TreePath,Gtk.TreeIter)
in <0x00086> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool_TreeModel_TreePath_TreeIter (Gtk.TreeModel,Gtk.TreePath,Gtk.TreeIter)
in <0x000f4> GtkSharp.TreeModelForeachFuncWrapper:NativeCallback (intptr,intptr,Gtk.TreeIter&,intptr)
in <0x00042> (wrapper native-to-managed) GtkSharp.TreeModelForeachFuncWrapper:NativeCallback (intptr,intptr,Gtk.TreeIter&,intptr)
in (unmanaged) 0xb710c2c1
in <0x00004> (wrapper managed-to-native) Gtk.TreeStore:gtk_tree_model_foreach (intptr,GtkSharp.TreeModelForeachFuncNative,intptr)
in <0x00046> Gtk.TreeStore:Foreach (Gtk.TreeModelForeachFunc)
in <0x002cb> Autopanog:OnComputeClicked (object,System.EventArgs)
in <0x00043> (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
in <0x000bb> GtkSharp.voidObjectSignal:voidObjectCallback (intptr,int)
in <0x00035> (wrapper native-to-managed) GtkSharp.voidObjectSignal:voidObjectCallback (intptr,int)
in (unmanaged) 0xb6d7aab2
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x002f8> Autopanog:Main (string[])

```

Any ideas? This program is actually developed with Mono, so it should work (and used to work before in Hoary)

Thanks!!!

---

### Post by kblood on 2005-10-23
I have managed to work around it by using the command line script, autopano-complete.sh, but it's a pity to have to give up the GUI. It seems there is a problem with the GTK# library and the GTK version included in Breezy.

Maybe it can be fixed by the people in charge of the Mono packages in Breezy?

---

### Post by Paul Atreides on 2005-10-27
I'm in the same trouble with autopanog.exe since I migrate to Breezy.
Breezy's Mono version seems to be the source of the problem...

---

### Post by python_boot on 2005-12-03
Curses! I came to this thread trying to get a fix for this error. If only I knew something about anything!

---

