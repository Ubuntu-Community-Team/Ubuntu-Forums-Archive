---
title: "Fresh install on 2 Laptops - no taskbar on one ?"
date: 2020-04-10
forum: Desktop Environments
---

### Post by oygle on 2020-04-10
Two laptops, one a HP 4330S and the other a Dell Inspiron 3542. Both have had a fresh installation of Kubuntu 19.10. The Dell install produced a taskbar and application menu by default. The HP produced no taskbar and no application menu or other menus. Had added a application menu on the HP by adding a widget. On the HP, how do I  ?

* Add a taskbar
* Move the (huge) "K" icon that represents the taskbar (launcher)
* Reduce the size of the icon on the launcher

I should add that the HP laptop has a broken screen and I have a VGA monitor plugged into the laptop. That _may_ be causing the problems ??

---

### Post by lvm on 2020-04-10
It could be that your laptop is configured with two screens and all the stuff your are looking for is on the first (broken) one. Check it in system settings, to start it without application menu run systemsettings5 from the shell. Anyhow, to add a taskbar rightclick on a desktop and select 'add panel-application menu'.

---

### Post by oygle on 2020-04-10
> **lvm said:**
> It could be that your laptop is configured with two screens and all the stuff your are looking for is on the first (broken) one. Check it in system settings, to start it without application menu run systemsettings5 from the shell. Anyhow, to add a taskbar rightclick on a desktop and select 'add panel-application menu'.

@lvm - thanks you are correct. I removed what I did have, a widget including an application menu so that the desktop was vacant. Then used the command **systemsettings5** and there were 2 monitors there. As soon as I defined the large monitor as the primary, I had a taskbar down the bottom and the "K" icon which enables the application menu. It has what looks like a taskbar on the right hand side, plus a black border on the left hand side and the top. I would like to get rid of the top, left and right hand bars, took a pic as 'print screen' wasn't working.

---

### Post by oygle on 2020-04-10
Have been able to remove the left hand and right hand bar/panels. Just the top one to remove, it won't disappear when I 'remove panel'. It looks like the top one is the menufunctions for Kate, almost as if Kate is connected to the top panel ?

---

### Post by oygle on 2020-04-12
So, twice now, when I boot up the HP laptop, even though the 'desktop' is mostly how I want it to be, is a mess again. No menu, taskbar, nothing, just a big "K" there.

How can the settings **not** be saved on shutdown ? Because that is what is happening. The only resolve at present is to go into those system settings and fix it all up. Once I had to reset what the primary and secondary monitor was, and synchronise the two.

---

### Post by oygle on 2020-07-11
How can these settings be saved on shutdown ?

---

### Post by oygle on 2020-11-02
This is now fixed in 20.04.1, so will mark this solved.

---

