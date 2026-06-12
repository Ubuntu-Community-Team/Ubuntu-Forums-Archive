---
title: "Themed root applications?"
date: 2009-05-12
forum: Desktop Environments
---

### Post by Fzang on 2009-05-12
Whenever I run an application as root themes are disabled and it uses this grey and ugly retro style.

Is there a way to have root applications themed as well?

---

### Post by mcduck on 2009-05-12
> **Fzang said:**
> Whenever I run an application as root themes are disabled and it uses this grey and ugly retro style.

Is there a way to have root applications themed as well?

That is most likely happening because youa re using a theme you have installed into your user's personal themes directory instead of the system-wide location. But there's a simple fix to that, just create symbolic links from your own theme directory to root's:
```

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```
..now root will always have the same themes available that you are using. ;)

---

### Post by m_duck on 2009-05-12
Yeah. Either when you install themes, use the /usr/share/themes or /usr/share/icons directories rather than ~/.themes and ~/.icons or make some simlinks in the root directory, pointing to the theme and icon folders in your home (method I use).

```
sudo ln -s /home/yourusername/.themes /root/.themes
 and
sudo ln -s /home/yourusername/.icons /root/.icons
```

Edit: Too slow...

---

### Post by Fzang on 2009-05-12
Ha, happens for all of us :P

Thanks for the help

---

