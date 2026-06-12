---
title: "XFCE Equivalent of gconfig-editor (For &quot;Show All Users&quot;)"
date: 2010-10-06
forum: Desktop Environments
---

### Post by Zanthir on 2010-10-06
Does anyone know the equivalent of ```
gconf-editor
``` for Xubuntu?

I would like to see hidden users in Applications>System>Users and Groups.

In Gnome this can be done by going to /apps/gnome-system-tools/users in gconfig-editor and checking the "Show All Users" box. The closest thing I can come up with in XFCE is Applications>Settings>Settings Editor, but I can't find a "Show All Users" value.

And yes, I know I can manage users from the command line, and I will do that (after I lookup how).

Thank you.

---

### Post by Zanthir on 2010-10-06
Upon further investigation, I realize that what I am really looking for as users are actually groups.

In the instructions for setting up Subversion, I am supposed to add the www-data user to the subversion group. But how can I if www-data is a group?

The question now is, can I add a group to a group? If so, why is this behavior not accounted for in the Users Settings?

---

### Post by Toz on 2010-10-06
www-data is both a user and a group. You can do this via the command line with a simple command. Open a terminal window and type in:

sudo usermod -a -G subversion www-data

/ToZ

---

### Post by Zanthir on 2010-10-06
Right. Thanks Toz. You are right on.

Thanks to twb and demonspork from the #ubuntu-server IRC channel, I learned that the GUI can be unreliable. The "groups" as shown in both Gnome and XFCE are actually both users and groups on Ubuntu Server. They seem to not interface properly with the GUI.

To solve my problem, I simply checked if the users I needed were in fact users with
```
cat /etc/passwd
stat /etc/passwd
```and the "groups" were in fact users.

To add www-data to subversion, all I had to do was
```
sudo adduser www-data subversion
```which I couldn't do from the GUI, but this would have been faster in the first place if I had just tried it instead of freaking out.

My friend keeps telling me "GUIs are the future man. Everything should have a GUI." But that's another story.

Thank you again twb and demonspork.

---

