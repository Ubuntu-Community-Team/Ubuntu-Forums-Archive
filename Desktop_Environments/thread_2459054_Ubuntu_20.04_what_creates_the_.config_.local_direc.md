---
title: "Ubuntu 20.04 what creates the .config .local directories"
date: 2021-03-09
forum: Desktop Environments
---

### Post by advation on 2021-03-09
I'm creating a script that will help me automate setting up a specifically configured user account on Ubuntu 20.04 using Gnome3. I'd like to know what generates the .config and .local directories in the /home/<new user> directory? Any help would be greatly appreciated. 

Thanks!

---

### Post by CatKiller on 2021-03-09
Anything that follows the [XDG base directory specification](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html).

---

### Post by advation on 2021-03-09
Thank you for the direction!

---

