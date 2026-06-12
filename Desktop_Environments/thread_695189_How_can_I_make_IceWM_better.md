---
title: "How can I make IceWM better?"
date: 2008-02-12
forum: Desktop Environments
---

### Post by diablo75 on 2008-02-12
I recently installed and tried IceWM out, looking for something lightweight, and it looks like I found what I was looking for.

The problem now is, the default menus that are given to me seems to only give me short cuts for a couple programs (firefox, gimp, and a hand full of apps I've never heard of).  Is there an easy way to populate the menu with shortcuts to more applications, like I have in my gnome environment?

---

### Post by nemilar on 2008-02-12
You should check out [http://www.icewm.org/FAQ](http://www.icewm.org/FAQ) 

You'll probably want to download one of the tools, instead of configuring the menus and whatnot by hand through the configuration files.  Via the FAQ, a list is available here:
[http://www.icewm.org/FAQ/IceWM-FAQ.html#toc11](http://www.icewm.org/FAQ/IceWM-FAQ.html#toc11)

I haven't used Ice in _years_ so I can't tell you which one to look at, but perusing the documentation should help.

---

### Post by RedSquirrel on 2008-02-12
It's been a while since I played with IceWM on Ubuntu, but...

If you install the menu package and then run 'sudo update-menus' it might help.

```
sudo apt-get install menu
```
```
sudo update-menus
```

---

