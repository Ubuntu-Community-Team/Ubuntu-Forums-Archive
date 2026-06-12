---
title: "Killed desktop with cube"
date: 2011-08-31
forum: Desktop Environments
---

### Post by DrMike on 2011-08-31
Hello All –
   
  Well, this morning I decided to play with my compiz configuration settings, and activate the “cube”. After selecting “yes” to disable some stuff (I believe compiz and largedesktop – In my excitement to experience the “cube”, I rashly did not pay sufficient attention), my desktop is now completely useless. No launchers, no bar at the top of my screen, nothing happens when I press the ubuntu button on my keyboard. 
   
  I can access a terminal with **ctrl+alt+F1**, but that’s about it. (ctrl+alt+T) does not work.
   
  After checking through the forums, I’ve found similar problems and solutions, none of which work for me:


  Resetting compiz settings:
  [http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html](http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html)
  [PHP]$ gconftool-2 --recursive-unset /apps/compiz[/PHP]  Reinstall compiz to a clean state:
  [http://ubuntuforums.org/showthread.php?t=439745](http://ubuntuforums.org/showthread.php?t=439745)
  [note: could not do “step 2”, as I cannot open/access any windows]
  [PHP]$ sudo apt-get remove --purge compiz-core libemeraldengine0
  $ gconftool-2 --recursive-unset /apps/compiz
  $ gconftool-2 --recursive-unset /schemas/apps/compiz
  $ gconftool-2 --unset /apps/gnome-compiz-preferences 
  $ sudo apt-get install ubuntu-desktop compiz-plugins[/PHP]  Any help would be extremely appreciated, as my lovely laptop is pretty much useless right now…
   
  Ubuntu 11.04

---

### Post by 3Miro on 2011-08-31
Do you login automatically or manually?

You should be able to login with Ubuntu classic (No Effects) and then access compiz-config-settingsmanager to disable the cube.

There is a way to start the cube with 11.04 and Unity, but it is tricky and I am not exactly sure how.

---

### Post by 3Miro on 2011-08-31
You can go to the terminal and go to:

```
.config/compiz/compizconfig
```

then edit the Default.ini file with the command:
```
nano Default.ini
```
(or you can use pico Default.ini).

You can then look at the as_active_plugins and disable anything cube and enable wall.

---

### Post by ajgreeny on 2011-08-31
The terminal command ```
compiz --reset
``` should get you back to default.

---

### Post by 3Miro on 2011-08-31
> **ajgreeny said:**
> The terminal command ```
compiz --reset
``` should get you back to default.

wow, that's useful, I didn't know of this command.

---

### Post by DrMike on 2011-08-31
> **3Miro said:**
> Do you login automatically or manually?

You should be able to login with Ubuntu classic (No Effects) and then access compiz-config-settingsmanager to disable the cube.

There is a way to start the cube with 11.04 and Unity, but it is tricky and I am not exactly sure how.

Thank you! 

I never noticed that you can change the environment when logging in. For the record, both Ubuntu Classic and Classic (no effects) work fine. I've checked off the cube option, however when I log back under Ubuntu, I still only get the wallpaper, and no status bar. In addition, for all versions of environment (ie: Ubuntu, Ubuntu Classic, etc) the ubuntu button on my keyboard does nothing.

however, I have my computer back, so I'm extremely happy! :)

---

### Post by DrMike on 2011-08-31
> **ajgreeny said:**
> The terminal command ```
compiz --reset
``` should get you back to default.

many thanks for the feedback, but I get 

Warn: Unknown option '--reset'

---

### Post by DrMike on 2011-08-31
> **3Miro said:**
> You can go to the terminal and go to:

```
.config/compiz/compizconfig
```then edit the Default.ini file with the command:
```
nano Default.ini
```(or you can use pico Default.ini).

You can then look at the as_active_plugins and disable anything cube and enable wall.

the 'compiz' directory does not exist under my ~/.config directory

perhaps I killed it?

---

### Post by 3Miro on 2011-08-31
> **DrMike said:**
> the 'compiz' directory does not exist under my ~/.config directory

perhaps I killed it?

They must have moved the folder to something else with a .

You can open Nautilus and then hit Ctr + H to show hidden files (starting with a dot). Then look into some of the folders and the compiz configuration should be there. However, you will probably have two configurations, one for Unity and one for regular Gnome. You need to disable the cube for the Unity one.

---

### Post by stinkeye on 2011-09-01
This is a pretty comprehensive guide to fixing compiz with unity.
[**_[COLOR="DarkRed"]http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html[/COLOR]_**]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by DrMike on 2011-09-01
> **stinkeye said:**
> This is a pretty comprehensive guide to fixing compiz with unity.
[**_[COLOR=DarkRed]http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html[/COLOR]_**]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

Looks like a pretty excellent set of instructions.

Unfortunately I'm failing at the first step. I confirmed that I do not have unity installed, but when I attempt to download and install, I get the error:
something wicked happened resolving 'deb.torproject.org:http'

After doing some reading on this, it seems the most common route is to wait for the issue to be resolved at the source.

---

### Post by The Llama on 2011-09-01
Quick note: The task bar and launcher you were referring to is called Unity, and the exact same happened to me when I began using Ubuntu. I on the other hand installed a different taskbar (Avant Window Navigator) as I didn't know how to fix the problem, it's awesome and I still use it because it's so customizable, use this code in terminal to install:
```
sudo apt-get install avant-window-navigator
```
Better than Unity!

---

### Post by DrMike on 2011-09-03
> **stinkeye said:**
> This is a pretty comprehensive guide to fixing compiz with unity.
[**_[COLOR=DarkRed]http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html[/COLOR]_**]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

Ok the download site for re-installing unity is now working, and these instructions worked great.

Everything is back to normal, except that the ubuntu button on my keyboard still does not work. But that's a minor quibble. 

Thanks!

---

