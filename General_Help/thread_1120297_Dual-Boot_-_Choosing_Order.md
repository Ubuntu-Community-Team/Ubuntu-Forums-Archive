---
title: "Dual-Boot - Choosing Order?"
date: 2009-04-08
forum: General Help
---

### Post by bsta520 on 2009-04-08
I have dual boot ubuntu/vista... how or can i make it so vista is the first option in grub?  ubuntu is now the first option.

---

### Post by benj1 on 2009-04-08
install startup manager from the repos, you can change the default os from there

---

### Post by bsta520 on 2009-04-08
alright...what is repos?

---

### Post by sekinto on 2009-04-08
He means install it using Synaptic Package Manager (System > Administration > Synaptic Package Manager).

Although you don't even need startup manager to configure it. You can open your menu.lst file using gedit with administrator permissions ([alt+F2] gksudo gedit /boot/grub/menu.lst [enter]) and rearrange entries there. Although it would be a good idea to make a backup of the file encase your screw something up.

---

### Post by rage9 on 2009-04-09
There's this little awesome tool I like to use called kgrubeditor.  It'll do just what you want.  sudo apt-get install kgrubeditor

---

### Post by benj1 on 2009-04-09
> **rage9 said:**
> There's this little awesome tool I like to use called kgrubeditor.  It'll do just what you want.  sudo apt-get install kgrubeditor

note.
don't use this unless you use kubuntu, im guessing its the kde equivelent but youll have to download 100+ mb of dependencies on ubuntu.

---

### Post by bsta520 on 2009-04-09
alright thanks guys ill try some of these and be back if i have problems

---

### Post by rage9 on 2009-04-13
> **benj1 said:**
> note.
don't use this unless you use kubuntu, im guessing its the kde equivelent but youll have to download 100+ mb of dependencies on ubuntu.

Yeah you do have to download some dependencies, but if your Internet connection speed and the room, it's the best tool I've found.

---

