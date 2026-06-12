---
title: "Indicator Applets Icon Spacing"
date: 2015-10-30
forum: Desktop Environments
---

### Post by Malevion on 2015-10-30
I was wondering if there's a way to modify the spacing between the icons in indicator-applet in Lubuntu. I've attached an example of my panel and I would like to group the icons (specifically in this case: Steam, Deluge, and the network indicator) closer together but the settings menu doesn't have an option to do that.

[ATTACH=CONFIG]265271[/ATTACH]

---

### Post by Frogs Hair on 2015-10-31
The option  to add or remove spacers is in panel settings, but if there are no spacers in use I don't know a way close the distance from the UI.

---

### Post by tturrisi on 2015-11-01
You'd have to edit your gtk3 theme.

[http://askubuntu.com/questions/143583/change-spacing-of-icons-in-indicator-applet-complete-preferably-by-editing-a-co](http://askubuntu.com/questions/143583/change-spacing-of-icons-in-indicator-applet-complete-preferably-by-editing-a-co)

---

### Post by Malevion on 2015-11-02
Well, I fixed the issue, and it was not in gtk3. I stumbled onto a bug report about this exact issue ([https://bugs.launchpad.net/indicator-applet/+bug/527267/+index?comments=all](https://bugs.launchpad.net/indicator-applet/+bug/527267/+index?comments=all)) and followed the advice from comment #92 which fixed my problem.

---

### Post by Rex Bouwense on 2015-11-02
Excellent.  Could you please mark your thread as solved using the thread tools at the beginning of your first post.  Thank you.

---

