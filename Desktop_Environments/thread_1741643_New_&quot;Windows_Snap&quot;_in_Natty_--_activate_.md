---
title: "New &quot;Windows Snap&quot; in Natty -- activate in classic/no effect mode?"
date: 2011-04-28
forum: Desktop Environments
---

### Post by revolutionären on 2011-04-28
I logged in on classical ubuntu with no effects, since my CPU is kind of  slow. I noticed that in ordinary Ubuntu there was a [**new "window snap"  feature built in**]("http://www.youtube.com/watch?v=9Fyk6mUUXPE"). It did not follow me when i logged into to the  classical version.
 
 Is there any way to activate it? Tried to do the [old "window snap"-clone  with CompizConfig]("http://www.multimediaboom.com/how-to-enable-windows-7-aero-snap-in-ubuntu-tweak/"), but that doesent seem to work either.
 
 I think the built in that came with 11.04 would be nice to have also when you login to "classic/no effects" -- is that possible?
 
 Best wishes, the Ubuntu n00b.

---

### Post by Calculon64 on 2011-04-28
I have the same question.  I am using VMWARE and VMWare tools installed flawlessly. How can I enable Unity?

---

### Post by Copper Bezel on 2011-04-28
revolutionären: Neither of those will work without Compiz, and "no effects" means you're using Metacity/Mutter. I haven't played with it, but the Grid plugin (which provides the Aero-Snap-like functionality) should work under the Classic desktop so long as you're running Compiz, and you can turn off the animations plugin and others to reduce the CPU load back to Metacity's levels. Run ```
compiz --replace
``` and enable the Grid in CompizConfig to try it out. The other edge-click commands you added probably shouldn't cause any conflict with the Compiz Grid, but you might deactivate the edge bindings just in case.

If that works out, we'll need to change a gconf setting to get Compiz as the default window manager in the Classic desktop, as this setting has changed since 10.10. (Previousy, enabling any desktop effects automatically set Compiz as the default.)

Calculon64: I don't think that's the same question. If Ubuntu is the guest OS on a Windows (or any other) host, then Compiz simply won't run and you'll default to the Classic desktop. The graphics accelleration that Compiz depends on doesn't work for Linux guests in VMWare.

---

### Post by r_mano on 2011-05-01
Any hint on which gconf setting should I change to have compiz by default in Natty classical desktop? Thanks

---

### Post by r_mano on 2011-05-01
Found by myself. 
It seems it is /desktop/gnome/applications/window_manager/default

The start of gnome-wm script says:

```
# The user can specify his prefered WM by setting the WINDOW_MANAGER
# environment variable or setting the
# /desktop/gnome/applications/window_manager/default gconf key.
```

will test at the next reboot.

---

