---
title: "liferea 1.4.26 crashes when i read any feed on jaunty (9.04)"
date: 2009-05-10
forum: Desktop Environments
---

### Post by costamatrix on 2009-05-10
hi guys...this problem start to occur a couple days ago...there was some ubuntu updates, but i dont know if they are related to this issue....


when i open liferea, it opens, and when i selected any feed to read a post, it crashes...

i open a liferea on a shell, and the error message was:

rodrigo@rodnote:~/projects$ liferea    
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files

(liferea-bin:4668): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'

Liferea did receive signal 11 (Segmentation fault).


i have a ubuntu jaunty installed...

---

### Post by costamatrix on 2009-05-12
hey guys, i tried to use Blam instead of liferea and the same problem occurs....

when i click in one new, the error occurs:

Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.ArgumentException: Culture name C is not supported.
Parameter name: C
  at System.Globalization.CultureInfo.CreateSpecificCulture (System.String name) [0x00000] 
  at Imendio.Blam.ItemView.Load () [0x00000] 
  at Imendio.Blam.ItemView.set_CurrentItem (Imendio.Blam.Item value) [0x00000] 
  at Imendio.Blam.Application.ItemSelected (Imendio.Blam.Item item) [0x00000] 
  at Imendio.Blam.ItemList.EmitItemSelected (Imendio.Blam.Item item) [0x00000] 
  at Imendio.Blam.ItemList.SelectionChanged (System.Object obj, System.EventArgs args) [0x00000] 
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
   at Imendio.Blam.Application.Main(System.String[] args)
**
ERROR:error.c:70:SetLastError: assertion failed: (ret == 0)
Aborted

---

### Post by isecore on 2009-05-22
Since a few days back I'm having lots of problems with Liferea. When I click on a post in a feed it crashes. After running it in the terminal I know it segfaults with "Signal 11". This is weird as I haven't done anything that I know of to provoke this.

---

### Post by costamatrix on 2009-05-22
yes...and i discover something more weird...
i tried to use blam instead of liferea, and it crashes the same way...

so i tried straw, the only one who is actually working.

---

### Post by isecore on 2009-05-22
> **costamatrix said:**
> so i tried straw, the only one who is actually working.

Only problem with Straw is that it hasn't been developed for 1½ years. Seems like a dead project.

---

### Post by isecore on 2009-05-22
FWIW this also happens when I press the Update All-button. Boom, Signal 11.

---

### Post by isecore on 2009-05-22
Here's another fun fact: If I remove the .liferea-1.4 folder and let it start fresh, it simply segfaults immediately with no given reason.

---

### Post by isecore on 2009-05-23
I ran it in a terminal as liferea --debug-all and when it segfaulted I got the following output:

```
DB: searching for duplicates took 0,018s
DB: loading item 99668 (thread=0x262a5b0)
DB: item load took 0,001s
DB: loading itemset for node "iafqwjo" (thread=0x262a5b0)
DB: loading of itemset finished
DB: loading item 99680 (thread=0x262a5b0)
DB: loading item 99680 (thread=0x262a5b0)
GUI: Fatal: no node with id "iafqwjo" found!
DB: loading item 99681 (thread=0x262a5b0)
DB: item load took 0,009s
DB: loading item 99681 (thread=0x262a5b0)
GUI: Fatal: no node with id "iafqwjo" found!
TRACE: - htmlview_render_item
GUI: itemlist selection took 0,082s
TRACE: - itemlist_selection_changed
#0  0x00007f80536b3496 in poll () from /lib/libc.so.6
#1  0x00007f80540b277f in ?? () from /usr/lib/libglib-2.0.so.0
#2  0x00007f80540b2dad in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#3  0x00007f80565b4bc7 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#4  0x00000000004317b3 in main ()
```

Doesn't really mean much to me, but maybe to someone else?

---

### Post by isecore on 2009-05-27
COME ON, nobody has any clues? I've been googling like crazy and the only things worthwhile I find are this forumthread and my own bugreport over on launchpad.

---

### Post by isecore on 2009-05-27
If you're also suffering from this problem, I recommend you check out my bug-report and make sure to change it to "this affects me too" so the devs see it.

---

### Post by isecore on 2009-08-25
For what it's worth, I've fixed my Liferea segfaulting with Signal 11.

The fix? Change one line in /etc/nsswitch.conf if you're running winbind to let your computer talk to Samba/Windows-computers.

Original line that I setup, that causes my Liferea to segfault:

```
hosts:          files mdns4_minimal [NOTFOUND=return] **wins** dns mdns4
```

Modified line, with which it works fine:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 **wins**
```

---

### Post by Ashly on 2009-08-26
> **isecore said:**
> Change one line in /etc/nsswitch.conf

Holy excrement, that fixed all my problems. I can't believe that, I thought Liferea was gone for good.

---

### Post by bornagainpenguin on 2009-08-27
> **costamatrix said:**
> so i tried straw, the only one who is actually working.

Wait--you had Straw working on Jaunty???  Please tell me what you did (or didn't do) that allowed it to work!  I've been having all sorts of trouble with Straw on any version of Ubuntu higher than Intrepid!  Are you sure everything was working?

--bornagainpenguin

---

