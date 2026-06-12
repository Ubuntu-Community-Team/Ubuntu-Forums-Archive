---
title: "Restore Ubuntu splash"
date: 2008-12-07
forum: General Help
---

### Post by minashokry on 2008-12-07
Hi All,
I am working with ubuntu and gnome very well
I wanted to give KDE a try. so, I installed kubuntu-desktop package
and now I can choose between gnome and kde at startup.

everything is fine except one thing.
splash while opening and shutting down shows kubuntu and I want it to show ubuntu!

I am sure it is possible but how? which files to edit?
thanks in advance.

---

### Post by geirha on 2008-12-07
I haven't messed around with usplash before, but there is a script called update-usplash-theme which sounds and looks like the way to go. It seems you should run it without any arguments first
```
update-usplash-theme
```
which should list all themes you have installed, then change it with
```
sudo update-usplash-theme *theme-name*
```

---

### Post by crwmike on 2008-12-07
```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by minashokry on 2008-12-07
> **geirha said:**
> I haven't messed around with usplash before, but there is a script called update-usplash-theme which sounds and looks like the way to go. It seems you should run it without any arguments first
```
update-usplash-theme
```
which should list all themes you have installed, then change it with
```
sudo update-usplash-theme *theme-name*
```

I tried it and it works!!
thanks a lot ):P

---

### Post by N9TA on 2008-12-18
> **geirha said:**
> I haven't messed around with usplash before, but there is a script called update-usplash-theme which sounds and looks like the way to go. It seems you should run it without any arguments first
```
update-usplash-theme
```
which should list all themes you have installed, then change it with
```
sudo update-usplash-theme *theme-name*
```

This worked for me as well! I had installed Mythbuntu...instead of Mythtv...and it "took over". The above commands fixed it back to "Ubuntu". Microsoft has driven me away with "Vista"....but MAN!!! This is an uphill climb learning a whole new game....for an old fart like me anyway!!

Toodles.....Fred in Indiana

---

### Post by stchman on 2008-12-18
The package StartUpManager will allow you to change your splash.

---

### Post by OzzyFrank on 2008-12-19
Anyone have this disappear after the Intrepid upgrade? I have Ubuntu 64-bit with widescreen, and I've changed themes a few times (apparently successfully) but still just get verbose text while booting.

---

### Post by Xanavi on 2008-12-24
Yeah my usplash is gone after a 8.04-8.10 32bit upgrade. Startupmanager wont fix it, ill get around to fixing it soon. :lolflag:

---

