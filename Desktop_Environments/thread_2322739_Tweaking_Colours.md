---
title: "Tweaking Colours"
date: 2016-04-30
forum: Desktop Environments
---

### Post by Crimple on 2016-04-30
Hi.

Under Xfce (I'm thinking Xubuntu 16.04) is it possible to change the windows and menus background colours? 
The idea is to produce something like the image bellow.

[ATTACH=CONFIG]268730[/ATTACH]

---

### Post by vasa1 on 2016-04-30
Yes. You'll have to share some information: which theme are you using currently?

---

### Post by Crimple on 2016-04-30
I don't have Xubuntu installed yet (I'm typing on Mate 16.04) but I already have a partition waiting for it.
I would start with the stock theme which is GreyBird.

---

### Post by Crimple on 2016-04-30
Well, Xubuntu latest up and running (snappy as usual).
Didn't change appearance settings which means GreyBird for both theme and windows manager.

---

### Post by Frogs Hair on 2016-04-30
Alternative themes can be found at the link and can be installed in usr/share/themes which requires elevated permissions or home .themes. If there is no .themes folder in home/hidden folders one can be created. As I remember you can navigate to the pictures folder from the appearance application and apply a background of your choice. 

[http://xfce-look.org](http://xfce-look.org)

---

### Post by Crimple on 2016-04-30
> **Frogs Hair said:**
> Alternative themes can be found at the link and can be installed in usr/share/themes which requires elevated permissions or home .themes. If there is no .themes folder in home/hidden folders one can be created. As I remember you can navigate to the pictures folder from the appearance application and apply a background of your choice. 

[http://xfce-look.org](http://xfce-look.org)

I went through all those themes when I was using 15.10 and none pleased me, so what I was looking for was to manually change the background colours of windows, menus etc.  and manage a consistent look across the whole OS, like in the image on my first post. You have the Theme Configuration in Settings but it's very limited as to what it can change.

---

### Post by Frogs Hair on 2016-04-30
I'm not familiar with GTK 3 CSS. I was able to modify some of the early themes , but not anymore. The theme configuration application doesn't apply changes on all themes, but does work with some.

---

### Post by Crimple on 2016-05-02
After searching the web for the last couple of days I got an idea of what's to be done but not how to do it  :confused:
I should create a folder, call it something like *New Theme* and copy the contents of Greybird's folder (usr/share/themes/Greybird) into it, this is the easy bit.
Then I should move or copy that new folder into usr/share/themes, this I don't know how to (need to use terminal I think).
Then I should edit some file inside the new folder; but which file, gtkrc under gtk-2.0 ? gtk.css under gtk-3.0 ? What about gtk-widgets (and what is that).

I'm attaching an image with the backgrounds I want to colour (but you got the idea from the first image).

[ATTACH=CONFIG]268783[/ATTACH]

---

### Post by vasa1 on 2016-05-02
> **Crimple said:**
> ...
I should create a folder, call it something like *New Theme* and copy the contents of Greybird's folder (usr/share/themes/Greybird) into it, this is the easy bit.
Then I should move or copy that new folder into usr/share/themes, this I don't know how to (need to use terminal I think).
Then I should edit some file inside the new folder; but which file, gtkrc under gtk-2.0 ? gtk.css under gtk-3.0 ? What about gtk-widgets (and what is that).
...

...
First, you can also create *~/.themes* and move your Greybird copy there rather than to */usr/share/themes*. Having it in the former location makes it easier to edit and the changes will affect only your particular user account. In the latter location, you'll need *sudo/gksudo/pkexec* or whatever.

Second, you need to know that some applications use the gtk2 toolkit. Others use the gtk3 toolkit. Even others use something else (qt4 or qt5, for example).

A "complete" gtk theme would try to keep visual consistency between gtk2 and gtk3 applications.

An example of a gtk2 application in Xubuntu 16.04 is Thunar (I think). Evince, Mousepad, Firefox 46, and LibreOffice are gtk3.

The gtk-widgets.css file clearly explains what's what. Loosely speaking, the UI (in gtk3) is made up of widgets: scrollbars, sliders, buttons, checkboxes, etc.

---

### Post by Crimple on 2016-05-02
Moving my Greybird to /.themes didn't work but I managed to put it in usr/share/themes/ with the terminal.
So far so good, but ... after hours playing with color codes I simply couldn't decide on a scheme... this is going to take a lot of time, but at least I think I know my way around,

thanks a lot vasa1 and Frogs Hair

---

### Post by vasa1 on 2016-05-04
Here's something that may interest you!

[http://www.webupd8.org/2016/05/easily-create-your-own-numix-based-gtk.html](http://www.webupd8.org/2016/05/easily-create-your-own-numix-based-gtk.html)

and

[https://github.com/actionless/oomox](https://github.com/actionless/oomox)

Caution: it involves installing a third-part application; such applications *may* be risky. Of course, the code is available for inspection and assessment by people who know about these things.

*** There are quite a few names from the Xubuntu team among the major code contributors there :)



There's a video as well: [https://www.youtube.com/watch?v=Dh5TuIYQ6jo](https://www.youtube.com/watch?v=Dh5TuIYQ6jo)

---

### Post by Crimple on 2016-05-04
That is quite a tool !!  Exactly what I was looking for, and it has a lot of preset themes as well.
Thanks a lot Vasa1  :)

---

### Post by vasa1 on 2016-05-04
Welcome! Keep us posted on how things go. The impression I get is that your starting point has to be Numix.

---

### Post by Crimple on 2016-05-04
> **vasa1 said:**
> The impression I get is that your starting point has to be Numix.

Not necessarily.

You pick any of the preset themes and "clone" it (you create a new preset just like the original so as to preserve the original intact).
Then you name it something like *Numix_custom* and tweak it.
Then you "save" and "export" it, and now it will show in your Appearance/Style (or Tweak Tool or whatever).
You can go back and tweak it again and again, just remember to save and export each time.

There's a learning curve and it's not an easy install, but it is a very powerful theming toll; it should be in the repositories.

---

### Post by vasa1 on 2016-05-04
> **Crimple said:**
> Not necessarily.

You pick any of the preset themes ...
Yes, but aren't the preset themes tweaked variants of Numix? In other words, could you tweak Greybird using this tool?

I have a post on the Numix theme in 16.04 here: [http://ubuntuforums.org/showthread.php?t=2322710](http://ubuntuforums.org/showthread.php?t=2322710)

---

### Post by Crimple on 2016-05-04
> **vasa1 said:**
> Yes, but aren't the preset themes tweaked variants of Numix? In other words, could you tweak Greybird using this tool?

I see what you mean.
No, you can't tweak Greybird. And you may be right about the presets being Numix variants.

---

### Post by Crimple on 2016-05-04
This is what I've managed, a soft blueish theme with Faience Azur icons.

[ATTACH=CONFIG]268836[/ATTACH]

---

### Post by vasa1 on 2016-05-04
Nice!

In case you don't know, you can easily have specific themes for specific gtk3 apps!

```
GTK_THEME=Greybird evince
```
will launch *evince* with the Greybird theme and
```
GTK_THEME=Numix mousepad
```
will launch *mousepad* with the Numix theme.

---

### Post by Crimple on 2016-05-04
Thanks.

---

