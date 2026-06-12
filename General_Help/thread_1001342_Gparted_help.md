---
title: "Gparted help"
date: 2008-12-03
forum: General Help
---

### Post by wissemeier05 on 2008-12-03
Good Evening,

I am trying to 'nuke' my hard drive and re-install 8.04 on a larger partition than before and make the rest a storage partition.

I made a "live" gparted CD as shown here :
[http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

But I am not getting to the main screen it hangs after I hit enter on the opening screen.

[IMG]http://img241.imageshack.us/img241/7355/image005qo3.jpg[/IMG]
[IMG]http://img383.imageshack.us/img383/1166/image004vi5.jpg[/IMG]

What do I need to do to make this work?

TIA

Dan

---

### Post by adult swim on 2008-12-03
im not sure about the gparted live error but if you have an ubuntu liveCD you can launch gparted from there.  just boot the cd to the live desktop and then go to system>administration>partition editor.
nice choice of beer :)

---

### Post by wissemeier05 on 2008-12-03
Good Idea!

Next Question, Is there a walk through on how to use the Gparted software in normal Ubuntu.  I have searched but I have net seen anything convincing.  I get pretty leary when it comes to screwing with hard drives I allready backed up on my external.


Warsteiner Dunkle makes a good evening better:D

Thanks,
Dan

---

### Post by adult swim on 2008-12-03
this guide seems pretty straight forward, it even has pictures.
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
i cant recall but if gparted wont let you make changes when opening it from the menu, you may need to run ```
gksudo gparted
``` from a terminal to launch it with administrative priveleges.

---

### Post by wissemeier05 on 2008-12-05
Took almost 10 hrs but it worked great thanks for your help!:D

---

