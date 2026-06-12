---
title: "gdmsetup"
date: 2010-02-18
forum: Desktop Environments
---

### Post by litemirrors on 2010-02-18
I just wanted to let you all know gdmsetup appears to be using the gtk themes now and so the old login screens etc. aren't compatible anymore. I've come across some interesting facts to share.

It seems that the login screen for ubuntu now has it's own username and by running

gksu -u gdm dbus-launch gnome-appearance-properties

you can access it then change both the background and the general theme during login.

I'm not sure how gksu differs from sudo or what the extra stuff is at the end however it does work and seems safe enough.

I read people complaining about how they can no longer use the old login screens and this lead me to find out what happened.

It's really rather goofy since in order to change root themes I need to run

sudo gnome-appearance-properties and then add the themes to that account as well in order to get the same theme going for things. There's another method I found but I don't know alot about it and manually changing stuff with Appearance manager seems safer

Set current theme under root account
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts

Well that's it for now.

What I'm saying is to get the same theme for the user/root/and login we need to basically install the themes 3 times for each account! Crazy lul

---

