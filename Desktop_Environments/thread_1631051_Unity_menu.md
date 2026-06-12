---
title: "Unity menu"
date: 2010-11-26
forum: Desktop Environments
---

### Post by PouncingAnt on 2010-11-26
I've just updated to UNR 10.10, very pretty, but I can't access openoffice without going through the terminal..

Clicking on the ubuntu icon in the top left brings me a sparse menu with "web" "office" etc. written on it. clicking on web will open google chrome, but clicking on office does nothing...

Is there any way to edit this? Basically all of the programs I want to use are hidden.

I dont want to revert to GNOME unless necessary, but equally don't want to use the terminal to open everything (v. cramped keyboard makes my fingers ache, lol). Am I stuffed? Or is there a way to fix this?

Many thanks,

Chris

---

### Post by Peter09 on 2010-11-26
click on the grey icon which looks like a pair of scissors. In the search bar type open office, which should give you the icons for open office. Start open office from the icon.
 
Once running you should see the icon in the dock. Right click and selct the option to keep the icon in the dock.

---

### Post by PouncingAnt on 2010-11-26
I dont see anything that looks like a pair of scissors anywhere, however I've tried the search functionality in the main menu, and after typing in open office it doesn't show anything

EDIT: This could be due to some troubles during install. I had to do the partial upgrade because it borked first time round (or rather, I borked it)

---

### Post by PouncingAnt on 2010-11-27
Still no progress with this. In the meantime I have tried everything I can think of. I'll continue googling for now, but if anyone knows a quick solution, please post it

---

### Post by PouncingAnt on 2010-11-27
As you might imagine, no amount of keyboard bashing is going to make a menu display correctly when it hasn't been installed properly. I fixed this by 
```
apt-get remove unity ubuntu-netbook
```
then using the recovery mode, used dpkg to repair broken packages then used:
```
apt-get install unity ubuntu-netbook
```

That'll teach me to interrupt an upgrade :oops:

btw, I really like the new interface.

---

### Post by whistlerspa on 2010-11-27
I really don't like the new Unity interface so far, and read with great dismay that it is to be the default in future Ububtu incarnations. 

I find it a pain to have to keep clicking on buttons which take up a lot of desktop space down the LHS of the desktop to find things,(especially on a 10" netbook) and then only be able to see one app or window at a time. On my netbook there is also a time lag of about 3 seconds before anything happens.
 
It's also frustrating that file management can't be undertaken when I open the files menu until I do an extra click on a file icon at the top right and want to copy or paste say between folders, which is made more difficult by only being able to have a single window in a single workspace. I also prefer my applications in sorted drop down menus rather than the solid mass of 'Applications' as in Unity. All in all I think that Unity is a retrograde and faddish desktop interface. I guess it's emulating cell phone menus but I don't want my computer desktops to look like cellphones.

---

