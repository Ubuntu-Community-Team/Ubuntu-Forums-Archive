---
title: "Keyboard config in KDE Settings"
date: 2006-01-14
forum: General Help
---

### Post by gnu2tux on 2006-01-14
Hi,

 Recently I had a need to reconfigure my x server settings for resolution, a task I've done many a time.

All was fine after restarting X apart from one thing: my UK keyboard is no longer giving me pound signs:

shift+3 should give a &pound; but it actually gives a 3.

I noticed it's fine outside KDE, so I went to the System Menu in the Kde menu, clicked on Settings, Perhiperals and then I got a blank box with a title of 'Configure - KDE Control Module'. 

1) Why is the Keyboard configuration box blank. Only option I have is 'Cancel' or OK.

2) Is there any other way to configure the keyboard properly?

Regards,

---

### Post by sharke on 2006-01-14
in a terminal type kdesu kcontrol and this will give you the kde control center. You should be able to set keys in here,
Regards
Sharke

---

### Post by gnu2tux on 2006-01-21
[QUOTE=sharke]in a terminal type kdesu kcontrol and this will give you the kde control center. You should be able to set keys in here,
Regards
Sharke[/QUOTE]

Many thanks sharke - that worked great.

 You would have thought that this would have been available through the main KDE menu though! - The only thing similar is the 'System Settings' item in the main menu. It shows the same stuff as your example, but doesn't offer a change in user to root like most other changes.

---

