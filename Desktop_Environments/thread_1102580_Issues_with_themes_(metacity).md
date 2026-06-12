---
title: "Issues with themes (metacity)"
date: 2009-03-21
forum: Desktop Environments
---

### Post by hackapelite on 2009-03-21
Well, I tried installing a whole lot of new themes, but for some reason whenever I dragged one to the themes list in Appearance options, it wouldn't appear as in the list as itself but it would become the"Custom" theme... now I don't get what's up with that. So, I decided unpacking all the archives to the /use/share/themes directory, but that didn't work either... so, I deleted all the themes from the folder (all that I put there myself, of course, not the default ones), but now whenever I drag a theme package in the appearance options box or try to install one, it comes up with the message 'Installation of theme "theme" failed - can't move directory over directory'. So, the questions are:

1) How do I fix the problem?
2) How can I make all the themes appear in the list? I figured just copying them to the "themes" directory isn't enough...
3)Anything else regarding how metacity/GTK/Gnome/ubuntu (w/e) themes work, especially "behind-the-scenes" stuff? I'm still fairly nooby with Linux, and like tinkering around, so any useful info will be greatly appreciated!

---

### Post by rozbarwinek on 2009-03-23
> **hackapelite said:**
> 1. How do I fix the problem?

Backup your themes and delete .themes folder in your home directory.
Now try to install new theme.
I don't know is this a solution for your problem but it's worth to try :)

> **hackapelite said:**
> 2) How can I make all the themes appear in the list? I figured just copying them to the "themes" directory isn't enough...

You can't :) It's like this: if an author of a theme create "full theme" (with index.theme file) it will appear in your themes list, if an author didn't do that it won't :)
Of course you can do it by yourself :) but what for? you can change theme in "custom" options :)
If you really need those theme on the main list create index.theme file in every theme folder and paste this to that file:

```
[X-GNOME-Metatheme]
Name=THEMENAME
Encoding=UTF-8
GtkTheme=THEMENAME
MetacityTheme=THEMENAME
IconTheme=ICON THEME YOU WANT TO USE WITH THIS THEME
```

Change THEMENAME to your theme name :)

---

