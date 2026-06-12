---
title: "OOPS! No only a trashcan in Gnome Classic"
date: 2013-02-17
forum: Desktop Environments
---

### Post by n4pgw on 2013-02-17
I goofed!  I was trying to add the system tray to my panal so HPLIP would quit giving me an error every time I boot.  I added what I already had, and was unable to delete it.  So I tried removing the panel so I could replace it clean and start over.  Unfortunately, there is nothing but a trash can on my desktop so all I could do is press alt-ctrl-del to get an option to log out. 

Is there a way to add the panel back to Gnome Classic when all I have is the desktop and a trash can?

Thanks
Buck

---

### Post by ibjsb4 on 2013-02-17
```
sudo apt-get install --reinstall gnome-panel
```

Should fix ya up :)

---

### Post by n4pgw on 2013-02-17
> **ibjsb4 said:**
> ```
sudo apt-get install --reinstall gnome-panel
```Should fix ya up :)
How do I get to terminal window?  Or can I do this from Gnome current?

---

### Post by ibjsb4 on 2013-02-17
Ctrl + Alt + t

or

Ctrl + Alt + F1

and to return to your GUI

Ctrl + Alt + F7

---

### Post by n4pgw on 2013-02-17
Thank you, That got me to the terminal, and I entered ```
sudo apt-get install --reinstall gnome-panel
```

It ran its cycles and said it was successful so I logged out and in again.  The panel is not there.  How do I make one visible?  

Is there an add panel command?

---

### Post by ibjsb4 on 2013-02-17
```
killall gnome-panel
```

---

### Post by n4pgw on 2013-02-17
[LEFT]Thank you, 

I was able to restore my panels (top and bottom) and put msot of the features back in.  

Somehow I have lost where my programs merge with the top panel.  I though I found it, but lost it somewhere. 

Well, I guess that's for another time.

Thank you
Buck
[/LEFT]

---

### Post by ibjsb4 on 2013-02-17
You can go to /usr/share/applications and drag your icons to the panel if thats what you mean.

---

### Post by n4pgw on 2013-02-17
> **ibjsb4 said:**
> You can go to /usr/share/applications and drag your icons to the panel if thats what you mean.

No, when I open firefox, it used to have the menu bar at the very top of the screen.  Now it is in its own window, unless I am mistaking it for Unity.

---

### Post by ibjsb4 on 2013-02-17
Can't you just right click on FF panel and add meun bar?

---

