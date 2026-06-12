---
title: "Blank icons, white topbar"
date: 2012-02-18
forum: Desktop Environments
---

### Post by Zyracksis on 2012-02-18
Sorry if I get something wrong, very new to this. I turned on my machine and all my icons were blank, and the top bar was white, see screenshot. I'm running unity on 11.10. Made sure I'm using the right drivers, tried to change theme, did a unity --reset, nothing. Even switched to gnome, still the same problem

[http://img571.imageshack.us/img571/6158/screenshotat20120218175.png](http://img571.imageshack.us/img571/6158/screenshotat20120218175.png)

Any suggestions would be very appreciated

---

### Post by Zyracksis on 2012-02-18
No-one else has experienced this?

EDIT: Solved, added a delay before starting the gnome-settings-daemon. Thanks anyway

---

### Post by Frogs Hair on 2012-02-18
Run the following in the terminal and see if there is a change .```
nautilus -q
```

---

### Post by Krytarik on 2012-02-18
> **Zyracksis said:**
> Solved, added a delay before starting the gnome-settings-daemon.
I'm curious, are you using GDM as the display manager? Because this kind of issue shouldn't occur anymore with LightDM, and this workaround shouldn't be necessary, neither would I expect it to work.

Regards.

---

### Post by Zyracksis on 2012-02-20
I'm using LightDM, not GDM. Unity still doesn't work properly, but gnome seems to. Here's a log of what happens when I do a unity --reset:

[PHP]Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no

Screen geometry changed:
   1680x0x1280x1024
   0x0x1680x1050

DEBUG 2012-02-18 19:02:42 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1680 h=1050
WARN  2012-02-18 19:02:42 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window56624877: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-02-18 19:02:42 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window56624880: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-02-18 19:03:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-18 19:03:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-18 19:03:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-18 19:03:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-18 19:03:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2012-02-18 19:03:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2012-02-18 19:03:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2012-02-18 19:03:42 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2012-02-18 19:03:43 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:03:43 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:03:43 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:03:43 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2012-02-18 19:03:43 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
WARN  2012-02-18 19:06:19 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:06:19 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:06:19 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:06:28 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:06:28 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:06:28 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:07:05 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:07:05 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:07:05 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:07:31 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:07:31 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:07:31 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:08:38 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:08:38 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:08:40 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:08:41 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:08:43 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:08:44 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:08:50 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:08:50 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:08:51 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:08:51 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:10:04 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:10:04 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:10:04 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:10:14 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:10:14 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:10:14 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:12:51 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:12:51 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:12:51 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:13:35 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:13:35 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:13:35 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:13:56 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:13:56 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:13:56 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:15:00 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon folder-documents folder at size 64
WARN  2012-02-18 19:15:00 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon text-x-log gnome-mime-text-x-log text-x-generic at size 64
WARN  2012-02-18 19:15:00 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon audio-mpeg gnome-mime-audio-mpeg audio-x-generic at size 64
WARN  2012-02-18 19:15:02 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:15:02 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
WARN  2012-02-18 19:15:02 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
WARN  2012-02-18 19:15:02 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:18:04 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:18:36 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window20972616: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-02-18 19:18:36 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window20972616: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-02-18 19:18:36 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:18:36 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
WARN  2012-02-18 19:18:36 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
WARN  2012-02-18 19:20:37 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:23:34 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:23:44 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:23:53 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:24:22 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:25:34 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:25:35 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:25:47 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window58720390: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-02-18 19:25:47 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window58720390: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-02-18 19:25:47 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:25:47 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
WARN  2012-02-18 19:25:47 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `(null)'
WARN  2012-02-18 19:25:47 glib.glib-gobject <unknown>:0 invalid uninstantiatable type `<invalid>' in cast to `BamfView'
WARN  2012-02-18 19:25:48 glib.glib-gobject <unknown>:0 invalid uninstantiatable type `<invalid>' in cast to `GObject'
WARN  2012-02-18 19:25:48 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
WARN  2012-02-18 19:25:48 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
WARN  2012-02-18 19:25:48 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
WARN  2012-02-18 19:25:48 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
WARN  2012-02-18 19:25:48 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
WARN  2012-02-18 19:25:48 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
WARN  2012-02-18 19:25:48 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
WARN  2012-02-18 19:26:30 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:26:30 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:26:31 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:26:34 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:26:34 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window48234650: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-02-18 19:26:34 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window48234650: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2012-02-18 19:26:34 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:26:34 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
WARN  2012-02-18 19:26:34 glib.glib-gobject <unknown>:0 instance of invalid non-instantiatable type `<invalid>'
WARN  2012-02-18 19:53:10 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:53:10 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:55:13 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 19:55:17 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


NOTE: child process received `Goodbye', closing down
WARN  2012-02-18 19:55:20 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 20:25:44 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2012-02-18 20:25:51 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


NOTE: child process received `Goodbye', closing down
WARN  2012-02-18 22:05:32 glib.gdk <unknown>:0 compiz: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.[/PHP]

---

### Post by syang0525 on 2012-06-27
i was browsing the net for a solution and i tried to edit it with no experience with how to edit anything with terminal (probably shouldn't have done that) but anyways i typed in:
```
 sudo /usr/bin/gnome-settings-daemon
```and it actually worked! :P

Then i rebooted the computer, and found that this is only a temporary workaround, and does not affect the blank icons. But, everything else including the top bar and terminal were fixed. Hope this helps!

EDIT: To fix the blank icons, you have to reboot nautilus:
```
nautilus -q
```Then, you have to click on the home folder to start nautilus.
Hope this helps!

---

