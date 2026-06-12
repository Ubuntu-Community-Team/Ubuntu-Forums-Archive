---
title: "Software Management missing in System Settings"
date: 2011-11-08
forum: Desktop Environments
---

### Post by Wolf-Ekkehard on 2011-11-08
I just did a clean new install of a 32 bit Kubuntu 11.10 from DVD on an old machine and noticed right away that the Software Management icon was missing in the System Settings panel.  Everything else seemed to be working fine.  Since I had not done anything with that machine yet, I just re-installed (wanted to re-do the partitioning anyway) - same problem :-( - at least we have consistency ;-)

Could anybody please shed some light on this as to how that could have happened (just for my education) and, probably more importantly, how to fix it?

Of course, there is always synaptic and most of my installs I do using apt-get if I know what I need, but it would just be nice to have the proper tools available and know what is going on.

---

### Post by mister_playboy on 2011-11-16
We have two GUI apps, Muon package manager and Muon software center, on 11.10.  Both can be found under Applications > System.

---

### Post by Wolf-Ekkehard on 2011-11-16
Thanks mister_playboy,

the muon software center is what I was expecting to see in the "System Settings".  I guess that gets me 90% there as this is the tool I wanted to use - I just didn't know what it was called.  For the remaining 10%, would you know if there is any configuration file for the System Settings (found under "Favorits") that I could hack such that the Muon Software Center shows up there as "Software Management" as it does on all of my other machines?  There is an Editor for the "Applications" tab but not for the "Favorits" tab and its "System Settings" submenu.  But from here on it is mainly "just cosmetics".

---

### Post by mister_playboy on 2011-11-16
My guess was that might be done by editing one of the files in ~/.kde/share/apps or ~/.kde/share/config, but I don't see any file apparently related to the System Settings.

Maybe someone more knowledgeable could give you a clearer answer. :)

---

### Post by Wolf-Ekkehard on 2011-11-16
yup - I had looked there earlier - and in ./config - to see if there was anything remotely related to System Settings that I could diff to the other machines where it is working fine - but with no luck.  Any KDE gurus out there?

Again, at the moment this is mostly cosmetic, but I'd just like to know...

---

### Post by marcgarsan on 2011-11-17
You have to install kpackagekit.

---

### Post by Wolf-Ekkehard on 2011-11-17
Yo Dude - you're a genius!  That did the trick.

Thanks a bunch!!!

---

