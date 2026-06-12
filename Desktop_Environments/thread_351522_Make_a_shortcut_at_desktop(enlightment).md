---
title: "Make a shortcut at desktop(enlightment)"
date: 2007-02-02
forum: Desktop Environments
---

### Post by znerk on 2007-02-02
Can any one help me with creating shortcut at desktop?
Need a shortcut for Nautilus file manager.. so I can browse my harddrives..Instead of pressing start and press "Files", that file manager is not good...



-Thanks-

---

### Post by paparucino on 2007-02-02
> **znerk said:**
> Can any one help me with creating shortcut at desktop?
Need a shortcut for Nautilus file manager.. so I can browse my harddrives..Instead of pressing start and press "Files", that file manager is not good...-
Open a terminal (gnome-terminal, xterm, rxvt, aterm....) then 
```

ln -s /usr/bin/nautilus /home/your_home_directory/Desktop/nautilus

```
You should see a an icon called nautils on your desktop. Right click on it, click on the left icon and configure as you prefer

---

