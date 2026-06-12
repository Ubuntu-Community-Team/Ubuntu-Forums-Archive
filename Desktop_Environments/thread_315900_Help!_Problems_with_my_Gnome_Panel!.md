---
title: "Help! Problems with my Gnome Panel!"
date: 2006-12-09
forum: Desktop Environments
---

### Post by thelinux_guy on 2006-12-09
I logged on to my computer today and noticed that i cant delete my panels,when i right-click on them,I get a little menu with the following listed: Help,and About Panels,can anyone tell me how to correct this error? I need to reset my panels,but cant delete them,or even add stuff to them,can someone help?










-jason

---

### Post by Dave54 on 2006-12-09
I really have no idea what's causing your problem, but I do have a way to manually change the settings of or delete your panels. Go to Applications > System Tools > Configuration Editor. Within the Configuration Editor, on the left side, browse to /apps/panel/. In here you can change different options about your panels. Within toplevels is a list of all your panels. Here you MAY be able to delete your panels, but DELETING THEM MAY BREAK YOUR SYSTEM. I really don't know.

I'm not sure if Configuration Editor is enabled by default. If not, got to System > Preferences > Menu Layout. (This is for Edgy. For Dapper, I think it's A La Cart Menu Editor or something under Applications.) Within Menu Layout, locate Configuration Editor and enable it.

This is all I could come up with. I have found messing around with the Configuration Editor can have adverse effects, so be careful. Hope this helps.

-Dave

---

### Post by mcduck on 2006-12-10
Before you start deleting the panels from Configuration Editor, you could check that apps/panel/global/locked_down is not selected, because your problem sounds exactly like locked panels.. :)

And you can strt Configuration Editor easily if you press F2 and run gconf-editor

---

### Post by Dave54 on 2006-12-10
I don't use key shortcuts much, but F2 doesn't seem to work for me. I think you might have meant Alt+F2.
That list of known applications is awesome, I'll never lose a program again! Thanks for the tip.

---

### Post by thelinux_guy on 2006-12-11
> **mcduck said:**
> Before you start deleting the panels from Configuration Editor, you could check that apps/panel/global/locked_down is not selected, because your problem sounds exactly like locked panels.. :)

And you can strt Configuration Editor easily if you press F2 and run gconf-editor

Thank you so much! that is exactly what my problem was,i was actually trying to change the image icon in the menu-bar (the one with applications-places-system)Dose anyone know how to do that? (I cant find the settings key anywhere in the configuration editor) I must of did something wrong :) ....

---

### Post by mcduck on 2006-12-12
It's only possible to change the icon for the 1-button menu applet with the Configuration Editor. For the Menu Bar applet I think you need to replace the actual image file used, and that will also change the same image everywhere it's used on your desktop..

I don't remember which image it was, but try searching the forum for 'distributor logo' or something.

---

