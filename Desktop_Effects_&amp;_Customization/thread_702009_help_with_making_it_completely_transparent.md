---
title: "help with making it completely transparent"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by bloodhacker2 on 2008-02-19
hey guys.
what i am looking to do is make conky completely transparent, that means the borders to. i am also looking to do this very same thing in the terminal.
i have got in the window transparent but i want to remove the borders.
i am in gnome using compiz.
i was wanting it to look sum thing like this. (look at the top left corner at the conky..)
[IMG]http://www.imgx.org/pthumbs/large/2489/exoduz_fluxbox.jpg[/IMG]

---

### Post by bloodhacker2 on 2008-02-19
still looking for help!!

---

### Post by tedt on 2008-02-20
You might want to look at  [DevilsPie]("http://live.gnome.org/DevilsPie")


This might  [work]("http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop")

---

### Post by DaymItzJack on 2008-02-20
Go to your compiz fusion manager, go to the "Window Deciratuins" plugin, and for "decoration windows" add:

any & !title=Conky

(I'm guessing the title name is conky. Try saving that and see what happens.

---

### Post by Nythain on 2008-02-20
conky is an easy one... somewhere in the conkyrc file, there's options for borders, thier widths, how they look, etc... just tell it not to have borders... as for making it transparent, thats covered towards the top of the conkyrc usually, something like
```

own_window yes
own_window_transparent yes
own_window_type override
#own_window_type default
#own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```
and further down, to handle the borders
```

# Draw borders around text
draw_borders no

```
i believe that would do the trick... no need to involve compiz with conky at all... now the terminal is a different story, and with compiz/gnome-terminal its gonna require a little work.

im not at home, so i cant tell you exactly where these options are in the compizconfig-settingsmanager, otherwise known as ccsm...
first, you have to make sure that your terminal has a title thats pretty unique... this can be achieved by creating a new profile and giving the profile a unique name, then in that profiles settings, make the background transparent, make sure to disable scrollbars, etc, and make sure it ignores new titles set by applications... give it a unique title, usually the profile name... and save that profile

then, in the ccsm there's a couple places that control decorations of windows with specific titles... as mentioned above in the conky suggestion actually, just add whatever teh unique title was instead of conky so it looks like
any & !title=uniquetitlehere
on all the different decorations... from here you can even have it stay under everything, make it non minimizable, etc...

hope that at least helped a little, wish i could help more, but im at work, so windows for me... now you can forum search for Desktop Terminal and ignore any of the devilspie methods, find one that mentions ccsm and try to follow that a little better than i have described here

---

