---
title: "A couple of gnome-related questions"
date: 2007-01-29
forum: Desktop Environments
---

### Post by Boule on 2007-01-29
Hi,

I installed ubuntu-desktop on my kubuntu install, and there are some things I can't find...
1. How to make the mounted partitions NOT to appear on the desktop
2. How to enable / disable numlock on login
3. How to enable auto-login
4. How to chose amarok as my default music player

For some unknown reason, when I double-click on my home folder on the desktop, nothing happens, but it works from places -> home

When I log out from KDE and log into gnome, the partitions of fstab can't mount. I get an error msg saying can't run "pmount". That doesn't happen when I log into gnome on startup.

Thx for ur help...

---

### Post by featherking on 2007-01-29
#3 = System > Admin > Login Window, then the Security tab - Check Automatic Login
#4 = On one of your music files (say bill.mp3 for example) right click and go to properties > "Open With" select Amarok if it is listed there and hit close. If it is not listed there then click 'add' then add amarok and select it and then hit close on the properties window. Now all mp3 files will open with amarok. (Repeat for other filetypes you may have)

---

### Post by Boule on 2007-01-29
#3. I figured it'd be there, but every time I try to open it, it prompts me for the password, I enter it and nothing happens... I don't know why the install is buggy :(
#4. That didn't work. It openned the file with the player I selected, but when I double-click, it opens them with Totem. And when I press the media button on my keyboard, it opens Rythmbox. I want it to be amarok instead...

---

### Post by blackened on 2007-01-29
#1 Applications->System Tools->Configuration Editor: /apps/nautilus/desktop in the right pain deselect "volumes_visible".
#2 Install numlockx.

---

### Post by Boule on 2007-01-29
hmm I don't have configuration editor under system tools ?!

So if I understand correctly, KDE has an embedded way of handling the numlock on, but not gnome ?

---

### Post by 3rdalbum on 2007-01-29
If you don't have "configuration editor", press Alt-F2 and type "gconf-editor".

---

### Post by Boule on 2007-01-29
Thanks for your help !

Installing kubuntu-desktop changes the load and shutdown screens to kubuntu ! Not that it's very annoying, but isn't there a way to change them back ?

---

