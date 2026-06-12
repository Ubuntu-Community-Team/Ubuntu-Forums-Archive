---
title: "Dual Screens + Compiz + Moving Windows"
date: 2010-04-09
forum: Desktop Environments
---

### Post by Tanner2007 on 2010-04-09
I have compiz working great, along with dual screens of my desktop

but there is a problem I cant move a windows, for example firefox from one to the other just goes off screen like as if there is only one screen

How could I fix this

thanks in advance

---

### Post by Tanner2007 on 2010-04-10
BUMP, anyone this is driving me crazy

---

### Post by hariks0 on 2010-04-10
Did you try Window management > Extra WM actions > Move window to next output in CCSM? Also try the Multi output mode under Expo plugin.:popcorn:

---

### Post by Tanner2007 on 2010-04-10
> **hariks0 said:**
> Did you try Window management > Extra WM actions > Move window to next output in CCSM? Also try the Multi output mode under Expo plugin.:popcorn:

Nope nothing.......

the screens are positioned like this

screen 1 screen 2

screen = primary

now when i click on a  program or windows to try to drag it to the other screen nothing happens except the windows acts like there is only one screen

the mouse can move to the other screen i can even create another folder...but also wierd anything i do on screen 1 like create a new folder, cannot be moved into screen 2. heres a pic to kinda show what i mean

[[IMG]http://img191.imageshack.us/img191/5015/20100410132006.th.jpg[/IMG]](http://img191.imageshack.us/i/20100410132006.jpg/)

---

### Post by sigmarhophi on 2010-04-10
Ok, there are several ways you can go about fixing this.  The easest is to setup your two screens as a "big desktop" and you can move windows around all day with out any issues.  Simply change your resolution to the max size of both your monitors added together.  Most likely you can set the resolution through your manufactures front end.  I use ATI and their catalyst app works fine.

Most likely what is happening right now is each monitor is displaying one "work space" so apps will not nativaly move.

The othe ways is to set the config with in X.  requires understanding how to configure X.

---

### Post by Tanner2007 on 2010-04-11
> **sigmarhophi said:**
> Ok, there are several ways you can go about fixing this.  The easest is to setup your two screens as a "big desktop" and you can move windows around all day with out any issues.  Simply change your resolution to the max size of both your monitors added together.  Most likely you can set the resolution through your manufactures front end.  I use ATI and their catalyst app works fine.

Most likely what is happening right now is each monitor is displaying one "work space" so apps will not nativaly move.

The othe ways is to set the config with in X.  requires understanding how to configure X.

Well screen 1 is 1280 x1024 while screen 2 max is 1024 x756

sorry if i typed the wrong digits but u get my point 

it worked before...after i took one screen out since i moved it to new location came back hooked it up try to set it up same way i did before but nothing

---

### Post by naurus on 2010-08-13
Could it be that you've got two seperate X sessions running in each and don't have xinerama activated?  Just a guess.

---

