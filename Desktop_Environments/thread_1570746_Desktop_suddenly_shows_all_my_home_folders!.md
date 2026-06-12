---
title: "Desktop suddenly shows all my home folders!"
date: 2010-09-08
forum: Desktop Environments
---

### Post by the.scarecrow on 2010-09-08
I have never seen anything like this before. Starting up today my usually completely free of clutter desktop is showing all of my home directory folders!

If I delete folders from the desktop, they are also deleted from my home directory. If I create a new home directory folder, it also appears on my desktop. In effect my desktop has become my home directory and I don't like it.

Please help, how do I get my empty desktop back?

---

### Post by TwelveGauge on 2010-09-08
Did you do any work with moving files and/or directories in the terminal recently?

what does:
```
cd /home
ls -a
```
output?

---

### Post by the.scarecrow on 2010-09-08
> name@name-laptop:~$ cd /home
name@name-laptop:/home$ dir
name
name@name-laptop:/home$ ls -a
.  ..  name
name@name-laptop:/home$ 

I don't think I did anything likely to cause this yesterday.

name = my home directory that contains all my top level folders like Documents, Downloads, Music etc.

---

### Post by the.scarecrow on 2010-09-08
The problem seems to be visible in Nautilus, my home directory in the list on the left under Places has disappeared. Leaving Desktop at the top of the list. Likewise Desktop has disappeared from my home directory...how odd is that? Looks like finger trouble but I have no idea how I did it and don't know yet how to restore it to normal.

---

### Post by the.scarecrow on 2010-09-08
Yep..

The problem is that the special folder "Desktop" has disappeared from my home directory. Anyone know the correct way to get it back?

---

### Post by 3Miro on 2010-09-08
You should be able to just create a new folder called Desktop, however, this will not have any shortcuts that you may have had before. To restore all the shortcuts, you will have to see what happened to Desktop in the first place (if it got wiped out somehow, it may not be possible to restore).

If this doesn't help, you will have to look at gconf-editor (hit Alt + F2 and type gconf-editor), then I think the folder shown is listed under apps -> prefs -> nautilus. I might be wrong, unfortunately there is no way for me to look at it right now.

---

### Post by the.scarecrow on 2010-09-09
> **3Miro said:**
> You should be able to just create a new folder called Desktop, however, this will not have any shortcuts that you may have had before. To restore all the shortcuts, you will have to see what happened to Desktop in the first place (if it got wiped out somehow, it may not be possible to restore).

If this doesn't help, you will have to look at gconf-editor (hit Alt + F2 and type gconf-editor), then I think the folder shown is listed under apps -> prefs -> nautilus. I might be wrong, unfortunately there is no way for me to look at it right now.

Thanks 3Miro, I have checked prefs>Nautilus Make Desktop Home folder already and it is not checked.

Adding a Desktop folder to the home directory I doubt will solve much. To return to normal my home directory needs to be back on the Nautilus side panel above the Desktop folder, and the contents of the Desktop folder need to be moved into my home directory along with the "empty" Desktop at the same level.

I am thinking that I need to:-
1 copy my entire home directory to my windows partition
2 create a temporary super user
3 delete my existing user completely
4 create another super user with my existing user name
5 copy everything back from the windows directory to my re-created username
6 delete the temporary super user

Incredibly tedious to do but relatively safe as I should not run into file ownership issues and I will have a complete backup if anything goes wrong at any stage.

---

