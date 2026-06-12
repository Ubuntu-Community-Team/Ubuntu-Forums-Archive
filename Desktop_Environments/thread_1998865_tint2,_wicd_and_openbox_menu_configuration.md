---
title: "tint2, wicd and openbox menu configuration"
date: 2012-06-07
forum: Desktop Environments
---

### Post by lea0342 on 2012-06-07
Hi everyone! first post in ubuntu forum :)

I've used Arch Linux for a couple of years, and now wanted to try lubuntu because i wanted something that "just works out of the box" but to have certain balance between heavyless apps and pleasing usability, so i installed Lubuntu and i really love it...

I wanted to use the default window manager and everything it has preconfigured, but i want to use tint2 as the bottom bar and wicd as network manager application.

So i'll describe what i did and you tell if it's the correct way...

First, i installed both applications with synaptic. Tint2 and wicd-gtk

Second, i edited /etc/xdg/lxsession/lubuntu/autostart
-commented "@lxpanel --profile lubuntu" with "#" and added
-added "@tint2"
-added "@volumeicon"

Now i have two problems... first, network-manager is still active, so i have both wicd-gtk and network-manager in the tint2 tray... and second, the applications menu (with right-click on the desktop) shows very few applications on it, what's the correct way to populate it with all the applications i installed with synaptic?

Thanks in advance!! :D

---

### Post by seppalta on 2012-06-07
For openbox:
[ http://douwil7.100webspace.net/linux/Tuning.html#3]("http://douwil7.100webspace.net/linux/Tuning.html#3")
For Tint2:
[http://douwil7.100webspace.net/linux/tint2.html](http://douwil7.100webspace.net/linux/tint2.html)
[]("http://douwil7.100webspace.net/linux/Tuning.html#3")

---

### Post by lea0342 on 2012-06-07
> **seppalta said:**
> For openbox:
[ http://douwil7.100webspace.net/linux/Tuning.html#3]("http://douwil7.100webspace.net/linux/Tuning.html#3")
For Tint2:
[http://douwil7.100webspace.net/linux/tint2.html](http://douwil7.100webspace.net/linux/tint2.html)
[]("http://douwil7.100webspace.net/linux/Tuning.html#3")

Thanks seppalta! I'll try it at home... 

another thing i forgot is that in the menu with the default config, the logout option works and displays a lot of options such as reboot, shutdown, etc... and without the lxpanel it only shows logout/cancel and it didn't work

---

### Post by lea0342 on 2012-06-07
answering myself to the dual network-manager & wicd simultaneous applications, i read that the simplest way is to uninstall network-manager...

I only need to solve the logout difference in default lxpanel and the desktop openbox menu without the panel :)

---

