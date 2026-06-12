---
title: "mmorpg for ubuntu"
date: 2008-05-23
forum: Gaming &amp; Leisure
---

### Post by bribaetz on 2008-05-23
view the attachments the game says it would run but there is a problem my video card is ati rage or something and i think i either have the wrong drivers or to old of a graphics card but perhaps its the program i just downloaded the program from the site tar.gz extraced then at the end of the file put .deb

---

### Post by Crank Parity on 2008-05-23
'ATI Rage or something'? Do you still have the box you can look at?

---

### Post by bribaetz on 2008-05-23
no i do not the box i do not have in-fact i never had the box. the comp given to me where do i look at hardware at currently using fiesty

---

### Post by RIchard James13 on 2008-05-24
It just displays a dialog box with corrupted buttons on my system and when I click on the left one it segfaults. If you really want to play the game I suggest you ask some questions on their forum.

---

### Post by MaximB on 2008-05-24
Take the newest ATI drivers from here : [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Install them via command line (you must use "sudo" or be a root to install them).

1. download
2. go to that directory 
3. sudo ./nameofthatfile
4. restart the computer.

---

### Post by lswest on 2008-05-24
to find out what card you have run ```
lspci
lshw -C display
``` in the terminal, and post back the results.

---

