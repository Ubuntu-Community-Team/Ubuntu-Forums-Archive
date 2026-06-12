---
title: "How to break the icons in Gutsy"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by Murrquan on 2007-12-04
**Step One.** Go into System -> Preferences -> Appearance.

**Step Two.** Select Clearlooks theme. Your icons are now blurred.

**Step Three.** Select Customize -> Icons, and set it to have the icons from the Human theme. Your icons are still blurred.

**Step Four.** Exit out of the Customize menu, and select the Human theme again. *Your icons are still blurred.* Et voila!

I ran into this problem while trying to customize my desktop. I love the new Human theme, but I like blue a lot better than brown (I know, heresy). It won't *let* you change the color, so I set it to Clearlooks with Human borders and icons. Then, when I noticed the icons were blurred, I switched back -- but they were still all messed up!

**Questions**

[LIST=1]
[*]How do I get around this? Is there any way to have my cake and eat it too with the desktop themes, and not make everything blurry?
[*]Is this a reportable bug?
[*]Where do I go to find out how to file a bug report?
[/LIST]

Many thanks in advance. ^.^

*EDIT:* Some of the Gnome icons in the Clearlooks and Mist themes are blurred as well ... like the OpenOffice.org ones, the Terminal Server Client, and the About Gnome icon. It's not very pretty to look at ... I may have to edit them all manually.

---

### Post by smartboyathome on 2007-12-04
You can try logging in again (to refresh your icon cache).

---

### Post by Murrquan on 2007-12-04
> **smartboyathome said:**
> You can try logging in again (to refresh your icon cache).

Okay ... that cleared things up, but only for the Human theme. Clearlooks' icons are still blurred, even when I set it to use Human icons. Here's a compilation of test results:

[LIST=1]
[*]**Reset Human theme:** Pass.
[*]**Reset Clearlooks theme:** Fail.
[*]**Reset Clearlooks theme with Human icons:** Fail.
[/LIST]

I'm not sure what to do about the icons on Clearlooks, besides just manually resetting each one. Any ideas?

---

### Post by Murrquan on 2007-12-04
More weirdness: If I go to Edit Menus in order to change icons, it displays them properly there but not in the actual menus themselves. Furthermore, I'd thought it was because they were displaying icons of the wrong size and expanding them, but the sizes are actually inconsistent between icons. The "Accessories" icon is 48x48 and the "Games" icon is 24x24, and yet they're both blurred out.

I haven't the faintest clue what's going on, but it's very annoying.

---

### Post by smartboyathome on 2007-12-04
hm... sounds like corrupt icons. try reinstalling them via synaptic, maybe? (search for the icon theme's name)

---

### Post by Murrquan on 2007-12-05
> **smartboyathome said:**
> hm... sounds like corrupt icons. try reinstalling them via synaptic, maybe? (search for the icon theme's name)

Went into Synaptic. Marked the following packages for reinstall:

[LIST]
[*]**gnome-icon-theme**
[*]**gnome-themes**
[*]**human-icon-theme**
[*]**human-theme**
[/LIST]

Switched to Clearlooks. Changed color, window border and icons. Restarted my notebook. No dice. >.> The icons that were blurry still are.

---

### Post by BattlePanic on 2007-12-28
I have run into a similar issue when playing around with GNOME themes.  It was discussed in [this]("http://ubuntuforums.org/showthread.php?t=581277") thread and a [possible solution]("http://ubuntuforums.org/showthread.php?p=3679919#post3679919") was mentioned.  I haven't given it a go yet but it may provide a fix to your problems.

---

