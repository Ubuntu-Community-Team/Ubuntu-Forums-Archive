---
title: "I had an xubuntu desktop, so I tried to switch to Unity. I tried getting rid of xfce."
date: 2019-02-05
forum: Desktop Environments
---

### Post by emattpoyourebooted on 2019-02-05
I got Unity, but my greeter says &#8220;Booting in low-graphics mode&#8221; after deleting xubuntu desktop. The error I get in the terminal after running ```
unity 

GLib-GIO-CRITICAL **: g_dbus_connection_call_sync_internal: assertion &#8216;G_IS_DBUS_CONNECTION (connection)&#8217; failed

 GLib-GObject-CRITICAL **: g_object_unref: assertion &#8216;G_IS_OBJECT (object)&#8217; failed

 dconf-WARNING **: failed to commit changes to dconf: Cannot autolaunch D-Bus without X11 $DISPLAY
 compizconfig - Info: Backend     : gsettings
 compizconfig - Info: Integration : true
 compizconfig - Info: Profile        : unity-lowgfx

 dconf-WARNING **: failed to commit changes to dconf: Cannot autolaunch D-Bus without X11 $DISPLAY
 We&#8217;re already using profile &#8216;unity-lowgfx&#8217;, no need to switch
 WARNING: no DISPLAY variable set, setting it to :0
 compiz (core) - Info: Loading plugin: core
 compiz (core) - Info: Starting plugin: core
 compiz (core) - Fatal: Couldn&#8217;t open display :0
 compiz (core) - Info: Stopping plugin: core
 compiz (core) - Info: Unloading plugin: core 
```
 How do I fix this?

---

### Post by oldrocker99 on 2019-02-05
It looks as though you would be better off reinstalling Xubuntu-desktop, and simply log in to Unity. The desktop doesn't take up that much disk space. I tried installing budgie, and had similar problems, although not as bad. Later on, my installation apparently hosed itself, so I reinstalled, and I stay away from budgie.

I use Ubuntu MATE, which has, built-in, a Unity-like desktop, which is called Mutiny;), and Ubuntu MATE is lighter-weight compared to Unity.

---

### Post by emattpoyourebooted on 2019-02-05
I am trying to update from 16.04 LTS to 18.04.1 LTS. oldrocker99, I am on a chrome book with 16gb, so I need to use Unity or xubuntu. I would rather Unity&#8217;s helpful UI instead of xubuntu&#8217;s rough UI

---

