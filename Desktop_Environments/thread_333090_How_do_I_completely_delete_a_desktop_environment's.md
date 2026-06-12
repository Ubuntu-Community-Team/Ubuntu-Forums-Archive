---
title: "How do I completely delete a desktop environment's settings? [Resolved]"
date: 2007-01-06
forum: Desktop Environments
---

### Post by wersdaluv on 2007-01-06
After having my KDE and Xfce desktop environments crash, I have uninstalled and reinstalled them but I keep on seeing my old ruined desktop environment.

How do I completely delete a desktop environment's settings for me to have a fresh new one?

---

### Post by aysiu on 2007-01-06
Try these terminal commands: ```
mv ~/.kde ~/.kde.old
mv ~/.config ~/.config.old
mv ~/.xfce ~/.xfce.old
``` If you don't like the terminal, open up Nautilus and press Control-H and rename any suspicious-looking directories. I'd recommend renaming over deleting, as you may accidentally delete something important to you.

---

### Post by wersdaluv on 2007-01-06
hahaha... gotta love the terminal!

Thanks! :)

---

### Post by aysiu on 2007-01-06
> **wersdaluv said:**
> hahaha... gotta love the terminal!

Thanks! :)
So that worked?

---

### Post by wersdaluv on 2007-01-06
I'm still installing codecs via the terminal. I'm just going to try it.

Do you think I can do both tasks at the same time or only one can be done at a time?

---

### Post by wersdaluv on 2007-01-06
It said "No such file or directory."

Actually, I have the two uninstalled again.

I'll just install the two again and then I'll try the code that you gave me

---

### Post by wersdaluv on 2007-01-06
It works aysiu! It works! It works!!!

I have been posting many threads that have been describing this same problem in different ways but only solved it! thank you very much! :) :) :)

---

### Post by wersdaluv on 2007-01-23
> **aysiu said:**
> Try these terminal commands: ```
mv ~/.kde ~/.kde.old
mv ~/.config ~/.config.old
mv ~/.xfce ~/.xfce.old
``` If you don't like the terminal, open up Nautilus and press Control-H and rename any suspicious-looking directories. I'd recommend renaming over deleting, as you may accidentally delete something important to you.

This time, what I want to delete are the settings of my GNOME desktop. How do I do it? I don't want to experiment by improvising codes because I might delete valuable data.

---

### Post by aysiu on 2007-01-23
Don't delete. Just rename.

The files you want to rename are ~/.gnome, ~/.gnome2, ~/.gconf, ~/.gconfd, ~/.metacity

---

