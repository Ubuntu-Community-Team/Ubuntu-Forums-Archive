---
title: "Get back default panel"
date: 2010-03-09
forum: Desktop Environments
---

### Post by sinurge on 2010-03-09
Very n00b question. Am running lucid alpha 3 and while just checking it out i deleted the group icon which looks like a msg on the top right bar (the one that grouped the empathy and gwiber account)
 
Have tried multiple ways but its getting to the older setting
 
do i have to reset the panels to their defaults to get it corrected or is there any other way

---

### Post by d3v1150m471c on 2010-03-09
If you open your home folder and delete .gconf and .gconfd it will completely restore gnome to it's default settings and then recreate the files after you log back in. It will restore more than just a panel though but it won't delete any applications and what not.

---

### Post by practic on 2010-03-09
Have you tried just adding the "Indicator Applet" back to the panel? That's the one that handles Evolution/Empathy/Gwibber...

---

### Post by hhh on 2010-03-09
Try practic's advice first, but to reset your panels to their defaults without resetting anything else, see this post...
[http://ubuntuforums.org/showpost.php?p=8931869&postcount=4](http://ubuntuforums.org/showpost.php?p=8931869&postcount=4)

---

### Post by NicMagic on 2010-05-05
Hi All,

I found the perfect solution for this issue..

open terminal and type the following
```
gconftool --recursive-unset /apps/panel
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

after i typed in those three commands, default panels at top and bottom appeared...

I followed instructions here [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html")
So kudos has to go to thos guys...
:)

---

