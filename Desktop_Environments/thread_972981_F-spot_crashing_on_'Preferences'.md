---
title: "F-spot crashing on 'Preferences'"
date: 2008-11-06
forum: Desktop Environments
---

### Post by mkis62 on 2008-11-06
Reinstalled F-spot to avoid new crashes (cleared the old configuration in .gnome2). Still crashing,  in terminal with the following message:
[Info  15:31:28.804] Initializing DBus
[Info  15:31:29.089] Initializing Mono.Addins
[Info  15:31:29.784] Starting new FSpot server
[Info  15:31:32.999] Starting DBusService
[Info  15:31:33.021] Starting BeagleService
[Info  15:31:33.021] Hack for gnome-settings-daemon engaged
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.UI.Dialog.PreferenceDialog.LoadPreference (System.String key) [0x00000] 
  at FSpot.UI.Dialog.PreferenceDialog..ctor () [0x00000] 
  at FSpot.UI.Dialog.PreferenceDialog.Show () [0x00000] 
  at MainWindow.HandlePreferences (System.Object sender, System.EventArgs args) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)
It's a 'silent' crash, no crash report appears.

in debug mode:
** Running f-spot in Debug Mode **
** Running Mono with --debug   **
[Info  15:59:54.199] Initializing DBus
[Debug 15:59:54.501] DBusInitialization took 0.267746s
[Info  15:59:54.501] Initializing Mono.Addins
[Debug 15:59:55.016] Mono.Addins Initialization took 0.51469s
[Info  15:59:55.038] Starting new FSpot server
[Debug 15:59:55.446] Db Initialization took 0.192585s
[Debug 15:59:56.826] QueryToTemp took 0.001717s : SELECT id, time, uri, description, roll_id, default_version_id, rating, md5_sum FROM photos  WHERE id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC
[Debug 15:59:57.128] PhotosPerMonth took 0.007645s
[Debug 15:59:57.135] TimeAdaptor REAL Reload took 0.215633s
[Info  15:59:57.632] Starting DBusService
[Debug 15:59:57.651] DBusService startup took 0.01846s
[Info  15:59:57.654] Starting BeagleService
[Debug 15:59:57.656] BeagleService startup took 2.8E-05s
[Info  15:59:57.656] Hack for gnome-settings-daemon engaged
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.UI.Dialog.PreferenceDialog.LoadPreference (System.String key) [0x00000] 
  at FSpot.UI.Dialog.PreferenceDialog..ctor () [0x00000] 
  at FSpot.UI.Dialog.PreferenceDialog.Show () [0x00000] 
  at MainWindow.HandlePreferences (System.Object sender, System.EventArgs args) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)

---

