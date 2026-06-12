---
title: "stopping the beep."
date: 2006-08-26
forum: Desktop Environments
---

### Post by kakashi on 2006-08-26
hi.
i want to setop linux from beeping everytime i press tab to complete a filename or a commansd. it uses my motherboards speaker so i can just mute my speaker. how do i prevent this.

---

### Post by Ronbo on 2006-08-26
Click on *System->Preferences->Sounds*  click on the 'System Beep' tab and uncheck the box that says 'Enable System Beep'  and that should stop it.

---

### Post by kakashi on 2006-08-26
> **Ronbo said:**
> Click on *System->Preferences->Sounds*  click on the 'System Beep' tab and uncheck the box that says 'Enable System Beep'  and that should stop it.
thanks

---

### Post by az on 2006-08-26
If that does not work (it does not work for the console) blacklist the pcspkr module.

---

### Post by kakashi on 2006-08-26
> **azz said:**
> If that does not work (it does not work for the console) blacklist the pcspkr module.

umm how do i blacklist a certain module ?
sorry for the noob question

---

### Post by az on 2006-08-26
First see if it does the trick:

sudo rmmod pcspkr

and then try to make it beep.

If that's the case, then add the line

blacklist pcspkr

to /etc/modprobe.d/blacklist

---

### Post by kakashi on 2006-08-26
thanks. that did the trick.

---

