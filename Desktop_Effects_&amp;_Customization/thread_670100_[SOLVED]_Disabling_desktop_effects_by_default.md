---
title: "[SOLVED] Disabling desktop effects by default"
date: 2008-01-17
forum: Desktop Effects &amp; Customization
---

### Post by Tim.R on 2008-01-17
I am a systems administrator at a university and we run several computer labs that (will) run Ubuntu 7.10.

Unfortunately Matlab does not play nice with compiz, so it needs to be disabled.  Disabling the desktop effects via the Appearance customisation menu only does so on a per-user basis, and I would like them to be disabled globally by default.

If you log in as a user whose home directory has no .gnome* and .gconf directories, GNOME nicely regenerates them for you.  Does anybody know how I would go about changing the GNOME defaults to turn off desktop-effects?  The home directories are NFS-mounted and it's pre-semester, so I have no problems deleting everyone's .gconf or .gnome* directories.  There is nothing in /etc/skel (not that there should be), nor /etc/default, /etc/gnome or /etc/gconf that seems to be related.

I turned on the effects, copied the .gconf files to a temporary directory, turned them off again and ran a diff.  Apart from a bunch of meaningless changes (such as timestamps), I found this in .gconf/desktop/gnome/applications/window_manager/%gconf.xml
```

desktop/gnome/applications/window_manager/%gconf.xml
6,7c6,7
<         <entry name="default" mtime="1200540264" type="string">
<                 <stringvalue>/usr/bin/metacity</stringvalue>
---
>         <entry name="default" mtime="1200539625" type="string">
>                 <stringvalue>/usr/bin/compiz</stringvalue>


```

If I could find where GNOME stores its default config, I could make this change.  gconf-editor says that it's deprecated, though, so presumably therefore it makes the change somewhere else as well (and I can't find that).

I *could* just copy a sample set of user configurations over to each user's home directory, but that isn't very robust as it assumes that they won't delete this.

It's not necessary to lock the students from using it, only to have it off by default.

Ideas?

---

### Post by rune0077 on 2008-01-17
Wouldn't it be possible to just uninstall Compiz through Synaptic?

---

### Post by mannheim on 2008-01-17
You can set a default preference for all users using either gonf-editor or the command-line gconftool-2. An example using gconftool-2 is [here]("http://www.gnome.org/learn/admin-guide/latest/gconf-7.html").

To use gconf-editor, launch is as root using sudo. Then go to the "File" menu and select "New Defaults Menu". Make some changes in the gconf editor window that appears. You will be changing the defaults for all users.

---

### Post by Tim.R on 2008-01-17
Thanks, using gconf-editor worked great!

---

