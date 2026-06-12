---
title: "Can't change root preferences with kde and qtcurve"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by noahsark1126 on 2008-01-30
I recently switched over to a few KDE applications (Amarok, etc), but I'd still like to keep my Gnome environment, so I decided to try and unify the styles by using qtcurve.  I installed kcontrol and customized it pretty extensively, and it nicely applied the changes to both KDE and Gnome apps, so they all look the same.

The problem is with root user settings.  Before I had qtcurve installed, I could run "gksu gnome-appearance-properties," and then customize the settings there such that when I ran root applications, they still looked unified.  This came in handy when running synaptic, etc.  This no longer seems to work.  My root apps keep the standard qtcurve style no matter what I do.  I tried running "gksu kcontrol" and changing the settings, simply logging in as root entirely, copying my settings files over to the root user's folder...I can't get it to work.

I should also note that when I run "gksu gnome-appearance-properties", I get a dialog that says

```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

On the other hand, I always used to get this warning, and it still worked.  

Another strange thing is that it seems to be ignoring ALL of my settings now.  I can;t control the fonts or anything else.

Any way to regain control?? (other than removing KDE)

---

### Post by fracklaus on 2008-02-28
Hi,

copy .config/qtcurve* to roots .config-directory, and almost all settings of qtcurve get applied to your root account (basically, for some reason I did not yet figure out, some colors are missing, but most of them work).
The reason why you feel out of control of your roots gtk-settings is that gksu (at least for me, kdesu does so) copies your GTK2_RC_FILES environment variable over to the root shell (try with gksu xterm and echo $GTK2_RC_FILES), which then point to the gtk settings of your user account. This enables qtcurve, but qtcurve in this situation does not find its settings file which are expected to be in .config/qtcurve* in the home of the respective user.

Hope that helps.

Regards
Heiner

---

