---
title: "Starting GNOME Display Manager - failed"
date: 2005-12-25
forum: Desktop Environments
---

### Post by arg on 2005-12-25
hi,
Still very new at ubuntu and had just had my ubuntu system running well, till this morning when I turned her on only to find that the Display Manager has failed to load... clearly no gui means very little understanding to me :confused: 

I believe a set of updates downloaded last night using the update manager may be the cause of the problem, i notcied some were to do with the graphics and GNOME.

Any help would be great thanks,
Alan.

---

### Post by bob phillips on 2005-12-26
not sure if this helps, but when mine opens up with a text screen (and i have no idea why) i have to type the username and password in, then type
```
sudo gdm
```
this then brings up the graphical start page, i log in again and everything works fine

so it works, but not sure how to consistently get it opening up with the Gnome Desktop Manager straight away

---

### Post by Sutekh on 2005-12-26
To start the display manager, its proper to use
```
sudo /etc/init.d/gdm start
```
Next time you load up to the console try
```
sudo dpkg-reconfigure gdm
```

---

### Post by arg on 2005-12-26
Thanks heaps for the ideas... Unlucky for me neither worked :( 

sudo gdm 
asked for a password and then said
"gdm: error while loading shared libraries: /usr/lib/libgtkx11-2.0.so.0: invalid ELF header"

sudo /etc/init.d/gdm start
"* Starting GNOME Display Manager [fail]"

sudo dpkg-reconfigure gdm
"* Reloading GNOME Display Manger configuration...
* Changes will take effect when all current X sessions have ended.
invoke-re.d: initscript gdm, action "reload" failed."

Sso far no good :( I dont want to go back to a Windows system ... 

Thanks Again,
Alan.

---

### Post by Barttim69 on 2008-05-29
:(I am also having the same issue, I have tried a number of different things but no luck. :(  

So any help would be great.

---

