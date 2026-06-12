---
title: "Creating desktop starter?"
date: 2006-01-19
forum: Gaming &amp; Leisure
---

### Post by Garyu on 2006-01-19
I wanted to create a desktop starter shortcut to start Neverwinter Nights. I have installed the game in my home folder and it's running smoothly without any kinds of problems when I type "nwn" in the program folder (thank you bioware for an easy installation procedure!).

When I right-click the desktop and choose "Create starter" I first tried typing this in Command:
sh /home/dan-erik/NwN/nwn.sh
...but that didn't work, so I tried changing it to
/home/dan-erik/NwN/nwn
...but that didn't work either... any tips?

Rather annoying that I don't get an error dialog. Nothing happens. At all.

EDIT/ADD: oh, and also... anyone know of a good NwN-icon to use? Right now I use the one for gmush, but it just doesn't seem right...

---

### Post by Sutekh on 2006-01-19
Usually when a program is installed (don't know about NWN though), it can be run by invoking the name of the executable... try simply 'nwn'.

As for an icon, try this one
[http://thilockdominus.freehomepage.com/download/NWN.png]("http://thilockdominus.freehomepage.com/download/NWN.png")

---

### Post by Perfect Storm on 2006-01-19
You need a script:

> 
#!/bin/bash

cd /home/<username>/.games/nwn
sh /home/<username>/.games/nwn/nwn


remember to **chmod +x** the script file. Usually I put the script file in the same directory as nwn. Make a launcher to the script you made. [b]sh /home/<username>/blah/blah/blah/scriptfile.sh


ah, remember that linux is case sensitive.


@Sutekh

Are you leeching from my homepage ^^

---

### Post by Sutekh on 2006-01-19
[QUOTE=Artificial Intelligence]
@Sutekh

Are you leeching from my homepage ^^[/QUOTE]
:oops:  um no...  :oops: 

Got that from your Dec05 desktop
[http://ubuntuforums.org/gallery/showimage.php?i=1601&catid=searchresults&searchid=5923]("http://ubuntuforums.org/gallery/showimage.php?i=1601&catid=searchresults&searchid=5923")

---

### Post by Perfect Storm on 2006-01-19
s'okay, I'm just fooling around ^^

---

### Post by Sutekh on 2006-01-19
Nary a problem!  But it is a good icon :)

---

### Post by Garyu on 2006-01-20
[QUOTE=Artificial Intelligence]
remember to **chmod +x** the script file. Usually I put the script file in the same directory as nwn. Make a launcher to the script you made. [b]sh /home/<username>/blah/blah/blah/scriptfile.sh
[/QUOTE]

Thank you very much, that did the trick. :)
Although, I actually forgot to chmod the script, but it started anyways. =P

oh, and thank you for the icon, it's great. =)

---

