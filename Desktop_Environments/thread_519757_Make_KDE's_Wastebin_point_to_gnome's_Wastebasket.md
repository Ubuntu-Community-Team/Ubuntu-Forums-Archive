---
title: "Make KDE's Wastebin point to gnome's Wastebasket"
date: 2007-08-07
forum: Desktop Environments
---

### Post by wild_oscar on 2007-08-07
Is it possible to make the kde's wastebin point to gnome's wastebasket, so that kde applications delete the files to gnome's trash instead of 

/home/miguel/.local/share/Trash/files

?

---

### Post by aysiu on 2007-08-08
I'm not 100% this will work, since I think KDE also keeps info on the files and not just a folder with the files themselves, but you can try this: ```
mv /home/miguel/.local/share/Trash/files /home/miguel/.local/share/Trash/files.old
ln -s /home/miguel/.Trash /home/miguel/.local/share/Trash/files
```

---

