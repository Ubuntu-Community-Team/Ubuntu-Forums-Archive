---
title: "Openbox + Log Out Script + LightDM"
date: 2011-08-19
forum: Desktop Environments
---

### Post by crking on 2011-08-19
As far as my search goes; all of the openbox logout scripts depend on GDM Display Manager.  (Could any one re-Direct me to best one?)
But what happens to those who use LightDM instead. which script they should use to logout or restart the openbox as normally as those who use GDM.
If there is any script or any method to EXIT openbox { logout -suspend- restart- shtdown} please paste it for those how use LightDM.

---

### Post by kerry_s on 2011-08-19
well the switch to lightdm is not till 11.10, unless a person is testing, i doubt anyone's doing scripts yet.

anyways the normal methods should still work.

terminal commands:
log out = openbox --exit
suspend = sudo pm-suspend
restart = sudo reboot
shutdown = sudo halt

the problem with suspend, restart & shutdown is requires root. there is a method using dbus, which doesn't require password. you can google the dbus commands.

---

### Post by crking on 2011-08-20
> **kerry_s said:**
> 
anyways the normal methods should still work.

terminal commands:
log out = openbox --exit
suspend = sudo pm-suspend
restart = sudo reboot
shutdown = sudo halt



Does these commands and DBUS commands Universal among Linux distros or just for ubuntu?

---

### Post by crking on 2011-08-20
What about Zinethy or OBlogout  scripts?
Do they depend on GDM or something???

---

### Post by kerry_s on 2011-08-20
> **crking said:**
> What about Zinethy or OBlogout  scripts?
Do they depend on GDM or something???

No, they should work. 
The commands are all Linux.

---

