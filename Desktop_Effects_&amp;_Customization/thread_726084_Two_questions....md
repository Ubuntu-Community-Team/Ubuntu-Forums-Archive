---
title: "Two questions..."
date: 2008-03-16
forum: Desktop Effects &amp; Customization
---

### Post by Izobalax on 2008-03-16
Hello all again!

**Question 1:** The xfce4-panel... how do I remove the icons used in the task list?

**Question 2:** How do I make my fonts that I have available to the root user as well?

/izo\

---

### Post by yabbadabbadont on 2008-03-16
Not sure about the first one but, if your fonts are in ~/.fonts (the .fonts directory in your home directory) then you can create a symbolic link to the directory in /root.

```
sudo -i
cd /root
ln -s /home/yourusernamehere/.fonts

```

Then the fonts should be available to root.  You can also do the same for your .themes and .icons directories.

---

### Post by Izobalax on 2008-03-17
> **yabbadabbadont said:**
> Not sure about the first one but, if your fonts are in ~/.fonts (the .fonts directory in your home directory) then you can create a symbolic link to the directory in /root.

```
sudo -i
cd /root
ln -s /home/yourusernamehere/.fonts

```

Then the fonts should be available to root.  You can also do the same for your .themes and .icons directories.



Thank you. Yes, I already linked the themes and icons but never if the same could be applied to the fonts. Thanks a lot!

Anyone any clues on my first question?

/izo\

---

### Post by Izobalax on 2008-03-18
Ka-bump!

/izo\

---

### Post by Izobalax on 2008-03-20
Bumplicious!

/izo\

---

### Post by Izobalax on 2008-03-24
BUMPARGH!

/izo\

---

