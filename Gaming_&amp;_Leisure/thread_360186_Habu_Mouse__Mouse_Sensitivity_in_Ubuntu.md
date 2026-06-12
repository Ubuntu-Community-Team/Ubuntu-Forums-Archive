---
title: "Habu Mouse / Mouse Sensitivity in Ubuntu"
date: 2007-02-12
forum: Gaming &amp; Leisure
---

### Post by andy- on 2007-02-12
Been trying to get rid of all the acceleration in desktop / quake games and get that 'windows' feel of a precise mouse. 

    Came across a few walk-throughs, a few shortcuts as well like the "xset m 1 1" and "xset m 1 1 / 0 0" but that only makes the mouse stable in X, does nothing for games, and it's annoying to do that every time I reboot, relog, I've also went into 'System->Prefrences->Mouse' lowered the Acceleration bar all the way down, and maxed out the Sensitivity bar all the way up. This gives me a stable zero accel feeling, but makes the mouse very slow, usable, but slow. Mouse is on 2000-dpi with those settings too, and its still slow.

    Then I came across a utility from Razor called 'razortool'. Getting issues installing that as well, it's telling me "Error: Dependency is not satisfiable: libc6" no clue what to do with that either. 

     If anyone know a permanant fix please share, alott of gamers are switching to linux, and this is a very annoying issue to get used too. 90% of games is precision of a mouse, and we need a fix for the useless default acceleration. 

Help!

Thanks alott in advance. :)

---

### Post by Inhumane on 2007-02-13
> **andy- said:**
> Been trying to get rid of all the acceleration in desktop / quake games and get that 'windows' feel of a precise mouse. 

    Came across a few walk-throughs, a few shortcuts as well like the "xset m 1 1" and "xset m 1 1 / 0 0" but that only makes the mouse stable in X, does nothing for games, and it's annoying to do that every time I reboot, relog, I've also went into 'System->Prefrences->Mouse' lowered the Acceleration bar all the way down, and maxed out the Sensitivity bar all the way up. This gives me a stable zero accel feeling, but makes the mouse very slow, usable, but slow. Mouse is on 2000-dpi with those settings too, and its still slow.

    Then I came across a utility from Razor called 'razortool'. Getting issues installing that as well, it's telling me "Error: Dependency is not satisfiable: libc6" no clue what to do with that either. 

     If anyone know a permanant fix please share, alott of gamers are switching to linux, and this is a very annoying issue to get used too. 90% of games is precision of a mouse, and we need a fix for the useless default acceleration. 

Help!

Thanks alott in advance. :)

You should probably post it in the hardware/sofware section, just because it's a gaming mouse doesn't mean it should be in the gaming forum :lolflag: 

Try going to System->Preferences->Mouse and set the sensetivity there.

Also, for that libc6 error, try doing ```
sudo aptitude install libc6
```

---

### Post by andy- on 2007-02-13
Allright, thx, and that libc6 is apparantly installed, razortool just says its a wrong vesion. Doesn't make any sence. I'll poke around some more, thx again.

---

### Post by Inhumane on 2007-02-13
> **andy- said:**
> Allright, thx, and that libc6 is apparantly installed, razortool just says its a wrong vesion. Doesn't make any sence. I'll poke around some more, thx again.

What's the exact error messege?
Also try sudo aptitude install libc6-dev

---

### Post by andy- on 2007-02-16
> **Inhumane said:**
> What's the exact error messege?
Also try sudo aptitude install libc6-dev

Error: Dependency is not satisfiable: libc6

and sudo aptitiude install libc6-dev doens't do anything: 

```
andy@home:~$ sudo aptitude install libc6-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
andy@home:~$ sudo aptitude install libc6
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
andy@home:~$ 
```

=\

oh, AND: ```
andy@home:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andy@home:~$ 
```

So.. downgrade maybe? I don't know.

---

### Post by daimaru on 2007-05-31
@andy
hey thx after reading your thread i installed razertool from [sourceforge.net ]("http://sourceforge.net/project/showfiles.php?group_id=166890") 
downloaded these packages  	
razertool-gtk_0.0.7-1_i386.deb   -- graphical interface
and 
razertool_0.0.7-1_i386.deb --comandline.
installed it with gdebi --> graphical .deb file installer (didnt even know that existed till now) got no errors, but the prog works fine. had to start it with sudo though
```
sudo razertool-gtk 
```
only thing is that the tool is for controlling the Razer Copperhead(TM) mouse and i have a habu gaming mouse, but i was still able to select dpi 2000 and report rate 1000, and it actually worked \\:D/
havent tested the polling rate yet do you know of a prog for linux that does that gonna go search on google right now .

---

### Post by Cappy on 2007-05-31
I have a thread for changing your polling rate:
[http://ubuntuforums.org/showthread.php?t=392494](http://ubuntuforums.org/showthread.php?t=392494)

Try the last post before you try the "alternate solution" =P

---

