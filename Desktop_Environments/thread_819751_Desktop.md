---
title: "Desktop"
date: 2008-06-05
forum: Desktop Environments
---

### Post by fearful on 2008-06-05
I was wondering if some one could help me get my desktop to look similar as this one please! I've tried everything

[IMG]http://i27.tinypic.com/2pu0tif.jpg[/IMG]

---

### Post by russo.mic on 2008-06-05
Have you poked around here?

[www.gnome-look.org](www.gnome-look.org)

---

### Post by fearful on 2008-06-05
Yes I have but this looks like something more than just a theme, its using fluxbox and those kick *** Terminal status on the desktop. I don't know how to get them...

---

### Post by atomkarinca on 2008-06-05
This is not Gnome, this is Fluxbox, a different Window Manager. You can install it like this:

```
sudo apt-get install fluxbox
```

The system monitor on the right is most probably GKrellM, to install:

```
sudo apt-get install gkrellm
```

For Fluxbox styles see [here]("http://fluxbox.sourceforge.net/themes.php") and for GKrellM themes see [here]("http://www.muhri.net/gkrellm/").

---

### Post by fearful on 2008-06-05
I have installed fluxbox, but everytime i try and click on the right menu options it just closes and nothing opens. Also when it did work if i opened nautilus and got my GNOME background i couldn't right click to open the flux menu a GNOME menu came up any ideas?

---

### Post by atomkarinca on 2008-06-05
Also for the transparency I guess xcompmgr is used on this screenshot. To install

```
sudo apt-get install xcompmgr
```

and start it with the transparency and fading effects:

```
xcompmgr -fF &
```

---

### Post by atomkarinca on 2008-06-05
> **fearful said:**
> I have installed fluxbox, but everytime i try and click on the right menu options it just closes and nothing opens. Also when it did work if i opened nautilus and got my GNOME background i couldn't right click to open the flux menu a GNOME menu came up any ideas?

For the right-click menu problem you can this after settings up Fluxbox:

```
sudo update-menus
```

This should update your menu. Sorry I don't know about Nautilus problem.

---

### Post by fearful on 2008-06-05
Thanks this is very helpful, but if I could only fix the fluxbox thing I'll be happy and just mess around with it myself. It really bugs me cuz I have to manually shutdown my computer cuz I can't click anything the toolbar just closes... also those terminals on the screen look hot

---

### Post by fearful on 2008-06-05
Is there any default shortcut to run the terminal cuz it won't even let me run that...

---

### Post by atomkarinca on 2008-06-05
> **fearful said:**
> Is there any default shortcut to run the terminal cuz it won't even let me run that...

Not that I know of. But you can easily configure your shortcuts inside your Gnome session. Open the keys file located in ~/.fluxbox/keys and add this line to the end

```
None F12 :Exec gnome-terminal
```

save and exit. Now when you hit F12, Gnome Terminal will pop up.

---

