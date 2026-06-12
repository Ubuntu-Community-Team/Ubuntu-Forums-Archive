---
title: "Compiz-Fusion was working yesterday...."
date: 2007-08-08
forum: Desktop Effects &amp; Customization
---

### Post by breenmachine on 2007-08-08
Hi.  I managed to get Compiz Fusion working on my ATI card with XGL a few days ago when I installed Ubuntu.  I really like the OS so far and its my first time using linux for more than a few days without getting fed up with bad hardware compatibility.

Anyways, Compiz was working great up until this afternoon now it just stopped working. When I try to load it I get the following

```

steve@steve-laptop:~$ compiz --replace
Checking for Xgl: present. 
Converting gconf plugin list: '' 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...

(gtk-window-decorator:5754): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5754): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5754): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5754): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5754): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5754): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5754): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5754): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

I really have no idea what to do from here.  The only thing I can think of that would have caused this is some recent updates that were for Compiz-Fusion.  Now that I think about it, that was only last night and this may have been my first time rebooting since then.

Does anyone know how to fix this? I've really started to love Compiz and Avant. Thanks.

---

### Post by dondad on 2007-08-08
Probably totally unrelated, but I had the same issue, although I have not rebooted. Yesterday Compiz-fusion was working fine, and today nothing worked. I use the icon to switch, and got the 4 workspaces shown in the panel, but couldn't do anything. I went to synaptic and did a complete uninstall of all of the compiz items, then reinstalled and that fixed it.

---

### Post by breenmachine on 2007-08-08
Well I just uninstalled and reinstalled and now its working again.... Must be a problem with an update, that kind of sucks. Thanks for the help though, hopefully doesn happen again.

---

