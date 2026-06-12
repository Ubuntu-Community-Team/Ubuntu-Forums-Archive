---
title: "How can I remove Rhythmbox from the indicator applet?"
date: 2010-10-29
forum: Desktop Environments
---

### Post by ahorriblemess on 2010-10-29
I started using Banshee. Having Rhythmbox always in the sound menu is redundant. Is it possible to remove it from there? I would like to keep the applet, not the Rhythbox launcher/controller.

---

### Post by irv on 2010-10-29
> **ahorriblemess said:**
> I started using Banshee. Having Rhythmbox always in the sound menu is redundant. Is it possible to remove it from there? I would like to keep the applet, not the Rhythbox launcher/controller.
Why do you want to remove it from the sound menu? If you want to keep the applet, if you remove it then you will have to launch it from the command line. If you don't plan to use it for a long period of time, then uninstall it and just reinstall it when you need it again. That will take it out of the menu.

---

### Post by hhh on 2010-10-29
Right-click your main menu, choose "Edit Menus". Highlight "Sound and Video" in the left pane of the window that opens and uncheck Rhythmbox in the right pane.

---

### Post by ahorriblemess on 2010-10-29
@irv: I want to remove it because I don't use it anymore. I thought Rhythmbox was attached to ubuntu-desktop (wasn't it in the past?)

I just uninstalled it, I didn't know I could do that. 

@hhh: I wasn't talking about the gnome menu, I meant the menu that pops up when you click on the volume indicator.

---

### Post by wanchai on 2010-11-14
see here: [http://ubuntuforums.org/showpost.php?p=10012561&postcount=5](http://ubuntuforums.org/showpost.php?p=10012561&postcount=5)

delete *~/.cache/indicators/sound/familiar-players-db.keyfile*, then restart the panel with *killall gnome-panel*

If you prefer a simpler volume control, see here: [http://www.ubuntugeek.com/how-to-remove-and-restore-the-volume-button-from-system-tray.html](http://www.ubuntugeek.com/how-to-remove-and-restore-the-volume-button-from-system-tray.html)

---

### Post by bswilson on 2010-11-18
Thanks, **wanchai**!  I had this same issue and I was able to fix it.  Appreciate the help.

---

### Post by ngc2997 on 2010-12-02
Hm, this is actually strange: Rhythmbox suddenly appeared in my sound indicator even though I've never ever started it - and the file mentioned above (~/.cache/indicators/sound/familiar-players-db.keyfile) does not exist, i.e. there is no ~/.cache/indicators/sound/ directory. Are there other ways of removing Rhythmbox from the sound indicator that do not require complete uninstallation? (I'd like to avoid that, as AFAIK Rhythmbox is part of ubuntu-desktop - correct me if I'm wrong here though).

Best wishes,
Karsten

---

### Post by Liverbones on 2010-12-02
> **ngc2997 said:**
> Hm, this is actually strange: Rhythmbox suddenly appeared in my sound indicator even though I've never ever started it - and the file mentioned above (~/.cache/indicators/sound/familiar-players-db.keyfile) does not exist, i.e. there is no ~/.cache/indicators/sound/ directory. Are there other ways of removing Rhythmbox from the sound indicator that do not require complete uninstallation? (I'd like to avoid that, as AFAIK Rhythmbox is part of ubuntu-desktop - correct me if I'm wrong here though).

Best wishes,
Karsten

Actually, Rhythmbox is not part of the ubuntu-desktop meta package. You can safely remove it if you wish without affecting your updates.

As to the other problem of having Rhythmbox in the sound indicator, I unfortunately do not have an answer for you. :(

---

### Post by genux05 on 2011-04-12
I did this to remove the rhythmbox from the indicators menu.

```

 gsettings set com.canonical.indicators.sound blacklisted-media-players "['rhythmbox']"

```

---

### Post by jaambutt on 2011-04-12
my ipod classic 6th gen used to work fine, but now when i plug it in to my win xp computer.

---

### Post by draztikrhymez on 2011-04-15
> **wanchai said:**
> see here: [http://ubuntuforums.org/showpost.php?p=10012561&postcount=5](http://ubuntuforums.org/showpost.php?p=10012561&postcount=5)

delete *~/.cache/indicators/sound/familiar-players-db.keyfile*, then restart the panel with *killall gnome-panel*

If you prefer a simpler volume control, see here: [http://www.ubuntugeek.com/how-to-remove-and-restore-the-volume-button-from-system-tray.html](http://www.ubuntugeek.com/how-to-remove-and-restore-the-volume-button-from-system-tray.html)

Worked perfectly, thanks!

---

### Post by genux05 on 2011-04-16
Hi draztikrhymez,

I am using 11.04 ubuntu with Unity and that directory is not present.

Thanks

---

### Post by ottabaub on 2012-02-11
> **wanchai said:**
> see here: [http://ubuntuforums.org/showpost.php?p=10012561&postcount=5](http://ubuntuforums.org/showpost.php?p=10012561&postcount=5)

delete *~/.cache/indicators/sound/familiar-players-db.keyfile*, then restart the panel with *killall gnome-panel*


There is no ***sound*** folder in ***~/.cache/indicators***. Only a folder called *messages*.

---

### Post by aussieade on 2012-07-10
> **genux05 said:**
> I did this to remove the rhythmbox from the indicators menu.

```

 gsettings set com.canonical.indicators.sound blacklisted-media-players "['rhythmbox']"

```


for 12.04 the schema name has changed slightly...

```

gsettings set com.canonical.indicator.sound blacklisted-media-players "['rhythmbox']"

```

---

