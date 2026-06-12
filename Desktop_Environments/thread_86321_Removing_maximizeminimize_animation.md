---
title: "Removing maximize/minimize animation"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Moonbuzz on 2005-11-04
I decided to cut off on unnecessary eye-candy (Not enough RAM), and part of what I wanted to remove were the desktop animation. I found that I can control some of them through Application> Configuration Editor, but I failed to locate where I can eliminate the animation for the maximize/minimize effect. 
Also, anyone has ideas to cut off a bit on resources, without killing any necessary features?

---

### Post by Kyral on 2005-11-04
Switch over to a lighter Window Manager for one...if you are really strapped

XFCE is quite good

```
sudo apt-get install xubuntu-desktop
```

---

### Post by Moonbuzz on 2005-11-05
I used to have it on my Laptop with Hoary, it's good, but I like Gnome.

---

### Post by 23meg on 2005-11-05
In gconf check the /apps/metacity/general/reduced_resources key. You'll also lose the ability to see window contents while dragging, which will help boost 2d performance a bit.

---

