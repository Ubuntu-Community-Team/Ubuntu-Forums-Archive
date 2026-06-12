---
title: "XGL help please"
date: 2006-06-14
forum: Desktop Environments
---

### Post by rishubhav on 2006-06-14
I have tried many guides, and I keep getting > compiz.real: No composite extension. Before you ask I have added the extra thing to my config file. I'm running a Nvidia 6600 GT. Any help would be appreciated

---

### Post by Amon_Re on 2006-06-14
[QUOTE=rishubhav]I have tried many guides, and I keep getting . Before you ask I have added the extra thing to my config file. I'm running a Nvidia 6600 GT. Any help would be appreciated[/QUOTE]

In the terminal do: 

```
glxinfo | grep "direct"
```

If it awnsers with "direct rendering: yes" then your 3D driver is working, if not, get 3D to work first

If direct rendering works, make sure you execute gnome-window-decorator prior to running compiz.

There's a good deal of info on this on the wiki ([https://wiki.ubuntu.com/CompositeManager/InstallingCompiz?highlight=%28compiz%29]("https://wiki.ubuntu.com/CompositeManager/InstallingCompiz?highlight=%28compiz%29"))

---

### Post by rishubhav on 2006-06-14
I have direct rendering according to that.

When I do > gnome-window-decorator & as per the wiki I get:
> [1] 11037

Then when i run > compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher water & also as per the wiki I get > [2] 11088 and > compiz.real: No composite extension

again :confused:

---

### Post by Amon_Re on 2006-06-14
after gnome-window-decorator & type the following:

```
ps ax | grep "gnome-window-decorator"
```

You should get something simular:

```
 5301 ?        Ss     0:02 gnome-window-decorator
 7013 pts/0    R+     0:00 grep gnome-window-decorator
```

Note that the line with grep might not show up.

If you do not get this, then gnome-window-manager died before you executed this command (and logicly also before compiz).

---

### Post by rishubhav on 2006-06-14
I get this > 12006 pts/0    R+     0:00 grep gnome-window-decorator


---

### Post by Amon_Re on 2006-06-14
You have a problem with gnome-window-decorator crashing.

Try running it without the & sign, this will prevent it to detach, and might give you some clues why it crashes

---

### Post by patrickfromspain on 2006-06-14
ok, before you run compiz, try doing in a terminal:

glxinfo | grep direct

If it gives out Yes, then you aren't running Xgl, but plain X.org.

---

### Post by Amon_Re on 2006-06-14
[QUOTE=patrickfromspain]ok, before you run compiz, try doing in a terminal:

glxinfo | grep direct

If it gives out Yes, then you aren't running Xgl, but plain X.org.[/QUOTE]


Heh, now that you mention it, yea, xgl doesn't report with direct rendering: yes.
Sorry for the confusion

---

### Post by rishubhav on 2006-06-14
when I do that it just sits there with the cursor flashing Is this normal? Should I wait longer?

---

### Post by Amon_Re on 2006-06-14
No, your xgl isn't working like it should, you were using an nvidia card right? In that case i can't help you (ati slave here).

---

