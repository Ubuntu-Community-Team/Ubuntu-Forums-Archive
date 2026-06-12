---
title: "Compiz Fusion locked screen opacity"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by Lapino on 2007-07-19
I'm using Compiz Fusion (from Trevino's repositories) and when I lock the screen, the black screen that is put over the desktop is transparent (which is logic, due to the opacity settings). But I'd like to have this screen completely opaque, like when using metacity for example. Any ideas on how to achieve this?

---

### Post by WinterWeaver on 2007-07-19
Open up your Compiz Settings:
System >> Preferences >> CompizConfig

Go the The General Options
Go to the Opacity Settings Tab

you will see there is a list of different window types that gets the opacity settings, Just edit the Opacity value at the end :) >> make it 100

have fun!

WW

---

### Post by rax_m on 2007-07-19
thanks.. that helped me too.

---

### Post by WinterWeaver on 2007-07-19
YAY!! Makes me happy ... ^_^  :guitar:

---

### Post by Lapino on 2007-07-19
I already figured that one out, but thanks nonetheless. 
But what I actually meant was to have only this window to be fully opaque, but the others still transparent. So I probably just need the right line to put into the settings.

---

### Post by pointone on 2007-07-19
I'd like to know, too. I like the other windows to be transparent (menus, etc.) but the transparent locked screen defeats the purpose of locking the screen somewhat. :P

---

### Post by Lapino on 2007-07-23
I found something that works for me
[LIST=1]
[*]Go to System>Preferences>CompizConfig Settings Manager
[*]Go to General Options > Opacity Settings
[*]Select the long string under "Opacity windows" and click edit
[*]Add "| name=gnome-screensaver" to the excluded windows (the part with the ! in front)
[/LIST]
In my case, the string changed from this:
((Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)

to this:
((Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer **| name=gnome-screensaver**)

---

### Post by pointone on 2007-07-23
Wonderful! Thanks bunches!

I was messing around with window rules, too--but thought it was xscreensaver; not gnome-screensaver!

---

### Post by BDNiner on 2007-07-26
Thank you for this, i too was messing around in those settings and just needed some direction.

---

### Post by fastpakr on 2007-07-31
This helped me out a lot - thanks so much!  Is there any way to make sure that NONE of the Compiz effects are active while the screen saver is running?  For some reason I can run Lattice just fine when Metacity is active, but probably get 5 jumpy frames per second when Compiz is running.

Edit - nevermind, I found the Compiz screensaver plugin which works fine and I like better than Lattice.

---

### Post by MrFurious on 2007-08-08
Thanks Lapino!  Your solution works perfectly.

---

### Post by PmDematagoda on 2007-08-27
Even i have the same problem but when i tried it your ways it didn't do anything except for the method by WinterWeaver, the locked screen still remains somewhat transparent even when i make the changes to the window opacities. The only thing that works as is WinterWeaver's method is by making all the screens opaque which I don't want.:(

---

### Post by Lapino on 2007-08-27
That's strange, here it still works perfectly, with the latest builds from treviño's repository. Could you post your opacity string over here, so I can try it here to see if the problem lies within that string.

---

### Post by PmDematagoda on 2007-08-27
```
((type=Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)
```

---

### Post by JustinForce on 2007-08-27
> **Lapino said:**
> ((Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer **| name=gnome-screensaver**)

This is exactly what I needed. Thanks!

---

### Post by fastpakr on 2007-08-27
> **PmDematagoda said:**
> ```
((type=Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)
```

It looks like you still need to add the exclusion for gnome-screensaver.

---

### Post by PmDematagoda on 2007-08-28
I did add the exclusion but no change occurred after I locked the screen which still remained translucent. Here is the code with the exclusion:

```
((type=Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer | name=gnome-screensaver)
```

---

