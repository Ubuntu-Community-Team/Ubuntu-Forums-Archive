---
title: "[Ubuntu] 14.04 Gnome window button arrangement"
date: 2015-05-09
forum: Desktop Environments
---

### Post by Karl_Hungus on 2015-05-09
Hey guys I was wondering if there is a way to change the side the **window buttons** are on? I found some terminal commands and a** tutorial** for** dconf-editor** that said it would change the side the window buttons are on but none of them would change the button arrangement.

the best results I could achieve only changed **some** of the more **basic looking windows** buttons to the left but I need ALL of them on the **LEFT**.

THANK YOU!

---

### Post by insil on 2015-05-10
Apparently it's impossible.  I'm right-handed and absolutely hate having window control buttons on the left.  And it seems to be a common complain that Ubuntu team doesn't care to address.

---

### Post by Karl_Hungus on 2015-05-10
****! Im literally going back to UNITY right now :(

---

### Post by mc4man on 2015-05-10
Not sure what you refer to about ' ALL of them on the LEFT.'
If on gnome-shell the window buttons can be determined (close, min, max or some of) in dconf - see screen 1, this enables all 3 on the left in gnome-shell
(location is org.gnome.shell.overrides button-layout, require a log out/in after changing

In gnome-flashback it's - org.gnome.desktop.wm.preferences button-layout

As far as nautilus any changes must be done in the source > nautilus-toolbar.c & likely only a close button anyway...

---

### Post by Copper Bezel on 2015-05-10
Yeah, I think that's the complaint - dconf can swap the ones that use standard titlebars, but the Gnome apps with the integrated toolbar / titlebar will always have their buttons where Gnome puts them. Nautilus under Ubuntu with Unity is specially tweaked to use the system titlebar instead. But even under Unity, if I open up Gnome Tweak Tool, it has the integrated tootlebar and only a close button, only on the right, and not respecting the window theme. Skinned apps that draw their own titlebars are of course the same way - Steam, for instance, uses the Windows button arrangement in its own skinned style.

---

