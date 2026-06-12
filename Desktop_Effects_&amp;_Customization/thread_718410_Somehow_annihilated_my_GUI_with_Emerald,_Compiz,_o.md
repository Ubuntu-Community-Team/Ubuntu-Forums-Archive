---
title: "Somehow annihilated my GUI with Emerald, Compiz, or some other program of the like."
date: 2008-03-08
forum: Desktop Effects &amp; Customization
---

### Post by Baelari on 2008-03-08
I couldn't get any of the eyecandy programs to work, so I was toying around with their settings. Somehow, I've managed to annihilate the functionality of everything but the desktop and menu. Opening any window crashes Ubuntu.

 I've been messing with AWN, Emerald, Compiz, and one other program that started with a G (yeah, reeeallly narrows it down, huh). I might've turned off the default GUI for Ubuntu in the process... I really have no clue. 

How could I uninstall/disable these? or set the default appearance editor back to normal? If that can't be done, how can I go in to copy my evolution downloaded email to another disk? That's the only thing I need to save.

I suppose the first question I need to ask is how to even access anything without using a window...

---

### Post by eddiesquared on 2008-03-08
ctrl + F7 to go into the text-based terminal. purge awn, compiz emerald etc, and then install gnome and ubuntu-desktop then restart ur machine.

should be fine after that, try and re-install compiz but try not to screw with the settings too much next time

---

### Post by Baelari on 2008-03-08
thanks for the help :)

I couldn't get to the text based terminal through the ctrl f7 trick, but eventually realized that the giant 'RECOVERY MODE' option in grub is just the terminal... I feel brilliant right about now...](*,)

anyhow:
```
sudo apt-get remove emerald
sudo apt-get remove compiz
sudo apt-get remove avant-window-navigator
sudo apt-get install gnome
sudo apt-get install ubuntu-desktop  
```
are what I typed in, and it seemed to work well enough to get the windows working. I got quite a few error messages for the installs, so I don't know if they actually did anything,

since I was root@angie-laptop, or whatever it said, was the 'sudo' part necessary?

---

### Post by Islington on 2008-03-08
> **Baelari said:**
> thanks for the help :)

I couldn't get to the text based terminal through the ctrl f7 trick, but eventually realized that the giant 'RECOVERY MODE' option in grub is just the terminal... I feel brilliant right about now...](*,)

anyhow:
```
sudo apt-get remove emerald
sudo apt-get remove compiz
sudo apt-get remove avant-window-navigator
sudo apt-get install gnome
sudo apt-get install ubuntu-desktop  
```
are what I typed in, and it seemed to work well enough to get the windows working. I got quite a few error messages for the installs, so I don't know if they actually did anything,

since I was root@angie-laptop, or whatever it said, was the 'sudo' part necessary?

no but its in good form. did your failsafe login also not work?

---

### Post by Baelari on 2008-03-08
No clue what that is.

---

