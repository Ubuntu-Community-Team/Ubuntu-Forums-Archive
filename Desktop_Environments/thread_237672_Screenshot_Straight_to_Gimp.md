---
title: "Screenshot Straight to Gimp?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by BitTorrentBuddha on 2006-08-16
Is there a way I could make a script to (or through some other means) automatically take a screenshot and send it to gimp for editing?

---

### Post by engla on 2006-08-16
This is perhaps not it, but you can take screenshots right from gimp, and edit them directly after that.

---

### Post by Ramses de Norre on 2006-08-16
```
sudo aptitude install scrot
```
```
scrot -q 85 -d 5 shot.png && gimp shot.png &
```
The -q gives the quality (a number between 0 and 100), -d specifies how many seconds to wait before the screenshot is token. Read man scrot for more info.

---

### Post by BitTorrentBuddha on 2006-08-16
Wow, much obliged. That's exactly what I was looking for!

---

