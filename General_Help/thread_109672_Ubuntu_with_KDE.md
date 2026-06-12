---
title: "Ubuntu with KDE"
date: 2005-12-29
forum: General Help
---

### Post by noeluylee on 2005-12-29
I just installed KDE and I liked it. 

Can I remove the gnome of this system? :-) as in the whole gnome, for space saving. I know I should install Kubuntu, but I already set up the system and I dont want to install from scratch again, :)

Thanks.


Noel

---

### Post by sunny_nwho on 2005-12-29
Yes I guess u can do that....by the way wht are the attractive features in KDE 3.5.....

---

### Post by adie273 on 2005-12-29
KDE 3.5 has some nicer transparency effects. You can also lock the taskbars now so you don't have applet handles all over the show, makes it look a lot cleaner.

I'm sure there's other stuff too, but I haven't use it an awful lot myself.

---

### Post by Drunken Pirate on 2005-12-29
I have two applet handles on my Gnome Panels. 
Just use synaptic to uninstall Gnome Base.

---

### Post by noeluylee on 2005-12-29
Lots of good stuff... looks kool :-)

But I cant find my shutdown option/button. I cant see it on my log off.

---

### Post by ed_d on 2005-12-29
You will need to install kdm vs gdm for the shutdown feature in KDE

---

### Post by Jeff Eklund on 2005-12-29
I think ```
sudo apt-get remove ubuntu-desktop
```should do the trick. Ubuntu-desktop is just a pseudo package containing links to alot of other packages that Ubuntu needs.

---

### Post by noeluylee on 2005-12-29
Where can I get that kdm vs gdm? I cannot find it on synaptics.

TY

---

### Post by ogregore on 2005-12-29
It (kdm) was probably installed when you installed kde.

Run:
             sudo dpkg-reconfigure kdm

in a terminal, then you should be able to choose your desktop manager.

Cheers
Ogre

---

### Post by noeluylee on 2005-12-29
Thanks so much. I got it. :)

Noel

---

### Post by digitalkarabao on 2005-12-29
or you can install kubuntu. :)

---

