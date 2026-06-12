---
title: "Unity Super+D Shortcut not working in Ubuntu 11.10"
date: 2011-10-27
forum: Desktop Environments
---

### Post by lads on 2011-10-27
Hello everyone,

This morning I ran down the [shortcut list]("http://www.ubuntugeek.com/list-of-ubuntu-unity-keyboard-shortcuts.html") to see what is working and what is not; and Super+D is the only one that doesn't do what it should. Any ideas why? 

Thanks.

---

### Post by lads on 2011-11-03
I've been running daily upgrades in the hope that this and other issues get solved, but no luck so far.

Today, trying to get windows to move across workspaces, I found out that [the Compiz Put plug-in doesn't work either]("http://ubuntuforums.org/showthread.php?t=1874438"), after experimenting with several different key combinations. Can this be related to the lack of the Super+D shortcut?

Also, I'm using a strange Suiss-German keyboard, could it be the cause?

Thank you.

---

### Post by stinkeye on 2011-11-03
Not related to the Super+D shortcut.
Just a bug.
They changed the key back to ctrl+alt+d.
You can change it to Super+D in 
ccsm > general options > key bindings

---

### Post by lads on 2011-11-03
Thank you stinkeye. I went to CCSM and changed the key combinations as you suggested, but it had no effect.

---

### Post by stinkeye on 2011-11-03
Try to change it in keyboard shortcuts as well.
Under navigation > hide all normal windows

---

### Post by lads on 2011-11-04
Hi stinkeye, I don't have a *Navigation* item at CCSM. Do I need to install something else, or is the item somewhere else?

Thank you.

---

### Post by stinkeye on 2011-11-04
> **lads said:**
> Hi stinkeye, I don't have a *Navigation* item at CCSM. Do I need to install something else, or is the item somewhere else?

Thank you.
Open up the dash (Super key) and type in **shortcut**.
Click on the keyboard icon and then the shortcuts tab.
You'll find **Hide all nornal windows** under the **navigation** heading.

---

### Post by lads on 2011-11-04
Thank you stinkeye, now it works. This overlapping between Compiz and the traditional settings is a bit confusing.

---

