---
title: "[SOLVED] Synaptic won't theme"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by Interestedinthepenguin on 2007-06-08
I've noticed that the Synaptic Package Manager won't obey custom themes.  

I modified one of the default themes, but even then, Synaptic didn't comply.

What's up with that?:-s

---

### Post by cyberlion on 2007-06-08
Simple...
you need copy the folders of themes to /usr/share/themes

if you install the themes with the gnome-theme-manager the themes are in the /home/you_user/.themes/

PS.: in the terminal you use "sudo gnome-theme-manager" and install the themes with you use. too work!

---

### Post by Interestedinthepenguin on 2007-06-08
Thank you, very much.:D

---

### Post by lawr_rawr on 2007-06-09
Or, you can link the theme, icon, and font folders so you do not have to install twice:
```
sudo ln -s /home/username/.themes /root/.themes
sudo ln -s /home/username/.icons /root/.icons
sudo ln -s /home/username/.fonts /root/.fonts
```

cyberlion's way might work best if you have multiple user accounts, but for just me and my sudo, this way is easier for me.

---

### Post by Interestedinthepenguin on 2007-06-13
Thanks for the info, lawr_rawr.  

I've taken note. :)

---

### Post by shearn89 on 2007-06-13
Its basically just that when you run synaptic, its running as the root user, so it'll only use the theme set for root.

---

