---
title: "simple wine question"
date: 2006-08-11
forum: Desktop Environments
---

### Post by computergroove on 2006-08-11
I installed wine and I would like to add a shortcut the the virtual drive c to be kept on my desktop. Any suggestions? Is there something similair to internet explorer with an address bar that I could just manually enter the location of the directory I would like to view in a GUI?

---

### Post by JerMe on 2006-08-12
Your whole "virtual windows" is contained within the .wine folder in your home directory.  So if you'd like, browse around your ~/.wine/ directory and set a shortcut to wherever you'd like to.

---

### Post by computergroove on 2006-08-12
Is there a program that I am not aware of that will "let me browse around"? The only thing I have fornd is firefox to browsy my root directory structure - which doesnt work very well.

---

### Post by JerMe on 2006-08-12
Use Nautilus (the explorer version of GNOME.)  Open your home directory, then hit Ctrl-L and add the .wine at the end.  So for me, it'd look like

/home/jerme/.wine/

You'll see the drive_c folder, which is essentially your "C:\" drive in wine.

---

### Post by goatflyer on 2006-08-12
Yes.

rightclick somewhere blank on your desktop
select Create Launcher
name is drive_c
type is Link
url is /home/yourusername/.wine/drive_c/
choose an icon image from one of the offered
click Ok

---

