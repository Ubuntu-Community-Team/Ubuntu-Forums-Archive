---
title: "Desktop Settings Reset and Cannot Be Changed"
date: 2013-02-10
forum: Desktop Environments
---

### Post by Migrashin on 2013-02-10
I restarted my computer once and all my settings for the desktop changed: My Background image disappeared replaced with original, launcher reverted back to original icons, launcher placed on both monitors.

When I try to change these settings again in the system settings nothing happens. I can even try to select a different background image and it won't do anything. Also if I try to turn off sticky edges in "Displays", it won't turn off but the "Displays" button will show that it is off. Same thing with launcher.

---

### Post by stinkeye on 2013-02-10
What Ubuntu release are you running and what does this terminal command give you....
```
echo $DESKTOP_SESSION 
```

---

### Post by Migrashin on 2013-02-10
I'm running 12.10 and the output is just "ubuntu"

---

### Post by stinkeye on 2013-02-10
> **Migrashin said:**
> I'm running 12.10 and the output is just "ubuntu"
In that case I don't really know the cause.
Sounds like a permissions issue with your home directory?
Try a reboot.

---

### Post by Migrashin on 2013-02-10
Rebooted several times already, no help. The only thing that has changed recently is that I installed python2.6 for an application I was working on. Then I switch it to the default version using these instructions: [http://ubuntuforums.org/showthread.php?t=1576508](http://ubuntuforums.org/showthread.php?t=1576508) 

I don't know if this would affect anything, but that is really the only thing I have done recently. Currently my python is running 2.6.8 and even after redoing the instructions for 2.7.3, I can't seem to get 2.7.3 to be the default version of python. Not sure if this is causing the problem.

---

### Post by stinkeye on 2013-02-10
Not something I know about, sorry.
Seems to be few threads were people have tried to install different
versions of python and messed up there system.
eg
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1990024[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1990024")

---

### Post by Migrashin on 2013-02-11
I ran the gnome-control-center from terminal and when I try to change a setting. For example in this case, the background I get these error messages.

GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(gnome-control-center:13531): GLib-GIO-CRITICAL **: g_file_new_for_path: assertion `path != NULL' failed

(gnome-control-center:13531): GLib-GIO-CRITICAL **: g_file_enumerate_children_async: assertion `G_IS_FILE (file)' failed

(gnome-control-center:13531): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-control-center:13531): background-cc-panel-WARNING **: Could not load /usr/share/themes/Adwaita/index.theme: No such file or directory

---

