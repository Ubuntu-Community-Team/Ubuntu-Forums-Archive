---
title: "cairo-dock -clock and show desktop"
date: 2009-02-14
forum: General Help
---

### Post by dyyyy on 2009-02-14
hi,
can i add to the cairo dock, a clock and a show desktop shortcut?
can you tell me also if it can be at 3D
thank you

---

### Post by fabounet on 2009-02-16
all of this is in the plug-ins.

---

### Post by kestrel1 on 2009-02-16
Go to the Applets section in the configuration of the dock. You will find the Clock in the top section & Show Destop in the next one.

---

### Post by dyyyy on 2009-02-18
the strange thing is that in my applet section
there is nothing, in all three parts

---

### Post by kestrel1 on 2009-02-18
How did you install Cairo-Dock?
Follow the instruction here:[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)
Sounds like you don't have the plugins installed.

---

### Post by dyyyy on 2009-02-18
i tried the way in your link it's the same,
one other thing is that in all the pictures i see the dock in 3D,
and on my Pc it's only on 2D, can't see where to change this.
thank you for ur help

---

### Post by kestrel1 on 2009-02-18
Did you add the source to your sources list as described in the link?
When you try to install the plugins do you get an error?

---

### Post by dyyyy on 2009-02-18
i installed now the .deb plugins from 
[https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=13311]("https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=13311")
i ran it,
and nothing happened

---

### Post by kestrel1 on 2009-02-18
I thibk your best bet would be to totally un-install Cairo-dock & re-install as per the instructions in the link I gave earlier.
Failing that try installing the deb file from the terminal. I will assume that the file is on your Desktop here: ```
cd Desktop
```
```
sudo dpkg -i 'filename.deb'
```
obviously change the 'filename.deb' to the name of the plugins file that you downloaded. If you get any errors post them.
To help identify the file so that you use the correct filename I normally type ```
ls
``` so that I can see the files that are currently in the directory that I just cd'ed to.

---

### Post by fabounet on 2009-02-20
[SIZE="4"]/!\ never install Cairo-Dock through the Ubuntu package, it is totally broken. /!\ [/SIZE]

use the official repository ;-)

---

