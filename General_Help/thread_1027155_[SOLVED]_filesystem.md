---
title: "[SOLVED] filesystem"
date: 2009-01-01
forum: General Help
---

### Post by thingy87654321 on 2009-01-01
how do i add files to ubuntu filesystem, it says acess denied

i am trying to install new themes for amsn and i cant copy the files i need, please help

---

### Post by sofasurfer on 2009-01-01
Most files in Ubuntu, except for those in your /home folder, are protected. In order to add directories to them you need to use the sudo command to open your file browser, such as ... sudo nautilus or sudo konqueror. Or if you are going to create a file you may need to open an edit with sudo gedit for example.

I know nothing about themes but my point is that you need to be a super-user (root) to access most directories.

---

### Post by adult swim on 2009-01-01
to add/edit files owned by / you have to prepend your command with sudo.  if you are trying to drag and drop files you will need to launch nautilus with root priveleges which you can do by hitting alt+f2 and entering in ```
gksudo nautilus
``` BE VERY CAREFUL when you are doing this because if you move/change/delete the wrong files you can run into some big problems!

---

### Post by wmdiem on 2009-01-01
if you're doing it from a terminal, sudo su root
plus all the caveats about messing around as root

---

### Post by thingy87654321 on 2009-01-01
thanks, i know the sudo gedit command and i am thankful for now knowing this new one

---

### Post by MaxIBoy on 2009-01-01
Basically, use "gksudo" if you're running a graphical program.

---

