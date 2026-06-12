---
title: "Gnome Login Screen Setup"
date: 2005-10-24
forum: Desktop Environments
---

### Post by gwilson on 2005-10-24
My gnome Login Screen Setup function under Administration doesn't come up when I click on it.

I'm basically a Gnome person, but I installed KDE to enable me to test a few programs. Now, when I boot up, the system comes up with the Kubuntu login and session selector. It all works properly, but is there some way I can get back the Gnome login screen and get my Gnome Login Screen Setup function to work again without un installing all of KDE?

Thanks for the help.

---

### Post by Kyral on 2005-10-24
A "sudo dpkg-reconfigure gdm" might help. I'm actually trying to find the file that controls which DM gets loaded

---

### Post by gwilson on 2005-10-24
[QUOTE=Kyral]A "sudo dpkg-reconfigure gdm" might help. I'm actually trying to find the file that controls which DM gets loaded[/QUOTE]

That solved my problem. Thanks.

---

