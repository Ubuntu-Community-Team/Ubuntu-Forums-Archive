---
title: "compiz no cube"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by metzy85 on 2007-10-31
ok so i have been trying to configure my compiz to like beryl but like the compiz will nto make a cube. I ahve found how to do it online and it will not work all i have is two desktops that i can flip back and fourth how can i fix this

---

### Post by Zorael on 2007-10-31
General Options -> Desktop Size

Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 1

You may need to start compiz with the --ignore-desktop-hints argument if you end up with a whole lot more than 4 sides.

---

### Post by metzy85 on 2007-10-31
sadly i still have no cube. Y could they not jsut keep beryl that worked and was easy to configure this is hard no very user friendly

---

### Post by theelk801 on 2007-10-31
I had the same problem, You have to install the control panel.
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Zorael on 2007-10-31
Configured as mentioned and having activated both the Desktop Cube and the Rotate Cube plugins, I don't see how you don't get a cube.

The number one (1) error is having erroneously set Number of Desktops to 4, rather than Horizontal Virtual Size. The second is not having started Compiz, but seeing as you have two desktops - like a flat screen you can rotate, yes? - you obviously have it running.

But given the benefit of the doubt, you could have encountered some bug.

As things grow in facets, they grow in options. You're free to add [Treviños repositories](http://3v1n0.tuxfamily.org) and install Beryl, if you wish. It may or may not work in Gutsy.

---

### Post by Zorael on 2007-10-31
> **theelk801 said:**
> I had the same problem, You have to install the control panel.
```
sudo apt-get install compizconfig-settings-manager
```

Well, that goes without saying. If you don't have the settings manager, you can't set the virtual desktop size.

---

### Post by Gremlinzzz on 2007-10-31
Good easy to follow guide
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by theelk801 on 2007-10-31
I didn't realize that he had the panel already.

---

### Post by metzy85 on 2007-10-31
ok i have to try it but i have another question on totally different topic. I want a dock like mac osx dock how do i do that

---

### Post by themusicwave on 2007-10-31
Add these repositories:

System ->Administration -> Software Sources -> Third Party -> add
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

Run these in terminal for the public key

wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update


Get avant-window-navigator from the repositories.

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

It should be set

---

### Post by metzy85 on 2007-10-31
ok thanks to u and thanks to the guys about i have got the new version working pretty good. Starting to like it thanks guys

---

### Post by metzy85 on 2007-10-31
ok so like i have no idea how u told me to install the dock i am lsot i tried but i could not add the repository

---

