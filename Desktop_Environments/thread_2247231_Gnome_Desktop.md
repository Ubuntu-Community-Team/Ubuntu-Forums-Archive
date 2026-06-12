---
title: "Gnome Desktop"
date: 2014-10-06
forum: Desktop Environments
---

### Post by phh on 2014-10-06
I updated to Gnome 3.10 (against my better judgement) and after trying some of the settings in Gnome Tweak Tool, program windows inside the desktop are now so big I can't scroll around to access every button.

Screen resolution is correct at 1440x900. Docky icons are all the correct, but clicking on them opens the program windows in this oversized mode. All Ally settings are set to off.

Anyone have any ideas on this one?

---

### Post by Frogs Hair on 2014-10-06
Moved to own thread.

---

### Post by redrumrogue on 2014-10-06
Try running this command as your username (not sudo or root user) ...
```
** gsettings set org.gnome.desktop.interface scaling-factor 1**
```
and then reboot.

Let me know if this helps!

---

### Post by phh on 2014-10-07
Hi redrumrogue

Many thanks. regrettably your suggestion did not solve my problem.

Here is a screenshot that may show the problem better than I have described in my post.

[ATTACH=CONFIG]257005[/ATTACH]

---

### Post by phh on 2014-10-07
And another screenshot...

[ATTACH=CONFIG]257006[/ATTACH]

---

### Post by redrumrogue on 2014-10-07
OK - open dconf-editor and check the following ...
org > gnome > desktop > interface > scaling-factor = 1
org > gnome > desktop > interface > text-scaling-factor = 1
org > gnome > nautilus > icon-view > default-zoom-level = standard

It's worth checking these I suppose.  I don't know what else it could be.

---

### Post by phh on 2014-10-08
All the dconf settings are already as you suggest.

Would a possible solution be to completely uninstall / re-install Gnome, and what would be the safest way to do this?

---

### Post by redrumrogue on 2014-10-08
I'm out of ideas i'm afriad.  Hopefully somebody else can chip in!

(Sorry I was not able to help a fellow South African!)

---

### Post by phh on 2014-10-08
No problem. Thanks for your interest.

Still hoping to avoid a system re-installation.

Will post if successful.

---

