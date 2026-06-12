---
title: "[SOLVED] KDE Theme manager problem..."
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by upthelum on 2007-08-11
For some reason i dont have the administrator option in my theme manager. Can someone offer a simple solution to this on kubuntu desktop?

Thanks...

---

### Post by EXCiD3 on 2007-08-11
I noticed i have the exact same problem when trying to change the KDM theme, i have never looked into it too much, and figured i would just leave it alone, but now im wondering, why isn't the Administrator Mode button there?

---

### Post by upthelum on 2007-08-11
I dunno but i can't change my boot theme because of it and you can see which one it's stuck on, it's not exactly stunning. Ok i have just un-installed it and re-installed the theme manager. I also just solved an issue with my sources.list file which i thought was affecting apt-get update. Still no cigar.

Anyone?

---

### Post by upthelum on 2007-08-11
> **upthelum said:**
> For some reason i dont have the administrator option in my theme manager. Can someone offer a simple solution to this on kubuntu desktop?

Thanks...

Perhaps this is the wrong place to try.

---

### Post by EXCiD3 on 2007-08-11
actually yeah, the Desktop Environments section is the correct place for this... might be able to contact a moderator to move it...

---

### Post by upthelum on 2007-08-11
Thanks..

---

### Post by cookies on 2007-08-11
Well yeah **KDM** Themes can only be changed by the administrator and you must launch kcontrol (the actual KDE control center) to have the Administrator Button, due to a bug in System Settings.

---

### Post by upthelum on 2007-08-11
How do i launch kcontrol i cant find it in my menu, is there a terminal command for it?

---

### Post by EXCiD3 on 2007-08-11
hey thanks man, ill have to try that in a min. hope this gets fixed for the gutsy release and/or kde4 release.

---

### Post by meierfra on 2007-08-12
I am using gnome and kde sessions and  I have similar problems, not with the theme manager, but other kcontrols. For example "kusers" no longer worked after   I used "users and groups" in a gnome session.   I reinstalled kcontrol  and "kuser" worked again.  Well,  foolishly I used "user and groups" again and "kusers" stopped working. Now I  just use "users and groups" also  in kde sessions, so its not much of a problem. 

Anyway, I suggest reinstalling kcontrol, it might solve the problem.

---

### Post by meierfra on 2007-08-12
> how do i launch kcontrol i cant find it in my menu, is there a terminal command for it?

```
sudo kcontrol
```

---

### Post by EXCiD3 on 2007-08-12
Taken directly from kde.org: > Starting the KControl

The KDE Control Center can be started in 3 ways:

[indent]1.
[indent]By selecting K Button->Control Center from the KDE Panel.[/indent]
2.
[indent]By pressing Alt+F2.
This will bring up a dialog box. Type kcontrol, and click Run.[/indent]
3.
[indent]You can type kcontrol & at any command prompt.[/indent][/indent]

All three of these methods are equivalent, and produce the same result. 

And i guess now that there is an alpha build of KDE4, you could try that also.

---

### Post by upthelum on 2007-08-12
Thanks to all i now have access to all the neat boot splashes etc that i couldn't apply before.

---

