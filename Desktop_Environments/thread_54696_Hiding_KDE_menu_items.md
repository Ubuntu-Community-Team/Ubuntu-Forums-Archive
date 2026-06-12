---
title: "Hiding KDE menu items"
date: 2005-08-05
forum: Desktop Environments
---

### Post by Hig on 2005-08-05
I recently installed the KDE package using apt-get because my girlfriend prefers KDE to GNOME, but it has poluted my menus with KDE based applications to beat the band. Is there any way of hiding these when in GNOME? I dont really care if they're still installed, as long as all those icon-less items are gone from my menu.

EDIT: If removing KDE is the only way to do so, will removing kubuntu-desktop from synaptic remove all associated applications?

---

### Post by rosslaird on 2005-08-05
I think there is a way. It's something like "showinkdeonly=yes" in the .desktop file for each item. But I can't remember the exact details (somewhere on the forum there's a thread about this -- let me know if you find it!).

Cheers.

Ross

---

### Post by Hig on 2005-08-05
```
cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*
```

Credit goes to Nekrataal.

(Sorry, I had spelled one of my search criteria wrong)

---

