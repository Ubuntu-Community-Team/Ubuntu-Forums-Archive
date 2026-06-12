---
title: "Unity Panel doesn't switch to Ubuntu Desktop"
date: 2013-06-23
forum: Desktop Environments
---

### Post by LinuxWillWin on 2013-06-23
Hello Friends,

my Unity Panel doesn't switch back to "Ubuntu Desktop" automatically when I close all windows. Just when I click on the Desktop the Panel says "Ubuntu Desktop". But I want it to automatically switch to Ubuntu Desktop. As you can see in the screenshot I have just closed all windows and Unity Panel in the top left corner still says "Terminal" because I just closed terminal. Is there maybe a setting in the compiz config settings manager or how do I get Unity Panel to automatically switch to Ubuntu Desktop?

Thank you for your answers!:D

---

### Post by dino99 on 2013-06-23
im not an unity user, but your "unity desktop" (aka ubuntu-desktop, as unity is the default) is as expected. About the last app used (terminal in that case), maybe you can choose to not remember that setting into dconf

---

### Post by LinuxWillWin on 2013-06-23
How can I do this in dconf?

---

### Post by cmcanulty on 2013-06-23
Please give  detailed instructions of how to make unity look like that I don't mean the picture but the dock , desktop shortcuts, topbar, sidebar, etc. I could maybe live with that as I have stuck with classic so far.

---

### Post by stinkeye on 2013-06-23
I believe this is a bug when using conky on the desktop.
In your conky config try using
```
own_window_type **override**
```
...to see if that makes a difference.

---

### Post by LinuxWillWin on 2013-06-24
> **stinkeye said:**
> I believe this is a bug when using conky on the desktop.
In your conky config try using
```
own_window_type **override**
```
...to see if that makes a difference.
Thanks. I changed it in the conky.config from ```
own_window_type normal
``` to ```
own_window_type override
```but it didn't change anything:(
Any other ideas?

---

### Post by stinkeye on 2013-06-24
Try with 
```
own_window_type normal
```

and in 
ccsm > window management > window rules
add to the **No Focus** box...
```
class=Conky
```

Restart conky after changing the ccsm setting.
Seems to work here after a quick test.

[COLOR="#FF0000"]**[/COLOR]ccsm is compizconfig-settings-manager
and you may need to install.
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by LinuxWillWin on 2013-06-24
Juhuu, Yes that worked! Now its fixed! Thank you so much for your help!

---

### Post by sk-random on 2014-04-30
Thanks - I had the same issue happening, except it was with Nagstamon (floating window) as the cause of the problem.  As a side note to anyone happening to be in the same situation, enable the "Window Rules" via CCSM and add "title=nagstamon" into the No Focus option.

---

### Post by linfidel on 2014-05-21
> **stinkeye said:**
> Try with 
```

...
ccsm > window management > window rules
add to the **No Focus** box...
[CODE]class=Conky
```
...
[/CODE]
Thanks for this; I've been trying to fix this problem ever since installing 14.04; never had the problem with any previous versions.  I had narrowed it down to conky, but previous tries to fix didn't work.  Neither did this one, until I noticed that my class name in .conkyrc was lowercase, and it does seem to matter.  So, anyone trying this, be forewarned. :-)

---

