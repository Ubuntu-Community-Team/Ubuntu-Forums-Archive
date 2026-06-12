---
title: "newbie"
date: 2006-07-16
forum: Gaming &amp; Leisure
---

### Post by tenny56 on 2006-07-16
hi guys,

was just wondering of any of you could explain to me how to actually use the wine emulator. 

tenny

---

### Post by eqisow on 2006-07-16
Try starting [here]("https://help.ubuntu.com/community/Wine"). If you still have questions after reading that, I'll be glad to try and help. :)

---

### Post by .Maleficus. on 2006-07-16
Typing wine (Program Name).exe doesn't work for me... at least not for Steam.  I guess it's looking in my system32 folder, but that's not where Steam is.  How do I make it go to the right folder?

---

### Post by eqisow on 2006-07-16
You need to type the pathname as well. You can, however, use the Windwos path OR the Linux path.

For example, Steam would be

```
wine 'C:/Program Files/Steam/steam.exe'
```

This can also be accomplished by typine wine then dragging and dropping whatever exe you want to run to the command line. It should paste the exact location for you. You can, of course, use these commands to add application shortcuts to you menu using the Gnome or KDE menu editors.

---

### Post by abowman on 2006-07-16
There is a how-to for installing steam with wine on this page:
[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

---

