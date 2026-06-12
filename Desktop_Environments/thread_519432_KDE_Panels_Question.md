---
title: "KDE Panels Question"
date: 2007-08-07
forum: Desktop Environments
---

### Post by dbbolton on 2007-08-07
Is it possible to use only one panel in KDE? I've noticed that when I have three or more panels, I can click on one of the main panels, then Remove Panel, and remove one of the extra ones that I made. However, when there are only two panels, the Remove Panel option is grayed out.

Basically, I want to keep the top panel and put Avant at the bottom. Is that doable?

---

### Post by tbroderick on 2007-08-07
The default in KDE is only one panel. GNOME has two by default. Both can have only one panel.

---

### Post by dbbolton on 2007-08-07
> **tbroderick said:**
> The default in KDE is only one panel. GNOME has two by default. Both can have only one panel.
Well, could you tell me how to get rid of the bottom panel?

---

### Post by Erunno on 2007-08-07
Right-click on the panel. The context menu should have an option like "Remove Panel Extension" or similar. Choose the panel you'd like to have removed but be careful not to remove the wrong panel or you'll have to rebuild it manually.  I can't tell you the correct labelling at the moment since I'm not using an english version of KDE.

---

### Post by dbbolton on 2007-08-07
> **Erunno said:**
> Right-click on the panel. The context menu should have an option like "Remove Panel Extension" or similar. Choose the panel you'd like to have removed but be careful not to remove the wrong panel or you'll have to rebuild it manually.  I can't tell you the correct labelling at the moment since I'm not using an english version of KDE.
As my first post indicates, that's exactly what I tried to do. However, it won't let me delete either of the last two panels.

Perhaps this screenshot will better explain my problem:

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/th_kpanels.jpg[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/kpanels.jpg)

---

### Post by tbroderick on 2007-08-07
Ok, that's the menubar. Should be an option in kcontrol.

Open kcontrol -> Desktop -> Behavior  -> Menu Bar

---

### Post by dbbolton on 2007-08-07
> **tbroderick said:**
> Ok, that's the menubar. Should be an option in kcontrol.

Open kcontrol -> Desktop -> Behavior  -> Menu Bar
I want to keep the menubar, and get rid of the panel at the bottom. Even if I right-click on the panel at the bottom, it won't let me remove it.

---

### Post by Nythain on 2007-08-07
been a while since i've run kde, but if you alt f2 and run kcontrol you might be able to delete the main panel... and if you really want to get rid of it you could kill kicker

---

### Post by Lord Illidan on 2007-08-07
> **dbbolton said:**
> I want to keep the menubar, and get rid of the panel at the bottom. Even if I right-click on the panel at the bottom, it won't let me remove it.

Perhaps it won't allow you to?

---

### Post by Erunno on 2007-08-07
Yes, KDE clings to the first panel. Not sure if it can be removed at all. On the other hand a lot of people use the MacOS X dockbar clone so there must be a way to disable the kicker panel. Requires further investigation...

---

### Post by milton1 on 2007-08-07
You could always disable the menu bar and use only the one main panel.

---

### Post by JLarson on 2007-08-16
KDE just really wants to keep that last panel at the bottom. Here's how I deal with it and use an external dock (ksmoothdock, AWN, kiba-dock). Make the size 1% and set up auto-hide so that it hides whenever the mouse cursor is not over it. Also align it to the right or left so that your cursor isn't likely to highlight and make it show. I do this and really don't notice that the bar still exists.

You *could* kill kicker, but then all the cool applets you added to the menubar panel would disappear. Maybe there is some way to remove that last panel without killing kicker entirely, but until someone in "the know" pipes up, maybe this will help.

Regards,

Jason

---

### Post by dbbolton on 2007-08-16
> **JLarson said:**
> KDE just really wants to keep that last panel at the bottom. Here's how I deal with it and use an external dock (ksmoothdock, AWN, kiba-dock). Make the size 1% and set up auto-hide so that it hides whenever the mouse cursor is not over it. Also align it to the right or left so that your cursor isn't likely to highlight and make it show. I do this and really don't notice that the bar still exists.

You *could* kill kicker, but then all the cool applets you added to the menubar panel would disappear. Maybe there is some way to remove that last panel without killing kicker entirely, but until someone in "the know" pipes up, maybe this will help.

Regards,

Jason
although not a panacea, this is definitely an intuitive and plausible solution!

---

### Post by Alex&amp;Linux on 2007-08-23
I just use the "panel hiding buttons" which allow a small arrow at either end, which upon clicking it, retracts the panel to the side of the screen, leaving only button.

The hide panel option didnt work well with a dock for obvious reasons.

I really wish they gave you absolute control over it though..seems to me to be what linux is all about...choice.

---

