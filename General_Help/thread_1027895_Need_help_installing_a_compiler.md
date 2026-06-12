---
title: "Need help installing a compiler"
date: 2009-01-01
forum: General Help
---

### Post by wildman4god on 2009-01-01
My brother has an old computer running Xubuntu 8.10 the computer is so old it didn't have an Ethernet card in it so he when out and bought a cheapy no name brand nic that came with the Linux drivers on a floppy (finally figured out how to get the floppy working) well now we need a c compiler to install the driver but he doesn't have internet because obviously his nic isn't working yet. So the only thing we can do is download files from my computer-put them on a flash drive and transfer them to his computer. I was going to do this for the compiler but there are so many dependencies I don't know which ones to download, I click on one dependency and that one has a dozen more and so on, can anyone give me a suggestion on how to get the compiler on his computer with no direct net access. Is there a package that has all the depends with it or at the lest can someone provide me with a list of what to get for a fresh (nothing installed beyond the live CD installer) install of Xubuntu 8.10. any help would be appreciated.

---

### Post by adult swim on 2009-01-01
[http://packages.ubuntu.com/intrepid/devel/build-essential](http://packages.ubuntu.com/intrepid/devel/build-essential)
this should take care of you
EDIT:  build-essential is also on the live cd, so if you have the cd checked as a repository source you should be able to just run ```
sudo apt-get install build-essential
``` with the cd in the drive.

---

### Post by wildman4god on 2009-01-01
> **adult swim said:**
> [http://packages.ubuntu.com/intrepid/devel/build-essential](http://packages.ubuntu.com/intrepid/devel/build-essential)
this should take care of you

No all it downloads is a 7 Kb file that tells synaptic to download the other depends i went to download the depends as well but same problem as before each depend has 4 or 5 more and so on and so on in a vicious cycle.

Thanks anyway.

oh thanks i replied before your edit, i'll give it a try.

---

### Post by adult swim on 2009-01-01
> **adult swim said:**
> 
EDIT:  build-essential is also on the live cd, so if you have the cd checked as a repository source you should be able to just run ```
sudo apt-get install build-essential
``` with the cd in the drive.
you were too fast for my edit!

---

### Post by taurus on 2009-01-01
Insert the CD into a drive.  Then, open a terminal and run

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

