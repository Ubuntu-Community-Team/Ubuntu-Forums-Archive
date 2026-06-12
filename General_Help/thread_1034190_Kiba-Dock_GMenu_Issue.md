---
title: "Kiba-Dock GMenu Issue"
date: 2009-01-08
forum: General Help
---

### Post by napalm brain on 2009-01-08
Whenever I start Kiba-Dock and try to access the GMenu, Kiba-Dock crashes.

This is the error:

```
** (kiba-dock:8165): WARNING **: Error (tray.c @ line 201):
    Tray allready running!

    For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:8165): WARNING **: Error (plugin.c @ line 434):
    '/usr/local/lib/kiba-dock/dock_plugins/libtray.so' is not loadable

    For a core dump, run kiba-dock with --g-fatal-warnings.
Traceback (most recent call last):
  File "/usr/local/share/kiba-dock/dbus_scripts/kiba-feeder.py", line 163, in <module>
    kiba_feeder=KibaFeeder()
  File "/usr/local/share/kiba-dock/dbus_scripts/kiba-feeder.py", line 69, in __init__
    self.check_feeds()
  File "/usr/local/share/kiba-dock/dbus_scripts/kiba-feeder.py", line 106, in check_feeds
    self.status = open(STATUS_DIR + '/Status.txt','r')
IOError: [Errno 2] No such file or directory: '/tmp/Status.txt'

(kiba-dock:8165): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(kiba-dock:8165): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(kiba-dock:8165): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
```I assure everyone reading that I am only running one instance of Kiba-Dock. I am not sure if the Gnome Panel is conflicting with the script or not. The instance above is without the Gnome Panel GMenu running. Kiba starts off fine, it's just whenever I click the gnome menu icon, it crashes.

Any suggestions?

---

### Post by napalm brain on 2009-01-09
A slight bump.

---

### Post by Proteusiq on 2009-01-16
Well, I have posted that a month ago, with no luck of answer, Same problem too

[http://ubuntuforums.org/showthread.php?t=1012219&highlight=kiba+dock+error](http://ubuntuforums.org/showthread.php?t=1012219&highlight=kiba+dock+error)

If you hear or get how to fix it but, please do let me know :D

---

### Post by Proteusiq on 2009-03-23
> **napalm brain said:**
> Whenever I start Kiba-Dock and try to access the GMenu, Kiba-Dock crashes.

This is the error:

```
** (kiba-dock:8165): WARNING **: Error (tray.c @ line 201):
    Tray allready running!

    For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:8165): WARNING **: Error (plugin.c @ line 434):
    '/usr/local/lib/kiba-dock/dock_plugins/libtray.so' is not loadable

    For a core dump, run kiba-dock with --g-fatal-warnings.
Traceback (most recent call last):
  File "/usr/local/share/kiba-dock/dbus_scripts/kiba-feeder.py", line 163, in <module>
    kiba_feeder=KibaFeeder()
  File "/usr/local/share/kiba-dock/dbus_scripts/kiba-feeder.py", line 69, in __init__
    self.check_feeds()
  File "/usr/local/share/kiba-dock/dbus_scripts/kiba-feeder.py", line 106, in check_feeds
    self.status = open(STATUS_DIR + '/Status.txt','r')
IOError: [Errno 2] No such file or directory: '/tmp/Status.txt'

(kiba-dock:8165): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(kiba-dock:8165): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(kiba-dock:8165): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
```I assure everyone reading that I am only running one instance of Kiba-Dock. I am not sure if the Gnome Panel is conflicting with the script or not. The instance above is without the Gnome Panel GMenu running. Kiba starts off fine, it's just whenever I click the gnome menu icon, it crashes.

Any suggestions?
I am using Cairo-dock now! It is working Brilliantly and I have to say it is more STABLE than Kiba-dock. Plus is has more features and just sweet!

You Can Do It this way(From Cairo-Dock Forum)

Add Cairo-Dock repository to your sources open the sources.list file:

**sudo gedit /etc/apt/sources.list**

and add the appropriate repository to the end of the file:

[B]deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock[/B]

[B]deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) gutsy cairo-dock
[/B]
The signed GPG key for identification of the repository is:

[B]wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -
[/B]
Then, to install Cairo-Dock, issue these two commands in the terminal:

**sudo apt-get update**
**sudo apt-get install cairo-dock cairo-dock-plug-ins**

Note: if you get the error "E: Couldn't find package cairo-dock-plug-ins" try the code below as it seems there has been a name change and the package is now called cairo-dock-plugins in intrepid.

**sudo apt-get install cairo-dock-plugins**

Then Add it to you Sessions for it to start on log on:P


*> If You Can Not Fight Them Join Them*

---

