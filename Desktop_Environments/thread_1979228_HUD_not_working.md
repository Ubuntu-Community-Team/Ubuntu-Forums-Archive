---
title: "HUD not working"
date: 2012-05-13
forum: Desktop Environments
---

### Post by bejoysat on 2012-05-13
Upgraded from 10.04 to 12.04. Everything went well, except that HUD is not working. It brings up the prompt when I press Alt key, but upon typing, it searches for a while(5 seconds) and gives up. Tried with different applications and nothing seems return any matches.

---

### Post by vasa1 on 2012-05-13
What do you type? Which application is open when you type whatever it is you type? Please give some details.

---

### Post by bejoysat on 2012-05-13
> **vasa1 said:**
> What do you type? Which application is open when you type whatever it is you type? Please give some details.

Tried Chrome, Gimp, etc. Typed anything that could possibly throw up results. Like in Chrome, I typed 'ubuntu'. Also in Gimp, I tried 'Shadow', 'Drop', like they show in the Youtube videos.

---

### Post by bejoysat on 2012-05-14
Any suggestions?

Is there any way to 'reset' HUD?

---

### Post by vasa1 on 2012-05-14
I'm sorry you're facing this problem and I don't know what the solution is. HUD is working for me though I'm still getting used to it. This is what I see with Chrome:

---

### Post by bejoysat on 2012-05-15
Ok, I did a unity reset. And here are the messages on terminal:


```

bejoy@ubuntu:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
Window manager warning: from event callback
Window manager warning: from event callback
Window manager warning: from event callback
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done




compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1c00004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x20000e2

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3c000e6

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:2584): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0xe0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe000a4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-05-15 19:05:03 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-15 19:05:03 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-15 19:05:03 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-15 19:05:03 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-15 19:05:03 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-15 19:05:03 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-15 19:05:03 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-15 19:05:03 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-15 19:05:03 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-15 19:05:03 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-15 19:05:03 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-15 19:05:03 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-15 19:05:03 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-05-15 19:05:03 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-15 19:05:03 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-15 19:05:03 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-15 19:05:03 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
.
.
.
ERROR 2012-05-15 19:05:03 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-15 19:05:03 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window62914790
Initializing addhelper options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing extrawm options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
ERROR 2012-05-15 19:05:05 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2012-05-15 19:05:22 unity.glib.dbusproxy GLibDBusProxy.cpp:283 Calling method "StartQuery" on object path: "/com/canonical/hud" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name com.canonical.hud was not provided by any .service files
WARN  2012-05-15 19:05:40 unity.glib.dbusproxy GLibDBusProxy.cpp:283 Calling method "StartQuery" on object path: "/com/canonical/hud" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name com.canonical.hud was not provided by any .service files
WARN  2012-05-15 19:06:04 unity.hud.hud Hud.cpp:185 Attempted to close the hud connection without starting it
compiz (decor) - Warn: failed to bind pixmap to texture
```

The last but two WARNs were due to the keys entered in HUD.

Any ideas folks?

---

### Post by waperboy on 2012-05-29
I have the same issue here.

I also get this when typing in the prompt:

```
WARN  2012-05-29 22:21:08 unity.glib.dbusproxy GLibDBusProxy.cpp:283 Calling method "StartQuery" on object path: "/com/canonical/hud" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name com.canonical.hud was not provided by any .service files
```

---

### Post by matt_symes on 2012-05-29
Hi

Look in this folder

```
ls /usr/share/dbus-1/services
```

Do you see a file named

```
com.canonical.hud.service
```

If you do, what is the contents of the file ?

```
matthew@matthew-Aspire-7540 ~ % cat /usr/share/dbus-1/services/com.canonical.hud.service
[D-BUS Service]
Name=com.canonical.hud
Exec=/usr/lib/indicator-appmenu/hud-service
matthew@matthew-Aspire-7540 ~ %
```

I'm hoping your just missing this file.

Kind regards

---

### Post by colin.p on 2012-05-30
Had the same problem when I upgraded to 12.04 from lucid. Even though I did a clean install, the installer offered to keep my "home" partition and settings.
HUD didn't show anything until I removed all my hidden folders from "home" and then HUD started to work. I then just moved over whatever hidden folders I needed (from backup), overwriting the new ones. Everything is back to the way it was in lucid except I am of course using Precise.

---

### Post by pormenese on 2012-09-17
I have also upgraded from Lucid Lynx and have been strugling with this issue since that. Today I found a solution **[COLOR=RoyalBlue][here]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/939255")[/COLOR]**. So, it was enough to try

```
apt-get install indicator-appmenu
```May be it still helps somebody who waited some time to upgrade and had this issue.

---

### Post by penreturns on 2012-09-20
try reinstall unity by running following command
> sudo apt-get update sudo apt-get install --reinstall ubuntu-desktop sudo apt-get install unity 

please tag me if you facing problem

---

