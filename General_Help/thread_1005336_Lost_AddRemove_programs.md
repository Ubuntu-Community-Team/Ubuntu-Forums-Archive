---
title: "Lost Add/Remove programs"
date: 2008-12-08
forum: General Help
---

### Post by ali_williams on 2008-12-08
Its the weirdest thing I lost my add and remove programs from my account. I did a reboot and it was gone and when i go to system > pref > main menu
I can check the box for the add/remove option to show on my main menu but it unchecks itself right after i check it. whats up wit dat?!!!

---

### Post by plucky on 2008-12-08
Do you still have administration privileges on your account?

Open a terminal and ```
id
gnome-app-install
``` and post any errors.

Or 

Install the application again and see if that works.```
sudo apt-get install gnome-app-install
```

Or 

Open **Synaptic Package manager** and search for "gnome-app-install" and see if it is installed.If not,tick the box and install it.

Good Luck

---

