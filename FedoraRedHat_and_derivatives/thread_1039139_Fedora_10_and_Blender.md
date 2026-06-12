---
title: "Fedora 10 and Blender"
date: 2009-01-14
forum: Fedora/RedHat and derivatives
---

### Post by demosthene1 on 2009-01-14
I run Blender very smoothly in Ubuntu, Slax and Puppy on my emachine. I am experimenting with Fedora 10 and like it but it will not run Blender correctly. Blender runs the 3d window just fine and renders the default box model with no problem, but the menus and buttons are distorted and buggy. Fonts are distorted, images in buttons are missing, the texture preview window is squashed down, making Blender unusable.

Anyone have this experience and discovered a solution?

---

### Post by Simian Man on 2009-01-15
It seems to be working fine for me.  Do you have hardware drivers for your video card installed?  Are you able to turn on Compiz?

---

### Post by demosthene1 on 2009-01-15
I didn't think I needed any special drivers because on the same machine Ubuntu and Puppy run Blender just fine. And when I'm in Fedora 10 all seems fine but for Blender. I haven't run compiz, I don't use any desktop effects. I made SElinux permissive because it seemed not to like something with Blender, but that made no difference. 

Also, the 3D window works fine in Blender running in Fedora 10, it is just everything else that's screwed up! Strange.

Thanks for the reply.

---

### Post by demosthene1 on 2009-01-15
I fixed it. Fedora 10 does not come with an Xorg.conf file so I created one and set it to run standard VGA. It works!

---

