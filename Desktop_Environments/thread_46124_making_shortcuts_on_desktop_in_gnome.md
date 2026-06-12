---
title: "making shortcuts on desktop in gnome"
date: 2005-07-03
forum: Desktop Environments
---

### Post by dworzec.net on 2005-07-03
I want to make shortcuts to various directories (for ex. /mnt/windows/documents) on my Desktop.
In KDE it's there's this very easy "drag and drop" option for this, but how to do this in Gnome?

---

### Post by frodon on 2005-07-03
I use command line to do it but it's certainly possible with graphical interface.
I just build a symbolik link of the wanted directory in Desktop repertory : ```
cd /home/your_user_name/Desktop
sudo ln -sf the_wanted_directory .
```

that's all, generally after doing that I change the default icon for a customized one.

---

