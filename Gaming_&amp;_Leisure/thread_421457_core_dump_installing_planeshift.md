---
title: "core dump installing planeshift"
date: 2007-04-24
forum: Gaming &amp; Leisure
---

### Post by regor210 on 2007-04-24
Just installed Feisty Kubuntu and I cant intall PLaneshift.
I use this to start planeshift as i have done 10 or more times with Edgy.

 sudo chmod a+x planeShift_CBV0.3.018.bin
 
 sudo ./PlaneShift_CBV0.3.018.bin
 
 The Planeshift installer starts then crashes giving me this Segmentation fault (core dumped)
 
 I tried down loading from 2 different sources and installing it, with no luck.
 
 It allways worked on Edgy.

The 2 computers I have tried to install planeshift on are using Feisty Kubuntu with Nvidia drivers. One is a Dell Dimension 4100 P3 with a 64M video GeForce2 and the other is a Dell Dimension 4600 P4 with a 128m GeForce4. The 3d drivers are working on both computers and work fine with other games.

---

### Post by regor210 on 2007-04-25
Ok here is the deal.
planeshift can be install in text mode using this

sudo chmod a+x PlaneShift_CBV0.3.018.bin

sudo ./PlaneShift_CBV0.3.018.bin --mode text

The bad news is, Don't put it in your /home/nameDir or it will mess up your permissions and it will not let you back in.

---

### Post by lordhebe on 2007-04-25
Or just don't run it as root.

---

### Post by regor210 on 2007-04-25
./PlaneShift_CBV0.3.018.bin

Still gives me a Segmentation fault (core dump).

Using 

./PlaneShift_CBV0.3.018.bin --mode text 

and installing planeshift in /home/"your name DIR"/planeshift

is the way to go. Iordhebe is right!

so to install planeshift use


sudo chmod a+x PlaneShift_CBV0.3.018.bin 

./PlaneShift_CBV0.3.018.bin --mode text

when the installer asks where to install it use

/home/"your name DIR"/planeshift

---

