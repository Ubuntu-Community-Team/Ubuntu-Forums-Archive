---
title: "KDE Menu Button Icon"
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by Baelfael on 2007-05-13
I have a little problem,

When I go to switch the icon "kmenu.png" in /usr/share/icons/default.kde/apps/, with my own kmenu.png, it won't replace because I "don't have permission". How do I override this?

---

### Post by krussell on 2007-05-14
Hello :-)

Two ways to do it:
Firstly, log-in as root and go to /usr/share/icons/default.kde/apps/ and paste your preferred picture. Then rename your picture as kmenu.png (before doing it rename the existing kmenu.png as something else, say kmenu_old.png)

OR, another way
Create a folder in your home directory just like below:
/home/your home directory/icons/default.kde/apps/
Now copy the icon you want to show as K-menu icon and rename it as "kemu.png"

Now log-out and re-login.

---

### Post by Baelfael on 2007-05-14
How do I log in as root?

---

### Post by fiftynine on 2007-05-15
> **Baelfael said:**
> I have a little problem,

When I go to switch the icon "kmenu.png" in /usr/share/icons/default.kde/apps/, with my own kmenu.png, it won't replace because I "don't have permission". How do I override this?

One way is to run konqueror as sudo. Just start konsole and write sudo konqueror. Then you have all the permissions you could possibly want when using konqueror. This is for GUI people :)

---

