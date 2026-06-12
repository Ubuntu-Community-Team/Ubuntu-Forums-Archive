---
title: "no icons on desktop"
date: 2007-04-20
forum: Desktop Environments
---

### Post by thebluejay on 2007-04-20
I have installed Xubuntu 6.06 with the xcfe4 desktop. My problem is there are no icons on the desktop and there does not appear to be any way to install them. I have two panels, top and bottom, where I can install widgets  and launchers, but how do I get launchers on to the desktop. When I right-click the desktop, I get my Menu. Hmmmmmm, must be a way to change that, right? :)

Slowly learning...... thx for all the help!

thebluejay

---

### Post by davegod75 on 2007-04-20
> **thebluejay said:**
> I have installed Xubuntu 6.06 with the xcfe4 desktop. My problem is there are no icons on the desktop and there does not appear to be any way to install them. I have two panels, top and bottom, where I can install widgets  and launchers, but how do I get launchers on to the desktop. When I right-click the desktop, I get my Menu. Hmmmmmm, must be a way to change that, right? :)

Slowly learning...... thx for all the help!

thebluejay

ditto, I'm on just plain ubuntu and I cannot figure out how to create desktop shortcuts

---

### Post by s_p_a_r_k_y on 2007-04-20
right click on desktop and click on create launcher. Or just drag the button from the application menu to the deskop

---

### Post by RedSquirrel on 2007-04-20
> **thebluejay said:**
> I have installed Xubuntu 6.06 with the xcfe4 desktop. My problem is there are no icons on the desktop and there does not appear to be any way to install them. I have two panels, top and bottom, where I can install widgets  and launchers, but how do I get launchers on to the desktop. When I right-click the desktop, I get my Menu. Hmmmmmm, must be a way to change that, right? :)

Slowly learning...... thx for all the help!

thebluejay

Look in your menu under "Desktop Preferences".

Make sure "Allow Xfce to manage the desktop" is checked.

Click on the Behavior tab. Make sure "right click on desktop opens menu" is _**unchecked.**_

Below that, there should be something about desktop icons, and there's a pull-down menu where you can select what to allow (launchers etc.)

After doing all of that, you should be able to right-click on the desktop and there will be a little menu with options to create different things (launchers, for example).

HTH

---

### Post by thebluejay on 2007-04-21
> **RedSquirrel said:**
> Look in your menu under "Desktop Preferences".

Make sure "Allow Xfce to manage the desktop" is checked.

Click on the Behavior tab. Make sure "right click on desktop opens menu" is _**unchecked.**_

Below that, there should be something about desktop icons, and there's a pull-down menu where you can select what to allow (launchers etc.)

After doing all of that, you should be able to right-click on the desktop and there will be a little menu with options to create different things (launchers, for example).

HTH

When I do that, I no longer get the regular desktop menu when I right-click (as to be expected). But instead, I get no reaction at all. No popup menu at all. Is there not an xfce config file somewhere which tells xfce to open that menu and what to put in it?

---

### Post by RedSquirrel on 2007-04-21
> **thebluejay said:**
> When I do that, I no longer get the regular desktop menu when I right-click (as to be expected). But instead, I get no reaction at all. No popup menu at all. Is there not an xfce config file somewhere which tells xfce to open that menu and what to put in it?


Strange. Works for me. Try logging out and logging back in to make sure the settings stick, OR there's also a "Restart" button on the dialog you get when you select 'Quit'. Try that.

RE: editing the menu: I think that's done through the same dialog, under "Edit Menu". I believe the file is ~/.config/xfce4/desktop/menu.xml, but it's probably safer to use the dialog to make changes.

Here's a screenshot...

---

### Post by thebluejay on 2007-04-21
I know what to do, but it just isn't working, even after reboot. Need a fix. :)

---

