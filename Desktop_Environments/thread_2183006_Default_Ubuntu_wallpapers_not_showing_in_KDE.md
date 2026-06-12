---
title: "Default Ubuntu wallpapers not showing in KDE"
date: 2013-10-23
forum: Desktop Environments
---

### Post by PokerLegion on 2013-10-23
I installed default Ubuntu wallapers but they are not showing in KDE desktop settings. As you can see, there are just default KDE wallpapers.

```
sudo aptitude install ubuntu-wallpapers-karmic ubuntu-wallpapers-lucid ubuntu-wallpapers-maverick ubuntu-wallpapers-natty ubuntu-wallpapers-oneiric ubuntu-wallpapers-precise ubuntu-wallpapers-quantal ubuntu-wallpapers-raring
```

[IMG]http://i.imgur.com/krNFB7v.png[/IMG][COLOR=#40e0d0][/COLOR]

---

### Post by qamelian on 2013-10-23
KDE and Gnome/Unity store wallpapers in dofferent locations. KDE uses /usr/share/wallpapers,while the regular Ubuntu wallpapers go to /usr/share/backgrounds. You should be able to click the button with the folder icon on it to navigate to and add the Ubuntu wallpapers from /usr/share/backgrounds.

---

### Post by PokerLegion on 2013-10-23
Can i just copy wallpapers from backgrounds to wallpapers folder?

---

### Post by qamelian on 2013-10-23
If you add them using the button I mentioned above, I believe they'll just show up in your wallpaper selection after that. I can't remember for sure, as I haven't used KDE in a while.

---

