---
title: "[SOLVED] Desktop Right-Click Menu (Submenus)"
date: 2008-07-30
forum: Desktop Environments
---

### Post by quazi on 2008-07-30
So I've been using nautilus actions to successfully (to an extent) modify my right-click menu on the desktop.  The way to do that is add an entry in nautilus-actions-config and under advanced conditions add the condition "x-nautilus-desktop".  I'm not sure how to remove the default items (or if I even can).

What I'm trying to do now (and not sure if it's possible) is add a submenu with nautilus actions so I don't have one huge menu when I right click the desktop.  Any suggestions?

---

### Post by CC_Joe on 2008-07-30
Fluxbox!

If you want serious desktop clicking functionality, that's the way to go. I'm not so sure how to go about it through gnome.

---

### Post by Gourgi on 2008-07-30
try compiz desktop menu 
[http://forum.compiz-fusion.org/showthread.php?t=7070](http://forum.compiz-fusion.org/showthread.php?t=7070)

[http://gitweb.compiz-fusion.org/?p=users/crdlb/compiz-deskmenu;a=summary](http://gitweb.compiz-fusion.org/?p=users/crdlb/compiz-deskmenu;a=summary)

or compiz desktop click
[http://gitweb.compiz-fusion.org/?p=users/smspillaz/desktopclick;a=summary](http://gitweb.compiz-fusion.org/?p=users/smspillaz/desktopclick;a=summary)

---

### Post by quazi on 2008-07-30
Got it, thanks for the help.  I found the compiz-deskmenu to be the best option.  The documentation is a wee bit lacking for new users like me, but after enough googling/apt-cache searching I found what I needed.  Here's what I had to do to replace the default right-click menu on the desktop:

**[SIZE="4"]compiz-deskmenu[/SIZE]**

[[IMG]http://img120.imageshack.us/img120/2474/cpzdeskmenuwr4.th.jpg[/IMG]](http://img120.imageshack.us/my.php?image=cpzdeskmenuwr4.jpg)
Obviously compiz needs to be running for this to work and a few packages are necessary beforehand.  

Open a terminal and enter ```
sudo apt-get install python-lxml libgtk2.0-dev libwnck-dev libdbus-1-dev git-core compizconfig-settings-manager libdbus-glib-1-dev
```

Now enter ```
$ cd ~
$ git clone git://anongit.compiz-fusion.org/users/crdlb/compiz-deskmenu
$ cd compiz-deskmenu
$ make
$ sudo make install

```

To make this menu show up we need to make some changes in the compiz settings.  To bring this up, simply open a terminal and enter ```
ccsm
```

Now we just need to map this to the right mouse  button.  When in ccsm, click on general options and go under the commands tab and commands dropdown menu.  Click on one of these that's unused and set it to compiz-deskmenu.  Now go to Viewport switcher and set the Plugin for initiate action to "core" and the action name for initiate to "run_command#_key", where # is the number of the command corresponding to compiz-deskmenu.  Change initiate plugin action key to Button 3 and now the right mouse button should popup the compiz deskmenu.  If you'd prefer to keep the gnome right click menu, just leave initiate plugin action as button 2.  To edit the menu, just click on the edit item in the menu.

One quirk I've noticed with the menu editor is that icons need to be located under /usr/share/pixmaps.

---

### Post by Rubicon421 on 2008-12-08
Anyone know why my right click menu would just quit working altogether? Ubuntu 8.10/GNOME, with Compiz and Avant. 

Desktop icons are not displayed, but if I go to the dsktop folder in a file manager then they are there and I can right click the folder. Right clicking the desktop does nothing though.

View my other posts for more info, I started one on it a while ago but just found this one that was kinda related.

---

### Post by Doc Hoss on 2008-12-15
Maybe you have Button 3 set to initiate compiz-deskmenu, but deskmenu is broken?  I'm having that same problem.  Followed the above install instructions for deskmenu but it does nothing when I set it to use button 2 or 3.  Any ideas?

---

### Post by quazi on 2008-12-16
There were a couple of typo's in my post which could easily have caused this to not work.  Here's the passage which you should look at again:

"Now go to Viewport switcher and set the Plugin for initiate action to core and the action name for initiate to run_command#_key, where # is the number of the command corresponding to compiz-deskmenu."

Before I had said "run_command0_key" which is only correct if you have compiz-deskmenu as your first command.

Additionally, try holding down control when you right-click.  For me that brings up the gnome right-click menu regardless of what I have compiz-deskmenu set to.

---

### Post by Boaslad on 2009-02-15
o.k. this was cool. but I have one issue that I hope some one can help with. I want the Ubuntu Main Menu to come up when I right click. Any idea how to make that work with this?

---

### Post by quazi on 2009-02-17
> **Boaslad said:**
> o.k. this was cool. but I have one issue that I hope some one can help with. I want the Ubuntu Main Menu to come up when I right click. Any idea how to make that work with this?

I don't know how to do this, but I suspect it can be done (Alt+F1 brings up the menu, so I'm sure there's a command to bring it up).

---

### Post by merlin_ie on 2009-07-06
Great thread, helped me out a lot. But, I can't get the icons in the menu like you said. They are in the /usr/share/icons/gnome/16x16 category like you said, but all I get beside the label is a big red X. So, is there anything you can suggest or that I might be doing wrong?

---

### Post by quazi on 2009-07-12
> **merlin_ie said:**
> Great thread, helped me out a lot. But, I can't get the icons in the menu like you said. They are in the /usr/share/icons/gnome/16x16 category like you said, but all I get beside the label is a big red X. So, is there anything you can suggest or that I might be doing wrong?

Put them in /usr/share/pixmaps.

---

### Post by DumaIT on 2011-10-29
Great Topic, but in newest version of Compiz, if I set core and run_command#_key doesn't work.
I'm running Ubuntu Lucid and Compiz Works good... someone could help me?

____EDIT____

Ok, I've solved... instead of  core, now we have to use ```
commands
```!

---

