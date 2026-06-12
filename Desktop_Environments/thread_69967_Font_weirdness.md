---
title: "Font weirdness"
date: 2005-09-28
forum: Desktop Environments
---

### Post by Old *ix Geek on 2005-09-28
I wasn't sure where to post this, but I guess it's KDE-related so here it is!

I use Mozilla Suite, and I'm really struggling with getting my fonts to look the way I want.  I've tried adjusting my system fonts AND Mozilla's fonts, but I still end up with some things that are so small they're almost unreadable.  For example, the "File | Edit | View..." menu, the location box, and the headings on each tab are TINY.  Also, in my mail and newsgroups the list (on the left) of newsgroup names and e-mail folder names, as well as each message's subject, are tiny, while the messages themselves are more readable.

Does anyone know precisely which font setting, whether in KDE or Mozilla, controls items such as the ones named above?

---

### Post by mlomker on 2005-09-28
Install the **qtk2-engines-gtk-qt** package.  When you restart KDE it'll add a menu pick to Control Center under Appearance & Themes, GTK Styles and Fonts.  You can either set it to use the same font selections as KDE or larger ones.

It took me a while to figure this out!  :mad:   The problem is that Firefox is a gtk application (gnome) and it won't normally take KDE font settings.

---

### Post by Old *ix Geek on 2005-09-28
Thanks.  I'm off to give that a try and will report back later.

BTW, you're an awfully big help! :D   And it is appreciated.

---

### Post by Old *ix Geek on 2005-09-29
Update: I definitely think I'm on the right track, but I'm still struggling with some font sizes in Mozilla.  Going to keep plugging away at it!

---

### Post by mlomker on 2005-09-29
I tested it with Firefox, not the Mozilla suite.  Did you change the setting the GTK control panel applet?

---

