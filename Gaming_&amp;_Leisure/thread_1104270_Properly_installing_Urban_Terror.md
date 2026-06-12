---
title: "Properly installing Urban Terror"
date: 2009-03-23
forum: Gaming &amp; Leisure
---

### Post by Jameshardy88 on 2009-03-23
Hi yesterday i downloaded Urban terror (zip file for linux/mac) tried the game inside and i love it works fine with apparently no problems. What i want to know is how can i properly install it onto my system (so that it is inside the filesystem, will have its own icon and can be added to the menu etc?).

Thanks for any help

---

### Post by rizzeh on 2009-03-23
For "proper" install the game should be in /usr/local/games and executable linked to /usr/local/bin.

---

### Post by Jameshardy88 on 2009-03-23
sorry im a bit confused what do you mean by this exactly?

---

### Post by Chemical Imbalance on 2009-03-23
Having the file in your home folder is perfectly fine--I've been using it like that for two years.

Your home folder *is* in the filesystem.

If you want a menu shortcut, just right click on your menu button on the panel and choose "edit menus" and point it to your launcher

/usr/local/games is another common place to put it as the OP mentioned, but it really doesn't matter

---

### Post by rizzeh on 2009-03-23
you'll need to extract the archive, move it to /usr/local/games and then create a symbolic link to the file that launches the game in folder /usr/local/bin.
Once this done you can go about creating shortcuts in your menu or where you want it.
This is how to install games "properly".
 
Not that you HAVE to do it. You could just happily unzip Urban Terror in you home folder and run it from there. The downside is - only you and no other user on your machine will be able to play it.

---

### Post by Chemical Imbalance on 2009-03-23
> **rizzeh said:**
> The downside is - only you and no other user on your machine will be able to play it.

Yep that's pretty much the only reason to put it there, so unless you are sharing your computer you'll be fine

Oh and you can make shortcuts in your menu just fine from your home folder

---

### Post by Jameshardy88 on 2009-03-23
I know this is going to sound incredibly anal but how do you assign a default icon to an application? or is that something abit technical?

---

### Post by rizzeh on 2009-03-23
Google is you friend, use it..

[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

---

### Post by Jameshardy88 on 2009-03-23
Sorry i didn't mean for an individual case i meant broadly for the application in general, so every copy of Urban Terror would have it (again sorry im abit of a freak like that lol)

---

### Post by Chemical Imbalance on 2009-03-23
What do you mean by "every copy"?

---

### Post by Jameshardy88 on 2009-03-23
basically in the same way that say firefox or amarok have their own icons (which when the icon theme is changed are liable to change) that are consistent across each copy of it. Sorry if thats still a little unclear

---

### Post by rizzeh on 2009-03-23
i'm not sure if i fully understand what you mean. if you want to change the icon of a file type?  Try Right-click on the file in question -> properties -> click on the icon image in properties tab -> select custom icon.

---

### Post by Chemical Imbalance on 2009-03-23
> **Jameshardy88 said:**
> basically in the same way that say firefox or amarok have their own icons (which when the icon theme is changed are liable to change) that are consistent across each copy of it. Sorry if thats still a little unclear

Since Urban Terror doesn't have any inclusions in any icon theme I know of, just specify the icons included with the game (in the q3ut4 folder in your UrbanTerror directory) when you need to make shortcuts on your desktop or menu.

This one: [ATTACH]107419[/ATTACH]

---

