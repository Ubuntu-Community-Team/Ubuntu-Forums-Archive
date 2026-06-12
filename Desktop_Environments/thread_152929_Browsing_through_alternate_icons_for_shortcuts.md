---
title: "Browsing through alternate icons for shortcuts"
date: 2006-03-30
forum: Desktop Environments
---

### Post by DjKritical on 2006-03-30
Sup,

If you're like me you enjoy changign the icons that launch your applications..

Why is it that I only get to choose from a very small number of icons, even when I have tonnes of icon themes installed on my box?

Anyone know a trick to get it to display more icons without having to browse through the directories?

Cheers :cool:

---

### Post by Qrk on 2006-03-30
For themes I like, I copy the /usr/share/icons/themename/apps to /usr/share/pixmaps

For example, OSX icons 
```
sudo cp /usr/share/icons/OSX/scalable/apps/*.png /usr/share/pixmaps
```

---

### Post by 5-HT on 2006-03-30
You could create symbolic links in the main icon directory pointing to all other directories where you have icons if you want to keep them relatively separate (i.e., if you dont want to copy them over or move them).

If you'd like to just copy them over, Qrk's advice is great.

The format is:  ln -s <directory where you have the icons you want included> <directory to link the icons to>

HTH

---

### Post by DjKritical on 2006-03-30
Thanks I'll give it a try ;)

---

