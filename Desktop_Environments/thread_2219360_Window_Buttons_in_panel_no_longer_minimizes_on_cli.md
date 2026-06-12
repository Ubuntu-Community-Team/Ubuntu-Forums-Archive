---
title: "Window Buttons in panel no longer minimizes on click"
date: 2014-04-23
forum: Desktop Environments
---

### Post by Moses_Moore on 2014-04-23
Xubuntu 13.04 and 13.10 -- I have xfce4 panel with the "window buttons" item.  It shows an icon or an icon + title for each window on the current desktop (or all desktops, if I wish).  Clicking on the windows button item for an open window would minimize the window, or it would restore the window if it was minimized.

Xubuntu 14.04 -- xfce4 panel, "windows buttons" item, now if I click on a window button item, I see the window button item toggles a highlight around it, but does not affect the window at all.

How can I get the old behaviour back, where I can click on a window's icon/title in the xfce4 panel to make it minimize or restore?  While I'm here, what does that highlighting mean when I click on it?

---

### Post by Luke M on 2014-04-25
Strange, I'm running xubuntu 14.04 and it works normally.

---

### Post by david-m-oneill on 2014-04-28
> **Moses_Moore said:**
> Xubuntu 13.04 and 13.10 -- I have xfce4 panel with the "window buttons" item.  It shows an icon or an icon + title for each window on the current desktop (or all desktops, if I wish).  Clicking on the windows button item for an open window would minimize the window, or it would restore the window if it was minimized.

Xubuntu 14.04 -- xfce4 panel, "windows buttons" item, now if I click on a window button item, I see the window button item toggles a highlight around it, but does not affect the window at all.

How can I get the old behaviour back, where I can click on a window's icon/title in the xfce4 panel to make it minimize or restore?  While I'm here, what does that highlighting mean when I click on it?

This is also happening to me :(


Anyone know how to fix this?

---

### Post by david-m-oneill on 2014-04-28
BTW, I posted [http://askubuntu.com/q/455477/6161](http://askubuntu.com/q/455477/6161) here, but haven't gotten any responses yet.

---

### Post by afxmac on 2014-05-06
I have the same problem.
Ever since the install of Xubuntu 14.04 my left mouse button no longer toggles the window minimize/sow on the icons in the window button panel.
Instead, left opens a window and middle iconizes it.
I'd love to see the old toggle on left mouse button back

---

### Post by ultrabook on 2014-10-08
Try this:

 1. Right click on windows button handle and click **Properties**
 2. Under **Behaviour**, set **Middle click action** to **Nothing**
 3. Close the window and try clicking on window buttons, it should minimize and restore

[IMG]http://s28.postimg.org/ijdai02cd/sample.png[/IMG]

---

### Post by afxmac on 2014-10-09
> **ultrabook said:**
> Try this:

 1. Right click on windows button handle and click **Properties**
 2. Under **Behaviour**, set **Middle click action** to **Nothing**
 3. Close the window and try clicking on window buttons, it should minimize and restore

[IMG]http://s28.postimg.org/ijdai02cd/sample.png[/IMG]

That does not work. Please read what was written above. Middle button was used as a configurable workaround because the old method did not work.

cheers
afx

---

### Post by Igor_Parra on 2015-03-11
I solved in this way:

panel -> items -> windows buttons -> behaviour -> Middle click action: Nothing

In the screenshot looks more clear. Exactly as ultrabook said.

---

