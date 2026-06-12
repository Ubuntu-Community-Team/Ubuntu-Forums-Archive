---
title: "Creating a panel launcher for NeverWinter Nights"
date: 2006-12-14
forum: Gaming &amp; Leisure
---

### Post by happy-and-lost on 2006-12-14
I've just installed NWN Platinum on my Edgy and, in spite of the ATi drivers, is running great. Now I want to create a launcher for it. To run the game I have to open up a terminal and type

jo@mithos:~$ cd Games/nwn/
jo@mithos:~/Games/nwn$ ./nwn

or navigate to the nwn file in Nautilus and launch it from there.

I've tried creating launchers in various ways, but to no avail.

---

### Post by hikaricore on 2006-12-14
This is so simple you'll smack yourself for overlooking it.

Open up a terminal and you should be at your home directory ~

type:

```
pico nwnlaunch.sh
```

then in pico, type or paste:

> 
#! /bin/bash
cd ~/Games/nwn/
./nwn


Hit Ctrl+o to save, then Ctrl+x to close pico.

Now type:

```
chmod +x nwnlaunch.sh
```

That's it, you now have a launcher file in your home directory that will launch NWN from anywhere you link it from.  You can link a desktop shortcut to this, or a gnome menu item, or a gnome/kde launcher item.  Any of them should work.

Hope this helps.

--Aaron

---

### Post by happy-and-lost on 2006-12-15
I've been trying to figure out how to make scripts like that for ages! Worked a charm, thanks :)

---

### Post by thx_1138 on 2007-01-29
Thanks for the easy fix, I had been wondering why it would'nt work while trying to make a default icon for nwn using the gnome options. I will have to give it a try here

---

### Post by leech on 2007-01-30
You don't even need to do that.  Step 7 in my HOW TO states

7: After installation, if you want an icon either on the desktop or on the menu you will need to edit the nwn start up script. Just


```
gedit ~/nwn/nwn
```

and add a line

```
cd /home/<username>/nwn
```

Then use Alacarte to add the menu item under Games (or wherever you prefer) and the icon is in your nwn directory as well.  Or you can create the launcher directly on the panel itself by either dragging the menu item you had just created over to the panel, or by right clicking on the panel, selecting add to panel, click on Application Launcher and follow the same method as for adding a menu item.

Leech

---

