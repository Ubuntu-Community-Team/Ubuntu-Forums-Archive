---
title: "Compiz Fusion no cube (did a search already)"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by 71CH on 2007-07-01
Hey all
Compiz Fusion installed fine and works fine.  I just can't seem to get the cube to work.  I have 4 workspaces set up and I can go to all the different workspaces using ctrl+alt (left or right) but I can't get the cube to pop out when I press ctrl+alt (mouse button1).  Am I missing something?

---

### Post by hyperair on 2007-07-01
When you use the Ctrl+Alt+Left/Right does it have any animation at all? If so, then make sure you have the Rotate Cube and Desktop Cube plugin enabled in CompizConfig Settings Manager

If not, then make sure that under General Options->Desktop Size in CompizConfig Settings Manager, make sure that your Horizontal Virtual Size = 4, Vertical Virtual Size = 1, and your Number of Desktops = 1.

---

### Post by steveneddy on 2007-07-01
Did you read t[his post]("http://ubuntuforums.org/showthread.php?t=486307")?

:popcorn:

---

### Post by 71CH on 2007-07-01
thanks for the responses
I can change workspaces just fine
I just can't make the physical cube
in beryl I could just hold down the scroll button and it'll pop up but no dice here

---

### Post by chronic on 2007-07-01
i had the same problem and i managed to fix it easily 

with compiz fusion you have 2 compiz settings managers one called conpizconfig settings manager and one called compiz settings manager. go into compiz settings manager and click reset all to defults.

i have no idea if this will work for you but it fixed my problem.

---

### Post by 71CH on 2007-07-01
> **chronic said:**
> i had the same problem and i managed to fix it easily 

with compiz fusion you have 2 compiz settings managers one called conpizconfig settings manager and one called compiz settings manager. go into compiz settings manager and click reset all to defults.

i have no idea if this will work for you but it fixed my problem.

how can you get to compiz settings manager?

---

### Post by ner0tic on 2007-07-01
compiz fusion does not use worksapces. it uses viewports.

set you're machine to 1 workspace and turn on cube and rotate cube via system->preferences->compiz settings manager.

do you have any of the other features working?

if not, do alt-f2 and enter > compiz --replace

---

### Post by chronic on 2007-07-01
> how can you get to compiz settings manager?

its under system >> prefences >> compiz settings manager

but do you have any effects at all?

---

### Post by 71CH on 2007-07-01
> **chronic said:**
> its under system >> prefences >> compiz settings manager

but do you have any effects at all?

all i see is compizconfig settings manager
pretty much all the effects work except for the cube

---

### Post by hyperair on 2007-07-02
Does Ctrl+Alt+LeftClick work for you?

---

### Post by 71CH on 2007-07-02
> **hyperair said:**
> Does Ctrl+Alt+LeftClick work for you?

nope

---

### Post by steveneddy on 2007-07-02
In Compiz Config Setting Manager you have to click the "ROTATE CUBE" check box.

---

### Post by 71CH on 2007-07-02
> **steveneddy said:**
> In Compiz Config Setting Manager you have to click the "ROTATE CUBE" check box.

already checked

---

### Post by jjross on 2007-07-02
Seems to be a few of us with the cube not working and I have not found any fixes for it yet.
All the settings are correct and some of the other compiz features work but not the cube.

---

### Post by 71CH on 2007-07-02
> **jjross said:**
> Seems to be a few of us with the cube not working and I have not found any fixes for it yet.
All the settings are correct and some of the other compiz features work but not the cube.

yea thats what it looks like

---

### Post by jjross on 2007-07-02
71CH
Take a look at this link and put the settings as shown and the cube works, but it is different than what we were used to in Beryl
[http://forums.opencompositing.org/download.php?id=141&mode=view]("http://forums.opencompositing.org/download.php?id=141&mode=view")

---

### Post by llamakc on 2007-07-02
I too had the same non-rotating problem. Restarting Compiz or logging out/in did the trick for me.

---

### Post by cymbolic on 2007-07-02
OK, had same problem, with all settings as described correct. Here is what I did to fix it.

Applications Menu, then system tools, then beryl manager, then select window manager, then click Beryl. Mine had got stuck on Metacity Gnome Manager, needed to be set back to Beryl...all good now.

---

### Post by 71CH on 2007-07-05
any updates?

---

### Post by kodoku on 2007-07-06
Here's what I did,

Under General Options -> Desktop Size -> Values are 4, 1 and 1 respectively

Then Under Desktop -> Check the following: Rotate Cube, Desktop Cube, and Viewport mouse switch.

Voila, the cube pops out with the scroll wheel.

---

### Post by dahoba on 2007-07-06
Thanx a lot. It's work! for me :D

---

### Post by NewJack on 2007-07-06
> **hyperair said:**
> When you use the Ctrl+Alt+Left/Right does it have any animation at all? If so, then make sure you have the Rotate Cube and Desktop Cube plugin enabled in CompizConfig Settings Manager

If not, then make sure that under General Options->Desktop Size in CompizConfig Settings Manager, make sure that your Horizontal Virtual Size = 4, Vertical Virtual Size = 1, and your Number of Desktops = 1.

Not to hijack, but wanted to thank hypeair.  Had the cube non-rotate problem and this did the trick!!!

---

### Post by 71CH on 2007-07-14
I think the problem might be with my mouse
does anybody know how to remodify the mouse settings on xorf (sp?)
or can somebody post the original mouse settings on there?

---

### Post by hyperair on 2007-07-15
Reconfigure your mouse eh, first make a backup of your /etc/X11/xorg.conf file, then run this command and answer all the questions:
```

sudo dpkg-reconfigure -plow xserver-xorg

```

---

### Post by 71CH on 2007-07-15
thx for replying can you teach me how to backup please
thanks

---

### Post by hyperair on 2007-07-16
Copy the /etc/X11/xorg.conf somewhere safe. You can do it using the default file manager.

---

