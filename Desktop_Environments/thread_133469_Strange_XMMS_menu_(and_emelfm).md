---
title: "Strange XMMS menu (and emelfm)"
date: 2006-02-20
forum: Desktop Environments
---

### Post by yootje on 2006-02-20
I don't know exactly when this happened, but suddenly the menu of XMMS is very weird. Emelfm was also like this, but I thought it was emelfm-only. Any ideas how to fix this? Thanks in advance!

---

### Post by audax321 on 2006-02-20
Try resetting your user settings by renaming the /home/username/.xmms folder. This will cause XMMS to reset to the default installed settings and create a new .xmms folder. If this gets rid of the issue then something went screwy with your configuration. Otherwise there's something else wrong :)

To get your old settings back just delete the new .xmms folder and change the name of your old one back to .xmms

Also, I noticed that Emelfm uses GTK v1 so maybe something is wrong with one of your /home/username/.gtkrc-blah-blah files? Try changing your theme, which should cause Gnome to write a new /home/username/.gtkrc-1.2-gnome2 file. If the problem persists, post the contents here.

---

### Post by yootje on 2006-02-20
[QUOTE=audax321]Try resetting your user settings by renaming the /home/username/.xmms folder. This will cause XMMS to reset to the default installed settings and create a new .xmms folder. If this gets rid of the issue then something went screwy with your configuration. Otherwise there's something else wrong :)

To get your old settings back just delete the new .xmms folder and change the name of your old one back to .xmms

Also, I noticed that Emelfm uses GTK v1 so maybe something is wrong with one of your /home/username/.gtkrc-blah-blah files? Try changing your theme, which should cause Gnome to write a new /home/username/.gtkrc-1.2-gnome2 file. If the problem persists, post the contents here.[/QUOTE]
Thanks for your help :)

Hm, it's definitely not a xmms-problem, also xwine has the problem.

Changing the theme doesn't work, and I don't have .gtkrc files? Maybe I should reinstall gtk?

---

### Post by audax321 on 2006-02-20
Hmm, thats odd. I have the following in my home folder (use CNTRL+H in Nautilus to see hidden file):
.gtk-bookmarks (which is empty, I think its used for Nautilus's bookmarks)
.gtkrc-1.2-gnome2 , which has the following inside of it:

```

# Autowritten by gnome-settings-daemon. Do not edit

include "/home/audax321/.themes/GentlemanQ/gtk/gtkrc"

include "/home/audax321/.gtkrc.mine"

```

and is specific to the theme I'm using. If you don't have this file, you could try creating it... but you'll have to change the first include line to point to the gtkrc file for the theme you are using. I have no idea what the second include line is because .gtkrc.mine doesn't exist for me.. probably for custom settings.

---

### Post by yootje on 2006-02-20
[QUOTE=audax321]Hmm, thats odd. I have the following in my home folder (use CNTRL+H in Nautilus to see hidden file):
.gtk-bookmarks (which is empty, I think its used for Nautilus's bookmarks)
.gtkrc-1.2-gnome2 , which has the following inside of it:

```

# Autowritten by gnome-settings-daemon. Do not edit

include "/home/audax321/.themes/GentlemanQ/gtk/gtkrc"

include "/home/audax321/.gtkrc.mine"

```

and is specific to the theme I'm using. If you don't have this file, you could try creating it... but you'll have to change the first include line to point to the gtkrc file for the theme you are using. I have no idea what the second include line is because .gtkrc.mine doesn't exist for me.. probably for custom settings.[/QUOTE]
Hm, very strange thing happened. I made the file in gedit, but when I tried to save the file gedit said there already was a file named like that. So I look and I look, but I couldn't find it. But then I ordered on date and suddenly I saw him. Strange.

But I edited the file with my theme, and restarted X to be sure, but it didn't help :(

Does any have a suggestion?

---

### Post by yootje on 2006-02-21
Okay... Suddenly it works again. I didn't do anything special.

Computers are weird things ;)

---

### Post by yootje on 2006-02-21
Okay, it's back again. It's also with VLC and Audacity...

Anyone has an idea?

---

