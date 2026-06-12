---
title: "No GUI after installing GNOME 3"
date: 2011-08-19
forum: Desktop Environments
---

### Post by Mars11 on 2011-08-19
I installed GNOME 3, but when I restarted there is no GUI. :\

---

### Post by Mars11 on 2011-08-19
It seems like installing GNOME 3 breaks GDM. I can't find anyone else with the same issue though. I can use other Login Managers and it works. I can't find any other good looking ones. Could you guys suggest me some?

Edit: LightDM would be fine if I could find a theme.

---

### Post by dummy910 on 2011-08-20
Same thing happened to me upon wanting to experiment with Gnome3 just the day before yesterday.

[COLOR=crimson][B]What I did to get my GUI back
[/B] [/COLOR] 
* **boot into a recovery console** (in Grub, select 'Recovery' of the kernel version# you normally boot into) 

* **sudo apt-get remove gnome-session**

* **sudo ppa-purge ppa:gnome3-team/gnome3**

* **sudo apt-get install ubuntu-desktop**

* **reboot** and in Grub, select the **normal kernel version** and _I now had my GUI back, woo hoo!_.

---

