---
title: "disable_lock_screen not working in Gnome Classic"
date: 2011-11-28
forum: Desktop Environments
---

### Post by ppareit on 2011-11-28
In previous versions of Ubuntu I would set from gconf-editor
/desktop/gnome/lockdown/disable_lock_screen
so that when the desktop returns from sleep it would not ask me for my password (stupid thing to ask if autologin is set!)

But currently on Gnome Classic (in ubuntu 11.10) this is not working? Am I missing something?

---

### Post by Frogs Hair on 2011-11-28
Open Screen in system settings and turn off lock screen .

---

### Post by ppareit on 2011-11-28
Thank you for your answer. But this is not the problem. This option I already disabled and has nothing to do with suspending the system. I'm talking about suspending the system to RAM. So this is more than just blanking the screen. This is a putting the pc in S3 state.

On previous versions of ubuntu, setting disable_lock_screen would not show a password to the user when coming out of this state. I'm running fedora 16 on an other pc and using Gnome Shell 3.2. That system works correct. I'm seeing the wrong behavior with Ubuntu 11.10 when running GNome Classic 3.2.

---

### Post by ppareit on 2011-11-29
bump

---

### Post by mcduck on 2011-11-29
> **ppareit said:**
> In previous versions of Ubuntu I would set from gconf-editor
/desktop/gnome/lockdown/disable_lock_screen
so that when the desktop returns from sleep it would not ask me for my password (stupid thing to ask if autologin is set!)

But currently on Gnome Classic (in ubuntu 11.10) this is not working? Am I missing something?

Try settng the equivalent option in Dconf instead. Most of the options have already been moved from gconf to gsettings/dconf.

(you'll need to install the [dconf-tools]("apt:dconf-tools") package to get dconf-editor)

---

### Post by ppareit on 2011-12-01
Thanks, that did it. The setting in dconf-editor is at:
org/gnome/desktop/lockdown/disable-lock-screen

---

