---
title: "Cairo Dock Problem With OpenGL (ATI)"
date: 2009-12-17
forum: Desktop Environments
---

### Post by Mr.TAEL on 2009-12-17
Hi guys,

I installed Cairo Dock, but I have problem with running it via openGl. I have Dell Inspiron 6400 with ATI Mobility Radeon x1400 graphic card. When I run Cairo Dock (with openGl), it shows like this screen shot.

[IMG]http://kimag.es/share/47958579.png[/IMG]

What's the problem? What should I do or install ?

Regards.

---

### Post by fabounet on 2009-12-17
if you have the latest ATI drivers, you should probably run it with *cairo-dock -c*

---

### Post by danielesil on 2009-12-17
cairo-dock-o is the command to run it with openGL
Otherwise you can try with cairo-dock-c

If you can't fix it, you may want to install from source.
You need to install :
sudo apt-get install build-essential (so you have the compiler)
sudo apt-get build-dep  (so you have all the dependencies needed)

Then you go to the directory with "cd"
then
./configure
sudo make
sudo make install

Et voila !!!

---

### Post by mCion on 2009-12-18
if you go to system configuration within Cairo-dock you can turn on "emulate fake transparency"

I;ve heard that helps.

For me, also with an ATI card it takes care of the black backgrounf, but Im left with a Weird halo surrounding Cairo dock

---

### Post by fabounet on 2009-12-18
> a Weird halo surrounding Cairo dock
probably the shadow made by the WM

---

### Post by mCion on 2009-12-20
You're right.  Switching back to Metacity takes care of the Halo.

Still can't get OpenGL working fine though.  Using AWN for now...

Thanks

---

