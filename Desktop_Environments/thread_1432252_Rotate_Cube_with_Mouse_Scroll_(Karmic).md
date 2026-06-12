---
title: "Rotate Cube with Mouse Scroll (Karmic)"
date: 2010-03-17
forum: Desktop Environments
---

### Post by karasuman on 2010-03-17
I just switched from Jaunty to Karmic, and in the process of setting up desktop effects, I'm having a hard time with configuring the rotate cube compiz effect.  Before, I was able to scroll on the desktop (ie, not over a window/application) to spin the cube to the next face.  Now, it seems that I either have to use keyboard shortcuts or lose the ability to scroll in applications.  

I've tried enabling the mouse scrolling to button 4/button 5 a la [this post]("http://ubuntuforums.org/showthread.php?t=1278343&highlight=cube+scroll"), but this doesn't fix the problem.  This is one of the few desktop effects that really made a difference in terms of convenience, so I'd really like to be able to fix this setting.

---

### Post by blackmail on 2010-03-17
Well you can easily set what you want in compiz

---

### Post by prince_sabin on 2010-03-17
I know this one

install compizconfig-setting-manager

```
sudo apt-get install compizconfig-settings-manager
```

Systems>Preferences>CompizConfig Settings Manager

In the "desktop" section find "Viewport Switcher"

Check the box to enable it (if not already) and enter the properties by clicking on it.

Go to the "Desktop-based Viewport Switching" tab and set "Move Next" to Button5 by clicking the disabled button and then checking enabled and selecting "Button5"

Do the same to set "Move Prev" to Button4 

if you want to rotate the cube when you middle click the desktop then set "Initiate plugin action" to Button2 (this will prevent you from middle-click and drag item from your desktop)

---

### Post by teet on 2010-04-03
> **prince_sabin said:**
> I know this one

install compizconfig-setting-manager

```
sudo apt-get install compizconfig-settings-manager
```

Systems>Preferences>CompizConfig Settings Manager

In the "desktop" section find "Viewport Switcher"

Check the box to enable it (if not already) and enter the properties by clicking on it.

Go to the "Desktop-based Viewport Switching" tab and set "Move Next" to Button5 by clicking the disabled button and then checking enabled and selecting "Button5"

Do the same to set "Move Prev" to Button4 

if you want to rotate the cube when you middle click the desktop then set "Initiate plugin action" to Button2 (this will prevent you from middle-click and drag item from your desktop)

Wow thanks prince_sabin!  This worked perfectly for me on lucid.  I could have poked around in the compiz settings for weeks before stumbling across this.

-teet

---

### Post by Xswitch on 2011-05-27
> **prince_sabin said:**
> I know this one

install compizconfig-setting-manager

```
sudo apt-get install compizconfig-settings-manager
```

Systems>Preferences>CompizConfig Settings Manager

In the "desktop" section find "Viewport Switcher"

Check the box to enable it (if not already) and enter the properties by clicking on it.

Go to the "Desktop-based Viewport Switching" tab and set "Move Next" to Button5 by clicking the disabled button and then checking enabled and selecting "Button5"

Do the same to set "Move Prev" to Button4 

if you want to rotate the cube when you middle click the desktop then set "Initiate plugin action" to Button2 (this will prevent you from middle-click and drag item from your desktop)

I know this is old, but just wanted to say thank you to prince_sabin for this...  And thanks to the original poster as well...

---

