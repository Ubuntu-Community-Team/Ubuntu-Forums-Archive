---
title: "no Panel in Xubuntu?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by theadventuresofanidealist on 2006-08-22
my panel disappeared, and nothing happens when i go to the settings manager to try and open it.
it seems like its not loading.
im a newbie in linux so i would really appreciate some help.

---

### Post by ahaslam on 2006-08-22
Open up a terminal and try:
[B]
xfce4-panel[/B]

If it's installed & not broken, it should load.

If it works, type the same in to 'run application' & save your session upon log out.

Tony.

---

### Post by theadventuresofanidealist on 2006-08-22
that did the trick.
why didnt it load in the first place?
thats weird. i might have closed it in my last session but i dont think so.
thanks.

---

### Post by theadventuresofanidealist on 2006-08-22
now the main menu also isnt there anymore.....
im sure i didnt remove it. its weird

---

### Post by ahaslam on 2006-08-22
> **theadventuresofanidealist said:**
> now the main menu also isnt there anymore.....
im sure i didnt remove it. its weird

The main menu on the panel?
If so, it's just an aplet - right click & add (or something like that - using kde atm).

I find xfce very fragile on my laptop. Once it's all set up as desired it's fine, it's just getting it there :rolleyes: 

Have you tried a minimal kde install? If not just install kdebase and see what you think. I find it just as fast as xfce but harder to break ;)

Tony.

---

### Post by theadventuresofanidealist on 2006-08-23
i wouldnt know what to do.
im a total newbie...lol
how do i do a kde install?

---

### Post by ahaslam on 2006-08-23
I would open up a terminal and type:

[B]sudo aptitude update 
sudo aptitude install kdebase[/B]

[I]You can also search for kdebase in Synaptic but if you don't like it, it wont remove its dependencies when uninstalling, aptitude will ;)
To remove kdebase & its dependencies, type: sudo aptitude remove kdebase
[/I]
After installation, you will then be able to select a KDE session at login.

I hope that helps ;)

Tony.

[I]PS. I can't remember if aptitude is part of a standard install. If the above commands don't work, try the following first:

sudo apt-get update
sudo apt-get install aptitude

Or you can search for it in Synaptic - I don't think it has any major dependencies & who would remove this useful tool?[/I]

---

### Post by theadventuresofanidealist on 2006-08-28
it a great help.
thanks.

---

### Post by Zieher on 2006-09-15
I'm having the exact same problem. There is one difference though; the panel stops working when I close the terminal. Additionally, the panel help doc is unavailable, although the rest of the help docs are (via Alt + F1)
I am currently using XFCE4.2 updated completely from all repos just this morning... my old settings on the panel are still there (not all).
I'd like to keep xfce due to personal preference. Thanks in advance

---

### Post by Zieher on 2006-09-15
Problem resolved

[http://ubuntuforums.org/showpost.php?p=1213871&postcount=10](http://ubuntuforums.org/showpost.php?p=1213871&postcount=10)

---

### Post by krazikiwi on 2008-06-23
this thread was a great help, 
thanks

---

