---
title: "Gnome: application menu vanished from menu bar applet"
date: 2006-09-12
forum: Desktop Environments
---

### Post by Zerberos on 2006-09-12
Hi there,

I've got a little problem with the menu bar applet. 
Despite being able to edit the menu in alacarte, the application menu doesn't show in the applet. No problems with the system or locations menu (Don't know whether that are the right names, just translated them from my german localisation).

Does anyone have an idea in which *%gconf* best to look first? Or which key in gconf-editor should be edited? :confused:

---

### Post by moore.bryan on 2006-09-12
*did you accidently delete it off the panel and have you tried right-clicking the gnome-panel, add to panel, and choosing the application menu choice?  *

---

### Post by hulio40 on 2008-02-24
the same thing hapened to me and im a  big noob in ubuntu and dont know how to run my applications from else then my applications menu  when i put the other kind of menu the application menu is empty and cant add anything to it i didnt delete anything and when i do edit menus it doesnt start pls help

---

### Post by hulio40 on 2008-02-25
i resolved the problem here is how to fix it

```
cd /home/user/.config/menus/
rm applications.menu
```


replace user by ur ubuntu username

---

