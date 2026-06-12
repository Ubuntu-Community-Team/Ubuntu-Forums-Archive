---
title: "Animation time of compiz visual system beep"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by rwh on 2007-10-25
Hi All,

I use gutsy at work, so I turn off the system beep using:

System->Preferences->Sound->System Beep->Visual system beep

This worked really well under metacity, and it still works under compiz, however instead of the window simply flashing, which was really fast, compiz now uses an effect to fade the window back in, which takes around a second on my computer.

When I'm working in a terminal, I often create beeps really quickly, which means that I may have to wait a few seconds before the screen becomes responsive again after being faded back in repeatedly.  Is there an option to speed up the animation or turn it off?  I couldn't find anything in gconf-editor or Advanced Desktop Effects Settings.

Thanks,

Rob

---

### Post by stevux on 2007-11-03
I too found that there is a bug for compiz not remembering the settings in sound preference, but that's not my main concern. I also found the 'sudden nightfall'  on my term to last a bit long, so i googled following;
   [http://en.opensuse.org/Compiz#Fade](http://en.opensuse.org/Compiz#Fade)

To disable the visual bell effect, do following;
  Untick the following box; System -> Preferences -> Advanced Desktop Settings -> Fading Windows -> Visual Bell

To keep the bell, but make the fading screen re-appear faster, set the 'Fade Speed' variable higher. I like 25, the maximum  :)

All above is assuming you've installed the package 'compizconfig-settings-manager'. If not, you can do so by typing 'sudo apt-get installl compizconfig-settings-manager'

hth,

---

### Post by rwh on 2007-11-06
Perfect!  Thanks heaps :)

---

