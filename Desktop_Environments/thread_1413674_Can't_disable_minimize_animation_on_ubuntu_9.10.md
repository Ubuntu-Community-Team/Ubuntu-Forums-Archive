---
title: "Can't disable minimize animation on ubuntu 9.10"
date: 2010-02-22
forum: Desktop Environments
---

### Post by cnicog on 2010-02-22
I already tried disabling the animations under gconf editor and it won't work.. 

I tried under metacity, gnome interface, apps, whatever.. and I can still see the black animated square when minimizing....

any ideas of whats wrong?

---

### Post by koleoptero on 2010-02-22
If you have desktop effects enabled then compiz is responsible for the animations, so you'll have to edit its settings. You'll need to install compizconfig-settings-manager for that, so enter in a terminal:

sudo aptitude install compizconfig-settings-manager

And after the install hit alt+f2 and run compizconfig-settings-manager. It has somewhere the window animations plugin where you can configure it to act as you want.

---

### Post by cnicog on 2010-02-22
I have no visual effects enabled (None selected) under the appearance options but I downloaded the compizconfig settings manager anyways and disabled the animation under effects and I can still see the windows animated while being minimized...

Why is it not taking into accoutn my settings anywhere?

---

### Post by koleoptero on 2010-02-22
Well if you don't have desktop effects enabled then the compizconfig settings manager won't do anything about it so you can uninstall it again. It looks like a metacity issue.

---

### Post by cnicog on 2010-02-22
Do you know of any other window manager that is really simple? that I could use instead of metacity?

thanks

---

### Post by koleoptero on 2010-02-22
The best choice is to enable desktop effects. That will make compiz as the window manager. Then you can disable all window animations if you like from the settings manager. Or you can set them all to be a fast fadeout (I like that best). If you think it's too heavy for your PC you can disable any plugins you don't like, but if you have a PC that's at most 5 years old it should run fine. :)

Other than that you can use openbox on top of gnome but I wouldn't recommend it unless you're feeling particularly adventurous.

---

### Post by -VladV- on 2010-07-10
Just for the record, here is a thread with a solution: [http://ubuntuforums.org/showthread.php?t=175976](http://ubuntuforums.org/showthread.php?t=175976)

---

