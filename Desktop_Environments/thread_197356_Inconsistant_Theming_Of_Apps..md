---
title: "Inconsistant Theming Of Apps."
date: 2006-06-15
forum: Desktop Environments
---

### Post by rshd301 on 2006-06-15
Why do some GTK2 themes not theme the controls of say Synaptic and others do?
The Human GTK theme does a nice job of theming all apps but other themes leave Synaptic (as an example) all clunky and Windows 95 looking.

Any suggestions ?

---

### Post by aysiu on 2006-06-15
Have you already symlinked root's theme directories to your home's theme directories?

---

### Post by bruce89 on 2006-06-15
Synaptic is fine for me.

---

### Post by rshd301 on 2006-06-15
Could you explain what you mean exactly please ?

---

### Post by ayoli on 2006-06-15
sylinked symbolic link by type as root: ln -s /home/user_name/.themes /root

that's a way, i prefer have themes wide installed in /usr/share/themes.

---

### Post by aysiu on 2006-06-15
[QUOTE=rshd301]Could you explain what you mean exactly please ?[/QUOTE] ```
sudo mv /root/.themes /root/.themes.old
sudo mv /root/.icons /root/.icons.old
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

### Post by rshd301 on 2006-06-15
Many thanks. Everything working fine now.

---

### Post by newman on 2007-09-14
I was wondering the same thing, but now it works. Simple solution to a simple promblem that should not exist in the first place.

---

### Post by z0phi3l on 2007-09-14
> **newman said:**
> I was wondering the same thing, but now it works. Simple solution to a simple promblem that should not exist in the first place.

Why is that?

If you don't put your themes in the root theme folder how can Admin apps run themed?

---

### Post by newman on 2007-09-14
I was referring to the fact that when you install a theme it should be consistent, ie - skin the entire OS, but I could be mistaken...

---

### Post by miggols99 on 2007-09-15
Actually, I like having root apps look "out of place" to tell me hey you're running this as root so be careful. Well in KDE you can change the settings for root separately.

---

### Post by z0phi3l on 2007-09-15
Same I rather prefer the visual reminder that I'm in admin mode and to be slightly more careful messing with certain files.

---

### Post by krismatth3 on 2007-09-15
Not if you install the theme as user only. Then it will only work for.. that user.

---

