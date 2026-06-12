---
title: "[SOLVED] Changing Logoff Icon from Green Running Man WITHIN Crux theme"
date: 2008-06-01
forum: Desktop Environments
---

### Post by ant1060 on 2008-06-01
Does anyone know how to change JUST the logout icon WITHIN a theme?  I have chosen the Crux theme for my 8.04, but I really don't like the Green Running Man icon.  I have tried to use gconf-editor to change just this logout icon to the standard Human gnome-logout... but nothing happens.
Can anyone shed any light please?
Thanks!
Ant

---

### Post by ant1060 on 2008-06-15
Does no-one have any leads on this at all?  No-one encountered anything similar, or have an idea of what I might try?
Thanks in advance for any illumination!

---

### Post by Rhubarb on 2008-06-15
It seems as though there's no icon for that for the crux icon theme.
So it seems to use the default gnome icon (the green running man).
This icon can be changed to an icon that you like by overwriting the file, or perhaps copying an icon that you like into the crux icon directory.

The green running man icon can be found here:
/usr/share/icons/gnome/24x24/actions/system-log-out.png
But I'm not sure exactly which one is used, as there are 24x24 icons, 32x32, 48x48, and scalable etc etc.

I haven't tried this myself, but you may need to copy the nice system-log-out icon that you like into the relevant crux icon directory, which is somewhere in here:
/usr/share/icons/Crux

Remember you'll need to have root privileges to copy files around here.

---

### Post by ant1060 on 2008-06-16
Thank you very much for replying to me!
Unfortunately, neither overwriting the Green Running Man nor copying the good icon into the Crux theme has done the trick.  
Is there any other way of achieving this, do you think?
Best wishes from Brussels :)

---

### Post by blackmachine on 2008-06-23
I've manage to change the running man icon to icon of my choice.

gain root access:```
gksu nautilus
```

navigate to ```
/usr/share/icons/gnome/24x24/actions
```
find icon name system-log-out. backup the icon by renaming it into system-log-out.png.original (or whatever name u prefer)

then paste the icon of your choice within the same folder.
change the filename to system-log-out.png

voila.. new icon!!
[[IMG]http://img171.imageshack.us/img171/8366/screenshotms3.th.png[/IMG]](http://img171.imageshack.us/my.php?image=screenshotms3.png)

---

### Post by ant1060 on 2008-06-27
Thank you very much indeed!  I have finally managed to replace that icon with the one I wanted!  The key to success was that you knew the size was 24 x 24 - before I did not know which one I needed and thought it was "scaleable".  Thanks once more :)

---

### Post by g_dragn on 2008-08-02
I jumped ship from Suse 10.0 a few days ago, and I'm lovin' Hardy pretty hard. However, like ant1060 and others, the Green-Running-Man is part of my preferred desktop theme and I really don't care much for him. Sorry, he just doesn't say "Logout here" to me. More like "I gotta go pee." Whatever.

   Anyway, I jumped for joy when I stumbled on this thread because it gave me hope. I followed blackmachine's advice pretty carefully: I selected /usr/share/icons/crystalsvg/22x22/actions/exit.png and after a little renaming, used Nautilus to make it the new /usr/share/icons/gnome/24x24/actions/system-log-out.png. Woo-hoo! \\:D/ 

   But *it didn't work.* ](*,) Out of desperation, I even used Gimp to resize it to 24x24, just in case that had anything to do with it. No luck. The Green-Running-Man ain't runnin' nowhere. He's here to stay and it's driving me nuts that I can't get rid of him. I can't think of anything that I might have done that was substantially different, and yet ant1060 says it worked for him. 

   You know how it is...it's not that the Green-Running-Man is so bad, it's just that it becomes an obsession when your system says [-X when you want to change something that you feel you ought to be able to change.

   Any other suggestions?

---

### Post by adept_king on 2008-08-15
/b/

here's a great replacement for the green running man in ubuntu...  

**Cactaur! **  

[IMG]http://img112.imageshack.us/img112/1251/cactuariconal4.png[/IMG]

That's right, its the green cactus man meme!  
(normally saying 'dont mind me, im just on my way to page 10') 

did it on my machine, looks dynomite.  you might want to add a hint of a shadow under his foot like the running man, and maybe add a little space under him so he doesnt touch the bottom of the screen.

---

### Post by Xm3buX on 2008-08-16
> **blackmachine said:**
> I've manage to change the running man icon to icon of my choice.

gain root access:```
gksu nautilus
```

navigate to ```
/usr/share/icons/gnome/24x24/actions
```
find icon name system-log-out. backup the icon by renaming it into system-log-out.png.original (or whatever name u prefer)

then paste the icon of your choice within the same folder.
change the filename to system-log-out.png

voila.. new icon!!
[[IMG]http://img171.imageshack.us/img171/8366/screenshotms3.th.png[/IMG]](http://img171.imageshack.us/my.php?image=screenshotms3.png)
I've changed the icon names and everything, but the log out icon hasn't changed... do I have to press anything or restart my computer or something?

---

### Post by ant1060 on 2008-08-31
I'm sure you did, but could you have forgotten to use root privileges to make the change?  Another way of doing that (the one which I use) is to navigate simply to the place where the icons are, then right click and choose (from SCRIPTS) root-nautilus-here.  Do the change and then close and it should work!  It did for me!

---

### Post by malupel on 2008-09-11
try this:

System -> Preferences -> Appearence 

then choose the theme you like and click on customize. select the tab "icons" and then select a different icon package that contains a different loggoff icon e.g. "Human". 

regards

---

### Post by fisherm on 2008-09-11
Another option is to create a custom application launcher, and remove the button given by the system from the panel. To do this: Right click on the panel, and choose "Add to Panel". Then select "Custom Application Launcher". Type should be "Application", Name - "User Logout" (or whatever you like), Command - "gnome-session-save --kill" (same command issued by the original button). Or if you want to skip the menu generated by that and simply log out quickly make the command "gnome-session-save --kill --silent". You can add a comment to your button if you like, and at the upper left of the Create Launcher window you can select any icon you like (the point of this whole post), doesn't even have to be from another icon set. Just save your image of choice somewhere and use the GUI to navigate to it. I keep all of my self created icons, GDM's, Wallpapers etc. in a folder called Themes in my Home directory. Hope that helps for those that had no luck with the other options.

---

