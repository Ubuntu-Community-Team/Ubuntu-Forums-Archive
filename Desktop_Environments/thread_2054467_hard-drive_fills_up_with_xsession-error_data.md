---
title: "hard-drive fills up with xsession-error data"
date: 2012-09-07
forum: Desktop Environments
---

### Post by derekcentrico on 2012-09-07
I have a 500GB hard-drive of which only 60GB is used for real data.  However, .xsession-error fills up this entire disk every three days.  Mainly I VNC to the machine although I don't know that this matters in the grand schema.

I setup the following script to remove old .xsession data and to /dev/null output.  The script runs upon login.
```
#!/bin/bash 

rm -rf /home/derek/.xsession-errors
rm -rf /home/derek/.xsession-errors.old
sudo -u derek ln -sf /dev/null /home/derek/.xsession-errors

```

Everything went fine for five days.  However, I noticed the hard-drive full again today.  I searched for the offending file, but none could be found of any size value.  I thought /dev/null would keep this from clogging up...

I rebooted and I'm back to the ~60GB usage level.

How can I keep from having to reboot often for excess data? 

Input appreciated.

---

### Post by SlugSlug on 2012-09-07
remove the link and post output of error log

---

### Post by derekcentrico on 2012-09-07
> **SlugSlug said:**
> remove the link and post output of error log

Currently, it isn't huge.  The growth takes off after a while out of no where...  However, here's the quick amount of errors within about three minutes of the log file existing.
6.5K Sep  7 11:52 .xsession-errors

```
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done

(vino-server:2577): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion `global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
07/09/2012 11:49:21 AM Autoprobing TCP port in (all) network interface
07/09/2012 11:49:21 AM Listening IPv6://[::]:5900
07/09/2012 11:49:21 AM Listening IPv4://0.0.0.0:5900
07/09/2012 11:49:21 AM Autoprobing selected port 5900
07/09/2012 11:49:21 AM Advertising security type: 'TLS' (18)
07/09/2012 11:49:21 AM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
07/09/2012 11:49:21 AM Listening IPv6://[::]:5900
07/09/2012 11:49:21 AM Listening IPv4://0.0.0.0:5900
07/09/2012 11:49:21 AM Clearing securityTypes
07/09/2012 11:49:21 AM Advertising security type: 'TLS' (18)
07/09/2012 11:49:21 AM Clearing securityTypes
07/09/2012 11:49:21 AM Advertising security type: 'TLS' (18)
07/09/2012 11:49:21 AM Advertising authentication type: 'No Authentication' (1)
07/09/2012 11:49:21 AM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
07/09/2012 11:49:21 AM Listening IPv6://[::]:5900
07/09/2012 11:49:21 AM Listening IPv4://0.0.0.0:5900
07/09/2012 11:49:21 AM Clearing securityTypes
07/09/2012 11:49:21 AM Clearing authTypes
07/09/2012 11:49:21 AM Advertising security type: 'TLS' (18)
07/09/2012 11:49:21 AM Advertising authentication type: 'VNC Authentication' (2)
07/09/2012 11:49:21 AM Clearing securityTypes
07/09/2012 11:49:21 AM Clearing authTypes
07/09/2012 11:49:21 AM Advertising security type: 'TLS' (18)
07/09/2012 11:49:21 AM Advertising authentication type: 'VNC Authentication' (2)
07/09/2012 11:49:21 AM Advertising security type: 'VNC Authentication' (2)

(vino-server:2577): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
** Message: applet now removed from the notification area
Initializing composite options...done
** Message: using fallback from indicator to GtkStatusIcon
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
I/O warning : failed to load external entity "/home/derek/.compiz/session/10b491f39fb84b455a134703295554204600000016990038"
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done

(gnome-settings-daemon:2064): color-plugin-WARNING **: failed to get edid: unable to get EDID for output

(gnome-settings-daemon:2064): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

(gnome-settings-daemon:2064): color-plugin-WARNING **: failed to reset xrandr-default gamma tables: gamma size is zero
Initializing ezoom options...done

(compiz:2554): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Setting Update "icon_size"
Setting Update "num_launchers"
** Message: moving back from GtkStatusIcon to indicator

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed
```

**EDIT:**

And just a little while later, same sort of errors appear while I'm connected.  The above errors had no vino connection.

```
07/09/2012 12:00:49 PM [IPv4] Got connection from client Derek-Laptop.the-beach.net
07/09/2012 12:00:49 PM   other clients:
07/09/2012 12:00:49 PM Client Protocol Version 3.7
07/09/2012 12:00:49 PM Advertising security type 18
07/09/2012 12:00:49 PM Advertising security type 2
07/09/2012 12:00:49 PM Client returned security type 2
07/09/2012 12:01:00 PM Pixel format for client Derek-Laptop.the-beach.net:
07/09/2012 12:01:00 PM   32 bpp, depth 24, little endian
07/09/2012 12:01:00 PM   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
07/09/2012 12:01:00 PM no translation needed
07/09/2012 12:01:00 PM rfbProcessClientNormalMessage: ignoring unknown encoding type 8
07/09/2012 12:01:00 PM Using compression level 2 for client Derek-Laptop.the-beach.net
07/09/2012 12:01:00 PM Using image quality level 7 for client Derek-Laptop.the-beach.net
07/09/2012 12:01:00 PM Enabling LastRect protocol extension for client Derek-Laptop.the-beach.net
07/09/2012 12:01:00 PM Enabling NewFBSize protocol extension for client Derek-Laptop.the-beach.net
07/09/2012 12:01:00 PM Enabling cursor position and shape (rich encoding) updates for client Derek-Laptop.the-beach.net

** (gnome-system-monitor:3743): WARNING **: SELinux was found but is not enabled.


(polkit-gnome-authentication-agent-1:2580): polkit-gnome-1-WARNING **: Couldn't open user icon: Failed to open file '/home/derek/.face': No such file or directory

(polkit-gnome-authentication-agent-1:2580): polkit-gnome-1-WARNING **: Couldn't open user icon: Failed to open file '/home/derekcentrico/.face': No such file or directory

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

07/09/2012 12:08:10 PM Client Derek-Laptop.the-beach.net gone
07/09/2012 12:08:10 PM Statistics:
07/09/2012 12:08:10 PM   key events received 30, pointer events 3806
07/09/2012 12:08:10 PM   framebuffer updates 219, rectangles 110559, bytes 58026808
07/09/2012 12:08:10 PM     LastRect and NewFBSize markers 218, bytes 2616
07/09/2012 12:08:10 PM     cursor position updates 80, bytes 960
07/09/2012 12:08:10 PM     tight rectangles 110261, bytes 58023232
07/09/2012 12:08:10 PM   raw bytes equivalent 1805578684, compression ratio 31.118203

```

---

### Post by derekcentrico on 2012-09-07
Aside from the above quoted text a few hours ago, the file is growing to nearly 1MB at this point.

I see a flood of the following which is above too:

```
(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed

(vino-server:2577): GLib-CRITICAL **: the GVariant format string `(u)' has a type of `(u)' but the given value has a type of `()'

(vino-server:2577): GLib-CRITICAL **: g_variant_get: assertion `valid_format_string (format_string, TRUE, value)' failed
```

---

### Post by derekcentrico on 2012-09-07
Now, vino-server is not the culprit.

```
(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:5414): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed
```

---

