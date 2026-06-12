---
title: "Location of Desktop settings for New User"
date: 2008-11-08
forum: Desktop Environments
---

### Post by fballem on 2008-11-08
Use Case:
[LIST=1]
[*]Add a new user using Users and Groups from System menu.
[*]Log off
[*]Login as the new User
[*]User has a desktop that includes default theme, icons, and background.
[/LIST]

Question: Where does ubuntu store the information that is used to determine what the new user panel looks like?

The reason is that I would like to poke around to see if I can change this so that any new user gets a desktop that contains a custom theme, icons, and background.

I tries Sabayon, but it crashed, so I need to find out how to do this the hard way.

Thanks,

---

### Post by ad_267 on 2008-11-08
The default home directory is in /etc/skel

Edit: Looks like you can set the gtk and icon themes in the .gtkrc-2.0 file.
Edit2: After a bit more reading that might not work, because it isn't used by gnome-settings-daemon. You might have to edit the configuration in ~/.gconf/desktop/gnome/interface.

The easiest method would probably be to make a new user, log in as them and change all the settings you want. Then copy their whole home directory to /etc/skel.

---

### Post by fballem on 2008-11-08
> **ad_267 said:**
> The default home directory is in /etc/skel

Edit: Looks like you can set the gtk and icon themes in the .gtkrc-2.0 file.
Edit2: After a bit more reading that might not work, because it isn't used by gnome-settings-daemon. You might have to edit the configuration in ~/.gconf/desktop/gnome/interface.

The easiest method would probably be to make a new user, log in as them and change all the settings you want. Then copy their whole home directory to /etc/skel.

I'll have a look and let you know how I make out. This may take a day or three.

Thanks!

---

### Post by hictio on 2008-11-09
This is an interesting post, there has been another one recently, regarding pretty much the same: [Changing default icons on Gnome panel](http://ubuntuforums.org/showthread.php?t=973014), that also went without a definitive answer.
If there are not on the /etc/skel/ directory, where does the system get the defaults?

---

### Post by ad_267 on 2008-11-09
I don't know if the default theme is set in a configuration theme, I haven't been able to find this out. I think it must be hard coded somewhere because /usr/share/themes/Default/ is pretty much empty except for the keybinding file which says this:

```
#
# Default keybinding set. Empty because it is implemented inline in the code.
#

```

So I think the only way to change the default theme would be to add it to the configuration in /etc/skel

---

### Post by fballem on 2008-11-09
It looks like everything, at least in GNOME is set through gconf. The following link: [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) is making for some very interesting reading.

It will take me a few days to digest this, as well as to closely examine my systems (production and play) to see if this is useful.

I think there is something similar in KDE, but I'm not sure and I'm not in a position to check it out.

I'll keep this thread open and post back the results in a few days.

Thanks,

---

### Post by frenchsquared on 2008-11-21
Desktop configurations are not controlled by /etc/skel
let me know if you figure this out. I want to do the same thing

---

### Post by ad_267 on 2008-11-21
> **frenchsquared said:**
> Desktop configurations are not controlled by /etc/skel
let me know if you figure this out. I want to do the same thing

No the default configuration is not controlled by /etc/skel, but by setting the configuration in /etc/skel you could overwrite the default configuration for new users.

---

