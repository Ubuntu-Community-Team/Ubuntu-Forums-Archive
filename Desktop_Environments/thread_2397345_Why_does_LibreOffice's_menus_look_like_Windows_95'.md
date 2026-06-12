---
title: "Why does LibreOffice's menus look like Windows 95's in 18.04?"
date: 2018-07-28
forum: Desktop Environments
---

### Post by davidboom on 2018-07-28
After upgrading from 16.04 to 18.04 LibreOffice's menus look straight out of Windows 95?

See screenshot. Anyway to get them looking like they did in 16.04?

[[IMG]https://thumb.ibb.co/bXOYM8/Screenshot_from_2018_07_28_12_52_42.png[/IMG]]("https://ibb.co/bXOYM8")

---

### Post by ajgreeny on 2018-07-28
I am not sure exactly what you are complaining about so more detail of how it looked before might help.
Ubuntu 16.04 used global menus which placed them in the title-bar of most applications but not LO if I remember correctly; is that what you are asking about?

---

### Post by davidboom on 2018-07-28
Unfortunately I no longer have access to the old because it was upgraded to 18.04.

No it wasn't the global menus (although I really, really miss them!) See in the screenshot the File, Edit, View, etc are grey with blue highlighting, same for the column and row letters/numbers. In 16.04 these were nicely integrated into the same style as the OS, the dark background with orange highlighting (the same as if you right clicked on the desktop - the menu you see there).

Thanks

---

### Post by mc4man on 2018-07-28
Maybe because of the upgrade vs fresh install. You seem to be half ambiance, half adwaita themes. 
Maybe open gnome-tweaks, (install if not already), switch theme to adwaita, then switch back to ambiance (if that's what you want..

---

### Post by davidboom on 2018-07-28
Sorry - this was actually a fresh installation of 18.04 minimal install as opposed to a 16.04 to 18.04 upgrade. I did try the Gnome Tweaks setting change and revert but to no effect.

---

### Post by mc4man on 2018-07-28
> **davidboom said:**
> Sorry - this was actually a fresh installation of 18.04 minimal install as opposed to a 16.04 to 18.04 upgrade. I did try the Gnome Tweaks setting change and revert but to no effect.
No real idea, does this show anything of interest/related  (just a simulation
```
sudo apt -s install ubuntu-desktop
```

Also - check if LO is the .deb version or the snap version

---

### Post by davidboom on 2018-07-28
`sudo apt -s install ubuntu-desktop`

What does this do?

It is the snap version of LibreOffice, it is the same for LibreOffice Writer.

It could be it just looks like this in 18.04 since they removed Unity?

---

### Post by mc4man on 2018-07-28
> **davidboom said:**
> `sudo apt -s install ubuntu-desktop`

What does this do?

It is the snap version of LibreOffice, it is the same for LibreOffice Writer.

It could be it just looks like this in 18.04 since they removed Unity?
The apt command just simulates installing all ubuntu-desktop depends & recommends, i.e what a regular install would have installed.

snaps and .debs can co-exist, maybe install the .deb & see if it themes correctly.
 sudo apt install libreoffice-calc

Otherwise there could be some snap connect or snap theme related missing,  personally don't have snapd on this install.. run snap list & post..

---

### Post by davidboom on 2018-07-28
@mc4man

"ubuntu-desktop is already the newest version (1.417).
The following packages were automatically installed and are no longer required:
libfreehand-0.1-1 libpagemaker-0.0-0 libvisio-0.1-1"

Upon looking through the snap list it's not there, I must have been wrong - it must have been the non-snap package. It shows as installed on Ubuntu Software Center - BUT I can't find it anywhere in Synaptic Package Manager?!?

---

### Post by mc4man on 2018-07-28
> **davidboom said:**
> @mc4man

"ubuntu-desktop is already the newest version (1.417).
The following packages were automatically installed and are no longer required:
libfreehand-0.1-1 libpagemaker-0.0-0 libvisio-0.1-1"

Upon looking through the snap list it's not there, I must have been wrong - it must have been the non-snap package. It shows as installed on Ubuntu Software Center - BUT I can't find it anywhere in Synaptic Package Manager?!?
In synaptic search libreoffice-calc, if showing as not installed then install.
Then open with 
```
/usr/bin/libreoffice --calc
```

(- i've an install that still has gnome-shell & snapd, installed the snap, themes fine as does the .deb, screen shows. Notice the window menu item is just lightly highlighted. Weird that in gnome-shell menu items will not show in screenshot... , they still do in a unity session.

---

### Post by davidboom on 2018-07-28
Okay I have somewhat resolved this.

I have an 18.04 minimal install, and I was trying to just install the individual apps: Writer & Calc.

I could see LibreOffice and Draw as installed in Ubuntu Software Center - this is because some of these are dependencies of Writer/Calc.

So I removed LibreOffice, this removed everything - although software center still shows Writer/Calc/Draw as installed (until you reboot)

I then opted to install the full LibreOffice using:

```
sudo apt install libreoffice
```

I am guessing this then downloaded dependencies including the themes which you don't get if you just install Writer and/or Calc on their own.

---

### Post by ajgreeny on 2018-07-28
Great news! 

I aam glad you seem to have got this sorted.
Please mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by davidboom on 2018-07-28
Thanks - I have done that :D

---

### Post by mc4man on 2018-07-28
The  package theme wise was libreoffice-gtk3 though  libreoffice-gnome would also be useful.

---

