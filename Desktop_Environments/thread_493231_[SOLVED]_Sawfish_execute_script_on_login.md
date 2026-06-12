---
title: "[SOLVED] Sawfish: execute script on login"
date: 2007-07-05
forum: Desktop Environments
---

### Post by x1a4 on 2007-07-05
Hi,

Does anybody know where I can tell SawfishWM to execute a script when I log in?  Thank you.

---

### Post by x1a4 on 2007-09-14
Anyone?

---

### Post by BLTicklemonster on 2007-10-26
Hmmmm. This is troubling. I've discovered sawfish, and am wondering how to set things up in it. I find ~./sawfish, but there's a file in there that says not to edit it. Help on sawfish's site is typically "How to levitate: float above the ground" if you know what I mean.

Anyone else out there ever run sawfish and have any help?

---

### Post by D-EJ915 on 2007-10-27
if you click on the root ("desktop") a menu should pop up which has a "customize" menu on it.  Just go through there and mess around, it should work.

And to get the menu for apps to work correctly type "update-menus" in a terminal then restart sawfish and it should have all your programs now.

To "execute a script" you could modify the sawfish.desktop to execute an executable file which executes sawfish as well as some other things.

you could have like "sawfish-script" wherever (you just have to tell the Exec="/location/./sawfish-script")   The ./ is important.

Yeah...have any questions just im me.  [herer](http://img.photobucket.com/albums/v104/enthauptet/bin/sawfish3.jpg) is my setup on my desktop with the "Titanium" theme, I think it's in sawfish-themes in the repository.

---

### Post by x1a4 on 2007-12-30
Here's how to do it:  

in ~/.sawfishrc add the following: 

```
(system "/path/to/script")
```

It's also a good idea to add

```
(require 'sawmill-defaults)
```

as the presence of ~/.sawfishrc skipps loading of Sawfish's defaults and this will load them.

---

