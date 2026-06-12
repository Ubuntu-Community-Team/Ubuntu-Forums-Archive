---
title: "Covergloobus NOT working and having a border"
date: 2011-06-04
forum: Desktop Environments
---

### Post by Melophonic on 2011-06-04
So I just installed Covergloobus successfully, when I start it on. Looks like I should, like if no song is being played, but also has a the window border around it, which is not supposed to be there. And when I put on a song, it doesn't work, it's like if it didn't even respond. Covergloobus is although, responsive because when I touch the buttons inside it, it does react. Rating stars work, but not the >/II buttons.

[IMG]http://cl.ly/7K0b/gloobuslookingbadandnotworkingatall.png[/IMG]
What exactly do I want? I don't want the windows border to be around it and I want it to work, pretty much that.

Thanks for reading, hope somebody helps :)

---

### Post by webofunni on 2011-06-04
How you installed it ?

---

### Post by Melophonic on 2011-06-04
> **webofunni said:**
> How you installed it ?
I opened the .deb package, and clicked on "Install" ?
When I used $ gdebi covergloobus_1.7-6_i386.deb
Said I needed to be on root, and I was like "Uhm, what?"
Well, then I just decided to install it manually through the centre, clicking on "Install" button, saw it installed perfectly. And then, this happened. :(

---

### Post by Melophonic on 2011-06-04
Anyone? I really want to make Covergloobus work!

---

### Post by webofunni on 2011-06-04
Try following. 

```

sudo apt-get purge covergloobus
sudo apt-get autoremove
bzr branch lp:covergloobus
cd covergloobus
./autogen.sh
make
sudo make install

```

---

### Post by Melophonic on 2011-06-05
> **webofunni said:**
> Try following. 

```

sudo apt-get purge covergloobus
sudo apt-get autoremove
bzr branch lp:covergloobus
cd covergloobus
./autogen.sh
make
sudo make install

```
It worked! but the border is still there, is this because of Emerald? because I have it working, and I use it. The border on my screenshot, that's the .emerald.

---

### Post by webofunni on 2011-06-05
It should be, can you try changing the window manager ?

---

### Post by Dolsilwa on 2011-06-05
Hi, if you want to get rid of window border around covergloobus you should do that:

1. Go to compizconfig - window decoration (i'm not sure if it's proper english name - i'm using polish)
2. second from the bottom will be "window decoration" (next will be something like boarder shadow or window shadow) with value "any" -> change it to: 

(any) & !(class=Covergloobus.py)

now covergloobus on desktop will have no window decoration but also covergloobus configuration window will be boarderless (i think we can live with that).

---

### Post by Melophonic on 2011-06-05
> **Dolsilwa said:**
> Hi, if you want to get rid of window border around covergloobus you should do that:

1. Go to compizconfig - window decoration (i'm not sure if it's proper english name - i'm using polish)
2. second from the bottom will be "window decoration" (next will be something like boarder shadow or window shadow) with value "any" -> change it to: 

(any) & !(class=Covergloobus.py)

now covergloobus on desktop will have no window decoration but also covergloobus configuration window will be boarderless (i think we can live with that).
It actually worked! thanks! and yes the configuration is now borderless but I can live with that, and it still remains awesome. :)

---

### Post by webofunni on 2011-06-06
Mark it solved, if the issue is fixed

---

