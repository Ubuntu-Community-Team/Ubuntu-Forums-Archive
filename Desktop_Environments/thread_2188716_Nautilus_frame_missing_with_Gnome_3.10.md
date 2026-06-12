---
title: "Nautilus frame missing with Gnome 3.10"
date: 2013-11-18
forum: Desktop Environments
---

### Post by miceagol on 2013-11-18
After replacing Unity with Gnome 3.10, the Ubuntu windows theme was replaced with a Gnome theme. I then used gnome-tweak-tools to get back the Ubuntu theme.

But some programs don't look right. Among them Nautilus, which is missing its entire frame:

[IMG]http://i.imgur.com/JADRJdx.png[/IMG]

And also the arrows are missing from the scrollbar. Here from the terminal:

[IMG]http://i.imgur.com/qiCJzUx.png[/IMG]

**Any ideas how to repair the issues?** [Here are screenshots]("http://imgur.com/raDXRWw,1e8cOpX") of my settings in gnome-tweak-tools.

---

### Post by fantab on 2013-11-19
Its not missiing, ita a new feature. Read more about Client Side Decorations or CSD, [HERE]("http://www.webupd8.org/2013/09/see-whats-new-in-gnome-310-video.html").
And its not just Nautilus, its the same with all gnome core apps.

---

### Post by miceagol on 2013-11-20
Ah, didn't know that.

Nevertheless, my dialog boxes don't look as nice as in the screenshot with rounded edges. Also the scroolbars look fine in the link, while mine is ****ed up. What theme are they using? Is it possible to keep the Ubuntu theme with rounded edges on the corners of the dialog boxes?

---

### Post by fantab on 2013-11-20
Gnome 3.10 (as earlier versions) uses 'Adwaita' as default theme. And its the same theme in those screenshots. I don't know if the Ubuntu's default 'Ambiance Theme' has been updated for Gnome 3.10, yet. See if it works.
The trouble with Gnome since 3.x versions, with respect to a few features and especially Themes, is that the 'backward compatibility' is poor at best. Older themes don't work well after the gnome version upgrade.

Here's a screeshot of my Arch Linux running with Gnome 3.10; Gtk theme = 'Gnommish Dark' (with 3.8 compatibility) and a customized 'Default' Shell theme:
[http://i.imgur.com/P4unWqx.png?1](http://i.imgur.com/P4unWqx.png?1)

---

