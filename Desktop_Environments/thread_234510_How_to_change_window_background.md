---
title: "How to change window background?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by graybark on 2006-08-11
Is there any way to change the default window background?  Mine is a blinding white that I would like to tone down a bit.  I gather this is controlled by the theme, but I don't want a whole new theme, (I did try the various themes that I seem to have already -- Low Contrast is the only one I found that seems to affect the window background, but its settings are way too low contrast).  I just want to make the background not so blinding white. Is there some way to edit the settings of my current theme?

---

### Post by goatflyer on 2006-08-11
The only true 'user' way I know of changing the look of windows and borders is to install and select themes.  Good places to look for new themes are:

[www.gnome-look.org](www.gnome-look.org) (look at GTK 2.0 themes)

[art.gnome.org](art.gnome.org)   (look at application themes)

I found a few which had more subdued application backgrounds.

The problem with editing the background colour of a window seems to be that there are more than one of them, depending on the window's state, etc.  Basically you have to create your own theme (since you don't want to overwrite your current ones).

I have not found any graphic utility that lets you edit 'any' theme, but I have found a theme (clearbox) which provides a small utility which allows you to edit many of its parameters.

Good luck and welcome to Ubuntu forum!

---

### Post by Anduu on 2006-08-11
Piece of cake...

Open File browser and Select Edit>Backgrounds and Emblems.Pick one you like or choose one of your own :)

Note this will only affect Nautilus windows but it is a start ;)

---

### Post by goatflyer on 2006-08-11
Hey wow!!!

Great tip! :D

---

### Post by chavo on 2006-08-12
You can also change the colors of a theme by editing the gtkrc file located in the themes gtk-2.0 subdirectory. GTK is actually very powerful with coloring and you can change colors of individual widgets, even change the colors in individual apps. But along with this power comes complications. This is probably why there's no GUI color editor for Gnome while there is for KDE.

The best thing to do is to make a copy of the theme first and name it whatever you want. Systemthemes are in /usr/share/themes, themes that you install are in ~/.themes. So copy it to ~/.themes then open up ~/.themes/your_theme_name/gtk-2.0/gtkrc in gedit.

Anyway I won't get too in depth here with GTK themeing as it can be complicated. Just look for the first instance of something like this ->

```

  base[NORMAL]            = "#ffffff"
```

Now change the #ffffff which is white of course, to something a little darker #efefef or whatever use the colorpicker applet if you don't know the color codes. Now save the file and go to the theme selector, open the Theme Details window and click on the Controls tab. Now choose your newly created GTK theme. 

Like I said alot of colors can be changed from this file so experiment, once you get the hang of it you can create some nice themes.

---

### Post by graybark on 2006-08-13
Thanks for the pointers.  I did find a theme with a more subdued background, but it also tones down a lot of other things that I'm not sure I like.  So I might try messing with that base[NORMAL] setting.  I had looked at that file in various themes but I wasn't sure what setting was what.  If you could help out with one more question: where might I find this colorpicker applet?

---

### Post by graybark on 2006-08-13
Oh never mind about the colorpicker, I found it (or its equivalent) in the file browser settings that let you change the background...

---

### Post by Apex-jb on 2007-07-22
> **goatflyer said:**
> The only true 'user' way I know of changing the look of windows and borders is to install and select themes.  Good places to look for new themes are:

[www.gnome-look.org](www.gnome-look.org) (look at GTK 2.0 themes)

[art.gnome.org](art.gnome.org)   (look at application themes)

I found a few which had more subdued application backgrounds.

The problem with editing the background colour of a window seems to be that there are more than one of them, depending on the window's state, etc.  Basically you have to create your own theme (since you don't want to overwrite your current ones).

I have not found any graphic utility that lets you edit 'any' theme, but I have found a theme (clearbox) which provides a small utility which allows you to edit many of its parameters.

Good luck and welcome to Ubuntu forum!Could someone tell me how I can use and install GTK 2.0 themes? Im completely new to Ubuntu and linux and I have been looking at some of those themes and they seem to be what I have been looking for. But I dont know how to use them.

---

