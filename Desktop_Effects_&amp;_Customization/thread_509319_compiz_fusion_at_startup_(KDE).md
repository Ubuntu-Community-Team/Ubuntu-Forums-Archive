---
title: "compiz fusion at startup (KDE)"
date: 2007-07-25
forum: Desktop Effects &amp; Customization
---

### Post by BDNiner on 2007-07-25
How do i get compiz fusion to startup on KDE, all the solutions i have found have been for gnome. And is there a more kde specific forum here? i know i can ask questions about any flavor of ubuntu, but there is not a lot of info/solutions for kde.

---

### Post by dreadlord_chris on 2007-07-25
> **BDNiner said:**
> How do i get compiz fusion to startup on KDE, all the solutions i have found have been for gnome. And is there a more kde specific forum here? i know i can ask questions about any flavor of ubuntu, but there is not a lot of info/solutions for kde.

open an editor - kate's a good one in KDE:
```

#!/bin/sh
compiz --replace

```
Save the file as _/home/.kde/Autostart/compizstart.sh_

If you'd like to use the Emerald theme engine then change add **-c emerald** to the end of the *compiz --replace* line....

Now Compiz should start whenever you log into your KDE desktop...

---

### Post by Happy_Man on 2007-07-25
For KDE solutions, you could try [http://kubuntuforums.net](http://kubuntuforums.net).

---

### Post by hyperair on 2007-07-25
You should save it in /home/YOURUSRENAME/.kde/Autostart/compizstart.sh.

---

### Post by dreadlord_chris on 2007-07-25
> **hyperair said:**
> You should save it in /home/YOURUSRENAME/.kde/Autostart/compizstart.sh.

:oops:: good catch

---

### Post by Tyl3r on 2007-07-25
I recommend using compiz-icon, or fusion-icon which is more simple.
Download:
[http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=f0842e0866671232531debdce57417d9d5342d89](http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=f0842e0866671232531debdce57417d9d5342d89)
once in fusion-icon folder just type "*sudo make install*".
Now you need to start fusion icon at kde startup with:
```
sudo ln -s /usr/bin/fusion-icon /$HOME/.kde/Autostart/fusion-icon
```

In this way you'll not only start compiz fusion, but you can switch from the decorators or reload compiz if it crashes.

---

### Post by BDNiner on 2007-07-25
> **Tyl3r said:**
> I recommend using compiz-icon, or fusion-icon which is more simple.
Download:
[http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=f0842e0866671232531debdce57417d9d5342d89](http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=f0842e0866671232531debdce57417d9d5342d89)
once in fusion-icon folder just type "*sudo make install*".
Now you need to start fusion icon at kde startup with:
```
sudo ln -s /usr/bin/fusion-icon /$HOME/.kde/Autostart/fusion-icon
```

In this way you'll not only start compiz fusion, but you can switch from the decorators or reload compiz if it crashes.

Now i lost my windows decorations, how do i undo this. can i just delete the files?

---

### Post by BDNiner on 2007-07-25
> **dreadlord_chris said:**
> open an editor - kate's a good one in KDE:
```

#!/bin/sh
compiz --replace

```
Save the file as _/home/.kde/Autostart/compizstart.sh_

If you'd like to use the Emerald theme engine then change add **-c emerald** to the end of the *compiz --replace* line....

Now Compiz should start whenever you log into your KDE desktop...

This worked for me, thank you. It took me a couple minutes to figure out that i had to change the permissions on the compizstart.sh file. Thank you again.

---

### Post by Tyl3r on 2007-07-25
> **BDNiner said:**
> Now i lost my windows decorations, how do i undo this. can i just delete the files?
Reload compiz or change decorator, these options are in fusion icon, it's very very easy.

---

### Post by BDNiner on 2007-07-25
Sorry, i uninstalled fusion-icon and went with the other solution. I will try your solution tomorrow and see if it works better. How do i launch the fusion-icon? I could not find the icon or shortcut anywhere and typing fusion-icon the run box thing did not do anything.

Thank you for your help.

---

### Post by Tyl3r on 2007-07-25
Weird, I have a menu entry in "System". fusion-icon is in /usr/bin, be sure you installed it properly.

---

### Post by PresidentJFJ on 2007-07-26
Thank you so much. I looked everywhere and this is the first thing that actually worked. :)

---

