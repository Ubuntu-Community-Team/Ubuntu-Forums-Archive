---
title: "[unity] No global menu for desktop."
date: 2012-01-18
forum: Desktop Environments
---

### Post by dawidmt on 2012-01-18
I got global menu for applications but when there's no active application, theres no global menu. Picture:
[IMG]http://dl.dropbox.com/u/3505741/panel.png[/IMG]
Tried to restart unity settings, but nothing changes. Also tried to create new, clean user account and there was the same problem. Please help.

---

### Post by BC59 on 2012-01-18
Try this, open a terminal CTRL+ALT+T and run:
```
sudo apt-get install --reinstall ubuntu-desktop

```

---

### Post by dawidmt on 2012-01-18
> **BC59 said:**
> Try this, open a terminal CTRL+ALT+T and run:
```
sudo apt-get install --reinstall ubuntu-desktop

```
It doesn't help. Tried also reinstall unity and still nothing.

---

### Post by saneearth on 2012-01-18
This may sound silly, but have you clicked on the desktop window. Often the menu for any window will not become active till you click on the window or heading bar itself. If you are still having issues you may try and open terminal and enter "unity --reset". This will default everything if you have happened to make changes inadvertantly that caused this.

---

### Post by BC59 on 2012-01-18
Looks strange...go [URL="Everything about Unity
http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity"]here[/URL] there is everything about Unity, try to see if there is something that could help you.

---

### Post by dawidmt on 2012-01-18
> **saneearth said:**
> This may sound silly, but have you clicked on the desktop window. Often the menu for any window will not become active till you click on the window or heading bar itself. If you are still having issues you may try and open terminal and enter "unity --reset". This will default everything if you have happened to make changes inadvertantly that caused this.
Yes, I click on desktop and there still is no global menu.

UPDATE
Sometimes when I maximize application the global menu is also empty and there's no window buttons (close etc.).

---

### Post by BC59 on 2012-01-18
Then you have to try the difficult solution. You have to reset Compiz. Sometimes it's not working and maybe you have more problems than solutions. Run to a terminal:

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```
After running you may still have no buttons and you need to run this command again
```
compiz --replace & disown
```
Takes time to be reset and need patience.

---

### Post by dawidmt on 2012-01-19
> **BC59 said:**
> Then you have to try the difficult solution. You have to reset Compiz. Sometimes it's not working and maybe you have more problems than solutions. Run to a terminal:

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```After running you may still have no buttons and you need to run this command again
```
compiz --replace & disown
```Takes time to be reset and need patience.
It doesn't help - still no global menu for desktop.

---

### Post by cbennett926 on 2012-03-31
I too am having this problem, I went through all the other solutions as well :(


(Update)

I uninstalled CCSM and I also switched my laptop to only run discrete graphics, and rebooted, now it works.

---

