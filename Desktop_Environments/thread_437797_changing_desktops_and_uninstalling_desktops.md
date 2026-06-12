---
title: "changing desktops and uninstalling desktops"
date: 2007-05-09
forum: Desktop Environments
---

### Post by rufi_dukes on 2007-05-09
i've just installed Xubuntu, after trying gnome and kde;
as a result, i've used about 6 gig of a precious little 20gig;

2 questions:
1)how do i switch betw. desktops? do i have to go back to login prompt each time?
and:
2) can i safely dump kde and gnome to free up space, if i should choose to go with Xubuntu?
if so, how do i do it cleanly and simply (if possible, as i am a real beginner!)
thx for taking time to read this,

rufio

---

### Post by Kobalt on 2007-05-09
1. Yes, you need to log out, select your session (KDE, Gnome or XFCE) and then log back in in order to change your desktop environment.
2. You can easily remove these environment with such commands as : ```
sudo aptitude remove kubuntu-desktop
```

More info on removing Gnome, KDE or XFCE see the "Pure *xxx*" sections of this good guide : [http://psychocats.net/ubuntu/](http://psychocats.net/ubuntu/)

---

### Post by rufi_dukes on 2007-05-09
merci beaucoup, c'est gentil de vous de m'avoir repondu
please excuse my spontaneous outburst of french (mais ca fait du bien de le parler de temps en temps)

now i'll have a little play with all 3 environments avant de choisir....(heeheeeheee)

thx once again,
rufio

---

### Post by mcduck on 2007-05-09
> **Kobalt said:**
> 
2. You can easily remove these environment with such commands as : ```
sudo aptitude remove kubuntu-desktop
```


That only works if they were installed with Aptitude in the first place.

---

### Post by rufi_dukes on 2007-05-09
i think i installed them using synaptic...
cd u give me a solution for uninstalling ?
thx,

---

### Post by mcduck on 2007-05-10
If you are running Edgy or Feisty you could try to uninstall the kubuntu-desktop package, and then see if all the kde stuff appears under 'Autoremovable' section in Synaptic. It *should*. Then repeat the same for Gnome.

If that doesn't work, try this: [http://psychocats.net/ubuntu/purexfce]("http://psychocats.net/ubuntu/purexfce")

Which ever way you do it, check the lists of packages to be removed and make sure you don't remove any applications you wish to keep, like OpenOffice or Amarok.

---

### Post by rufi_dukes on 2007-05-10
thx again to all who have posted responses here and elsewhere over the past few days;
been avidly reading and saving all this input against the day of decision when, out of the blue, my monitor died....

i'm writing this from a local library while i wait for a friend to bring me a spare monitor of hers...

hope to back in action on sunday...

thx again, to one and all: my first experience of linux has been made all the richer for your generous and timely support

rufus

---

