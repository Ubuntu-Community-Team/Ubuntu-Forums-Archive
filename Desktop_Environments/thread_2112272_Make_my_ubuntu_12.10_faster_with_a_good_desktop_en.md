---
title: "Make my ubuntu 12.10 faster with a good desktop environment"
date: 2013-02-04
forum: Desktop Environments
---

### Post by AngJinhang on 2013-02-04
hi guys, i had a quantal quetzal (ubuntu 12.10) on my cranky pc. it was pretty slow...so i thinked of making it faster, and as fast as it can. on startup, it took me one minute above, and it was really slow, and it took me twenty seconds to take the firefox up, ten seconds to see the home dash, ten seconds to open up my system settings, fifteen seconds to open libreoffice and so on and this is frustrating. i thought of using a lighter desktop to make it faster, is that possible? i log out and i don't see a ubuntu sign like precise for me to change it into lxde, ubuntu 2d, xfce, openbox and so on. 
how to install a desktop environment? fast, light, small in size (the best is below 20 mb), fast booting, and also, good look. i don't accept a bad looking desktop (and thats why i choose ubuntu).

---

### Post by ibjsb4 on 2013-02-04
```
sudo apt-get install lxde

sudo apt-get install xfce

sudo apt-get install openbox

sudo apt-get install fluxbox

sudo apt-get install gnome
```And choose at boot (login).

---

### Post by dan000 on 2013-02-04
If you want a full-featured desktop environment that you won't have to add a lot of stuff to, and it will basically just work, consider XFCE. I used it for a long time. It looks and feels a lot like Gnome2, but is much lighter weight.

I, personally, use Fluxbox now, with cardapio for the menu. Cardapio is basically the same as the default menu in Gnome. I bound it to Super+Menu button, so it's easy to bring up, and I have everything I need.

If you go with fluxbox, you'll probably want to add the following to your .fluxbox/startup:
```

nm-applet -sm-disable &   # For the NetworkManager icon, to manage Internet
gnome-sound-applet &      # Volume control

```
You could also add cairo-compmgr for cool transparency effects.

---

### Post by Jake Sweeney on 2013-02-04
If you want a fast and lightweight desktop enviroment that uses little RAM and processing power, you may want to consider installing the Lubuntu or Xubuntu destop enviroment, which are based on XFCE and LXDE.

To install these, copy and paste either of these into the Terminal:
To install Xubuntu
```
sudo apt-get install xubuntu-desktop -y
```
or, to install Lubuntu
```
sudo apt-get install lubuntu-desktop -y
```

If you want to keep ubuntu but put less strain on your GPU, try using Unity in 2D. 
To do this and to switch desktop environments, on login look for the little ubuntu logo on the top-right hand corner of the user box. This allows you to switch desktop environments within Ubuntu

Hope this helps :D

---

### Post by Yellow Pasque on 2013-02-04
> **Jake Sweeney said:**
> If you want to keep ubuntu but put less strain on your GPU, try using Unity in 2D.

Unity 2D is no longer available in Ubuntu 12.10. If Unity detects no 3D hardware acceleration, it falls back on using the CPU to do all the graphics acceleration (through llvmpipe), which is painfully slow unless you have a really fast CPU.

---

### Post by BBQdave on 2013-02-04
As said before... [**Xubuntu**]("http://xubuntu.org/") :D

I am not for sure, as my testing only went so far... but Ubuntu Unity 12.10 compared to Fedora 17 Gnome 3 - Ubuntu is noticeably sluggish. I suspect the data indexing for dash searches is what slows application response - though I am not sure. Not trying to pick at Ubuntu; Unity, IMO, has it's advantages over Gnome 3. But Unity is definitely slower in application execution and over all response, compared to Gnome 3.

---

### Post by snowpine on 2013-02-04
Tell us about your hardware? It's meaningless to discuss performance without mentioning hardware specs...

---

### Post by llanitedave on 2013-02-04
Xubuntu is not only snappy, but quite pleasing to the eye.  It's not flashy, but it's very elegantly designed.

---

### Post by ACubed10 on 2013-02-05
My vote is for cinnamon!

---

### Post by AngJinhang on 2013-02-05
i have a 7-year-old laptop, intel celeron m processor 520 (1.6ghz) single core (really slow), 512 mb of ram, but i only see 498 mb in system monitor, 512 mb swap space, and i only know these. i love lxde's speed but i love ubuntu's default look. if i can use unity 2d and thats really perfect.

---

### Post by NikiNfOuR on 2013-02-06
> **AngJinhang said:**
> i have a 7-year-old laptop, intel celeron m processor 520 (1.6ghz) single core (really slow), 512 mb of ram, but i only see 498 mb in system monitor, 512 mb swap space, and i only know these. i love lxde's speed but i love ubuntu's default look. if i can use unity 2d and thats really perfect.

I don't know friend, i too have a AMD sempron 1.6Ghz desktop with 512Mb Ram!! It doesn't support ubuntu latest versions!! (haven't gone with a larger swap area because it's not working at the moment!! So if it's gona work, i recommend upgrading the swap area to 1Gb, which is because in ma laptop i have seen it going 900MB or just above, but never have seen it using more than 1GB Ram!! This is to my knowledge!!

---

