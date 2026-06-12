---
title: "Changing icon of Ubuntu Main Menu"
date: 2008-11-01
forum: Desktop Environments
---

### Post by Valsum on 2008-11-01
Changing the icon of the Main Menu in the panel was easy in Xubuntu but now I've switched to Ubuntu I haven't discovered the way to do it. Can someone help me, please?

---

### Post by ww711 on 2008-11-01
Right click on the Ubuntu icon and then choose 'edit menu'.

---

### Post by OrangeCrate on 2008-11-01
Yes, it is much easier in Xfce. I have the same custom icon in Gnome, and here is how I did it...

Put your new icon in your home folder, and label it "start-here.png"

Then, open your terminal, and type the following command:

```
gconf-editor
```

When you execute this command, a "Configuration Editor" window will open. You will need to go down the list on the left to get to a certain item, so do the following:

apps > panel > objects > object_0 (or it may be another number - check all of them to find the right one - mine happens to be 5)

Second, in the right pane, check the box for "Use Custom Icon". Then go up, and right click:

Custom Icon > Edit Key 

In the value box type:

/home/USERNAME/start-here.png

Once you have entered this into the box, click OK. If you followed all steps correctly, then you should see your icon on your Main Menu.

---

### Post by Valsum on 2008-11-02
Thank you, OrangeCrate! ww711, next time check before you answer please. Edit Menus doesn't have an option to change the icon.

---

