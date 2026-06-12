---
title: "Adobe Flash Player 10 problems"
date: 2009-05-31
forum: General Help
---

### Post by M3ga on 2009-05-31
Hi, I just installed Adobe Flash Player 10 and it says it's installed, when I go to firefox and Epiphany it still has flash player 9, Ive quited the browsers and everything Ive uninstalled/reinstalled still no luck, Help is appreciated.

---

### Post by lovinglinux on 2009-05-31
You need to remove other flash plugins.

Open a terminal from "Applications >> Accessories >> Terminal" then paste the following command and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree
```

It will ask for your password, which you cannot see while typing. Just type it and hit enter again, follow the instructions on the terminal.

This will remove the swfdec and gnash plugins. I have included the installation of the adobe flash plugin in the command just in case. If it is properly installed, the package manager will detect it and won't make additional changes.

---

### Post by M3ga on 2009-06-02
Thanks for this Ill try it when I get on my ubuntu.

Edit: I got on my ubuntu works perfectly, thanks alot.

---

