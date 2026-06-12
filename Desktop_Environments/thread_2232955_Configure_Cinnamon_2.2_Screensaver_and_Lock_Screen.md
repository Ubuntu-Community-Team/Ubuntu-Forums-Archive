---
title: "Configure Cinnamon 2.2 Screensaver and Lock Screen"
date: 2014-07-05
forum: Desktop Environments
---

### Post by kschiff on 2014-07-05
I recently upgrade to 14.04 with Cinnamon 2.2. Previously when I locked my screen there was a black background with the time showing in front of it (time was white against the black). After the upgrade, the lock screen is showing my desktop wallpaper. I can't seem to find any way to configure this. If possible, I would like the lock screen (ctrl + alt + L) to go to a blank screen, same with general screen saver activity.

I uninstalled gnome-screensaver as it was providing an unecessary secondary login.

[ATTACH=CONFIG]254489[/ATTACH]

---

### Post by michel9 on 2014-07-05
> **kschiff said:**
> I recently upgrade to 14.04 with Cinnamon 2.2. Previously when I locked my screen there was a black background with the time showing in front of it (time was white against the black). After the upgrade, the lock screen is showing my desktop wallpaper. I can't seem to find any way to configure this. If possible, I would like the lock screen (ctrl + alt + L) to go to a blank screen, same with general screen saver activity.

I uninstalled gnome-screensaver as it was providing an unecessary secondary login.



Hi there,

You can't change the screensaver because it's actually not a screensaver but a lock screen. there are no screensaver (and settings) in Cinnamon.
I can't say when you dissable the lockscreen if the gnome screensaver starts up... I don't use Cinnamon 2.2 yet.
in cinnamon 1.8 there is a way to dissable the lock screen in the settings, but much is changed in 2.2 so...

Normally the lock screen should be transparant. the clock should only be fonts no background.
In your case you get a bar with the clock in it.
I think your graphic card isn't sufficient or there is something wrong with the driver!

---

### Post by kschiff on 2014-07-05
I found a way to disable the lock screen in dconf, but I'm going to use this solution for now until I come up with something better:

[http://askubuntu.com/a/400716/2692](http://askubuntu.com/a/400716/2692)

I disabled the inbuilt shortcut for lock screen and replaced it with a custom keyboard shortcut: [FONT=Ubuntu Mono]bash -c "cinnamon-screensaver-command -l; xset dpms force off;"[/FONT] 

This makes the screen go black on demand, which is not elegant but works.

---

