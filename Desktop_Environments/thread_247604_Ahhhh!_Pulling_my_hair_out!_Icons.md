---
title: "Ahhhh! Pulling my hair out! Icons"
date: 2006-08-30
forum: Desktop Environments
---

### Post by aceracer24 on 2006-08-30
I, for the life of me, can NOT find that stupid little menu bar icon. The little one on the top tray to the very left. It's the stock Menu Bar Icon I guess. I have tried to find every icon that looks like that and change it to something else but that ONE little icon is hiding very well. Does anyone know where it is so I can change it? It's REALLY not looking good with my theme. Any help would be appreciated thank you!

---

### Post by distroman on 2006-08-30
Take a look here -
[http://www.ubuntuforums.org/showthread.php?t=208457](http://www.ubuntuforums.org/showthread.php?t=208457)

There a couple of easy suggestions as well, but Ill bet you they wont work, if your in dapper. 
I did what wargames suggested and it worked.
> **wargames said:**
> Ok this is what I did to change the Ubuntu logo next the word Applications in the menu bar to a custom icon in Dapper.

1. I followed this guide to change the Ubuntu logo icon to the Gnome foot logo icon in the menu bar:

[http://doc.gwos.org/index.php/Gnome_Icon_Dapper](http://doc.gwos.org/index.php/Gnome_Icon_Dapper)

(Thanks to Perfex above for this info.)

2. Then I copied my custom icon to replace the gnome-foot icon to this location:

/usr/share/pixmaps/gnome-logo-icon-transparent.png

3. I then used command "killall gnome-panel" and then my custom icon replaced the gnome-foot icon next to the word Applications in the menu bar.

Enjoy! :)

---

### Post by aceracer24 on 2006-08-31
Thx for the reply. I tried all of them steps and nothing has worked. I followed them to the letter. I don't get it why some people can make it work and others can't :( Guess I am stuck with this stupid icon....

---

### Post by distroman on 2006-08-31
Did you get the foot applet after reinstalling the panel? Instead of the default ubuntu one?

Did you rename **your** icon to “gnome-logo-icon-transparent.png” and replaced it with “gnome-logo-icon-transparent.png” in ~/pixmaps?

I am just saying this because I tried quit a few ways and this one did it for me. 
The way it is done makes sense too, it gets rid of the distributor-logo.png, which is pure evil.

---

### Post by crossedout on 2006-09-01
The super easy way to do this is to choose an icon theme.  You can find many at gnome-look.org and edit the icons in there to suit your tastes.

For your particular issue, choose the icon you want to replace the ubuntu logo with and copy/paste it to your theme folder.  You can find it by opening your "home" directory - ctrl+h - .icons - <themefoldername> - apps.

After you paste it into the apps (suggested based on experience) folder, rename it to distributor-logo.png.  Next time you login, it will be changed.  Plus by doing it that way, you can alter any of the icon themes so its different for each theme.

-Xout

---

### Post by aceracer24 on 2006-09-13
Better late then never :) I tried all of that. I have followed every how to I can find, most describing the same way, but nothing has worked. So..I am just going to live with it I guess. I hope the develeopers manage to cahnge this in Edgy.

---

