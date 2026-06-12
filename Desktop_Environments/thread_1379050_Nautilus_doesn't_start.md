---
title: "Nautilus doesn't start"
date: 2010-01-12
forum: Desktop Environments
---

### Post by larsbjo on 2010-01-12
Hi

All of a sudden Nautlius doesn't start anymore. I can still start it using gksudo but typing nautilus on the command line gives:

```
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension
** Message: Initializing gksu extension...

** (nautilus:19764): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:19764): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:19764): WARNING **: No marshaller for signature of signal 'ShareCreateError'

(nautilus:19764): GLib-GIO-CRITICAL **: g_file_info_set_attribute_string: assertion `attr_value != NULL' failed

(nautilus:19764): GLib-GIO-CRITICAL **: g_file_info_set_attribute_string: assertion `attr_value != NULL' failed

(nautilus:19764): GLib-GIO-CRITICAL **: g_file_info_set_attribute_string: assertion `attr_value != NULL' failed

(nautilus:19764): GLib-GIO-CRITICAL **: g_file_info_set_attribute_string: assertion `attr_value != NULL' failed
Segmentation fault

```

My computer did run out of space during a backup using SpiderOak backup utility but I don't know if that is the reason for this problem. 
I've tried several suggested solutions like removing the .gconf/apps/nautilus folder and reinstalling nautilus but I still get the same message. I also tried to un-install Dropbox to see if that could have caused the problem.
Any help will be most welcome!

---

### Post by larsbjo on 2010-01-14
Bump.

Does anyone have a suggestion for what I can do to fix nautilus? I can start nautilus by using gksudo but it takes a long time to start. 

Is there a way to reset nautilus completely? I've tried removing nautilus using "Mark for complete removal" in Synaptic. It didn't resolve the problem. I get the same problem when reinstalling.

Nautilus seems to be integrated in everything in gnome so this is really annoying. I've tried to replace it by thunar but "Places" still seems to be using nautilus. 

Does anyone know what the "nautilus-gdu extension" does and if there is a way to turn it off?

Thank you!

---

### Post by 3Miro on 2010-01-14
Places uses Nautilus, Thunar has to be started from the Application menu. Thunar is fast, but doesn't have all the features of Nautilus (that is why it is fast). I personally use both, depending on the task I am trying to do.

For nautilus, did you try to remove the settings .nautilus folder?
```

mv .nautilus .nautilus_mybackup

```

This will move Nautilus settings folder .nautilus to a folder called .nautilus_mybackup. You can always restore the original folder back if you have to. With the folder moved, try starting Nautilus and see if it works.

---

### Post by larsbjo on 2010-01-18
Hi 3Miro

Thanks for the advice. Unfortunately it didn't help. I've also tried to remove the .gconf/apps/nautilus folder to see if that helped.

I think this problem goes deeper than only nautilus as I'm experiencing problems with the update service as well. Every day I get the icon notifying me that "The update information is outdated.." It will then tell me that it is 12 days since last update. This is the same date that the nautilus problem first occurred. When I do an update the icon disappear but it will appear again next day. 

I'm considering reinstalling Ubuntu (as it's 3 years since I did a fresh install), but on the other hand it would be nice to fix the problem as well.

Any other suggestion?

---

### Post by larsbjo on 2010-01-18
Bump. 

Does anybody know how to :

a) replace nautilus completely by another file-manager like thunar, or
b) reset all of nautilus settings, or
c) debug the problem further?

This problem is getting increasingly annoying as nautilus seems to be tied in to most programs. Everything from gnome to web downloaders and beagle search.

Thanks for any help!

---

### Post by larsbjo on 2010-01-19
last bump..(I promise)

When I left Windows for good some years ago I was hoping that reinstalling the whole operating system for the sake of a bug, was a thing of the past..

Now it seems as I would have to do it because of a bug in the nautilus file-manager. I'm using my machine for research and I've got zillion of weird programs running. (there you see It's my own fault ;). 

I would love to avoid spending a week getting it all up running again..

Can nobody help? :(

---

### Post by kavoura on 2010-02-26
The error I get is

$ Initializing nautilus-dropbox 0.6.1

** (nautilus:5212): WARNING **: Unable to add monitor: Not supported

(nautilus:5212): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:5212): WARNING **: Got GFileInfo with NULL name in computer:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:5212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:5212): Gtk-CRITICAL **: gtk_widget_queue_resize: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:5212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:5212): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:5212): Gtk-CRITICAL **: _gtk_container_queue_resize: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:5212): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(nautilus:5212): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:5212): Gtk-CRITICAL **: _gtk_container_queue_resize: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:5212): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(nautilus:5212): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed

(nautilus:5212): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed

(nautilus:5212): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed

(nautilus:5212): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(nautilus:5212): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nautilus:5212): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `NautilusKeepLastVerticalBox'

(nautilus:5212): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed




I don't understand any of these error messages. E.g. why is it unable to add a monitor? I have 1 monitor and it works just fine, and I can view everything on it.

---

### Post by aaa on 2010-03-10
I had the same issue few mins ago... 
and found a solution by doing this

mv ./.local/share/gvfs-metadata ./.local/share/gvfs-metadataold

i hope work for you. it did for me

O try setting up another user to see if the problem is actually linked to some bad/corrupted configuration. if it is, try to find al the dir tha have been accessed by nautilus and keep moving until you find the problem.

---

