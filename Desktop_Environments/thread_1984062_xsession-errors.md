---
title: "xsession-errors"
date: 2012-05-21
forum: Desktop Environments
---

### Post by davidbilla on 2012-05-21
Hi all,

I have Ubuntu 12.04 64-bit running on my machine. This morning, it refused to login (the login screen was stuck with 'Logging In' message). The only thing I was able to do was to click on restart. I restarted twice or thrice with the same result.

Then I booted with the older kernel which booted up fine. I restarted it again with the newer kernel and it worked fine this time. Now, in my $HOME, I found a '.xsession-errors.old' file which I attach here.

```
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
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
I/O warning : failed to load external entity "/home/user/.compiz/session/107fdb90dc3d3c2728133759021021488600000017350033"
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
** Message: applet now removed from the notification area
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done
** Message: using fallback from indicator to GtkStatusIcon

(nm-applet:1816): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(compiz:1801): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "launcher_hide_mode"
Setting Update "icon_size"
Setting Update "edge_responsiveness"
** Message: moving back from GtkStatusIcon to indicator

** (gnome-screensaver:1983): WARNING **: screensaver already running in this session

** (zeitgeist-datahub:1982): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///data/current/website/optimus.html" was not found, exec: seamonkey-bin, mime_type: text/html

** (zeitgeist-datahub:1982): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///data/current/website/meqtrees.html" was not found, exec: seamonkey-bin, mime_type: text/html

(gnome-settings-daemon:1784): print-notifications-plugin-CRITICAL **: gsd_print_notifications_plugin_finalize: assertion `plugin->priv != NULL' failed

(gnome-settings-daemon:1784): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-settings-daemon:1784): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-fallback-mount-helper:1817): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nm-applet:1816): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(bluetooth-applet:1821): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gdu-notification-daemon:1948): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(telepathy-indicator:1952): Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nautilus:1819): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


** (zeitgeist-datahub:1982): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 151 requests (151 known processed) with 0 events remaining.
```

I would like to know whether this is a compiz/unity error and if it is, whether anyone else has come across such error. This is my work machine and it would really be a pain to have to re-install everything.

Also, if it helps, the daemon 'colord' crashes whenever I boot up.

Thanks!

---

