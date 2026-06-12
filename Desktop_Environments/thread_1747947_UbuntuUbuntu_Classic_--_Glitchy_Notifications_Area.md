---
title: "Ubuntu/Ubuntu Classic -- Glitchy Notifications Area After Update to Natty"
date: 2011-05-03
forum: Desktop Environments
---

### Post by blenderfox on 2011-05-03
Title essentially says it all. I updated from Maverick to Natty, and I've noticed that the notifications area is glitchy. I have TweetDeck, Skype and Wally (wallpaper changer) starting when I login, and, randomly, 1, 2 or maybe all of the icons will not appear. If I remove the notifications area and re-add it, 90% of the time, they all appear. But when I then reboot or logout and back in, the same behaviour occurs. This has only started happening since my update to Natty. I really don't like the new interface, so I'm sticking with the old style Gnome environment.

Anyone else noticed this behaviour, or am I the only one?

---

### Post by Alpha1Dash1 on 2011-05-03
I certainly have - I'm using the Unity interface and start my Skype manually. Whether the icon appears or not seems to be related to how much other stuff I've done since log-on. If I start it straightaway or after using just firefox for a bit, it always appears (or at least it hasn't NOT appeared so far!). If I've been using banshee, checking emails, update manager has run etc then no icon. Maybe those use the notification area & muck it up for other apps? Or just that Skype etc don't play nicely with the new environment.

The only system setting change I've made to Unity is to "not auto-hide" the left hand pane/launcher thingy.

Annoying, and unfortunately I have no solution either...

[edit]
A bit of experimentation reveals that the above is wrong! My icons fail to appear if I have an app running that has written something in the top panel (like "Firefox web browser" for example) and has "exported" (for want of a better word) its menu to the top panel. Closing/minimizing that app allows the Skype icon to appear if it is re-launched.

I realize this doesn't solve your problem (except perhaps to point to a timing issue?), so sorry about that.
[/edit]

---

### Post by blenderfox on 2011-05-03
Well, this happens on both the new Unity desktop, AND the Ubuntu Classic (old Gnome) environment, so I don't think that the "name in the menu bar" is the cause.

---

