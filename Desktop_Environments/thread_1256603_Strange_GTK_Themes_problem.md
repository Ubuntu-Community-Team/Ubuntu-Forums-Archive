---
title: "Strange GTK Themes problem"
date: 2009-09-02
forum: Desktop Environments
---

### Post by osarusan on 2009-09-02
A few days ago I was playing with the "Themes" section of the System>Preferences>Appearance menu, switching between the themes installed -- Human, Murrine, Darklooks, etc. While doing so, at one point, the system locked up entirely and I had to reboot.

Now, I can't change the theme anymore. I'm stuck on Darklooks. If I go back to the menu and try to change the theme, the window border changes properly, but the "inside" of the window remains on Darklooks. (Does that make sense?) This happens with every theme.

What happened? And how can I fix this?

Thanks!

---

### Post by steveneddy on 2009-09-02
You need to give the software time to change the theme before you select another.

If you don't figure it out just create a new user and copy your settings from the old /home to the new user's /home folder.

Then erase the old user.

---

### Post by blackened on 2009-09-03
Could be a problem with permissions. Try moving one of the extraneous global themes to your user directory and see what happens.

```
sudo cp -R /usr/share/themes/DarkRoom ~/.themes
sudo chown -R **yourusername**:**yourusername** ~/.themes/DarkRoom
sudo rm -R /usr/share/themes/DarkRoom
```

Remember to replace **yourusername** with your actual username.

After that, try to switch to the DarkRoom theme and see if your control decorations change.

---

### Post by osarusan on 2009-09-25
Well I'm not sure what was the cause of this problem, but on upgrading to Karmic, the themes seem to have fixed themselves and the Appearance tool works normally once again.

---

