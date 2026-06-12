---
title: "GTK in ALL applications......"
date: 2007-05-01
forum: Desktop Environments
---

### Post by Izobalax on 2007-05-01
Firstly: huzzah to Feisty! :) 

Installed yesterday after a break on Sabayon, and I'm totally lovin' it! Once I can get my screen resolution to show 1280x960 instead of 1024x768 (*I've noticed this seems to be a common problem with many at the mo*), all will be reet. :)

Anyway, I've just set my nice new GTK theme, yet the Synaptic Package Manager and GIMP and others are still using a rather basic, blocky theme. What's the command I need to enter in the terminal so that my GTK applies to ***all*** apps? I can't remember, and it's in the forum ***somewhere***.........

Thanks in advance, people. :)

/izo

---

### Post by ComplexNumber on 2007-05-01
are you using a theme that is stored in your home directory? if so, i don't see why it should apply to the gimp, although i know why it applies to synaptic.
you need to store your themes in /usr/share/themes so that root applications(eg synaptic and all other you enter a password to run them) can make use of the selected theme.

---

### Post by ayoli on 2007-05-01
Apps such as synaptics run as root, if your theme is in ~/.themes you can link this dir to your root home
```
sudo ln -sf ~/.theme /root
```
you may want link your icon theme also:
```
sudo ln -sf ~/.icons /root
```

---

### Post by Izobalax on 2007-05-01
> **ComplexNumber said:**
> are you using a theme that is stored in your home directory? if so, i don't see why it should apply to the gimp, although i know why it applies to synaptic.
you need to store your themes in /usr/share/themes so that root applications(eg synaptic and all other you enter a password to run them) can make use of the selected theme.
I didn't know that, personally. However, what I was looking for was this little gem below.......

> **ayoli said:**
> Apps such as synaptics run as root, if your theme is in ~/.themes you can link this dir to your root home
```
sudo ln -sf ~/.theme /root
```
you may want link your icon theme also:
```
sudo ln -sf ~/.icons /root
```

That's what I was looking for! \\:D/ 

Thanks to both of you. =D> 

/izo

---

### Post by ComplexNumber on 2007-05-01
> lzobalax
the result is exactly the same for both solutions. the main difference is that placing them in /usr/share/themes works 100% of the time.

---

### Post by ayoli on 2007-05-01
> **ComplexNumber said:**
> the result is exactly the same for both solutions. the main difference is that placing them in /usr/share/themes works 100% of the time.
this true, it's also a wide setting (available for all other users), but i have a separate partion for home and iam the only user of my laptop and prefer to store as much as possible my settings in it this is a facility for re-install or migrate. this just a choice :)

---

