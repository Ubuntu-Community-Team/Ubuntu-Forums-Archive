---
title: "gnome-screenshot crashes and then shows endless pop-ups"
date: 2009-05-12
forum: General Help
---

### Post by agnes on 2009-05-12
Hello everybody,

when I take a screenshot with gnome-screenshot I have to wait quite long for the pop-up window to show, and then, often, it goes wrong: 

it keeps giving me a new pop-up window every second, i.e. it keeps re-opening itself an infinite number of times - I have to type **killall gnome-screenshot** in the Terminal to resolve this.
(So what I mean is that under System->Administration->System Monitor->Processes you see like 40 gnome-screenshot's running, and entering more.)

When I typed **gnome-screenshot** in the Terminal it gave me this error:
```
(gnome-screenshot:24802): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(gnome-screenshot:24802): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

```
(The number after the "gnome-screenshot:" part differs between successive calls.)

This is what I get when typing **gksudo gnome-screenshot**:
```
** (gnome-screenshot:25100): WARNING **: Couldn't find window manager window

(gnome-screenshot:25100): GLib-GIO-CRITICAL **: g_file_new_for_uri: assertion `uri != NULL' failed

(gnome-screenshot:25100): GLib-GIO-CRITICAL **: g_file_get_parent: assertion `G_IS_FILE (file)' failed

(gnome-screenshot:25100): GLib-GIO-CRITICAL **: g_file_get_basename: assertion `G_IS_FILE (file)' failed

(gnome-screenshot:25100): GLib-GIO-CRITICAL **: g_file_get_uri: assertion `G_IS_FILE (file)' failed

(gnome-screenshot:25100): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-screenshot:25100): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-screenshot:25100): Gtk-CRITICAL **: gtk_file_chooser_set_current_folder_uri: assertion `uri != NULL' failed

(gnome-screenshot:25100): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

(gnome-screenshot:25100): GLib-CRITICAL **: g_strrstr_len: assertion `haystack != NULL' failed
```


I've had this from the very beginning of my install of Intrepid. 
Also, the infinite-pop-up-thing does not happen always, it happens when the CPU used is relatively high.
But my processors are not slow (2 * 2,2 GHz). I have an ATI Radeon HD 3650 graphics card. Kernel 2.6.27-14, Gnome 2.24.1, x86_64. Compiz' screenshot function just works. 

Anyone has any ideas?

---

### Post by agnes on 2009-05-15
* bump *

---

### Post by agnes on 2009-05-26
Ok well, I'll just use scrot instead...

---

