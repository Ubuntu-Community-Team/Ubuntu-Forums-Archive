---
title: "Compiz in 7.04"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by T3KN33K on 2007-09-20
Few questions regarding the default version of Compiz installed in Feisty....

1) Is a way to "zoom out" the compiz cube when rotating? ...as in, when I press alt+super and click to drag the cube, the cube is smaller, effectively showing more of the skybox while doing so.

2) Is there a way I can make the positioning of the cube cap static, so as to NOT dynamically rotate as i spin the cube?

3) For the 3D options...  is there a way I can make the windows "pop" further from the cube than they do by default?

Thanks.

-T3KN33K

---

### Post by Happy_Man on 2007-09-20
I believe that at least one of those settings is in the package "gnome-compiz-manager". Install it with: ```
sudo apt-get install gnome-compiz-manager
```

---

### Post by Nulifier on 2007-09-20
You will need to install some more packages namely compizconfig-settings-manger
The difference between it and the gnome package I don't know but this one sounded more complete

I do not know how to open this program you will have to figure that out for yourself.

1. Under this menu go to Rotate Cube
    The setting you want is Zoom (near the bottom)

2. Mine doesnt rotate but you should be able to find a setting for this

3. The option you are looking for is 3d Windows

If this doesn't work for you don't fret as I am using compiz fusion (the options should be the same) The only problem is that the default Ubuntu effects doesn't give you a method of adjusting them

---

### Post by T3KN33K on 2007-09-20
I have already downloaded the compiz-settings manager, but I see no mention of any of these 3 issues.. :(

-T3KN33K

---

### Post by Nulifier on 2007-09-20
Does it have a list of settings as icons?

Do these settings have any effect on your desktop?

Yet again I am running gutsy with fusion (git)

---

### Post by T3KN33K on 2007-09-20
yes, and yes.  it seems to have most of the functionality as using gconf does, but as with an easy-to-use GUI.  But, I do not see anything of relevance to those three items.  Not big deals, by any stretch of the imagination, but it would be nice if there were, in fact, a way to control them.  

Thanks

-T3KN33K

---

### Post by Happy_Man on 2007-09-20
Yeah, I didn't think they were in there, just as a wild throw. :(

I believe you will have to find a way to get compizconfig-settings-manager, like the poster above said. Perhaps try Trevino's repos?

---

### Post by T3KN33K on 2007-09-20
> **Nulifier said:**
> You will need to install some more packages namely compizconfig-settings-manger
The difference between it and the gnome package I don't know but this one sounded more complete

I do not know how to open this program you will have to figure that out for yourself.

1. Under this menu go to Rotate Cube
    The setting you want is Zoom (near the bottom)

2. Mine doesnt rotate but you should be able to find a setting for this

3. The option you are looking for is 3d Windows

If this doesn't work for you don't fret as I am using compiz fusion (the options should be the same) The only problem is that the default Ubuntu effects doesn't give you a method of adjusting them

Sorry, I actually somehow missed this post.  I have seen mention (through googling the issue) of being able to zoom, but all are in reference to Compiz Fusion, and I assumed that they may not apply.  In either case, I will take your suggestion and try to find compizconfig-settings-manager. 

Thanks.

-T3KN33K

---

### Post by Happy_Man on 2007-09-20
> **T3KN33K said:**
> Sorry, I actually somehow missed this post.  I have seen mention (through googling the issue) of being able to zoom, but all are in reference to Compiz Fusion, and I assumed that they may not apply.  In either case, I will take your suggestion and try to find compizconfig-settings-manager. 

Thanks.

-T3KN33K
the compizconfig package isn't available in the Ubuntu repos, you will have to add Trevino's repos to get it. Just a heads-up.

---

### Post by T3KN33K on 2007-09-20
well, I found compizconfig, in Trevino's repositories as you suggested.  I have installed it, it now shows under the menu system>preferences, but when i click on it, it does not open.  Could this be some kind of conflict between "compizconfig settings manager" and "compiz settings manager"?  If so, how would I resolve it?

-T3KN33K

---

### Post by Nulifier on 2007-09-20
uninstall the first package with synaptic or type:

sudo apt-get remove <package name>

---

### Post by Happy_Man on 2007-09-21
```
sudo apt-get remove gnome-compiz-manager
```

---

