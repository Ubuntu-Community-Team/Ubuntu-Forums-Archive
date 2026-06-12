---
title: "Installing Amarok."
date: 2008-12-21
forum: General Help
---

### Post by Jerfo on 2008-12-21
So I just found out the newest version of Amarok is out there, I tried to install it following the instructions but nothing appears in Synaptic... could it be that it *has* to Adept? Anyway, if you could help me out here I'd really appreciate it.

Oh and since I'm already here, can you tell me how to make it so that Drivel detects the music being played, obviously on Amarok?

---

### Post by cdtech on 2008-12-21
> **Jerfo said:**
> So I just found out the newest version of Amarok is out there, I tried to install it following the instructions but nothing appears in Synaptic... could it be that it *has* to Adept? Anyway, if you could help me out here I'd really appreciate it.

Oh and since I'm already here, can you tell me how to make it so that Drivel detects the music being played, obviously on Amarok?

Which instructions did you use? Did you add anything to the repository to install it?

---

### Post by binbash on 2008-12-21
remove amarok , then

add this to your sources.list

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

then  :

sudo apt-get update && sudo apt-get install amarok-kde4

---

