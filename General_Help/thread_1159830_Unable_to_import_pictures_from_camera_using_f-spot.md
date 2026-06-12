---
title: "Unable to import pictures from camera using f-spot - get error"
date: 2009-05-15
forum: General Help
---

### Post by rod40cool on 2009-05-15
Hi Just recently I started to get errors when importing pictures from my Canon camera using F-Spot onto my laptop. I had previously imported all the pictures from the camera and wanted to import the new pictures. 

When I connect the camera the system asks do I want to Open F-Spot, which it does and loads all the preview pictures fine. I then say to import (detecting duplicates) into the Pictures folder in my home folder and the import starts but then some way along the import process I get a message dialog stating:
"Win32 IO returned ERROR_ALREADY_EXISTS. Path: 
  at System.IO.File.Move (System.String sourceFileName, System.String destFileName) [0x00000] 
  at FSpot.CameraFileSelectionDialog.SaveFile (Int32 index) [0x00000] 
  at FSpot.CameraFileSelectionDialog.Download () [0x00000]" 
with options to Retry, Skip or Cancel. (See attached screenshot)

[ATTACH]113852[/ATTACH]

If I retry the same error keeps reappearing. If I skip I later noticed that some of my new pictures were missing in the F-Spot library. If I click cancel, the Fspot program crashes.

I tried running F-Spot in the terminal window to get more detailed info and this is what I get.

```
rod@rod-laptop:~$ f-spot
[Info  16:03:14.477] Initializing DBus
[Info  16:03:14.686] Initializing Mono.Addins
[Info  16:03:14.917] Starting new FSpot server
[Info  16:03:15.924] Starting BeagleService
[Info  16:03:15.924] Hack for gnome-settings-daemon engaged

(f-spot:30822): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
item ImportCommand+SourceItem
Testing gphoto path = usb:
PortInfo Universal Serial Bus, usb:
System.IO.IOException: Win32 IO returned ERROR_ALREADY_EXISTS. Path: 
  at System.IO.File.Move (System.String sourceFileName, System.String destFileName) [0x00000] 
  at FSpot.CameraFileSelectionDialog.SaveFile (Int32 index) [0x00000] 
  at FSpot.CameraFileSelectionDialog.Download () [0x00000] 
cleanup context
Marshaling activate signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at FileImportBackend.Prepare () [0x00000] 
  at ImportCommand.DoImport (.ImportBackend imp) [0x00000] 
  at ImportCommand.ImportFromPaths (.PhotoStore store, System.String[] paths, FSpot.Tag[] tags, Boolean copy) [0x00000] 
  at ImportCommand.ImportFromPaths (.PhotoStore store, System.String[] paths, FSpot.Tag[] tags) [0x00000] 
  at FSpot.CameraFileSelectionDialog.ImportFiles () [0x00000] 
  at FSpot.CameraFileSelectionDialog.Run () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
  at ImportCommand.set_Source (.SourceItem value) [0x00000] 
  at ImportCommand+SourceMenu.HandleActivated (System.Object sender, System.EventArgs args) [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Dialog.gtk_dialog_run(IntPtr )
   at Gtk.Dialog.Run()
   at ImportCommand.ImportFromFile(.PhotoStore store, System.String path)
   at MainWindow.HandleImportCommand(System.Object sender, System.EventArgs e)
   at System.Reflection.MonoMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MethodBase.Invoke(System.Object obj, System.Object[] parameters)
   at System.Delegate.DynamicInvokeImpl(System.Object[] args)
   at System.MulticastDelegate.DynamicInvokeImpl(System.Object[] args)
   at System.Delegate.DynamicInvoke(System.Object[] args)
   at GLib.Signal.ClosureInvokedCB(System.Object o, GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.Invoke(GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)
rod@rod-laptop:~$ 
```

I haven't spotted anyone else with this problem so far.

Grateful if anyone can shed any light onto this and help me get my new photos off my camera.

Rod

**System**: Toshiba Tecra M3, Jaunty 9.04 
Uname -a: Linux rod-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by rod40cool on 2009-05-15
Hmm...

Looks like F-Spot (or I) was getting confused with images and folders stored in two different folders. I think I had been importing into Pictures and Photos on different occasions.

I looked in the folders and found I indeed had pictures in Pictures and in Photos as well and duplicates too. 

So I moved all the photos I had in Pictures folder to the Photos folder and chose Skip when I came across a duplicate, and then started F-Spot and removed all the photos from the Catalog by selecting all the images and right-clicking and selecting Remove from Catalog.

Then I imported all the photos from the folder Photos an unticked the Copy to Photos folder, then tried connecting my Camera again and was careful to select to import into Photos not Pictures this time.

This time it worked without errors. And for good measure I tried taking a few more test photos and re-imported detecting duplicates and all the new photos were successfully imported.

Solved.

---

### Post by endref on 2009-07-05
I have also problems importing. But I dont have any duplicates, I try importing with the wizard that prompts when inserting the camera-memory-card, and get an error.
I get this error when I try importing to a NTFS disk: 

```
Win32 IO returned ERROR_ALREADY_EXISTS. Path:
System.IO.IOException: Win32 IO Returned ERROR_ALREADY_EXISTS. Path:
 at System.IO.File.Move (System.String sourceFileName, System.String destFileName) [0x00000]
 at FSpot.CameraFileSelectionDialog.SaveFile (Int32 index) [0x00000]
 at FSpot.CameraFileSelectionDialog.Download () [0x00000]
```

I tried importing to a temp-folder on my main-disk (which is ext4), and this works fine. So I think there is a problem with importing to NTFS disk. Does anyone else have a similar problem, or a solution for this?

---

