---
title: "login background / gdm theme has turned black"
date: 2011-06-27
forum: Desktop Environments
---

### Post by foresto on 2011-06-27
Hi, all.

I just installed xubuntu natty, and the gdm theme (xubuntu-gdm-theme) has somehow reverted to something ugly.  The background is black instead of showing xubuntu-greybird.png, the panel bar is light gray, and the shutdown button is now gray instead of a red/orange power icon.

The problem appeared while I was tweaking my account settings, possibly when I used the users-admin tool, but I'm not sure.

I tried purging and reinstalling the following packages:

gdm
xubuntu-gdm-theme
xubuntu-artwork
xubuntu-default-settings
xubuntu-desktop

...but that didn't help.

For comparison, I'm attaching screen shots of my (broken) gdm screen and a correct one from a virtual machine.  (Try to ignore the fact that they're different screen resolutions.)

Anyone have any ideas?

---

### Post by Toz on 2011-06-27
Not sure what the problem is, but perhaps you can use something like GDM Tweaker to fix it: [http://www.webupd8.org/2011/05/change-gdm-theme-background-in-ubuntu.html]("http://www.webupd8.org/2011/05/change-gdm-theme-background-in-ubuntu.html")

---

### Post by foresto on 2011-06-27
Thanks for the idea, but I'd prefer to figure out what actually went wrong, and fix it properly.  GDM Tweaker doesn't seem to have any documentation about what changes it makes, and its source code seems to be unavailable.

---

### Post by Krytarik on 2011-06-27
I can't guess what led to the faulty settings but if you want to fix it with a more transparent approach, see this guide:
[http://ubuntu4beginners.blogspot.com/2011/05/customize-gdm-plymouth-grub2.html](http://ubuntu4beginners.blogspot.com/2011/05/customize-gdm-plymouth-grub2.html)

Greetings.

---

### Post by foresto on 2011-06-27
> **Krytarik said:**
> I can't guess what led to the faulty settings but if you want to fix it with a more transparent approach, see this guide:
[http://ubuntu4beginners.blogspot.com/2011/05/customize-gdm-plymouth-grub2.html](http://ubuntu4beginners.blogspot.com/2011/05/customize-gdm-plymouth-grub2.html)

Thanks, but running gnome-appearance-properties (as suggested on that page) is only marginally better than running GDM Tweaker.  It won't help me identify the bad settings, and will probably change more settings than I want changed.  I really want to know why the xubuntu-gdm-theme package isn't taking effect, and to make it work again.

---

### Post by Toz on 2011-06-27
From the GDM Tweaker source code (available at: [https://launchpad.net/~madnessmike/+archive/madnessmike]("https://launchpad.net/~madnessmike/+archive/madnessmike"))

here is the contents of the subroutine that sets the settings that GDM Tweaker uses to configure the greeter:
```
PUBLIC SUB Applica_Click()
  DIM Valore AS String
  'Applco lo sfondo
  SHELL "sudo -u gdm gconftool-2 --set --type string /desktop/gnome/background/picture_filename '" & PercorsoSfondo.Text & "'" WAIT 
  'il tema GTK
  SHELL "sudo -u gdm gconftool-2 --set --type string /desktop/gnome/interface/gtk_theme '" & Trim(TemaGTK.Text) & "'" WAIT 
  'le icone
  SHELL "sudo -u gdm gconftool-2 --set --type string /desktop/gnome/interface/icon_theme '" & Trim(TemaIcone.Text) & "'" WAIT 
  'nascondiamo o meno la lista degli utenti
  IF NascondiUsername.Value THEN 
    Valore = "true"
  ELSE 
    Valore = "false"
  ENDIF 
  SHELL "sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list " & Valore WAIT 
  'Abilitiamo o meno Compiz
  IF UsaCompiz.Value THEN 
    Valore = "true"
  ELSE 
    Valore = "false"
  ENDIF 
  SHELL "sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/wm_use_compiz " & Valore WAIT 
  SHELL "dpkg-reconfigure gdm" WAIT 
  Message.Info("Settings correctly applied")
END
```

So it looks like it is setting gconf configurations under the gdm profile.

Specifically:
- background image: /desktop/gnome/background/picture_filename
- gtk theme: /desktop/gnome/interface/gtk_theme
- icon theme: /desktop/gnome/interface/icon_theme
- hide username list: /apps/gdm/simple-greeter/disable_user_list
- enable compiz: /apps/gdm/simple-greeter/wm_use_compiz

*Note: You can use the command: **sudo -u gdm gconftool-2 --get <gconf_setting>** to view the current configuration value.

---

### Post by foresto on 2011-06-27
Interesting.  Most of those are the very same gconf settings that xubuntu-gdm-theme sets, and the values are correct:

```
$ for i in /desktop/gnome/background/picture_filename /desktop/gnome/interface/icon_theme /desktop/gnome/interface/gtk_theme /desktop/gnome/interface/buttons_have_icons /desktop/gnome/interface/menus_have_icons ; do sudo -u gdm gconftool-2 --get $i; done
/usr/share/xfce4/backdrops/xubuntu-greybird.png
elementaryXubuntu
greybird
true
true

```

Yet gdm is ignoring them.  Anyone know why?
The image/theme files are present.

---

### Post by Toz on 2011-06-27
Anything in the log files in /var/log/gdm? Looks like **:0-greeter.log** may be the relevant one.

---

### Post by foresto on 2011-06-28
Here it is:

[QUOTE=:0-greeter.log]gnome-session[1042]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
gnome-session[1042]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
** (process:1051): DEBUG: Greeter session pid=1051 display=:0 xauthority=/var/run/gdm/auth-for-gdm-UgF3zU/database

(xfwm4:1053): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.28.6/./gobject/gvalue.c:184: cannot initialize GValue with type `gint', the value has already been initialized as `gint'
gdm-simple-greeter[1051]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
gdm-simple-greeter[1051]: WARNING: Unable to load CK history: no seat-id found
gdm-simple-greeter[1051]: WARNING: Unable to parse history: (null)   1[/QUOTE]

All of those messages except "cannot initialize GValue" and "Unable to parse history" are also present in the virtual machine that correctly displays the xubuntu gdm theme.

(I wonder if that last one was because just I purged and reinstalled gdm again.)

---

### Post by foresto on 2011-06-28
There are some interesting messages in /var/log/syslog, though:

> gdm-session-worker[1059]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
gdm-simple-slave[906]: WARNING: GdmSettingsClient: unable to find schema for key: daemon/DefaultSession

---

### Post by groggyboy on 2011-07-20
I had an identical problem with my installation of Xubuntu.

After reading your output from /var/sys/log, I installed the following two packages on a hunch and restarted: *gnome-settings-daemon* and *gsettings-desktop-schemas*.

One of those packages solved the problem, because I have the proper Xubuntu GDM screen back!

Try it out, and if it works, mark it as solved!

---

### Post by foresto on 2011-07-20
Thank you!  Installing gnome-settings-daemon brought xubuntu-gdm-theme back to life.

I haven't dug deep enough to find out why.  (Does xubuntu-gdm-theme really need gnome-settings-daemon, or just some configuration from its postinst script?  If the former, shouldn't a proper Depends be put in place rather than a mere Recommends?)  Regardless, I'm glad to have things working again.

---

