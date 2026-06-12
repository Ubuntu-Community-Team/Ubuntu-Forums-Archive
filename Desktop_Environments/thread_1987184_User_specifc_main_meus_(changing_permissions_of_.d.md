---
title: "User specifc main meus (changing permissions of .desktop files)"
date: 2012-05-26
forum: Desktop Environments
---

### Post by go4unkwn on 2012-05-26
Hello all

I'm responsible for the IT equipment at a little school.
Now I'm going to set up Lubuntu 12.04 on our public PC's (til now I use Windows Vista in combination with Steady State.)
Now I will use the advantage of (L)Ubuntus guest account (steady state  is really slow on old PC's).

On each PC there will be an account for an administrator and one for the students (guest account).
Now I have in mind, that the guests (students) doesn't could see the whole main menu.
They should see only that part of the menu with the applications they need (office, multimedia, graphics).

I tried to reach my aim changing the permissions of the .desktop files:
a) I created a group adminmenu.
b) I added the admin user to this group.
c) I changed the group of the .desktop files from root to adminmenu.
d) I set the permissions of all .desktop files the guest should not see to 640.

Unfortunately in this way the menu of the administrator get lost completely, too.
Is there a background service (daemon) I have to add to the group adminmenu?

Kind regards, go4unkwn.

---

### Post by rai4shu2 on 2012-05-26
Rather than using the troublesome "guest" feature of lightdm, you should probably go ahead and create new users for each student (or at least one account that students can use for that computer). This will enable you to create custom .menu files which that account can be configured to use.

It's not really a good idea to mess around with .desktop files, as those are really meant to be codified by the maintainers rather than the users.

---

### Post by Rodney9 on 2012-05-26
You could add your own designed panel for users and remove the original.

How to add panel video - [http://blip.tv/ubuntu-switcher/lubuntu-screencast-lxpanel-2-panel-configuration-5316669](http://blip.tv/ubuntu-switcher/lubuntu-screencast-lxpanel-2-panel-configuration-5316669)


For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by go4unkwn on 2012-05-27
Thank's** a lot** for your answers!!

Kind regards, go4unkwn.

---

