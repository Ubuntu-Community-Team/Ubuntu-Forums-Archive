---
title: "Remove Item from Menu"
date: 2005-03-28
forum: Desktop Environments
---

### Post by vassie on 2005-03-28
I was playing around with Cedega and it has created an entry in my menu, I have removed Point2Play and Cedega, but it has left the menu entry behind, how can I delete it?

[img]http://benvassie.net/blog/uploads/menu.png[/img]

Please pardon the ropey highlight, it's a bit hard with a synaptic touchpad :)
Thanks
Ben

---

### Post by bored2k on 2005-03-28
[QUOTE=vassie]I was playing around with Cedega and it has created an entry in my menu, I have removed Point2Play and Cedega, but it has left the menu entry behind, how can I delete it?

[img]http://benvassie.net/blog/uploads/menu.png[/img]

Please pardon the ropey highlight, it's a bit hard with a synaptic touchpad :)
Thanks
Ben[/QUOTE]
 Did you try amaranth's menu editor ?
[http://ubuntuforums.org/showthread.php?t=21390&highlight=menu+editor](http://ubuntuforums.org/showthread.php?t=21390&highlight=menu+editor)

---

### Post by vassie on 2005-03-28
Yes, but it's not on the list for me to remove
Ben

---

### Post by ubuntu_demon on 2005-03-28
[QUOTE=vassie]Yes, but it's not on the list for me to remove
Ben[/QUOTE]
 try to locate the .desktop file that corresponds with the menulink

for example :
locate TransGaming

if you have found this .desktop file edit it and put this in :

"OnlyShowIn=KDE;"

that way it won't show up in gnome anymore. It's a bit of a hack ofcourse.

---

### Post by vassie on 2005-03-28
[QUOTE=demon666_nl]try to locate the .desktop file that corresponds with the menulink

for example :
locate TransGaming

if you have found this .desktop file edit it and put this in :

"OnlyShowIn=KDE;"

that way it won't show up in gnome anymore. It's a bit of a hack ofcourse.[/QUOTE]

I've done a search for *.desktop but can't find anything with TransGaming in :(

Ben

---

### Post by vassie on 2005-03-28
Found it :)

/etc/X11/applnk/

sudo nautilus /etc/X11/applnk/ took care of it ;)

Ben

---

