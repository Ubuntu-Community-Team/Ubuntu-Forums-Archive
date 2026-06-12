---
title: "copy existing user"
date: 2009-09-29
forum: Desktop Environments
---

### Post by cccc on 2009-09-29
hi

I've Ubuntu 9.04 with Gnome.
Howto copy an existing user profile with ALL settings: Desktop Icons, Firefox Bookmarks etc?

BTW I'd like to create a new user, copy all settings and delete the existing one.

---

### Post by aysiu on 2009-09-29
Create a new user.

Then enter these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo -i
cp -R /home/*oldusername*/* /home/*newusername*/
chown -R *newusername*:*newusername* /home/*newusername*
``` Not guaranteed to work. You're better off copying over only specific subdirectories (in *gksudo nautilus*, press Control-H to see hidden folders and copy over the .gconf, .gnome2, .themes, .icons, and .mozilla folders).

---

### Post by cccc on 2009-10-28
hi

I've done the following and it works great:

1.) # sudo -i
2.) # cp /etc/group /etc/group_save
3.) # adduser new_username
4.) # cp -a /home/old_username/* /home/new_username/
5.) # chown -R new_username:new_username /home/new_username
6.) # userdel old_username
7.) check in /etc/group_save for old_username and compare with a new_username in /etc/group

greetings
cccc

---

