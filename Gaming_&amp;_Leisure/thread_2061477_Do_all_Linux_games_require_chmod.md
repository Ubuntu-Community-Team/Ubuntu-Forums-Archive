---
title: "Do all Linux games require chmod?"
date: 2012-09-22
forum: Gaming &amp; Leisure
---

### Post by Holiday101 on 2012-09-22
Hi, coming from Windows I am accustomed to running an install exe and then being given a desktop icon/launcher for the game and that's all that's needed to play. First game I tried on linux required work to find the appropriate launcher file and chmod it. Is this standard? Running latest Ubuntu.

---

### Post by MG&amp;TL on 2012-09-22
> **Holiday101 said:**
> Hi, coming from Windows I am accustomed to running an install exe and then being given a desktop icon/launcher for the game and that's all that's needed to play. First game I tried on linux required work to find the appropriate launcher file and chmod it. Is this standard? Running latest Ubuntu.

This depends on whether it's been packaged or not. If it has been packaged (a bit like a windows exe), theoretically, everything should work out of the box. Packaged files will have a .deb extension. Just double-click, and they'll open in the software centre.

Some (less Linux-centric) companies or individuals simply give us a load of program files, and occasionally an install script. This requires you to make a launcher. Most file managers make new files without the executable bit set (the piece of any file that allows it to be executed), so chmod (or ticking the relevant option in the file manager properties dialog) is needed.

That help?

---

### Post by Holiday101 on 2012-09-22
Ah, thanks. I tried the Amnesia Dark Descent Demo and I was informed I should have received upon install a desktop icon launcher but never did. I had to find the .Desktop file in the program folder and chmod it. I might have did something wrong during the install. Or maybe something in Ubuntu I need to enable.

At any rate curious to see if games run better in Linux than my Win partition, so I've been testing it out.

Cheers

---

### Post by MG&amp;TL on 2012-09-22
> **Holiday101 said:**
> Ah, thanks. I tried the Amnesia Dark Descent Demo and I was informed I should have received upon install a desktop icon launcher but never did. I had to find the .Desktop file in the program folder and chmod it. I might have did something wrong during the install. Or maybe something in Ubuntu I need to enable.

At any rate curious to see if games run better in Linux than my Win partition, so I've been testing it out.

Cheers

Ah, you're one of the first of the expected gamer influx following the valve newsflash thing here: [http://blogs.valvesoftware.com/linux/]("http://blogs.valvesoftware.com/linux/"). Welcome!

---

### Post by Sealbhach on 2012-09-26
> **Holiday101 said:**
> Hi, coming from Windows I am accustomed to running an install exe and then being given a desktop icon/launcher for the game and that's all that's needed to play. First game I tried on linux required work to find the appropriate launcher file and chmod it. Is this standard? Running latest Ubuntu.

No it's not standard. That's not how applications are normally installed in Ubuntu.
 
Normally you install stuff using the package manager.

.

---

### Post by Asraniel on 2012-09-26
You can also just right click on the file and add the executable flag in its properties (at least using KDE), no need to open the console.

---

### Post by Rustybolts on 2012-09-26
> **Asraniel said:**
> You can also just right click on the file and add the executable flag in its properties (at least using KDE), no need to open the console.
Also with Gnome.
I'm glad someone pointed this out people never show the way to do anything via the gui and I think this puts a lot of inexperienced people off Linux by making it look daunting through use of the terminal.
Although it is much easier writing what to type in the command line rather than tell people what to click on and where.

---

