---
title: "Icons &amp; Trash"
date: 2007-03-21
forum: Desktop Effects &amp; Customization
---

### Post by starfleetcaptainrob on 2007-03-21
I have two questions that may or may not have been answered already in previous threads.  I've done quick searches on each, but come up empty handed and it's getting late so I figured I'd post them myself.

Anyhow, my first question is pretty simple:  how do I get my trash can on my desktop rather than on a panel?  I know this has to be a pretty simple fix and it's something I'm most likely over looking, but any help would be appreciated.

My second question is where can I find GAIM's icon in the file system.  I'm setting up some launcher screenlets and want to put GAIM up on there, but I don't want to look at the default X icon.  It's like trying to find a needle in a haystack.

Thanks in advance!

---

### Post by reclusivemonkey on 2007-03-22
> **starfleetcaptainrob said:**
> 
Anyhow, my first question is pretty simple:  how do I get my trash can on my desktop rather than on a panel?  I know this has to be a pretty simple fix and it's something I'm most likely over looking, but any help would be appreciated.

If you have a look in gconf's settings for Nautilus, there is a tick box in there for the trash icon on your desktop. I am at work ATM, so I can't tell you the exact entry but it shouldn't be too hard to find.

> **starfleetcaptainrob said:**
> 
My second question is where can I find GAIM's icon in the file system.  I'm setting up some launcher screenlets and want to put GAIM up on there, but I don't want to look at the default X icon.  It's like trying to find a needle in a haystack.


This depends on which icon theme you are using. What do you mean by "screenlets"?

---

### Post by mcduck on 2007-03-22
For desktop icons:

1. Press Alt-F2 and run 'gconf-editor'
2. Browse to apps/nautilus/desktop and enable icons you want

For Gaim Icon, take a look in /usr/share/pixmaps. Some icon themes may have their own icons so look also in /usr/share/icons and ~/.icons

---

### Post by cdenning on 2007-10-23
So now that you have added the "My Computer" icon how do you change the names of the drives?

---

