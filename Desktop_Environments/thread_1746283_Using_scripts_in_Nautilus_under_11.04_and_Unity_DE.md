---
title: "Using scripts in Nautilus under 11.04 and Unity DE."
date: 2011-05-01
forum: Desktop Environments
---

### Post by irv on 2011-05-01
When I used Nautilus in Ubuntu 10.10, I keep all my Nautilus scripts in .gnome2/nautilus-scripts directory and when I right mouse clicked on a file or directory I had an option to open with a script. How can I do this in 11.04 using Unity? Things changed there is no script option on the right mouse click menu any more. Is it possible to get this option back?

Under Unity it still uses Nautilus so I would thing this would be possible.
I put all my scripts back in .gnome2, so I am thinking they have to go in something like .unity or something like that. There is a .nautilus but it is empty.

EDIT: I marked this thread Solved.

---

### Post by efflux on 2011-05-09
I changed back to gnome from the log in window and I have the old location inside .gnome2 for nautilus scripts but they won't work.

To be honest, I see this release of Ubuntu as the death of Ubuntu. I've had masses of problems. I'm going back to 10.10 until I decide on an alternative distribution. Other systems I have now run Debian.

---

### Post by fjgaude on 2011-05-09
I'm not sure what's going on but I simply replaced my old nautilus-scripts root file with this one:

```
#!/bin/bash
# Opens a nautilus window as root.
gksudo nautilus
```

I did the same kind of thing with gedit and other similar scripts.

---

### Post by mc4man on 2011-05-09
There has been no great change in nautilus between 10.04 >> 11.04

See no problem creating and using nautilus scripts, same way, same location
There are 2 choices as far as nautilus-scripts-manager  packages, using the latest here (1.5-1

---

### Post by irv on 2011-05-09
> **fjgaude said:**
> I'm not sure what's going on but I simply replaced my old nautilus-scripts root file with this one:

```
#!/bin/bash
# Opens a nautilus window as root.
gksudo nautilus
```

I did the same kind of thing with gedit and other similar scripts.
Thanks for the tip, I went with script files also. Nautilus right mouse click menu doesn't even have a script selection on the menu. If no one know if this can be done, then I will give it a few more days then I will mark this thread solved because of the fact this can also be done with scripts.

---

### Post by mc4man on 2011-05-09
Really don't see any issue with ~/.gnome2/nautilus-scripts/
Works just like before, the r. click, 'scripts',  is available everywhere but in an app window
Ex.  - new install, just made one to open an album in audacious

---

### Post by irv on 2011-05-09
> **mc4man said:**
> Really don't see any issue with ~/.gnome2/nautilus-scripts/
Works just like before, the r. click, 'scripts',  is available everywhere but in an app window
Ex.  - new install, just made one to open an album in audacious

No Scripts available on mine:
[ATTACH]191715[/ATTACH]

---

### Post by irv on 2011-05-09
Oh ya, I have all my scripts files in .gnome2/nautilus-scripts:
[ATTACH]191716[/ATTACH]

---

### Post by mc4man on 2011-05-09
> **irv said:**
> No Scripts available on mine:
[ATTACH]191715[/ATTACH]
Clearly it isn't - 
I can't imagine it's the theme (though I use ambiance

What i'd probably do  - rename and move the nautilus-scripts folder somewhere for safe keeping
Completely remove nautilus-scripts manager in synaptic or apt-get purge, then log out/in
Re-install nautilus-scripts manager, open ~/.gnome2/nautilus-scripts and just to test - r. click > Create Folder
Then see if 'scripts' and it (untitled folder) shows up on the r.click

If so then move your scripts into the new nautilus-scripts folder and see if they also show up.
If so you can delete the untitled folder

---

### Post by irv on 2011-05-10
> **mc4man said:**
> Clearly it isn't - 
I can't imagine it's the theme (though I use ambiance

What i'd probably do  - rename and move the nautilus-scripts folder somewhere for safe keeping
Completely remove nautilus-scripts manager in synaptic or apt-get purge, then log out/in
Re-install nautilus-scripts manager, open ~/.gnome2/nautilus-scripts and just to test - r. click > Create Folder
Then see if 'scripts' and it (untitled folder) shows up on the r.click

If so then move your scripts into the new nautilus-scripts folder and see if they also show up.
If so you can delete the untitled folder

Well, I gave this a try, and back to square one.

---

### Post by nolo on 2011-05-12
Be sure to make your scripts executable otherwise the scripts option won't appear in your context menu.

---

### Post by irv on 2011-05-12
> **nolo said:**
> Be sure to make your scripts executable otherwise the scripts option won't appear in your context menu.

I had them all mark executable and they all had the check mark in the box, but it was grayed out. I selected them all and re-marked them and the gray went away and everything works. 
[ATTACH]191946[/ATTACH]

---

### Post by pmorton on 2011-05-19
Thanks for all the help on this, particularly nolo above.

Here's a recap:

Nautilus scripts work as normal in Unity. Locate scripts just as with gnome - in the directory  ~/.gnome2/nautilus-scripts.
Ensure they're all execute-enabled. The scripts option will appear as normal in Nautilus when a right click is made.

---

### Post by irv on 2011-05-19
> **pmorton said:**
> Thanks for all the help on this, particularly nolo above.

Here's a recap:

Nautilus scripts work as normal in Unity. Locate scripts just as with gnome - in the directory  ~/.gnome2/nautilus-scripts.
Ensure they're all execute-enabled. The scripts option will appear as normal in Nautilus when a right click is made.

Now that I have installed Gnome 3, it works there too.

---

