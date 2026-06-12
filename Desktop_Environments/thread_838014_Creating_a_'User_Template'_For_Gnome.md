---
title: "Creating a 'User Template' For Gnome"
date: 2008-06-23
forum: Desktop Environments
---

### Post by linuxsudo on 2008-06-23
There's something I'd really like to be able to do in Gnome ready for when I switch my home network over to Ubuntu clients. The following would involve creating some sort of a user template for different users on my machine.

I will be keeping the default gnome stuff so my profile isn't anything that I need to worry about, however I would like to make sort of a template so that all users by default have the same settings apart from admin accounts.

To explain in more detail I would like to set up a profile with customisations such as menu items, Window Settings, Colour Settings, Resolution Settings etc and then apply these settings to every other user I add to the machine, sort of like a 'user profile template'. 

Please ask me if you need more information.

---

### Post by ad_267 on 2008-06-23
I'd also be pretty interested in this if anyone knows a simple way to set this up. If there isn't any I think it would be quite a useful feature. It would also be useful to be able to have things like the same plugins in firefox enabled.

---

### Post by mcduck on 2008-06-23
Create a new account, make all the changes you want, and then copy the contents (or the setting files) from that account to /etc/skel.

Alternatively, you might want to take a look at Sabayon (which is a graphical tool made for purposes like this).

---

### Post by Maddy on 2008-08-01
> **mcduck said:**
> Create a new account, make all the changes you want, and then copy the contents (or the setting files) from that account to /etc/skel.

Alternatively, you might want to take a look at Sabayon (which is a graphical tool made for purposes like this).



Hello, I've been searching true this forum and I have read the answer you give several times, but when checking the /etc/skel folder I only see 3 files en 1 folder, if creating a new user without changing the /etc/skel folder I get the default folders we normally have in Ubuntu, I get a choice of 3 wallpapers when i try to choose a different wallpaper and none of these files are in the /etc/skel folder, so my question is, where are these first time files, where does the system gets its information when creating the new settings for the new user.

---

### Post by mcduck on 2008-08-01
I don't know about the directories created for new users, but at least the wallpapers, just like themes and fonts and other that kind of stuff, are available for new users simply because they are installed system-wide (wallpapers in /usr/share wallpapers, for example). So they are never copied to new user's homes, they are simply available for all users.

---

### Post by Maddy on 2008-08-01
> **mcduck said:**
> I don't know about the directories created for new users, but at least the wallpapers, just like themes and fonts and other that kind of stuff, are available for new users simply because they are installed system-wide (wallpapers in /usr/share wallpapers, for example). So they are never copied to new user's homes, they are simply available for all users.

Hello,


You probably mean /usr/share/backgrounds instead of /usr/share/wallpapers, and yes the 3 default wallpapers a new user gets are in that folder, but there are also 5 other wallpapers, so 8 in total, why do these not appear in the list. I guess thats because it is somewhere 'defined' that only the 3 brown colored wallpapers should be used. What I want to know is 'where are these pre-definitions' of the settings every user gets when creating a new account, if you want to make your own version of ubuntu for example (this is not what I want but it is maybe easier to understand what I mean)

Dirk

---

