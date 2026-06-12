---
title: "gnome-do (docky) crashes upon login"
date: 2009-11-29
forum: Desktop Environments
---

### Post by mtausig on 2009-11-29
Hy!

I have gnome-do in docky mode set as a startup application, but it crashes when I login. WHen I start it manually afterwards, everything works.

Here is the corresponding output from my .xsesseion-error:
```

** (gnome-panel:1934): DEBUG: Adding applet 11.
Marshaling composited_changed signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Docky.Interface.AutohideTracker.Dispose () [0x00000] 
  at Docky.Interface.DockArea.Dispose () [0x00000] 
  at Docky.Interface.DockWindow.Dispose () [0x00000] 
  at Do.Core.Controller.UnsetTheme () [0x00000] 
  at Do.Core.Controller.OnCompositingChanged (System.Object sender, System.EventArgs args) [0x00000] 
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
   at Do.Do.Main(System.String[] args)

```

I am using gnome in karmic

cheers
Mathias

---

### Post by mtausig on 2009-12-03
bump

---

### Post by stinkeye on 2009-12-04
First thing I would try if your running fusion-icon at startup is this
[_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=8381993&postcount=11[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=8381993&postcount=11")

If that doesn't work....
If your using compiz try delaying the start of gnome-do until after
compiz has loaded using this solution.
[_[COLOR="#8b0000"]http://ubuntuforums.org/showpost.php?p=8376643&postcount=9[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=8376643&postcount=9")

---

### Post by mtausig on 2009-12-05
> **stinkeye said:**
> First thing I would try if your running fusion-icon at startup is this
[_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=8381993&postcount=11[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=8381993&postcount=11")


That did the trick. Thanks a lot stinkeye.

---

