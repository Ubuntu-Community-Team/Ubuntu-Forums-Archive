---
title: "Better Icon Quality on Cairo Dock"
date: 2011-05-21
forum: Desktop Environments
---

### Post by miousername on 2011-05-21
Hi at all,

I've added some modification to cairo dock code to improve the icon visual quality when you use it with opengl. With this code cairo-dock 2.2.0-4 use libpng to load png icon and after build the texture with mipmap.

FEATURES ADDED:

I've added others modification that allow you to move the height of the icons on the panel  and allow the dock to go out of the screen when grow up.
You find them in control panel -> behaviour -> position.




I hope this will be usefull!

Bye

link cairo-dock-2.2.0-4~miousername-x32-x64 ->

[http://www.megaupload.com/?d=75OQYNMP](http://www.megaupload.com/?d=75OQYNMP)
md5sum 896ba4d81a4342e8f544bfc39971591a

P.s. You've to download also cairo-dock-plugins-2.2.0-4 here:

[http://launchpad.net/cairo-dock-plug-ins/2.2/2.2.0/+download/cairo-dock-plugins-2.2.0-4.tar.gz](http://launchpad.net/cairo-dock-plug-ins/2.2/2.2.0/+download/cairo-dock-plugins-2.2.0-4.tar.gz)

ICON QUALITY INCREASE ONLY FOR PNG ICON!You obtain the Best result with 256x256 png icons

---

### Post by Frogs Hair on 2011-05-21
That's great , when I used GLX , I never used Open GL because the icons where cartoon like and looked strange.

---

### Post by fatriff on 2011-05-21
I just cannot deal with Cairo Dock, You would think you could do something simple like put the icons where you want and separate the different groups with expanders like you can with awn.. Another issue with Cairo is it has left my machine in a frozen state several times all because of the indicator applet.. 

This is how I have my awn dock..

[http://dl.dropbox.com/u/2528687/linuxmintshot2.png](http://dl.dropbox.com/u/2528687/linuxmintshot2.png)

[http://dl.dropbox.com/u/2528687/linuxmintshot.png](http://dl.dropbox.com/u/2528687/linuxmintshot.png)

I like the features of Cairo like the slide out boxes when you hover and some of the desklets..

Any pointers to get Cairo to look like my Awn?

---

### Post by miousername on 2011-05-22
Hi,

I think that you can, now cairo dock has the panel mode view :

[http://img52.imageshack.us/i/ubuntucairodockpanelmod.png/](http://img52.imageshack.us/i/ubuntucairodockpanelmod.png/)

You can put the icon where you want and then you can separate them in groups with "separators" -> right click on cairo-dock-> add->add a separator.

To solve the frozen state of your machine it's better than you speak with the main developer: Fabounet -> post your bug in glx dock Forums here:

[http://glx-dock.org/bg_forumlist.php](http://glx-dock.org/bg_forumlist.php)

Ps : what's the features or the name of the application that show the preview in your nautilus?? (cover preview like nautilus)
It's very beautifull!

---

