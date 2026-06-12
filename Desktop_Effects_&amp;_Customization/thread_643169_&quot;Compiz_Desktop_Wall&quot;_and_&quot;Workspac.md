---
title: "&quot;Compiz Desktop Wall&quot; and &quot;Workspace Switcher Applet&quot; misscommunication"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by nikosm on 2007-12-17
Hello,

I have been using compiz for a while without problems, but a few days ago it started behaving in a strange way. Here is an example.

[INDENT]
I am in Workspace 1 with a firefox window, but the workspace switcher shows that I am in the second workspace (I know that I am in the first workspace because pressing Ctr + Alt + LeftArrow doesn't do anything). See screenshot1.png

I press Ctr + Alt + RightArrow and compiz shows the animation of switching to the second workspace. The firefox window is gone, but I can still see it on the panel (if I click on it, compiz takes me to the first workspace). The workspace switcher shows that I am still in workspace 2. See screenshot2.png

If I now click on the first workspace on the workspace switcher, I get to the "real" workspace 1 with all the windows I had started there.[/INDENT]

It seems to me that the two programs keep their own record independently about which workspace I am at. It has even happened that clicking on some other than the current workspace in the workspace switcher makes all the windows, panels and desktop icons disappear, leaving me with the desktop wallpaper and having to restart the x server. The applications were still running though, I could still hear xmms for example.

Thank you for your effords.
Nikos

P.S. In case it is relevant, in the compiz general options I have:
  Horizontal Virtual Size 4
  Vertical Virtual Size 1
  Number of Desktops 4

---

### Post by overdrank on 2007-12-18
> **nikosm said:**
> Hello,

I have been using compiz for a while without problems, but a few days ago it started behaving in a strange way. Here is an example.

[INDENT]
I am in Workspace 1 with a firefox window, but the workspace switcher shows that I am in the second workspace (I know that I am in the first workspace because pressing Ctr + Alt + LeftArrow doesn't do anything). See screenshot1.png

I press Ctr + Alt + RightArrow and compiz shows the animation of switching to the second workspace. The firefox window is gone, but I can still see it on the panel (if I click on it, compiz takes me to the first workspace). The workspace switcher shows that I am still in workspace 2. See screenshot2.png

If I now click on the first workspace on the workspace switcher, I get to the "real" workspace 1 with all the windows I had started there.[/INDENT]

It seems to me that the two programs keep their own record independently about which workspace I am at. It has even happened that clicking on some other than the current workspace in the workspace switcher makes all the windows, panels and desktop icons disappear, leaving me with the desktop wallpaper and having to restart the x server. The applications were still running though, I could still hear xmms for example.

Thank you for your effords.
Nikos

P.S. In case it is relevant, in the compiz general options I have:
  Horizontal Virtual Size 4
  Vertical Virtual Size 1
 [COLOR="Red"] Number of Desktops 4[/COLOR]

HI and that would be my guess is to change the number of desktops to 1, this is how it is setup for me.

---

### Post by red_Marvin on 2007-12-18
The second problem (firefox in panel on both workspaces) comes from that if a window overlaps the second workspace just a little, a single pixel column is enough, it will show up on both workspaces.

---

### Post by nikosm on 2007-12-19
Thank you overdrank, that solved it. Thanks red_Marvin, I will be more careful with the placement of the windows then.

Still don't know if this solves the problem of everything disappearing with just four background workspaces (without panels, icons, windows) remaining. I will let you know.

Thanks again,
Nikos

---

