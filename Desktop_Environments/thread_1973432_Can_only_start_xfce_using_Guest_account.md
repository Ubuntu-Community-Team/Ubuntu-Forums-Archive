---
title: "Can only start xfce using Guest account"
date: 2012-05-04
forum: Desktop Environments
---

### Post by NuxIT on 2012-05-04
Hi, I'm having an issue with starting my xfce using my user account. 

After putting in my user ID and password I get the splash screen, then a blank screen with the 'wait' cursor, and it goes back to the login prompt. I've tried both xfce Session and Xubuntu Session and they both do this. I was able to login after I did the upgrade using my user account but after I was ssh'd in at work today I got home and this happened. I think it could have to do with me messing around with xrdp over ssh today. I deleted startwm.sh out of xrdp directory because I was getting a failed to load gnome message when trying remote desktop which was strange because I don't have gnome installed. When I deleted startwm.sh and used mstsc (remote desktop) to login to the desktop it dropped me to a prompt. I then typed startxfce4 to startup the desktop from the prompt. This worked and I was able to use the GUI but I think it borked my settings somehow? I restored the startwm.sh from backup but issue still happens.

However, back on the machine locally when I choose the Guest Account to login it goes into xfce fine without issues. But whenever I try my user account xfce  won't load. Any ideas? Must be something on my user account that messed things up. I can't find anything in /var/log,etc.. Thanks

---

### Post by steeldriver on 2012-05-04
did you check to see if the permissions/ownership of your ~/.Xauthority and/or ~/.ICEauthority files got screwed up?

---

### Post by NuxIT on 2012-05-04
Hey, no I haven't checked that and I'm not exactly sure how? If I do a ll on that directory and list it here will that help? 

-rw------- 1 steve steve 8812 May  4 18:04 .ICEauthority
-rw------- 1 root root 0 May  4 06:37 .Xauthority

I'd rather not have to do a backup and start from scratch since I have quite a few customizations on this load. Thx again for any/all suggestions/help. Still digging around myself. I tried deleting .Xdefaults out of my user directory but that didn't help. Guest account works just fine. I'm pretty sure I borked X setup for my user acct when I connected @ work using rdp over ssh and then startxfce4 from the command line. I can still do that to connect using my user acct but that's not effective. Pretty sure that's what started this. *sigh*

Here's the output from my .xsession-errors
```
.xsession-errors |more
openConnection: connect: No such file or directory
cannot connect to brltty at :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
xrdb:  "Xft.antialias" on line 47 overrides entry on line 11
xrdb:  "Xft.hinting" on line 48 overrides entry on line 13
xrdb:  "Xft.rgba" on line 49 overrides entry on line 12
xrdb:  "Xft.hintstyle" on line 50 overrides entry on line 14
xfce4-settings-helper: Another instance is already running. Leaving...

(polkit-gnome-authentication-agent-1:1655): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(xfce4-indicator-plugin:1642): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(polkit-gnome-authentication-agent-1:1655): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (xfce4-clipman:1647): WARNING **: Clipboard manager is already running.

(xfce4-indicator-plugin:1642): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1642): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** Message: applet now removed from the notification area

(nm-applet:1666): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-mqwnNF/pkcs11: No such file or directory
Xsession: X session started for  at Thu May  3 20:41:27 MDT 2012
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:styles being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[2234]: WARNING: GSIdleMonitor: IDLETIME counter not found
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-mqwnNF/pkcs11: No such file or directory
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-mqwnNF/pkcs11: No such file or directory
2012-05-03 21:42:07,014 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2012-05-03 21:42:07,014 - root - ERROR - Could not find any typelib for Gst
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-mqwnNF/pkcs11: No such file or directory
2012-05-03 21:42:08,639 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-05-03 21:42:08,795 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-05-03 21:42:09,541 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2012-05-03 21:42:09,540 - root - ERROR - Could not find any typelib for Gst
2012-05-03 21:42:18,769 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-05-03 21:42:26,557 - softwarecenter.ui.gtk3.app - INFO - found a running software-center on dbus, reconnecting
2012-05-03 21:43:26,544 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2012-05-03 21:43:26,548 - softwarecenter.db.database - INFO - reopen() database
2012-05-03 21:43:26,549 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
** Message: xfsm-shutdown-helper.c:1472: Using ConsoleKit to Restart
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
xfce4-clipman: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(polkit-gnome-authentication-agent-1:1655): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
** Message: using fallback from indicator to GtkStatusIcon

(nm-applet:1666): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

Xsession: X session started for  at Fri May  4 06:20:34 MDT 2012
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:styles being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
Setting IM through im-switch for locale=en_US.
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[2347]: WARNING: GSIdleMonitor: IDLETIME counter not found
Xsession: X session started for  at Fri May  4 15:42:28 MDT 2012
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:styles being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[2875]: WARNING: GSIdleMonitor: IDLETIME counter not found
Xsession: X session started for  at Fri May  4 16:03:18 MDT 2012
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:styles being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
Setting IM through im-switch for locale=en_US.
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[2552]: WARNING: GSIdleMonitor: IDLETIME counter not found

```

---

### Post by NuxIT on 2012-05-04
> **steeldriver said:**
> did you check to see if the permissions/ownership of your ~/.Xauthority and/or ~/.ICEauthority files got screwed up?

w00t. Mad Beans4U My Friend!! I deleted .Xauthority and that worked!! Bam!! THANKS!!! ):P

---

