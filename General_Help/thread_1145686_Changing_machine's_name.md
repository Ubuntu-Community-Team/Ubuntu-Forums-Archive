---
title: "Changing machine's name"
date: 2009-05-01
forum: General Help
---

### Post by luigi_mb on 2009-05-01
I am running Ubuntu v9.04 (gnome, desktop). I would like to change the name of my machine.  How? Could there be side effects? 

/luigi

---

### Post by doas777 on 2009-05-01
there won't be any side affects unless you use somthing like nfs sharing, since very little in terms of net services uses it. samba or ip based naming schemes are both handled elsewhere.

you can change your hostname by editing your /etc/hostname file:
```
gksu gedit /etc/hostname
```just put your new hostname in the first line of the file (delete the old one), save and close. 

now we need to change it again in your hosts file:
```
gksu gedit /etc/hosts
```
and where you see your old hostname, change it to your new. should be on the line that says 127.0.1.1. save and close.

you may need to reboot before you will see a change if you run the hostname command.

I think there is a gui tool that can do this, but I don't think it's installed by default, and I have never tried it, and I'm not sure it fixes your hosts file anyway.

good luck

---

### Post by drs305 on 2009-05-01
Edit both these files. Change the name to whatever you want (within reason of course!):
```
gksudo gedit /etc/hosts /etc/hostname
```

---

### Post by luigi_mb on 2009-05-02
> **drs305 said:**
> Edit both these files. Change the name to whatever you want (within reason of course!):
```
gksudo gedit /etc/hosts /etc/hostname
```

Thank you. Did as you and the previous poster suggested. Restarted system. ok!

/luigi

---

### Post by BslBryan on 2009-05-02
Any time you want to change it, make sure you edit both of these files at the same time. 

It would not be a pretty sight if you didn't. :)

---

### Post by doas777 on 2009-05-02
> **BslBryan said:**
> Any time you want to change it, make sure you edit both of these files at the same time. 

It would not be a pretty sight if you didn't. :)

I;ve had it happen with the network admin tool in feisty and hardy. if you open the admin tool, it renamed "hostname" to "hostname.domain.net" in my hosts.

all that I ever noticed was that sudo would not run, because it could not verify the machine name with a hosts query. but gksu still worked so i could fix it with gedit or geany.

annoying wot?

---

