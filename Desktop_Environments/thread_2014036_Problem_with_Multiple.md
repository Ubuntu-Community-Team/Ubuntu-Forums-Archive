---
title: "Problem with Multiple"
date: 2012-07-01
forum: Desktop Environments
---

### Post by PyrexKidd on 2012-07-01
TL;DR, how do I remove the triple workspaces, double status bars, and triple menu buttons?  See the middle screen here: [http://i.imgur.com/RUgoF.jpg](http://i.imgur.com/RUgoF.jpg)

Everything was working this morning when I arrived at the office (using the "recommended" nvidia driver), I ran an apt-get upgrade and my right monitor was rotated back to "normal" position ("normal" for the screen, since I have it physically rotated, this is the incorrect orientation for human use.), 

after attempting to use the display gui to rotate my monitors I received an error "RandR missing", googling that error I found a solution that said to uninstall and reinstall the nvidia drivers.  

I did that.  

when I install the "recommended" driver, I am unable to rotate my monitor because I get the error "RandR is missing" (note uninstalling and reinstalling did not fix this) when attempting to use the "Displays" GUI.

When I install the "post-relase-update" nvidia driver, I am able to copy my xorg.conf over and rotate the screen but I get all of these duplicate (triplicate?) icons and this double bar at the top and bottom of the screen.  Attempting to use the "displays gui" also results in the error RANDR missing. (See the middle screen here: [http://i.imgur.com/RUgoF.jpg](http://i.imgur.com/RUgoF.jpg))  I think that I can use the desktop as it is, if ony I could get rid of the triple Icons (look at "Applications Places Applications Places Applications Places" on the top bar)

Honestly, I'd be happy with any solution that gets me back to working order.

---

### Post by msammels on 2012-07-03
First of all, kudos on the wallpaper - got a link to it?

Secondly, lets try this one step at a time. First of all, what happens if you remove the other two monitors? And then apply them all one at a time? Perhaps Ubuntu has trouble with it, I don't know. If you're really, really, daring you can try to delete your GNOME3 config by running the following:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails ~/.config/dconf/user ~.compiz*
```

**NOTE: You will loose ALL your GNOME3 settings.**

Perhaps the system just got confused. Anyway, try these things out and get back to us.

P.S: please backup your GNOME3 settings by using this command:

```
mkdir ./.old-gnome-config/ && mv ./.gnome* ./.old-gnome-config/ && mv .gconf* ./.old-gnome-config/ && mv ./.metacity ./.old-gnome-config/ && mv ./.cache ./.old-gnome-config/ && mv ./.dbus ./.old-gnome-config/ && mv ./.dmrc ./.old-gnome-config/ && mv ./.mission-control ./.old-gnome-config/ && mv ./.thumbnails ./.old-gnome-config/   && ~/.config/dconf/* ./.old-gnome-config/
```

---

