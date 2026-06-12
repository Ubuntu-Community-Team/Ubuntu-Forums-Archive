---
title: "Opens movie player!"
date: 2011-01-17
forum: Desktop Environments
---

### Post by bloodshot13 on 2011-01-17
For some reason, when I go to Places>Home folder,desktop,documents,ect. it opens movie player! How do I get it back to open folder correctly?

---

### Post by Vaphell on 2011-01-17
right click on any directory
click open with...
click 'remember this app for this type' checkbox in the window
select nautilus or filebrowser or whatever, confirm

i guess you opened some directory full of media files once in a player and left the checkbox marked, so the player became the default app for all directories

---

### Post by bloodshot13 on 2011-01-17
Thanks for the reply, but when I right click on the folder it still opens up movie player. Doesn't give me an option to "open with".

---

### Post by bloodshot13 on 2011-01-17
I've got it! Luckily I had a folder on my desktop and I was able to right click on folder and open with other application>file browser. I guess this is the correct action as it works. Thanks again for the reply.

---

### Post by mc4man on 2011-01-17
possibly you're inadvertantly d. clicking or holding the r.click a hair to long (after about 1/2 second the up on mouse button becomes execute on selected option which likely is open.
Try a 'tap' r. click or open this file
```
gedit ~/.local/share/applications/mimeapps.list
```
Look for this line
inode/directory=
and stick this at the front or just delete the line
```
nautilus-folder-handler.desktop;
```
Ex.

```
inode/directory=[COLOR="Red"]nautilus-folder-handler.desktop;[/COLOR]audacious.desktop;gnome-mplayer.desktop;vlc.desktop;totem.desktop;
```

Edit: See you got it - in future make sure the "Rememeber this appl..." option is unchecked when using the 'open with - other application menu'

---

### Post by bloodshot13 on 2011-01-17
> **mc4man said:**
> possibly you're inadvertantly d. clicking or holding the r.click a hair to long (after about 1/2 second the up on mouse button becomes execute on selected option which likely is open.
Try a 'tap' r. click or open this file
```
gedit ~/.local/share/applications/mimeapps.list
```Look for this line
inode/directory=
and stick this at the front or just delete the line
```
nautilus-folder-handler.desktop;
```Ex.

```
inode/directory=[COLOR=Red]nautilus-folder-handler.desktop;[/COLOR]audacious.desktop;gnome-mplayer.desktop;vlc.desktop;totem.desktop;
```Edit: See you got it - in future make sure the "Rememeber this appl..." option is unchecked when using the 'open with - other application menu'
  I did this and now it shows:inode/directory=nautilus-browser.desktop;totem.desktop;nautilus-folder-handler.desktop;. I try and right click from Places>(folder) and it just opens it up. I try it quick or long but doesn't seem to matter. Never gives me the "open with"option, or any other option for that matter.I don't know what I would of done if I didn't have the folder on my desktop(except for your help,of course). Thanks again.

---

### Post by mc4man on 2011-01-17
> I try and right click from Places>(folder) and it just opens it up.
That would be expected - there is no r.click menu from places so a r. click is the same as a left click.
nautilus-folder-handler.desktop is basically the same as nautilus-browser.desktop, -  whats important is that it (either), is the first listed on that line - first listed is the default

This is part of a nautilus bug that won't be fixed (the default for folders can be changed by the 'Remember..." option box. (or first listed on that line

Just make sure it's never checked in the future

---

### Post by bloodshot13 on 2011-01-17
gotcha.. Thanks.

---

