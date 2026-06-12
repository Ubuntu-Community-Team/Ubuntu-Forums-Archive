---
title: "Change the default GNOME configuration for new users"
date: 2010-08-22
forum: Desktop Environments
---

### Post by panfist on 2010-08-22
I'm looking to customize the environment for new users by changing the items in the GNOME menu, change the panel layout, add some shortcuts, and do a few other things. I looked in /etc/skel and there doesn't seem to be anything GNOME related in there; I also tried to put .gconf, .gconfd and .gnome2 from my home directory into /etc/skel and that didn't do what I wanted.

---

### Post by fredbird67 on 2010-08-23
1) To address your question regarding changing the GNOME menu items, it's been a while since I've used GNOME (I switched to Xfce earlier this year, so I'm trying to do this from memory), so I'll give it my best shot.  If memory serves me correctly, I think you should be able to right-click on your "Applications" menu, and there should be something in the popup menu that allows you to edit what's in the menu.

2) About the panel layouts, GNOME, KDE, and Xfce (and possibly other desktop environments) let you arrange the items in the panel(s) any way you want them.  In GNOME, what you do is right-click on the panel items and click "Unlock", and then drag and drop it to wherever you want it in your panel(s).

If you wish to move everything to a single panel, just right-click on any blank area of the panel you wish to delete, and in the menu, you should find something labeled "Delete panel" or something to that effect.  Bear in mind you'll lose everything that's in that panel, so you might want to add in everything to the other panel first.  However, you can't do this with the notification area, so once that's all that's left (if it's there), you're ready to delete that panel and then re-add that to the other panel.

To add items to the panel, right-click on any blank area of the panel and click on "Add panel items" or words to that effect (like I said, I'm trying to do this by memory), and then you'll see a list of all the little doodads you can add to your panel.  Just click what you need, position it to your heart's content, and you're good to go there.  You can also add shortcuts in this manner for any programs in your menu too, as this can also be found in the menu for adding menu items.

Lemme know if this helps! :-)

Fred in St. Louis

---

### Post by panfist on 2010-08-23
Ahh, sorry if I wasn't clear in my original post...I know how to edit the settings for the currently logged in user, I need to know how to edit settings for new users, so that any new users start with a customized environment. 

I'm reading this now: [GNOME Desktop System Administration Guide]("http://library.gnome.org/admin/system-admin-guide/")

---

### Post by iMisspell on 2010-08-23
Im the mist of setting up "my own Ubuntu CD" and part of that is customizing the default layout for newly created users.

The following is how ive been going about it and so far its working, ive tested creating new accounts via *System > Admin > Users & Groups* along with *sudo adduser* and both are working, new users are defaulted with the Desktop, Main menu, panels, launchers and Firefox bookmarks which i have set up in /etc/skel/

Heres the process im working with-in:

- Installed a clean/fresh install of Ubuntu inside a vBox guest (makes it easyer for testing so not to mess up my current "main" desktop).

- *Moved* (note: 'moved' and not 'copied') over the following (except for the .gnome2 folder) from my working user account to the /etc/skel/ folder. I did not copy the full .gnome2 folder, instead i only copied over acouple sub-folders from .gnome2 (listed second (below)). 

- After all the folders where copied over, i change the permissions of this folders to my current user account to have full access to them.
 
- Then created symbolic links from these folders to my current users account home folder.

- Restarted system.

By doing all that it gives me the freedom to customize my current user account and these customize settings are being saved in the /etc/skel/ dir to be used as the default settings for new accounts.

```
me@ubuntu:/etc/skel$ ll -A
-rw-rw-r--   1 me   users  1424 2010-08-20 23:06 .bash_aliases
-rw-r--r--   1 root root    220 2010-04-18 21:51 .bash_logout
-rw-r--r--   1 root root   3103 2010-04-18 21:51 .bashrc
drwxr-xr-x  20 me   users  4096 2010-08-20 21:46 .config/
drwxr-xr-x   2 me   users  4096 2010-08-21 22:55 Desktop/
drwxrwx---   5 me   users  4096 2010-08-21 23:12 .gconf/
drwxrwxr-x   5 me   users  4096 2010-08-10 01:29 .gnome2/
drwxrwxr-x   3 me   users  4096 2010-08-10 12:36 .local/
drwxrwx---   4 me   users  4096 2010-08-09 01:00 .mozilla/
drwxrwxr-x   2 me   users  4096 2010-08-09 13:37 myscripts/
-rw-r--r--   1 root root    675 2010-04-18 21:51 .profile

```

/etc/skel/.gnome2/
```
me@ubuntu:/etc/skel$ cd .gnome2; ll -A
drwx------ 2 me   users 4096 2010-08-10 01:29 accels/
drwxr-xr-x 2 me   users 4096 2010-08-09 14:45 nautilus-scripts/
drwxrwx--- 3 me   users 4096 2010-08-08 21:33 panel2.d/

```

As far as doing all the moving, permission changes and linking, i created a bash script to do all the work for me :)
Will post it if you want.

_

---

### Post by mcduck on 2010-08-23
Putting all the relevant configuration files and other stuff into /etc/skel is the way to go. Just make everything is owned by root and has normal permissions and they should be copied to every newly created user's home.

The way I usually do this is that I create a fresh new user, then adjust that user's desktop and settings the way I want them to be for all users, copy all the setting files & directories from that user's home to /etc/skel and then remove the user afterwards.

Of course also make sure you copy *all* the setting files and directories relevant for everything you want to configure for the new user accounts. Just .gconf, .gconfd and .gnome2 won't take you far. You can pretty much look for the stuff you *know* to not be needed, and copy everything else.

---

### Post by JaseP on 2010-10-05
> **mcduck said:**
> Putting all the relevant configuration files and other stuff into /etc/skel is the way to go. ...

The way I usually do this is that I create a fresh new user, ...



Thanks,... I've been looking for a way to do this for YEARS,... well, obviously, not looking too hard,... But thanks a million,...

---

