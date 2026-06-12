---
title: "Launcher shouldn't be this hard"
date: 2011-06-11
forum: Desktop Environments
---

### Post by asadullah on 2011-06-11
So I've been dual booting ubuntu on my laptop for a year now (gateway nv52). I really like how the new launcher looks even tried to go all the way ubuntu. Only thing is it's a pain trying to add things to the launcher. I know that it still has some kinks to work out and I can live with this but on the other hand I just dual booted a dell inspiron 6000 for my sister that could only run windows xp ( ubuntu made it look good ) So I'm asking how do you make shortcuts to other folders with the unity launcher?

Is their any way to theme the unity launcher? Where are the icon borders that it uses?
Is there a way to add folders to the files and folders shortcut?

[color="blue"]
Alright well I solved my first question. There are actually two ways to add a folder. What I did was type ```
gksu nautilus
``` into terminal then went to filesystem/usr/share/applications and copy pasted the home folder I right clicked it and opened properties changed the name to android then changed the command to nautilus /home/asadullah/Documents/android close that and drag and drop that onto the launcher. 
This is the same exact way to make a shortcut I just did it like that so I don't accidently erase the shortcut. I'm glad I got it figured out but I don't like having to go through all that [/color]

---

### Post by JRV on 2011-06-11
Right click on the desktop and select "Create Launcher".

The name you put in the box will be the name that will be displayed.

In the "Command" box put the command:
```
nautilus /path/to/folder
```

Move the launcher to a folder off your desktop.
(I use ~/.local/share/applications)

Then drag it to the launcher bar.

Hope this helps.

---

### Post by asadullah on 2011-06-11
Thankyou.

---

