---
title: "XGL weirdness"
date: 2006-12-23
forum: Desktop Environments
---

### Post by Moisteh on 2006-12-23
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

im following that guide to get XGL and Beryl on my ubuntu machine.

I added all four of the listed repositories, just to be safe (in case a server closes, etc)

Then i do the normal synaptic install, then click reload, and here is where i hit a problem:

[code]
xserver-xgl:
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20 is to be installed
[code]

so logically, i 
[code]
sudo apt-get install 2.3.6-0ubuntu20
[code]

But i lack that package.

](*,) 

Any help?

(i am a noob at linux, smack me if this is something incredibly obvious)

---

### Post by iamhugeinjapan on 2006-12-23
2.3.6-0ubuntu20 is a version number, not a package name. libc6 is the package name.

---

### Post by iamhugeinjapan on 2006-12-23
Select libc6 in Synaptic Package Manager and then go to the **Package** menu and choose **Force version**.

I am running XGL/beryl and only have 2.4.1 installed and that's the only one available.

I'm only using the **[http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main**  repository

---

