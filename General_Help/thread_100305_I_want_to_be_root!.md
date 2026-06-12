---
title: "I want to be root!"
date: 2005-12-07
forum: General Help
---

### Post by SkillZero on 2005-12-07
look, here is the problem i have and i want to get rid of it!
[IMG]http://img520.imageshack.us/img520/1046/screenshot6cq.png[/IMG]


i want to be "the owner" as it says in the picture.

---

### Post by Pablo_Escobar on 2005-12-07
Easy 
1.
> cd directory\of\the\file
2.
> sudo chown yourusername nameofthefile

And refrain yourself from using root while copying files from f.e. fat disk -> they will be copied with root as an owner.
sudo can be used for everything. :)

---

### Post by Bachstelze on 2005-12-07
or in a more "newbie-friendly" way, you can run nautilus as root (sudo nautilus) and then change the file owner as you show on the pic.

---

### Post by earobinson on 2005-12-07
If you want to actualy log on as root in the log on screen check this out [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo") and before anyone starts the root debate again go here [http://www.ubuntuforums.org/showthread.php?t=98176](http://www.ubuntuforums.org/showthread.php?t=98176)

---

### Post by hedone on 2005-12-07
Or you can even add script with witch u will be able to open files as root from right mouse click! 

Just do: ```
gedit $HOME/.gnome2/nautilus-scripts/Open\ root
``` 

put this in:```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done
```and save this file!

now just start this script by:```
chmod +x $HOME/.gnome2/nautilus-scripts/Open\ root
```now u have "Open root" in right mice menu as "Scripts"!

---

### Post by Bachstelze on 2005-12-07
Cheers for this hedone :)

---

### Post by hedone on 2005-12-07
Thanx and by the way: did u make to install fglrx on your laptop??? u do have igp radeon 9000, don't u?

---

### Post by SkillZero on 2005-12-07
well tnx guys..i guess... lol
i fucked my linux =]
when i extracted the file it replaced it with my usr folder instead of adding the files in the zip to it =\
im after a format
im not gonna try to be root again :)

---

### Post by sooqing on 2005-12-07
if u want to login as root, do an expert install and it will setup it for u..  :)

---

### Post by hedone on 2005-12-07
why dont u just make new user for your self???

---

### Post by hedone on 2005-12-07
[QUOTE=sooqing]if u want to login as root, do an expert install and it will setup it for u..  :)[/QUOTE]
great one!!!!!! :D

---

### Post by Bachstelze on 2005-12-07
Yes I have an IGP Radeon 9100 and I installed fglrx, it worked just fine.

---

