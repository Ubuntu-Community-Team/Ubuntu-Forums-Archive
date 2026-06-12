---
title: "Gnome panel menu bar"
date: 2013-06-26
forum: Desktop Environments
---

### Post by CatKiller on 2013-06-26
Just upgraded to Raring and it went relatively smoothly except for a couple of hiccups. I'm using Gnome fallback & then auto-loading Compiz. One thing that's annoying me, though, is that the Menu Bar on the panel is run together, so that instead of saying, "Applications Places" it says, "ApplicationsPlaces." It appears to be some kind of pikey faux-tab thing and it just looks stupid. Pointers on ways to make it less stupid would be appreciated, since a search hasn't managed to pick up anything.

---

### Post by Frogs Hair on 2013-06-26
Mine does't appear that way in 13.04, you could try resating the panel. The following was the command from Gnome 2 , but don't login or use classic very often.  ```
Killall gnome-panel
```

---

### Post by CatKiller on 2013-06-26
Given that it survives a reboot, just restarting the process isn't going to do anything.

Thanks anyway, though.

---

### Post by Frogs Hair on 2013-06-26
This post has additional  commands for resting the panel . [http://askubuntu.com/questions/125662/how-to-reset-gnome-panel](http://askubuntu.com/questions/125662/how-to-reset-gnome-panel)

---

### Post by CatKiller on 2013-06-27
Yeah, no dice. Which suprised me a little. I tried logging into the guest account to see if the problem persisted there, and that's just broken. It's an almost non-functional blue-and-black mess if I pick Gnome fallback & a black screen with a pointer if I pick anything else.

So at least my account isn't like that.

---

### Post by cmcanulty on 2013-06-27
I am using classic also and that happens if the top bar is too crowded it will even hide some icons if i get too many. It seems like 2 fixes could be done 1) pop up a warning message that bar is too full or 2) automatically double the bar when needed as I believe (gasp!) windows does. Being not  coder though, both are beyond my capabilities

---

### Post by CatKiller on 2013-06-27
I've only got two things on there - the menu bar and the indicator applet.

Just did a re-install because my packages were in a shocking state (one of the reasons I did the upgrade) and it's the same.

---

### Post by cmcanulty on 2013-06-27
2 things to try, just reinstall gnome-panel 
[https://launchpad.net/ubuntu/+source/gnome-panel]("https://launchpad.net/ubuntu/+source/gnome-panel")
also if you get it good use this handy panel backup or restore
[http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu]("http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu")

---

### Post by CatKiller on 2013-06-27
Having had a look at the Guest account, you still get the faux-tabs overlay, but the spacing is better. It's possible that it's because my account is using a different font for that part and the broken theming is unable to space it better. I'd play with that idea more, but the Gnome devs seem to have taken even more theming options away from us. Didn't think that was possible, but it seems you can't even pick your own wallpaper anymore :( Gnome-tweak-tool's being flaky so I'll probably poke dconf-editor when I get a chance.

---

### Post by cmcanulty on 2013-06-27
Try the clearlooks-phenix-master it works well for me with gnome icons see attached screenshot[ATTACH=CONFIG]244222[/ATTACH]

---

### Post by CatKiller on 2013-06-27
I quite like the theme I'm using, it's just broken now.

I've got as far as discovering the existence of the .gnome-panel-menu-bar section of /usr/share/themes/Ambiance/gtk-3.0/apps/gnome-panel.css, but I don't know what to put in it.

EDIT: In the meantime, I've abandoned the menu bar and just gone for main menu. Now it looks absurdly minimalist rather than broken, but it'll do for today.

---

### Post by CatKiller on 2013-06-28
Yeah, definitely something broken with the theme. Picking a different one solves the spacing problem, although for the particular theme I tried, it makes everything else look bad.

You know what I liked? Human. It's gone downhill since then. The new look of Nautilus is just awful.

---

