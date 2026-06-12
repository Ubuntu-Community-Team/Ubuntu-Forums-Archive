---
title: "prevent user from changing background"
date: 2006-10-05
forum: Desktop Environments
---

### Post by limiter on 2006-10-05
How do i prevent one of my user's from being able to change the background?  I've already disabled all useful user permissions and they can still change it.  The user is stupid and puts explicit backgrounds on the computers.

thanks

---

### Post by meng on 2006-10-05
The simplest answer:
Disable the user account altogether. Temporarily, perhaps - maybe that will teach a lesson, maybe you don't even care - in which case make it permanent.

---

### Post by Wicca on 2006-10-05
You can change the permissions of the file **/usr/bin/gnome-background-properties**.
Just remove the read and execute rights for *other*. Change the group from *root* to *admin*. Now only sudoers can change the background.

Or:
If there are normal (no sudoer) users that are a allowed to change their background, or you don't want to sudo all the time, you can do the following:

Make a new security group called, let say, *background*. Add all the users to that group besides your 'stupid' user. Now change the permissions of the file as mentioned above, but instead of changing the group from *root* to *admin*, change it to *background*.

---

### Post by limiter on 2006-10-09
That worked to disable the "right click on desktop background" option for changing the background but the user can still open up an image in "eye of gnome" and ask eye of gnome to change it for them.

---

### Post by skymt on 2006-10-09
Try Sabayon (sudo aptitude install sabayon). It's a good tool if you have unruly users. It lets you lock down any GNOME preferences you like.

---

