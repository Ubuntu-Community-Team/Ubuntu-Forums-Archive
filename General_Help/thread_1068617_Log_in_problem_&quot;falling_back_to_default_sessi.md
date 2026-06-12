---
title: "Log in problem: &quot;falling back to default session&quot;"
date: 2009-02-13
forum: General Help
---

### Post by jofre on 2009-02-13
Hi everyone,

I started having a funny problem some time ago: I could not log in into xfce or openbox, only to gnome. In addition, the gnome had the wrong screen resolution, even if I pretty sure that I do have a correct xorg.conf file.

I have been totally puzzled for a while but I think that I found what could help to find the source of the problem and therefore, to find a solution different from reinstall.

Here it is my .xsession-errors file:

/etc/gdm/Xsession: Beginning session setup...
/bin/sh: Can't open /usr/bin/which
Xsession: unable to launch "/usr/bin/gnome-session" X session --- 
"/usr/bin/gnome-session" not found; falling back to default session.
Xsession: warning: xrdb command not found; X resources not merged.
Setting IM through im-switch for locale=fr_FR.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Window manager warning: Failed to read saved session file /home/jofre/.config/metacity/sessions/10879900a450e0e78a123451442026233800000060270009.ms: Failed to open file '/home/jofre/.config/metacity/sessions/10879900a450e0e78a123451442026233800000060270009.ms': No such file or directory
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:6153): WARNING **: Unable to add monitor: Not supported

(gnome-panel:6149): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 23
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

x-session-manager[6027]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
Failure: Module initalization failed



I tried to find info about the error messages, but all I found was people with problems about the permission of the .ICEauthority file. I checked and I am well the owner.

Well now I hope that somebody much more knowledgeable than I am about this things could give me a hand!

---

### Post by jofre on 2009-02-14
No ideas? 

At least if somebody could told me where I can more info about what happen when I log in, which files are call and so on... I did not find much documentation in the GDM website....

Jofre

---

