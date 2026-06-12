---
title: "Custom start-ups for every DE"
date: 2011-06-11
forum: Desktop Environments
---

### Post by dimaursu16 on 2011-06-11
well, it's almost all written in the title. I have several DE, actually 5, and I want everyone to have custom start up. for example - 

wicd (daemon) and wicd-gtk to start up when I log in to 'awesome' ,'xfce4' and 'ratpoison'
and the standart ones for gnome and kde.

(btw, it's all happening in Arch linux, but I guess it's not a big deal)

Can you help me?

---

### Post by andrewthomas on 2011-06-12
While you can edit the .desktop files to only start in certain desktop environments, the simplest method would be to create a different user for each DE and log into the user of your choice to control which programs start.

---

### Post by dimaursu16 on 2011-06-12
> **andrewthomas said:**
> While you can edit the .desktop files to only start in certain desktop environments, the simplest method would be to create a different user for each DE and log into the user of your choice to control which programs start.

you could be right....I may skip me from some pain in the a** that way... I will think about it

---

### Post by manzdagratiano on 2011-06-13
I use Gnome, Blackbox, Ratpoison and Scrotwm in Arch Linux (as well as Ubuntu). I just create a custom script for each of these and ask the .desktop file to execute that (Exec=/path/to/my/script). For instance, the one for Scrotwm looks like:

```

scrotwm & wmpid=$!

# Wallpaper
feh --bg-scale /media/Cybertron/Opet/Warriors/Transformers/MoreThanMeetsTheEye.jpg
# Start trayer
trayer --expand true --transparent true  --alpha 255 --edge bottom --align right --expand true --SetDockType true --widthtype request --margin 130 &
# Start the gnome power manager
gnome-power-manager &
# Start the wicd client
wicd-client &
# Start dropbox
dropbox start
# Start the xscreensaver daemon
xscreensaver -no-splash &

# Wait until scrotwm exits
wait $wmpid


```and all works perfectly! For Blackbox, I ask the .desktop to start blackbox normally, but I put such a script in its rootCommand, except for the wmpid stuff.

**EDIT**: This idea is basically lifted from the Arch Wiki, from the Desktop Environments entry.

---

### Post by Copper Bezel on 2011-06-13
There are quirks, though, if you're running a full DE like KDE or Gnome by launching its parts a la carte like that. I do it myself (with Gnome) but there are a few irritating little problems that I can't quite solve because of it (none of which are worth going back to the troublesome and unpredictable autostart configuration, but still.)

---

