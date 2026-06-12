---
title: "3/4 of my desktop not displayed"
date: 2009-02-13
forum: General Help
---

### Post by Starman~ on 2009-02-13
I don't mean it's too small. It's missing 3/4 of the screen anytime I try to enable the desktop effects the only way it displays normally is to turn everything off.

Here is a picture 

[[IMG]http://img7.imageshack.us/img7/8061/screenshotvg5.th.png[/IMG]](http://img7.imageshack.us/my.php?image=screenshotvg5.png)

Worked fine, but it started after I was trying record streaming music. I uninstalled Sound record, rebooted, and get this. WTF? There really isn't any reason for it to do this. 

Anyone suggest a fix?

---

### Post by johnjohn2 on 2009-02-14
> **Starman~ said:**
> I don't mean it's too small. It's missing 3/4 of the screen anytime I try to enable the desktop effects the only way it displays normally is to turn everything off.

Here is a picture 

[[IMG]http://img7.imageshack.us/img7/8061/screenshotvg5.th.png[/IMG]](http://img7.imageshack.us/my.php?image=screenshotvg5.png)

Worked fine, but it started after I was trying record streaming music. I uninstalled Sound record, rebooted, and get this. WTF? There really isn't any reason for it to do this. 

Anyone suggest a fix?


Hey,

Sounds like the program has screwed with you xorg.conf, try this
> sudo dpkg-reconfigure xserver-xorg follow the on screen promts and then reboot.

---

### Post by Starman~ on 2009-02-14
Thank you johnjohn2 for the reply, 
I'll keep that command around for the next time (I'm pretty confident it'll screw up again).

Anyway, I have solved the problem, but am not sure which solution it was. Two things I did -


[LIST=1]
[*]Reinstalled all the compiz/gnome packages (actually I tried just the core, meta packages but it didn't do squat. Then I did all the installed packages).


[*]Second thing was in the compiz settings manager. Under "General options there is a box for entry of "output devices" wherein there is an entry "640+480+0+0" I don't even know what it does, but I deleted it.
[/LIST]


Following the actions above it worked correctly. 

I eventually end up having to go through and reload every gnome/compiz package that has anything to do with desktop. It solved, but why in the hell did my installing and removing sound recorder do any of that. Just more incompatible software.
Stuff like this is getting really old. Thank god I created a dual boot system. Ubuntu is NOT going to be my go-to OS anytime in the future, near or far. Don't look at it funny and it won't have an issue, stable my ***.

---

### Post by johnjohn2 on 2009-02-15
> **Starman~ said:**
> Thank you johnjohn2 for the reply, 
I'll keep that command around for the next time (I'm pretty confident it'll screw up again).

Anyway, I have solved the problem, but am not sure which solution it was. Two things I did -


[LIST=1]
[*]Reinstalled all the compiz/gnome packages (actually I tried just the core, meta packages but it didn't do squat. Then I did all the installed packages).


[*]Second thing was in the compiz settings manager. Under "General options there is a box for entry of "output devices" wherein there is an entry "640+480+0+0" I don't even know what it does, but I deleted it.
[/LIST]


Following the actions above it worked correctly. 

I eventually end up having to go through and reload every gnome/compiz package that has anything to do with desktop. It solved, but why in the hell did my installing and removing sound recorder do any of that. Just more incompatible software.
Stuff like this is getting really old. Thank god I created a dual boot system. Ubuntu is NOT going to be my go-to OS anytime in the future, near or far. Don't look at it funny and it won't have an issue, stable my ***.

it is free though,and alot more honest

---

### Post by Starman~ on 2009-02-15
> **johnjohn2 said:**
> it is free though,and alot more honest

Ya, I know. I can't argue that. But hey, don't tell anyone, but I've never paid for a MS OS either :popcorn:

---

### Post by johnjohn2 on 2009-02-15
> **Starman~ said:**
> Ya, I know. I can't argue that. But hey, don't tell anyone, but I've never paid for a MS OS either :popcorn:

neither did i


:P

---

