---
title: "Panels Won't Show"
date: 2008-01-13
forum: Desktop Environments
---

### Post by aflog on 2008-01-13
Hey sorry to bother you's yet again but i have another problem....
Im currently using the 'root' user in Xubuntu 7.10. The main user called 'jden' doesnt seem to load the panels at the top AND bottom of the screen when i login. Ive tried opening the Panel Manager but it wont open. 

Any Ideas?

Thanks

Jayden

---

### Post by santiagoward2000 on 2008-01-13
> **aflog said:**
> Hey sorry to bother you's yet again but i have another problem....
Im currently using the 'root' user in Xubuntu 7.10. The main user called 'jden' doesnt seem to load the panels at the top AND bottom of the screen when i login. Ive tried opening the Panel Manager but it wont open. 

Any Ideas?

Thanks

Jayden

Hi!
There's no problem, ask all you want! :)
About the panels, try pressing Alt+F2 and type: ```
xfce4-panel
``` I think that should bring them back.

---

### Post by aflog on 2008-01-13
Thanks ill try that in a mo~

---

### Post by santiagoward2000 on 2008-01-13
> **aflog said:**
> Thanks ill try that in a mo~

You're welcome! Tell us how it goes!

---

### Post by aflog on 2008-01-21
Works great lol

Jden

---

### Post by btdown on 2008-01-22
I have the exact same problem. it used to happen periodically, and a reboot would fix it, but now it happens consistently and I am forced to log in via a very annoying KDE (Ubuntu why do you torture me so?)

Tabbing to a term and entering xfce4-panel brings up at:

(xfce4-panel:5887): Gtk-WARNING **:" cannot open display:

error. Any ideas? .

Tried re-installing nvidia-glx-new and gdm, but no go... :(

---

### Post by aflog on 2008-01-22
My problem was one of the things i had on the panel was causing it to crash everytime i touched the panel. Can i suggest removing things you've added to it and try periodically re-adding them and seeing which one causes the crash? (If thats the problem).

Oh one more thing... are you using XUBUNTU? If not then im not too sure that xfce4-panel will work as Ubuntu and Kubuntu isnt xfce... i dunno really... Also can take a restart to get it back to normal, because once i fixed it, my icons on it were huge...

Jayden

---

