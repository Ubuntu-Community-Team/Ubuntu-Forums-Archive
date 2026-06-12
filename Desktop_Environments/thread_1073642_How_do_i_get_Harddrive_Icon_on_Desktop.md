---
title: "How do i get Harddrive Icon on Desktop"
date: 2009-02-18
forum: Desktop Environments
---

### Post by chato92 on 2009-02-18
Well i have the Mac OS X theme on my machine and i want to get the hard drive and all the drives on the desktop and can i also get some help changing my visual effects to normal or extra because it wont let me change them it starts off searching for drivers and it goes Grey and then i went to check on my video driver and it is enabled and up to date can some one help me??

---

### Post by Fzang on 2009-02-18
For putting your linux partition on the desktop in mac OS fashion I've found no other ways than simply creating a shortcut to "filesystem" and place it on the desktop

Showing other drives on the desktop should be enabled by default. If they aren't showing up on the desktop it's maybe because they aren't mounted

---

### Post by chato92 on 2009-02-18
well i already tried to make a shortcut for it on the desktop but its greyed out when i right click on it

---

### Post by JECHO on 2009-02-18
> **chato92 said:**
> well i already tried to make a shortcut for it on the desktop but its greyed out when i right click on it

the onlything i would say to try is press alt+f2 and type in:

```
gconf-editor
```

when the window opens up, browse to apps > nautilus > desktop and make sure that "volumes visible" is checked. :)

---

