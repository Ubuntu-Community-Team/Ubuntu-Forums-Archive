---
title: "Funny screen resolution in Virtual Box"
date: 2009-03-07
forum: General Help
---

### Post by unplugged23 on 2009-03-07
Hey there,

I'm trying to set backtrack 4 to run out of virtual Box OSE, It runs fine, my only problem is that it uses some weird screen resolution. While its starting up it looks fine, and takes up the entire screen, but once I get to the KDE desktop, the screen shrinks to about half the size. Ill post some pictures below. By the way, I have the O.S. set to linux kernel 2.6 and I'm running of of an ISO image. I also have it set to the PIIX 4 IDE controller. Hopefully this helps.[IMG]http://img27.imageshack.us/img27/5798/screenshotbt4runningvir.png[/IMG][IMG]http://img18.imageshack.us/img18/5798/screenshotbt4runningvir.png[/IMG]

Does anyone know what I should do to fix this? I could always change the monitor settings but it would be a pain to change back and forth for BT4 and ubuntu, there has to be another way. Any ways, thanks in advance!

---

### Post by unplugged23 on 2009-03-07
I used the auto adjust feature on my monitor, to maximize the screen size on backtrack 4, and here are the results: [IMG]http://img5.imageshack.us/img5/5798/screenshotbt4runningvir.png[/IMG] You can see how conky kind of runs off the screen, like it knows the screen should/can be bigger. Any solutions?

---

### Post by kylepotts on 2009-03-07
Have you installed the Vbox guest additions in the OS

---

### Post by unplugged23 on 2009-03-07
> **kylepotts said:**
> Have you installed the Vbox guest additions in the OS

Whats that and how do I install it?

---

### Post by kylepotts on 2009-03-07
Vbox gues additions are drivers for your guest OS so you can get full screen 

You boot up the system and on virtual box go to devices and install guest additions

Virtual box will download an ISO file and set it up as a removable media

Heres a picture of it
[IMG]http://i160.photobucket.com/albums/t182/punkkid219/instalguest.png[/IMG]

here is a guide how to do it in ubuntu [http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

---

### Post by unplugged23 on 2009-03-07
When I try to download this file from the virtual box prompt, it tells me the connection times out, but when I click on the link to the location of the iso, it downloads from my browser just fine. any ways now I have the guest additions iso but no way to use it, seeing as I can't modify virtual box files to place it in the correct place, and I can't download it from virtual box. so where do I go from here?

---

### Post by unplugged23 on 2009-03-09
Bump :D

---

