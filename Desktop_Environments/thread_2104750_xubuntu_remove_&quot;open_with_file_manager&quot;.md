---
title: "xubuntu remove &quot;open with file manager&quot;"
date: 2013-01-14
forum: Desktop Environments
---

### Post by vectorthorn on 2013-01-14
i don't know WHY they would put "open with file manager" in the right click context menu for EVERY SINGLE FILE YOU CLICK ON, but it takes up unnecessary space and makes the menu unnecessarily complex, especially for those of us who often use the keyboard to navigate it.

so, HOW do i get rid of it?

i'm using xubuntu 12.10 (but it does this in 12.04 as well).

TIA.

---

### Post by Frogs Hair on 2013-01-14
What version are you using ? When logged into XFCE and I use Nautilus instead of Thunar I see "open with" and there is menu if the option is selected . Thunar simply offers the option to open. Remember I am not Xubuntu though.

---

### Post by vectorthorn on 2013-01-14
i'm using version 12.10 (i should have put that in the title), which i just installed last night because i screwed up 12.04, which also had the same thunar problem.

thanks

---

### Post by LewisTM on 2013-01-14
vectorthorn,
Just know that this is not normal, I've never seen this entry in the Thunar context menus. There is probably something wrong with your MIME type associations.

Hopefully, it's not a system-wide issue. You can create a new user and log in, then see if the same menu item appears. If it doesn't, then it's a user config problem. You can try to hunt down the faulty file association but I would recommend you simply delete the directory ~/.local/applications to reset everything to system defaults. Make a backup copy just to be safe.

Cheers!

---

### Post by vectorthorn on 2013-01-14
it was there is 12.04 and now in 12.10, and i installed both of them twice, so IMO, it would appear that it's not a "fluke", since it's always there. oh, and i've deleted that directory before, when audacity ate up my free space.

thanks.

---

### Post by LewisTM on 2013-01-14
Did you do fresh installs with a new user or did you use the same old home directory?

I'm quite sure it's a "fluke". Just try a live CD session, you'll see.

---

### Post by vectorthorn on 2013-01-14
i always do fresh installs. i will try the live session tonight and see how it goes.

thanks.

---

### Post by LewisTM on 2013-01-14
I just looked at your screenshot more closely. The file manager displayed is Nautilus, not Thunar. I don't have the "Open with File Manager" item in Nautilus either, in Xfce, but I just though it would be important to point that out. There could be a conflict between file managers. 

When you click on the menu item, what file manager does it open?

---

### Post by vectorthorn on 2013-01-14
i completely forgot to mention that it's NAUTILUS, and not thunar. i just assumed that since it was an xfce-based desktop, that it was an xfce-based context menu. i looked into nautilus-tweak tool and did not see an option to remove it there, which furthered my assumption. so, it opens nautilus, and may well be a gnome/nautilus context menu. either way, i'm still aggravated by it, lmao.

thanks.

---

### Post by Frogs Hair on 2013-01-14
I could see you were using Nautilus because of the title bar and side pane.  My context menu looks different in both Nautilus and Thunar. I am running XFCE 4.10 as one of my desktops on Ubuntu 12.10 and may have a different or modified of version Nautilus than Xubuntu.

---

