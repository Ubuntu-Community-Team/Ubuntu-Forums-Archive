---
title: "Virtual Desktop Tweaks"
date: 2009-02-04
forum: General Help
---

### Post by Dooley on 2009-02-04
Two questions.

Firstly, is it possible to set different backgrounds for each virtual desktop? 

Secondly can you execute commands on login(via sessions) and specify the virtual desktop for it to run on? So say I want firefox to autostart on desktop one, but pidgin to autostart on desktop two.

If so for either, any chance of a link or howto.

Cheers in advance.

---

### Post by cherva on 2009-02-04
Are you using KDE or GNOME ?
In KDE it is easy to put different wallpapers...
In GNOME it is a little harder. Try this [http://gnomefiles.org/app.php?soft_id=270]("http://gnomefiles.org/app.php?soft_id=270")
And for your other thing (running firefox on desktop one and pidgin on desktop two ) use Devilspie [https://help.ubuntu.com/community/Devilspie]("https://help.ubuntu.com/community/Devilspie")

---

### Post by Dooley on 2009-02-04
Cheers for the response

I use gnome and actually discovered this for multiple wallpapers. Much easier to install/configure.

[http://wallpapoz.akbarhome.com/download.html](http://wallpapoz.akbarhome.com/download.html)

For devilspie should this config work for firefox?

(if (is (application_name) "firefox") (set_workspace 1))

---

### Post by cherva on 2009-02-05
> **Dooley said:**
> Cheers for the response

I use gnome and actually discovered this for multiple wallpapers. Much easier to install/configure.

[http://wallpapoz.akbarhome.com/download.html](http://wallpapoz.akbarhome.com/download.html)

For devilspie should this config work for firefox?

(if (is (application_name) "firefox") (set_workspace 1))

Wallpapoz looks nice :), as for devilspie I can't realy tell because I used it a while ago... give it a try and you will see what is the right config. :) GOOD LUCK HAVE FUN

> **pmicheal said:**
> is there any way to lock a specific virtual desktop with password? is this possible?

I think it's not possible. And why do you want such a thing ?

---

