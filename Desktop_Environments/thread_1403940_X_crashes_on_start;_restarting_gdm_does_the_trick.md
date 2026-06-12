---
title: "X crashes on start; restarting gdm does the trick"
date: 2010-02-10
forum: Desktop Environments
---

### Post by bruno321 on 2010-02-10
Hi. I've just done a fresh Xubuntu 9.10 install and I'm having this weird problem. When X is starting, the monitor does that "click" resolution change sound, but then it won't boot. The standard resolution was 1600*1200; I graphically changed it to 1280*1024 when in xfce.

I don't know if that has anything to do with it, but I *can* boot X if I

/etc/init.d/gdm restart

but of course, it's not nice having to do it on every boot. It starts up in 1280*1024 by the way.

Xsession-errors shows

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=es_UY.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
Failed to run gnome-keyring-daemon: Ha ocurrido un error al ejecutar el proceso hijo «gnome-keyring-daemon» (No existe el fichero ó directorio)

** (gnome-screensaver:2205): WARNING **: Failed to get session presence proxy: Could not get owner of name 'org.gnome.SessionManager': no such name
xfdesktop[2226]: starting up

(xfce4-mixer-plugin:2240): libxfce4mixer-CRITICAL **: xfce_mixer_get_track: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:2240): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_card: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:2240): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_track: assertion `GST_IS_MIXER_TRACK (track)' failed
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::odd-row-color' of type `GdkColor' from rc file value "((GString*) 0x9412a00)" of type `GString'

(firefox:2254): GLib-WARNING **: g_set_prgname() called multiple times

(polkit-gnome-authentication-agent-1:2261): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2261): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::odd-row-color' of type `GdkColor' from rc file value "((GString*) 0xb74e5230)" of type `GString'

```

Thank you for any help.

---

### Post by bruno321 on 2010-02-11
Bump, this is still unsolved

---

### Post by epp on 2010-06-09
I began having this same problem on a 64-bit installation a couple of weeks ago, no idea what is causing it.  

The .xesssion-errors file looks similar except it also makes reference to HPLIP (HP Linux printing software).  I deleted that package (hplip-gui) from the directory where they're stored and reinstalled it, no change.

---

