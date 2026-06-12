---
title: "Step by step guide to looking to Leopard?"
date: 2008-03-29
forum: Desktop Effects &amp; Customization
---

### Post by DrSunnysock on 2008-03-29
Is there a step by step guide to getting my Ubuntu to look like Leopard? I'm really new at this. Thank you!!!

Like, exactly like in this video:
[http://www.youtube.com/watch?v=Bm9vJ0e3tXs](http://www.youtube.com/watch?v=Bm9vJ0e3tXs)

---

### Post by darolu on 2008-03-29
I don't know of a video or have one of my own, but I can tell you how to do it, this is how my Ubuntu looks right now:
[http://www.subirimagen.es/08/0329/112047/ss.png](http://www.subirimagen.es/08/0329/112047/ss.png)

First, you need to find a good GTK theme, this is the one I used, in the same link it comes an Icons set (the one I'm using), a couple of wallpapers and a theme for Firefox, it also comes with an image to use on your top (and bottom) bar so it looks more leopardish:

[http://gekos.no/art1/index.php?option=com_content&task=blogsection&id=5](http://gekos.no/art1/index.php?option=com_content&task=blogsection&id=5)
Kudos to gekos, great theme.

OK, once you've downloaded all those files (if you don't use emerald don't download that one); is very easy don't worry.

First we install the GTK theme, don't untar the file, go to System - Preferences - Theme (not sure if it is how it comes in english :P) or simply right click your desktop and chose change desktop image and go to Themes tab; ok now you can do it the super easy way or the easy way, the super easy way is to simply drag your geko-leopard tag file (the gtk theme file) to the themes list, yes just like that, drop it there and will install automatic, the easy way is to click on Install and choose the file.
Once you've done this, simply click the theme on the list and should change your looks automatic, you can customize it, chose the geko leopard options instead of leopardish, looks better, make sure you change the windows look also so you have the little circles (I'll tell you how to put them on the left later).
Next you may want to install the icons, just untar them and copy the LeopardX folder to /usr/share/icons you'll need root priviliges to do this, a sudo mv LeopardX /usr/share/icons/ should do it, then go back to your theme window and customize the Icons, the LeopardX folder should be there, just click it.
Then go for the Firefox theme, you shouldn't have problems with that.
After that untar the wallpapers, if you don't like those (are tiger versions) just google for leopard wallpapers.
And finally set your maximize,minimze and close buttons to the left, to this (if you don't use emerald) press Alt+F2 and type gconf-editor
A window will pop up, on the left panel go to "apps - metacity - general" on the right panel go to Buttons-layout, and change the value to:  close,maximize,minimize:menu
This is how it works, you set the order of the buttons, separated by comas, the colon represents the middle point, what is on the left, will show on the left corner, what is on the right will show on the right, that simple.
Oh yeah I almost forgot, right click your top bar and go to properties, and change the background to the image you downloaded (menubar-geko.png), it makes it look great.
And that's it for the theme.

Next you'll have to install the AWN Dock.
To do that follow this post:
[http://ubuntuforums.org/showthread.php?t=385981&highlight=awn+dock](http://ubuntuforums.org/showthread.php?t=385981&highlight=awn+dock)


Edit: Oh yeah I forgot to mention, you can find many more themes here: [http://www.gnome-look.org](http://www.gnome-look.org)
you can also find a log in screen to match your mac os x theme, is under GDM

---

### Post by marckie on 2008-03-29
> **DrSunnysock said:**
> Is there a step by step guide to getting my Ubuntu to look like Leopard? I'm really new at this. Thank you!!!

Like, exactly like in this video:
[http://www.youtube.com/watch?v=Bm9vJ0e3tXs](http://www.youtube.com/watch?v=Bm9vJ0e3tXs)

Hi SunnySock,

You want to have this?
[img]http://sourceforge.net/dbimage.php?id=152332[/img]

Use mac4lin!!! Its the greatest! I've been using it since v0.2 and now its v0.4 and the 0.5 is already on its way. From Icons to Panel and all, its all in there. It has even skins and themes for AWN, Firefox, Pidgin and Movie players.

To download:
[http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)

It has a manual (always updated) so that users (us) won't get lost. But if you did get lost then go to its own thread. InfraRed is so approachable:
[http://ubuntuforums.org/showthread.php?t=555373](http://ubuntuforums.org/showthread.php?t=555373)

PM me if you have more questions too...

Enjoy!
maRckie

---

