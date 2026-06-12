---
title: "Panels hidden at login"
date: 2010-06-09
forum: Desktop Environments
---

### Post by samalone on 2010-06-09
I'm an experienced programmer on other systems, but pretty new to Ubuntu. I'm having trouble with a fresh install of 10.4 Lucid Lynx on an old Pentium III desktop that was working fine with a previous release of Ubuntu. The problem started after an upgrade to 10.4, persisted after doing a clean install from CD, and is still there after installing all recommended updates.

The symptom is that after login, neither the top nor the bottom gnome panels are displayed. I can right-click on the desktop and get the desktop menu, and I can type Alt-F1 and get the left-hand launcher menus, though the top panel still does not display.

The problem does not always occur, but nearly always. The first login to a newly created account will often show the panels, but in subsequent logins the panels are hidden.

If I login in Failsafe GNOME mode, the panels will appear.

I can fix the problem for a given login session by opening gconf-editor, editing /apps/panels/toplevels/top_panel_screen0, and toggling auto_hide on and then off again. If I log out and back in again, the problem recurs. The problem is that I'm trying to set up this computer for some very naive users, so this kind of workaround isn't really practical.

I'm not sure if it matters, but in the Appearance preferences, visual effects are set to "none".

Any suggestions on how I might get the gnome panels to appear reliably?

---

### Post by resolv_25 on 2010-06-10
I had quite a similar problems on 8.04.
so, it is still bugy this panel...
I was asked to delete some parts of the panel (as trash icon) and afterwards, panel would disapear.
Eventually, try to put on the panel as less elements as possible.

---

### Post by Ascurion on 2010-06-10
I had the same problem under Ubuntu 9.10, now with 10.04 it has disappeared. But what helped we was to kill the panel-task in the shell via:

```
p=`ps -d | grep panel` 
kill ${p:0:5} 
```After that the panel reloaded and everything appeared and worked normally. 
If you can not open a terminal from the plain desktop the 'nautilus-open-terminal' package is helpful. After installing it with 

```
sudo apt-get install nautilus-open-terminal 
```you can right click on the desktop and click on  'open in terminal' and you'll have access to the shell. 
Well this is a bit cumbersome, but I hope this helps also in your case.

---

