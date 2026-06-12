---
title: "Beryl on 8.10"
date: 2008-04-03
forum: Desktop Effects &amp; Customization
---

### Post by coolgamer512 on 2008-04-03
I am using Wubi Ubuntu 8.10 Beta. How do you install Beryl on the new version of Ubuntu? 


I am quite a beginner at Ubuntu, but you can tell me to use terminal to open a text document and put something in it.

---

### Post by richiewrt on 2008-04-03
I prefer nano, but I am sure others have their own prefrences

at terminal

```
nano filename
```

---

### Post by Hospadar on 2008-04-03
Beryl is actually out of date, current ubuntu uses compiz, it's the newer version of beryl (beryl and compiz merged a while back, so now they're just compiz)

To turn it on, go to System->Preferences->Appearance->Visual Effects and set it to anything but the lowest setting.

If you want tighter control of compiz (turning on the cube, any number of other things) you'll need to install "compizconfig-settings-manager" from synaptic, then go to System->Preferences->Advanced Desktop Effects.

Also note, you'll need to have 3d acceleration for compiz to work properly, generally this means activating the restricted drivers in System->Administration->Restricted Drivers manager.  If you arn't sure about your video hardware, or if you get an error when you try to activate compiz, tell us what kind of video hardware you have and we can help you get it working.

As for text editing, nano is probably the easiest for simple edits, if you want to put in some time googling and learning, vim or emacs can be good choices too.  of course you can just open up gedit from the terminal if you are in a graphical shell "gedit <filename>"

---

### Post by coolgamer512 on 2008-04-03
well how do i run beryl?

---

### Post by oldos2er on 2008-04-03
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by Hospadar on 2008-04-03
If you want to run beryl, just run compiz, they are one in the same, check out the notice on the beryl homepage [http://www.beryl-project.org/](http://www.beryl-project.org/)

If you *really* want to run beryl, I suppose you could go grab it out of the fiesty repositories, but it's really the exact same thing with more bugs and less features.

---

### Post by lswest on 2008-04-03
> I am using Wubi Ubuntu 8.10 Beta. How do you install Beryl on the new version of Ubuntu?  just to point out, what you're using is the 8.04 Beta code-named Hardy Heron - not 8.10 code-named Intrepid Ibex, but that's just being picky :P and Yes, compiz-fusion has now replaced Beryl.  However, after you enabled it, you can get the same beryl effects with ```
sudo apt-get install compizconfig-settings-manager compiz-plugins
``` and then enable/disable things from system-->preferences-->advanced desktop effects.

---

### Post by coolgamer512 on 2008-04-03
i got it running now. Im just playing around with it. thanks

but i dont have any images for the cube. where can i get them?

---

### Post by lswest on 2008-04-05
by images, do you mean cube caps?  that's a seperate option under "cube caps" and you can specify new pictures for it.

---

### Post by Dev'olution on 2008-04-26
You have 8.10 already? :popcorn:

---

