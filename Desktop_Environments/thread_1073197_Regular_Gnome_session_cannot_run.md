---
title: "Regular Gnome session cannot run"
date: 2009-02-18
forum: Desktop Environments
---

### Post by theshibboleth on 2009-02-18
Hi, I'm having a problem involving the Gnome desktop environment. I'm only able to log into it in failsafe mode. The content of ~/.xession-errors is

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Unable to create /home/username/.dbus/session-bus
** Message: Another GPG agent already running

I'm working from an untarred backup of my system and have tried reconfiguring X, which results in failsafe mode only being accessible in an 800x600 resolution.

Any suggestions as to how I can get Gnome working properly again?

Thanks.

---

### Post by theshibboleth on 2009-02-23
Anyone have any ideas about this? My system's been kind of static for a week or so now - I haven't installed any new updates for fear that it will break my system more than it's already broken.

---

### Post by theshibboleth on 2009-02-27
Maybe I should ask a different question - will using the command tar xvpfz backup.tgz -C / where backup.tgz is a full back up of the system, as stated at [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087), get rid of all the files that were in all directories before the backup was untarred?

I noticed that I have different versions of some software simultaneously installed, which might be part of the problem I'm having. If so, I'm thinking that my syatem is probably beyond repair, in which case I'll probably do a reinstall.

---

