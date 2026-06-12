---
title: "F-Spot and facebook."
date: 2009-05-06
forum: General Help
---

### Post by moosehadley on 2009-05-06
Not sure if it should go in this topic, but if not, please move it.

Anyway, trying to use the Export to Facebook plugin in f-spot.
It crashes after I log in, and I get this output:

```
*****@*****-desktop:~$ f-spot
[Info  21:04:54.853] Initializing DBus
[Info  21:04:55.346] Initializing Mono.Addins
[Info  21:04:56.153] Starting new FSpot server

(f-spot:18763): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
[Info  21:05:01.087] Starting BeagleService
[Info  21:05:01.088] Hack for gnome-settings-daemon engaged

(f-spot:18763): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
error checking orientation
FoxyProxy settingsDir = /home/*****/.mozilla/firefox/f1k109a8.default
Marshaling clicked signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.InvalidOperationException: There is an error in XML document. ---> System.InvalidOperationException: <photos_getAlbums_response xmlns='http://api.facebook.com/1.0/'> was not expected
  at System.Xml.Serialization.XmlSerializationReaderInterpreter.ReadRoot (System.Xml.Serialization.XmlTypeMapping rootMap) [0x00000] 
  at System.Xml.Serialization.XmlSerializationReaderInterpreter.ReadRoot () [0x00000] 
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.Xml.Serialization.XmlSerializationReader reader) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.Xml.Serialization.XmlSerializationReader reader) [0x00000] 
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.Xml.XmlReader xmlReader) [0x00000] 
  at System.Xml.Serialization.XmlSerializer.Deserialize (System.IO.Stream stream) [0x00000] 
  at Mono.Facebook.Util.GetResponse[AlbumsResponse] (System.String method_name, Mono.Facebook.FacebookParam[] parameters) [0x00000] 
  at Mono.Facebook.FacebookSession.GetAlbums () [0x00000] 
  at FSpot.Exporter.Facebook.FacebookExport.HandleLoginClicked (System.Object sender, System.EventArgs args) [0x00000] 
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
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)
*****@*****-desktop:~$ 

```

---

### Post by directhex on 2009-05-07
It sounds like Facebook changed their API to something F-Spot doesn't expect. Which version of Ubuntu is this?

---

### Post by moosehadley on 2009-05-07
Latest. 9.04
F-Spot is latest too. 0.5.0.3

---

### Post by directhex on 2009-05-07
Try reporting a bug upstream about it

---

### Post by holotone on 2009-07-31
> **directhex said:**
> Try reporting a bug upstream about it

I believe [this]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/363067") is the affecting bug. 

Same problem here, fwiw.

---

### Post by GeordieDS on 2009-08-16
Me too! Anyone come across a work around? (I'm on Jaunty).

---

