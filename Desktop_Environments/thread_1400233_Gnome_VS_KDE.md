---
title: "Gnome VS KDE?"
date: 2010-02-06
forum: Desktop Environments
---

### Post by Alberonn on 2010-02-06
I've recently installed Ubuntu Karmic Koala and I noticed that I have the Gnome desktop. What is the big difference between Gnome and KDE???

---

### Post by wojox on 2010-02-06
Find out for youself. Open a terminal and run:

```
sudo apt-get update && sudo apt-get kubuntu-desktop
``` 

Then log out and when you log back in, look at the bottom of the GDM and choose options and choose kubuntu.

---

### Post by Alberonn on 2010-02-06
Cool, I can have access to both? Yet another reason to love Linux. :p

---

### Post by Alberonn on 2010-02-06
Should I worry about this error?

E: Invalid operation kubuntu-desktop

---

### Post by wojox on 2010-02-06
Sorry:

```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```

I left out install

---

### Post by Alberonn on 2010-02-06
LOL It worked this time. KDE looks like it may need some more configuring, or perhaps the Ubuntu install of Gnome had set some stuff up for me. I'll play with the two until I know which one I like better. At least I can jump between the two.

I also need to get used to the terminal commands. I have a lot of experience with the Amiga OS (I've played with versions going up to OS 4.0)--where I jumped a lot between the Amiga Shell and Workbench; I'm not too scared of typing in commands. I just need to get to know them. 

Windows is really ticking me off right now, but I need it for some applications for school. I have my system set up to dual boot for now with Windows on one HD and Ubuntu on another.

---

### Post by Alberonn on 2010-02-08
I know that may be a little nit-picky, but how to I switch back to the original Ubuntu startup/exit graphic when I log on and off from Kubuntu ones? When I installed KDE, I just wanted to have the option to experiment with it. lol

---

### Post by shrimpy89 on 2010-02-09
> **Alberonn said:**
> I know that may be a little nit-picky, but how to I switch back to the original Ubuntu startup/exit graphic when I log on and off from Kubuntu ones? When I installed KDE, I just wanted to have the option to experiment with it. lol

I believe that the commands to restore the original are:

```

sudo update-alternatives --config usplash-artwork.so

sudo dpkg-reconfigure linux-image-`uname -r`

```

---

### Post by stumbleUpon on 2010-02-10
> **Alberonn said:**
> I've recently installed Ubuntu Karmic Koala and I noticed that I have the Gnome desktop. What is the big difference between Gnome and KDE???

This might also help

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

and also other pages on the same site about installing / removing kde, gnome or xfce

---

### Post by aeon.flux on 2010-02-10
hi there, i tried gnome, KDE and xfce. at first the KDE was best, but when i started to use gnome, i found KDE so much complicated and chaotic, also the default apps in KDE is not my cup of tea, but as you written wojox, everyone should find out by himself. 

the biggest problem that i wanna ask about, was problem with keyboard, that nobody could explain / fix. all the keys except letters and numbers are changed and changing the language of keyboard(usa/uk/fr/cs/sk) has no effect on this.

this happened when i added KDE to ubuntu (originaly with just gnome) on 9.04, i didn't try to install kubuntu or add KDE to 9.10

---

### Post by jekristiansen on 2010-02-10
Why don't you just download Ubuntu Ultimate 2.5? It has both KDE and Gnome right out of the box. Give it a try!
Still, i have another problem that i need help with.
I own a HIS Radeon HD 5750 and a 40 inch Samsung as my monitor, wich i cannot use to its fullest because lack of drivers, does anyone here know if there is a stable driver out yet?

---

