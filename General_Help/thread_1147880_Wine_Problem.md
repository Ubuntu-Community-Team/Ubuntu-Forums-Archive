---
title: "Wine Problem"
date: 2009-05-03
forum: General Help
---

### Post by Muscovy on 2009-05-03
I was trying to solve a little display problem in one of the programs I was running through Wine, and I entered the Wine Config and tried increasing the size. After a small increase did nothing, feeling annoyed, I made a HUGE increase, which *still* did nothing. I went to change the size back, but the Wine config Window is now so large I can't see the bottom, and I can't find any way to see it.
  I've tried uninstalling Wine, but it seems to be keeping the settings. How can I completely remove it?

---

### Post by TransitMan on 2009-05-03
> **Muscovy said:**
> I was trying to solve a little display problem in one of the programs I was running through Wine, and I entered the Wine Config and tried increasing the size. After a small increase did nothing, feeling annoyed, I made a HUGE increase, which *still* did nothing. I went to change the size back, but the Wine config Window is now so large I can't see the bottom, and I can't find any way to see it.
  I've tried uninstalling Wine, but it seems to be keeping the settings. How can I completely remove it?

```
sudo apt-get purge wine
```

---

### Post by CatKiller on 2009-05-04
> **Muscovy said:**
> I've tried uninstalling Wine, but it seems to be keeping the settings. How can I completely remove it?

Everything that you install through Wine, and all its settings for your user account, are kept in your Home folder. If you want to get rid of them, delete ~/.wine.

---

### Post by Muscovy on 2009-05-04
Having a weird problem, it's difficult to enter the admin password, most of the time it will not react to any key but enter. I assume you don't have to hold a button while you type or something?

---

### Post by CatKiller on 2009-05-05
If you're using the command line with sudo, you won't get any visual feedback from the password. This is deliberate. Just type the password in and press Enter.

You don't need to use sudo to remove the configuration files from your Home folder though.

---

### Post by bobdabilda on 2009-10-22
Thanks for that i did the same stupid thing. Spent days trying to put it right :P

---

