---
title: "Gnome Window Positioning"
date: 2006-06-30
forum: Desktop Environments
---

### Post by J0s3ph on 2006-06-30
Hello

Is there a way to make windows opened in Gnome remember their dimensions and positioning, or anything simmiler? I was once told about a scripting add on for Gnome which could do that but the name escapes me.

Thanks

---

### Post by bmgz on 2006-06-30
$ apt-cache search devilspie
devilspie - find windows and perform actions on them

$ sudo apt-get install devilspie
...

Visit the website here: [http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

---

### Post by thingy on 2006-06-30
Hi ya,

I've come across this question myself. I used to think that ALL X Window applications would honour the -geometry command line parameter (see below) but as GTK doesn't use XT it doesn't pay attention to the parameter unless the devs have parsed the command line themselves and made use of the value.

-geometry geometry

    The initial size and location of the window, in a format such as width x height +horz_offset +vert_offset or +horz_offset -vert_offset. Note that if you put in a negative horizontal or vertical offset, the window will be placed counting backward from the right or the bottom of the screen, respectively, instead of from the top left corner.


For example:

[-geometry widthxheight+X+Y]

xcalc -geometry 200x300+100+100

gedit -geometry 640x480-0-0

gedit -geometry 800x600

gedit -geometry +100+50


Here's a thread I came across which basically says that if the app you want to position and size doesn't honour the geometry parameter, then file a bug report about it.

[http://mail.gnome.org/archives/gnome-list/1999-March/msg01716.html](http://mail.gnome.org/archives/gnome-list/1999-March/msg01716.html)

So, for any application who's position/size you want to control, modify the properties of the gnome menu/panel item to add a -geometry parameter.

jin

---

