---
title: "How to enable a real 3d desktop"
date: 2009-04-12
forum: Desktop Environments
---

### Post by Daniel Darwood on 2009-04-12
Hi all, i got a bit frustrated from the guides telling you how to install the 3d stereo anaglyph desktop, so i made one myself :D

This guide is as complete as i can get it and should include everything you need.

This plugin will allow you to view your desktop in 3d using the Red-Green glasses.

[IMG]http://www.icram.de/files/Bildschirmfoto-1.jpg[/IMG]

Here goes...

Create folder ".compizPlugins" in your home folder. (This will keep the folder hidden and out of your way)

Go to terminal...

sudo apt-get install ccsm (To install the compiz settings manager if not already installed)

sudo apt-get install git-core
sudo apt-get build-dep compiz
sudo aptitude install build-essential
sudo apt-get install libtool
sudo apt-get install compiz-dev
sudo apt-get install compiz-fusion-bcop

cd ~/.compizPlugins
git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
cd ~/.compizPlugins/anaglyph

make
make install

Go to System>>Preferences>>CompizConfig Settings Manager
Look for the anaglyph plugin, play.

Happy 3Ding :)


Please tell me if any of this is incorrect, i will update.

---

### Post by linuxuser21 on 2009-04-13
That's a new one.  Unfortunately, I don't have any red-green glasses laying around though.  lol.

---

### Post by demoflare on 2009-04-13
lol screenshot is hard on the eyes, but i can imagine how cool that is with those legendary cardboard glasses. (i wouldn't play openarena with that :o, might get a few stray bullets)

---

### Post by Mcalhoun on 2009-04-22
I'm a total noob here, but it was just located in cd ~/anaglyph.

I got the option in Compiz, turned it on and set the keys but it didn't work.  It's not that big a deal to me but I thought it was cool as all get out and had to try.

---

### Post by lvleph on 2009-04-22
You can't use stereograph glasses then? It doesn't look as though you need the red blue from your screenshot.

---

### Post by roshanjose on 2009-04-22
is it any way good to install it..and do we have to wear the red-green glasses to view it??

---

### Post by lvleph on 2009-04-22
I can't seem to get it to initiate just like Mcalhoun.

---

### Post by lvleph on 2009-04-25
No one?

---

### Post by lvleph on 2009-04-25
That is weird it works now, but you definitely need the red green glasses.

---

### Post by Jakey_TheSnake on 2009-06-26
> **lvleph said:**
> That is weird it works now, but you definitely need the red green glasses.

What did you do? 

Mine won't initiate either. 

NB - Sorry to bump an old topic guys.

---

### Post by bear24rw on 2009-06-26
Where do you get the glasses? And it would be sweet if we could make a plugin for Nvidias 3d glasses as there would be no color distortion (then again youd probably need a 120hz monitor :( )

---

### Post by eshwar_andhavarapu on 2010-04-08
> **bear24rw said:**
> Where do you get the glasses? And it would be sweet if we could make a plugin for Nvidias 3d glasses as there would be no color distortion (then again youd probably need a 120hz monitor :( )

here;s the glasses bit!

[http://paperproject.org/3dglasses.html]("http://paperproject.org/3dglasses.html")

---

### Post by smokyink on 2010-09-28
That looks very interesting! Thanks. Though I don't use Compiz :(

Does anyone know of any small app that does the same thing ?
Or should I go messing around with the source code & hope that I can manage to make it run without compiz ?

Btw you can also find plastic glasses on ebay... I just ordered a pair for just 1.5 $ :P

---

