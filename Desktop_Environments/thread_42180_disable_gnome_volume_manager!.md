---
title: "disable gnome volume manager?!"
date: 2005-06-16
forum: Desktop Environments
---

### Post by bjunix on 2005-06-16
Hello

how do i disable the gnome volume manager. i do not need "hotplug". i like the debian style to mount and umount my devices manually. 

But noob as i am i dont know how to disable the gnome "automount"

---

### Post by raetsel on 2005-06-16
Hi bj,

You can control the operation of automounting under System -> Preferences -> Removable Drives And Media

Here you can un-tick all the auto mounting options.

I guess this still means the gnome-volume-manager is still running as  a background process but not doing much.

I would have thought there are some gnome config settings to stop it running but I am not sure where they would be.

Regards,
Simon

---

### Post by intangible on 2005-06-18
[QUOTE=bjunix]Hello

how do i disable the gnome volume manager. i do not need "hotplug". i like the debian style to mount and umount my devices manually. 

But noob as i am i dont know how to disable the gnome "automount"[/QUOTE]
 After doing what the other reply said, try this also:

Open gnome-system-monitor and kill the process, then goto **System->Preferences->Sessions** and remove gnome-volume-manager, and click apply.  Then make log out and make sure you choose to save session settings, or run **gnome-session-save --gui** to save settings now.

Log out, then back in and see if it is gone.

---

