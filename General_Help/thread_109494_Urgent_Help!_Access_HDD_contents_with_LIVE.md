---
title: "Urgent Help!: Access HDD contents with LIVE"
date: 2005-12-28
forum: General Help
---

### Post by thermopyl on 2005-12-28
Hi
I have two pc's...one using Ubuntu (main pc), one using XP (backup/File server).
My XP installation has become corrupted; even a reinstall of windows itself fails with a fatal error. I have content on the HDD that I must retrieve and therefore cannot reformat the drive to reinstall XP (the plan has been to install ubuntu on this drive...).

Can i use the Live CD to gain access to the HDD and copy files over the network to my main pc?

If not, can anyone suggest a way of using ubuntu (either on a USB? or other media) to do this?

your help would be really appreciated

---

### Post by Jammy_Stuff on 2005-12-28
I've used knoppix to retrieve data from a broken installation of windows before so I don't see why a Live CD of Ubuntu wouldn't.

---

### Post by Bachstelze on 2005-12-28
Indeed, it will work fine, but you'll have to mount your drive manually, while Knoppix oes it automatically.

---

### Post by thermopyl on 2005-12-28
argghh!

I have tried to boot from the live cd but it freezes at 'checking battery state'!!! a little googling returns that i need to 'please boot with bootparameter: acpi=off' although i have no idea how to do this??

any pointers guys please?

btw, knoppix d/ling but would rather stick with Ubuntu

---

### Post by Bachstelze on 2005-12-28
when you get the very first prompt, instead of just pressing enter, type this :

```
linux acpi=off
```

---

### Post by thermopyl on 2005-12-28
thanks for the quick reply...

...however this starts of the installation of ubuntu whereas i am only after a 'live' bootup...

is there a different command for the live boot up with the acpi flag?

ta

---

### Post by Bachstelze on 2005-12-28
If you downloaded a live CD, it is live even if at the beginning it asks for your language settings like for install. (In fact, a live CD installs the system on a virtual disk on your RAM.)

---

### Post by thermopyl on 2005-12-29
thanks hymn for the reply

however, i have the ubuntu dvd image not a dedicated live cd. this means if i use the linux command the installation starts not live

anyway i have done it with Knoppix!

---

### Post by anil_robo on 2005-12-29
I can only hope that the LIVE CD for Dapper would automount all the hard drives by default. It saves a lot of effort - and a live cd then truly doubles as a rescue CD as well!

---

