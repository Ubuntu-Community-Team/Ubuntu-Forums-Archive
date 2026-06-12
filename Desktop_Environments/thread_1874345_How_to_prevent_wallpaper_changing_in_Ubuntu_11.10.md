---
title: "How to prevent wallpaper changing in Ubuntu 11.10"
date: 2011-11-02
forum: Desktop Environments
---

### Post by news_js on 2011-11-02
Hi!

I need to prevent the user from changing the wallpaper in Ubuntu 11.10. In previous versions it was easy:

chmod 744 /usr/bin/gnome-appearance-properties 

But in Ubuntu 11.10 gnome-appearance-properties file is not there.

Thanks.

---

### Post by news_js on 2011-11-03
Hi!

Is there any way to do this? I've searched the web and find no answer.

---

### Post by phDaemon on 2011-11-03
Which DM are you using? Gnome or unity?

---

### Post by news_js on 2011-11-03
> **phDaemon said:**
> Which DM are you using? Gnome or unity?

I think it's unity. But if necessary, I can switch to Gnome.

---

### Post by ranjit. on 2011-11-09
well, there is no file gnome-appearance-properties.desktop in /usr/share folders, they have either changed the name of the file or they have moved the file to another location, I really needed the file cause i wanted to change my login screen using that file, If any one can find out what is the alternative for the file it would be really helpful:guitar:

---

### Post by Rakeshvijayan on 2012-02-29
how it possible

---

### Post by talkingtek on 2012-03-28
Did you find an answer for this?  I'm looking for the same answer as well. Let me know if find out the answer.  Thanks!

I'm using gnome.

---

### Post by Krytarik on 2012-03-28
Please see this doc how to *really* "lock down" specific settings keys in Gnome 3, it even has the wallpaper as the example:

[LIST]
[*][http://live.gnome.org/dconf/SystemAdministrators](http://live.gnome.org/dconf/SystemAdministrators)
[/LIST]
But definitely also lock down this key, to make sure the wallpaper is also displayed at all/correctly:

[LIST]
[*]"/org/gnome/desktop/background/picture-options"
[/LIST]
As for 'chmoding' "gnome-appearance-properties" in Gnome 2, that was a cheap, improper method in the first place, as there are at least 3 ways to circumvent that virtual block: GConf-Editor, "gconftool-2" command, editing the concerning XML file directly; plus, the 'lock' would be undone by an upgrade of the respective package, "gnome-control-center".

Regards.

---

