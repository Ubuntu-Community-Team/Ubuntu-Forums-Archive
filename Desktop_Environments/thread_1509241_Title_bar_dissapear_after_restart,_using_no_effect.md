---
title: "Title bar dissapear after restart, using no effects"
date: 2010-06-14
forum: Desktop Environments
---

### Post by itzco on 2010-06-14
Hi,

I just upgraded to Lucid Lynx,  every time I restart my computer the title bar disappears and everything is displaced (icons and dialogs opening).

If I change Visual Effect from None (My normal setting) to Normal and back, the title bars shows normal, but this happens every time I restart and it's very hard to fix with 70% of the dialog hidden on top :(

Any way I can fix this permanently?

My video card:
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation

And I use 2 monitors.

Thanks

---

### Post by Ryan Dwyer on 2010-06-14
This might be happening because the theme you were using before you upgraded is no longer installed. Try choosing a different theme in your Appearance settings.

You should also try checking dmesg or the syslog for clues about why Metacity is failing to start.

---

### Post by itzco on 2010-06-14
Hi Ryan,

Which themes are safe? I'm now using "Clearlooks". I'll give it a try tomorrow and let you know

Thanks!

---

### Post by Ryan Dwyer on 2010-06-14
Anything that's listed should be safe to use. If you're already using Clearlooks then it's probably not a theme issue.

So yeah, check dmesg and the syslog to see what's going on.

---

### Post by t.rei on 2010-06-14
hm, several things come to my mind:

a) compiz running, but window-decorations and desktop integration not "on" or

b) compiz running, but no window-decorator entered in its field:
ccsm -> window decoration -> commando field: gtk-window-decorator

c) startup scripts that used to be usefull, now breaking things: 
system -> preferences -> startup programs (sry, running german version here) 
check those for some odd entries

d) hm, also checking the metacity settings (if not running compiz) in gconf-editor -> apps -> metacity might reveal something

just my 0.2 cents (yes, that few!)

---

### Post by itzco on 2010-06-24
Hi guys thanks for your help,

@ryan I tried to check the dmsg can't see nothing special, no special warnings or errors (Don't really know what I am looking for to be honest) - Syslog ask me to install dsuslog of sysklogd

@rei. There's an 'auto rotate' screen application running on startup that I add following instructions on a forum to use with a tablet pc

Today after fixing by switching settings, i run >compiz, and the bars disappeared! and I got  this message:

```
WARNING: Application calling GLX 1.3 function "glXCreatePixmap"  when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when  GLX 1.3 is not supported!  This is an application bug!

```


Today I also tried running the appearance preferences from terminal and got  this messages when changing to None and Normal
  
```

(gnome-appearance-properties:2533): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2533): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2533): Gtk-CRITICAL **: gtk_tree_model_sort_real_unref_node: assertion `elt->ref_count > 0' failed
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.

(gnome-appearance-properties:2533): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

```

Can this have anything to do with it?

Thanks

---

### Post by itzco on 2010-07-30
Thanks guys, I finally found the solution!

The problem was:
Window manager was not loading after upgrading to 10.4

The default windows manager is not compiz but metacity

Solution on this thread by Kochin
[http://ubuntuforums.org/showthread.php?t=1466754&highlight=window+manager](http://ubuntuforums.org/showthread.php?t=1466754&highlight=window+manager)

---

