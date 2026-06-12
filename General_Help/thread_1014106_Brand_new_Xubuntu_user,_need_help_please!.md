---
title: "Brand new Xubuntu user, need help please!"
date: 2008-12-17
forum: General Help
---

### Post by pintar5775 on 2008-12-17
I just set up a "Wubi" dual boot between Vista and Xubuntu, and so far I think Xubuntu is amazing, so amazing that i want to put it on my sisters old Windows98 machine, but i am having some issues that i cant quite figure out.

1. I want to be able to play DVDs on my computer, but i cant figure out how to make it work with "Movie Player"

2. I was able to get mp3s to work on "Movie Player," but i would really like to be able to play them on "listen Music Player"

3. I would also like to be able to use "Flash Player" so i can watch videos on Megavideo, and Youtube.

Also, I would like instructions on how to put "VLC Player" on here, but all the directions on the internet are too confusing for "Ubuntu Virgins" like myself. 

Thanks for your help, i have been struggling with all day, and would really like for Xubuntu to be my only operating system

-John

P.S. please inform me if i missed out on any critical information.[LIST]
[/LIST]

---

### Post by taurus on 2008-12-17
1.  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

3.  Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
sudo apt-get install vlc
```

---

### Post by OrangeCrate on 2008-12-17
> **pintar5775 said:**
> I just set up a "Wubi" dual boot between Vista and Xubuntu, and so far I think Xubuntu is amazing, so amazing that i want to put it on my sisters old Windows98 machine, but i am having some issues that i cant quite figure out.

1. I want to be able to play DVDs on my computer, but i cant figure out how to make it work with "Movie Player"

2. I was able to get mp3s to work on "Movie Player," but i would really like to be able to play them on "listen Music Player"

3. I would also like to be able to use "Flash Player" so i can watch videos on Megavideo, and Youtube.

Also, I would like instructions on how to put "VLC Player" on here, but all the directions on the internet are too confusing for "Ubuntu Virgins" like myself. 

Thanks for your help, i have been struggling with all day, and would really like for Xubuntu to be my only operating system

-John

P.S. please inform me if i missed ot on any critical information.[LIST]
[/LIST]

If you haven't already done so, there are a couple of things you should install that should help you with all of your questions...

First, get the Medibuntu repositories. Follow the instructions here (and don't forget to add the key):

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

There's a link on that page to a list of the contents of the package.

Then go to Software Sources, and enable the repositories by putting check marks in the boxes to the left of the entries.

Second, install the xubuntu restricted extras package from Synaptic.

Here's what in that package:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by pintar5775 on 2008-12-17
Thank you so much! it has been killing me trying to figure this out!

---

