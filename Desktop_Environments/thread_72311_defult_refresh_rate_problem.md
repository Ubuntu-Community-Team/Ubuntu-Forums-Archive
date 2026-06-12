---
title: "defult refresh rate problem"
date: 2005-10-05
forum: Desktop Environments
---

### Post by evilgold on 2005-10-05
My screen keeps going back to its defult refresh rate (80hz) whenever i switch users or window managers. The only things it will stay in are KDE and Gnome. How can i make my xorg.conf (or gdm and all my window managers) defult to 60hz instead of 80.

---

### Post by Dolphin on 2005-10-05
CRT?  If so why would you want 60hz?  Yikes.

---

### Post by evilgold on 2005-10-05
[QUOTE=Dolphin]CRT?  If so why would you want 60hz?  Yikes.[/QUOTE]

Whats so bad about 60hz? Yes its a CRT.. its an ibm P77. The reason i want it at 60 is because anything higher then that the screen jitters. I dont know why it jitters, as its fully capable of running at that rate as far as i know, but it does, so I'd like to use 60.

---

### Post by Dolphin on 2005-10-05
Ah, I've seen that before.  Monitor won't handle it, despite that it saying it will.  I just mentioned it because 60hz is exceptionally low for a CRT.  I can spot at a distance when a CRT is running at 60hz.  It's very hard on the eyes and it's what causes the headaches you get for staring at the screen too long.

AFAIK, you'll have to change it to 60hz for every user.  I don't remember how to do it in gnome, but in KDE there's and option in kcontrol that you have to check so the settings will hold after you log off.

---

### Post by evilgold on 2005-10-05
[QUOTE=Dolphin]Ah, I've seen that before.  Monitor won't handle it, despite that it saying it will.  I just mentioned it because 60hz is exceptionally low for a CRT.  I can spot at a distance when a CRT is running at 60hz.  It's very hard on the eyes and it's what causes the headaches you get for staring at the screen too long.
AFAIK, you'll have to change it to 60hz for every user.  I don't remember how to do it in gnome, but in KDE there's and option in kcontrol that you have to check so the settings will hold after you log off.[/QUOTE]

well my monitor supports the higher refresh rates, i think the jittering is due to some kind of interference, because i've had it on 80hz before, but in another house (i recently moved into an apartment).  I have changed the setting for each user in KDE and gnome, but I use IceWM most of the time, and there is nothing to change the settings for it. I can use the Kde control panel in iceWM, but it will always go back to 80hz after i log out.

---

### Post by heimo on 2005-10-05
You could put VertRefresh line with just one value to your xorg.conf
```
VertRefresh	60
```

Related instructions:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by evilgold on 2005-10-05
[QUOTE=heimo]You could put VertRefresh line with just one value to your xorg.conf
```
VertRefresh	60
```

Related instructions:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)[/QUOTE]

Thank you very much heimo thats exactly what i needed.

---

