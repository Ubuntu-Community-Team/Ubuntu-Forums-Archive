---
title: "Gnome Panels Gone!"
date: 2013-01-29
forum: Desktop Environments
---

### Post by Autofac on 2013-01-29
This is rather embarrassing...Somehow while fiddling around with adding and removing things from my Gnome top panel I managed to remove the whole of what resides on the right side.

That is, the drop down menu under my name--complete with login, suspend, system settings &c. Volume, date/time, system monitors &c.

Is there an easy way to simply flash/reset the panels in Gnome to bring it all back to normal? I have searched around but can't find a way to drop those things back in--they all seemed to disappear at once in one group.

Sorry for my ignorance--I'm new, ha.

---

### Post by kurt18947 on 2013-01-30
Can you try a restart?  I've had this happen though I believe due to a graphics glitch.  A restart fixed it.  It's hard to restart with no power menu.  Perhaps ctrl-alt-delete will bring up a menu and let you do an orderly restart.  If that fails, ctrl-alt-F1 will bring up a terminal.  Then ctrl-alt-delete to restart.  Of course any current work may be lost but hopefully any unfortunate settings changes will be lost as well.

---

### Post by srekcahrai on 2013-01-30
```

gconftool-2 --recursive-unset /apps/panel 

```
reboot

---

### Post by Autofac on 2013-01-30
> **kurt18947 said:**
> Can you try a restart?  I've had this happen though I believe due to a graphics glitch.  A restart fixed it.  It's hard to restart with no power menu.  Perhaps ctrl-alt-delete will bring up a menu and let you do an orderly restart.  If that fails, ctrl-alt-F1 will bring up a terminal.  Then ctrl-alt-delete to restart.  Of course any current work may be lost but hopefully any unfortunate settings changes will be lost as well.

Thank you. I don't think it is a graphics glitch--in fact, I know this is 'user caused'. I went to delete a weather icon from that side of the bar and then all of a sudden _everything_ disappeared, rather than just the weather icon. I can still Ctl+alt+del and logout and restart from there, but it would be nice to see the time and date.

I'll attach a screen shot so you have an idea of what I mean.

> **srekcahrai said:**
> ```

gconftool-2 --recursive-unset /apps/panel 

```
reboot

Thank you, gave it a whirl and nothing happened. This all may be a way easier fix than I am making it out to be.

The image is my desktop, everything that normally lives in the top right corner of Unity and in this Gnome environment is gone:

---

### Post by Autofac on 2013-01-30
I ran this:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails ~/.config/dconf/user ~.compiz*
```

And it fixed the problem. It reset more than I would have liked, but it's nothing that I can't undo.

Thanks for the input everybody.

---

