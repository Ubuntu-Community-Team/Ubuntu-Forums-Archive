---
title: "Disable gdm autostart"
date: 2010-03-03
forum: Desktop Environments
---

### Post by letharion on 2010-03-03
Hello :)

I would like to remove gdm from the auto-starting scripts.
I tried
sudo update-rc.d -f gdm remove
which tells me what I wanna hear
"removing symlinks"
but after a reboot gdm starts anyway.

I manually unlinked /etc/init.d/gdm, but gdm still starts.
I have linux experience, but don't understand how Ubuntus upstart works.

I use 08.04 LTS

---

### Post by warp99 on 2010-03-03
The upstart file is located in /etc/init and now it's called gdm.conf. You could also empty the file "/etc/X11/default-display-manager" since the gdm.conf script does grep the file and will exit if the string doesn't match.

---

### Post by letharion on 2010-03-08
Thanks :)

---

