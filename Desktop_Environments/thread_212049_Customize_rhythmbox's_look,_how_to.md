---
title: "Customize rhythmbox's look, how to?"
date: 2006-07-09
forum: Desktop Environments
---

### Post by leeyee on 2006-07-09
Hi guys,
I'm using rhythmbox on Ubuntu Dapper, and I like this application very much! Here, I want to customize the look of it, just change some icons (tray icon, stocks etc.) Anyone know where can I find a howto?
Thank you in advance! Any sorry for my English! ;)

---

### Post by ShiningHolden on 2006-07-09
I think what you want is a theme for Rythmbox.

I don't believe there are themes made, just for Rythmbox, but you can try changing your system's theme instead:
```

System > Prefrences > Theme

```
Good luck.

---

### Post by leeyee on 2006-07-09
Well, I just want to find those icons used in the application and then I change it manually. However, rhythmbox seems embedded in the GNOME very well, it's not that easy to find its icons in the system.

---

### Post by escape on 2006-09-17
Let me first say, this took me FOREVER to figure out.  Find the icons you want to replace in /usr/share/icons/gnome/*x*/stock/media/ and replace them with your icons of the appropriate resolution. Then do gtk-update-icon-cache -f from the ../gnome/ directory. Reopen the app and the icons will have changed.

A HOWTO on this is pending approval by a mod somewhere...

---

