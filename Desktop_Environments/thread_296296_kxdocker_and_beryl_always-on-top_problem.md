---
title: "kxdocker and beryl: always-on-top problem"
date: 2006-11-09
forum: Desktop Environments
---

### Post by flapane on 2006-11-09
I installed the last kxdocker from repos.
However it's always on top of other windows, while I set up the old kxdocker without beryl to be auto-hidden.
If I set to auto-hide (SendToBackground="0")
it shows an ugly windowsed kxdocker
[IMG]http://img292.imageshack.us/img292/2074/screenshot1in6.png[/IMG]

---

### Post by kaajey on 2006-11-12
I have the same problem ->I installed kxdocker from the source and in kde(without beryl/compiz) i have an ugly black background when i move cursor on the kxdocker icons (some transparency bug, i think). In beryl is this transparency ok but there is this window decoration shown in the above pic.

---

### Post by orb9220 on 2006-11-12
Someone metioned that in your session manger to change the startup priority and have beryl load before gnome. I set mine to like 40 and all the gnome are 50. 

And sometimes my gdesklet shows up with the window decoration problem you mention and usally logging off  or reboot it goes away. 

Also sometimes my conky desktop is invisible and I have to re login to get it to show on desktop.

So it appears to be a beryl issue.

---

### Post by flapane on 2006-11-12
yes, it is for sure

---

### Post by flapane on 2006-11-13
bump

---

### Post by kowsik on 2006-11-13
I have the same problem of the 'ugly black background' whenever I take the cursor onto kxdocker. Has anyone found a cure to that?

---

### Post by flapane on 2006-11-14
it seems noone is using kxdocker with beryl O.o

---

### Post by skenliv on 2006-11-25
Shure there is, you can use the patch that is on kxdocker homepage!
[http://www.xiaprojects.com/www/prodotti/kxdocker/kxdocker114a-compiz.diff](http://www.xiaprojects.com/www/prodotti/kxdocker/kxdocker114a-compiz.diff)

Working 100% with beryl :-D

---

### Post by flapane on 2006-11-25
wow!
is there any chanche to found a packaged version?

---

### Post by panki on 2006-11-28
Excuse my ignorance... how do I install / run the diff file?

---

### Post by robt3hpirate on 2006-12-01
i have this same problem, and when not running beryl, i get this  big black box behind kxdocker. not sure if they problems are related.
edit: i used the configuration on this page and it worked! hope this helps you guys out 
[http://www.ubuntuforums.org/showthread.php?t=232128](http://www.ubuntuforums.org/showthread.php?t=232128)

---

### Post by flapane on 2006-12-10
I solved installing the 32bit version of kiba dock on my 64bit distro
it is marvellous with beryl
look here [http://www.youtube.com/watch?v=MiETvEIF-rE](http://www.youtube.com/watch?v=MiETvEIF-rE)

---

### Post by lalakis85 on 2007-03-20
[http://www.die.net/doc/linux/man/man1/patch.1.html](http://www.die.net/doc/linux/man/man1/patch.1.html)
or man patch  in terminal

---

