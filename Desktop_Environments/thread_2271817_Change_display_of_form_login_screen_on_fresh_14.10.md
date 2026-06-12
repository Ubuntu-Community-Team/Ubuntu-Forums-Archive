---
title: "Change display of form login screen on fresh 14.10 install"
date: 2015-04-01
forum: Desktop Environments
---

### Post by GODARD_Ludovic on 2015-04-01
Hi all, 


i've just installed Lubuntu 14.10 on my Asus eeepc 1015bx and it work great (really great :) )
But, because it must be having a but, the login screen feel me sick..

i've changed the wallpaper but the "white" or "Lightgrey" of the form login/password stay displayed.

Someone could help me to change color, change look or reduce opacity of this form ?

By default the manager is lightdm but they are many many conf files and anywhere i put somes instruction don't work :(

Well, i hope i was "clear" on my explain..

Thanks in advance.

Ludo.

---

### Post by kunitoki2 on 2015-04-06
Edit etc/xdg/lubuntu/lightdm/lightdm-gtk-greeter.conf as you wish
it's a text file (instructions slash comments are included)
to get rid of the white grey default login theme you have to change the line that starts with theme-name
the names of the other themes you have installed including a preview can be seen via customize look and feel (start menu)
if you want a really dark login theme there's no theme by default that matches that wish
but you can install the zorin theme which is really dark and nice looking for example
of course the web is full of other nice themes

---

### Post by GODARD_Ludovic on 2015-04-10
thanks, i'll try that this week-end.

---

### Post by kunitoki2 on 2015-04-11
i uploaded the zorin theme just in case you can't find it anywhere: [http://qed.bplaced.de/misc/zorin.zip](http://qed.bplaced.de/misc/zorin.zip)
this zip contains a folder which you have to extract into this folder: usr/share/themes
there should be a lot of theme folders in there - and now a new one called ZorinDark-8
now edit the aforementioned config text file and replace the line that starts with
theme-name=...
with
theme-name=ZorinDark-8
now you should have a nice dark login gui just like i do :)

---

### Post by GODARD_Ludovic on 2015-04-11
Really thanks it's better now :)

---

