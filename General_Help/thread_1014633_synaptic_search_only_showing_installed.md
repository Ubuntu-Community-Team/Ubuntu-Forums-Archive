---
title: "synaptic search only showing installed"
date: 2008-12-18
forum: General Help
---

### Post by brienzee on 2008-12-18
When I first open Synaptic it shows all the packets available, but when I search it only shows the installed packets. I've searched around a bit, but can't seem to find an answer that fixes the problem.

I'm running Xubuntu 8.10 on an MSI Wind, installed from a usb stick.
This problem has been present since the initial install (2 days ago), I've been just googling .deb files for anything i need installed at the moment.

Thanks in advance for your help.

---

### Post by Tim Sharitt on 2008-12-18
Goto the Settings > Repositories menu and make sure you have the downloadable sources checked, then hit reload in synaptic.

---

### Post by brienzee on 2008-12-18
those first 4 boxes are checked. 

it seems to be pulling the files up. they all seem to be there in the initial list. i can scroll through the 1000s of file names till i find the one i need.  but the search just shows whats installed. i dont have any filters on or anything in the search.

---

### Post by brienzee on 2008-12-19
does anyone else have any other suggestions?
i hate the thought of reinstalling, i've got everything just the way i like it. except being able to install files.

---

### Post by Elfy on 2008-12-19
sounds a bit odd - can you open synaptic, do a search then post a screenshot please

---

### Post by ShamanSTK on 2009-01-31
I started getting this too. I just did a fresh install of intrepid. The quick search only shows packages already installed and its getting to be a bit of a pain

---

### Post by ShamanSTK on 2009-01-31
sudo update-apt-xapian-index
does the trick

---

### Post by vauge on 2009-02-19
> **ShamanSTK said:**
> sudo update-apt-xapian-index
does the trick

Thank you!!

---

