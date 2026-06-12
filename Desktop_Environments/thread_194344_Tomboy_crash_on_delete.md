---
title: "Tomboy crash on delete"
date: 2006-06-11
forum: Desktop Environments
---

### Post by smgil on 2006-06-11
I'm running Tomboy 0.3.5 after upgrade from Breezy to Dapper. When I try to delete a note tomboy crash with this error:

```
Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00079> Tomboy.HIGMessageDialog:.ctor (Gtk.Window,Gtk.DialogFlags,Gtk.MessageType,Gtk.ButtonsType,string,string)
in <0x00065> Tomboy.NoteWindow:DeleteButtonClicked ()
in <0x0002f> (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
in <0x0000e> GtkSharp.SignalFuncWrapper:NativeCallback ()
in <0x00036> (wrapper native-to-managed) GtkSharp.SignalFuncWrapper:NativeCallback ()
in (unmanaged) 0xb67f7422
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x00007> Gnome.Program:Run ()
in <0x00044> Tomboy.Tomboy:StartTrayIcon ()
in <0x0013f> Tomboy.Tomboy:Main (string[])
```

I was running tomboy on breezy without any problem after upgrade. Do I need install some package to get my tomboy full working. 

I've tried apt-get install --reinstall tomboy but I still get same error.

---

### Post by twisted_steel on 2006-06-11
You shouldn't have to install any extra packages to get Tomboy working.  I don't have this problem in Dapper, but I did a clean install and copied over my backed up notes created in Breezy.  It sounds like Tomboy may be having trouble with your notes specifically.  I'd try backing up the folder (.tomboy in your home directory), deleting it, and seeing if it still happens.  You can always copy it back over to restore your notes.

If you're still seeing the problem, you may want to open a bug on launchpad - [https://launchpad.net/distros/ubuntu/+source/tomboy/+bugs]("https://launchpad.net/distros/ubuntu/+source/tomboy/+bugs").

---

### Post by smgil on 2006-06-11
You're right. For some reason my old tomboy folder was causing the crash.

I delete the .tomboy folder and everything works fine.

Thanks

[QUOTE=twisted_steel]You shouldn't have to install any extra packages to get Tomboy working.  I don't have this problem in Dapper, but I did a clean install and copied over my backed up notes created in Breezy.  It sounds like Tomboy may be having trouble with your notes specifically.  I'd try backing up the folder (.tomboy in your home directory), deleting it, and seeing if it still happens.  You can always copy it back over to restore your notes.

If you're still seeing the problem, you may want to open a bug on launchpad - [https://launchpad.net/distros/ubuntu/+source/tomboy/+bugs]("https://launchpad.net/distros/ubuntu/+source/tomboy/+bugs").[/QUOTE]

---

