---
title: "Everything is perfect, but these two icons..."
date: 2008-01-12
forum: Desktop Effects &amp; Customization
---

### Post by 449 on 2008-01-12
I have everything on my desktop how I want it, except for two icons. 

[IMG]http://img512.imageshack.us/img512/817/screenshotrl3.png[/IMG]

Is there a way to change these without screwing over the rest of my desktop?

---

### Post by CarpKing on 2008-01-12
Either your icon set doesn't have those icons or they are improperly linked.  Take a look in you're ~/.icons folder in the folder corresponding to that theme (i don't know what links should be there, but if either of those icons just aren't there it should be easy to figure out.

---

### Post by 449 on 2008-01-12
There's already the trash icons in there so I don't know why they aren't working, but I havn't been able to find the Volume control icon.

---

### Post by rune0077 on 2008-01-12
You can locate the icons in /usr/share/icons. You'll probably find them either in Gnome or Human (whichever one of these it is Ubuntu uses as default), or in Hicolor (but check the others first). You could theoretically just change them there, but then they'll be gone for good, even if you revert back to default theme. 

You may also just copy their name and then rename the relevant icons in your own icon-theme to this. (did that make sense? copy the name of the trash icon(s) from /usr/share/icons then paste it into the name of the trash icon you want in /.icons/name-of-your-theme). I'm not sure if this will actually work, but I see no reason why it shouldn't.

---

