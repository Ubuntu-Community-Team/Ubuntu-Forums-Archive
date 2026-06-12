---
title: "AWN problems"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by bibawa on 2007-08-12
Hello!

I've just installed ubuntu feisty on a 64 bit computer, the installation was great..

Now I want to ad AWN launch bar, so I installed first the latest NVidia drivers, and downloaded the .deb file for AWN and installed them..

Now when I run AWN there's a black box round the AWN bar, an when I point my mouse to a program the text is behind the bar.. also the bar is flashing hard when I move my mouse over it..

Here you can see my problem:

[http://img254.imageshack.us/img254/8247/screenshotsg5.png](http://img254.imageshack.us/img254/8247/screenshotsg5.png)

Here on the forums I've read that you need something like beryl I've installed it with synaptics, but the problem stays..


Hope someone could help me !


Thanks !!

---

### Post by qamelian on 2007-08-12
You need to have Beryl, Compiz, or Compiz-fusion actually running, not just installed. AWN requires that you be using a compositing window manager, so if you are still using Metacity, the default window manager used by Gnome, you'll get the black box around AWN.

---

### Post by bibawa on 2007-08-12
How do I run beryl?

I've clicked on beryl manager, but the problem stays :s

---

### Post by Nekiruhs on 2007-08-12
Now right clikc on the Red berly icon in the tray and go to window manager > Beryl

---

### Post by bibawa on 2007-08-12
Okey i've started beryl and now the black box is gone, and in place there's a white box, and AWN is also gone :)

When I now start the beryl configuration pane i'll see a black square on my screen... When I change the window manager back to the default I'll see the beryl configuration pane and also AWN back..

so I guess there's something wrong but what :s

---

### Post by bibawa on 2007-08-13
Somebody who can h elp me?

---

### Post by walkerk on 2007-08-13
try loading awn after

```
killall avant-window-navigator
```

now start beryl..

now load awn
```
avant-window-navigator &
```

---

### Post by petit.padavoine on 2007-08-13
Use compiz fusion.
First remove everything you have :D.
```
sudo apt-get --purge remove beryl* avant-window-navigator* compiz* desktop-effects emerald*
```
Then install compiz fusion:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29)
Then ```
sudo apt-get install compiz-fusion-plugins-*
``` to get all the compiz fusin plugins.
Add "compiz --replace" to your startup programs in System, Preferences, Plugins.
Then install avant window navigator again:
[http://ubuntuforums.org/showthread.php?t=354009](http://ubuntuforums.org/showthread.php?t=354009)
If you want emerald:
```
sudo apt-get install emerald emerald-themes
``` and add "emerald --replace" to your startup programs.

Beryl is alpha and is not being developped/fixed/patched anymore. Compiz Fusion is the way to go and as far as I know it works perfectly with Avant Window Navigator.

---

