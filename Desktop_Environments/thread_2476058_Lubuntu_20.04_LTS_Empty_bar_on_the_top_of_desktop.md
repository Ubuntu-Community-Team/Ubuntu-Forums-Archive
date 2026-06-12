---
title: "Lubuntu 20.04 LTS Empty bar on the top of desktop"
date: 2022-06-15
forum: Desktop Environments
---

### Post by almyyy on 2022-06-15
I have empty bar on the top of desktop. This area is unusable.
 I have positioned my Task Manager (taskbar) on bottom. But when I move my Task Manager on the top of desktop, mentioned empty bar is filled with Task Bar and everything is working as expected.
But I want to have Task Bar on the bottom and it causes smaller usable desktop area due to empty par on the top of desktop.

---

### Post by almyyy on 2022-06-15
Oh sorry for creating new thread.
Thanks to this: [https://askubuntu.com/questions/311060/blank-menu-bar-in-lxde](https://askubuntu.com/questions/311060/blank-menu-bar-in-lxde), I found solution: right click on empty bar -> "- Remove Panel"
(Empty bar was just by my mistake somehow added new panel without any widget)

---

### Post by guiverc on 2022-06-15
I'm glad you got it solved.  Well done.

The panel is covered in the Lubuntu manual - [https://manual.lubuntu.me/lts/5/5.1/lxqt-panel.html?highlight=panel](https://manual.lubuntu.me/lts/5/5.1/lxqt-panel.html?highlight=panel)

> To add a second panel right click on the panel and Add New Panel  and a new panel will be created with the dialog to customize your  second panel. To remove a panel right click on the panel and select Remove Panel  and you will be asked if you really want to do this as it can&#8217;t be  undone. To then make your new panel useful you will need to add widgets  which you will need to see the above section.

ie. adding a new panel does just that; adds a second (empty) panel, which is why the manual says you need to add widgets to it to make it useful.

Please note:  For now the *LTS* manual points to 20.04, and *STABLE *points to the Lubuntu 22.04 LTS manual. After release of Lubuntu 22.04.1 (*after 4-August-2022* *and when 20.04 users are offered the chance to upgrade to 22.04*) this is expected to change, but when it does we'll adjust our [link page on our discourse]("https://discourse.lubuntu.me/t/manual-links-currently-available-20-04-lts-22-04-stable/3242") to reflect that.  *(We also may decide to delay this change until after the release of current Lubuntu kinetic (22.10) but the discourse link I provided will be updated when we make this change)*

---

