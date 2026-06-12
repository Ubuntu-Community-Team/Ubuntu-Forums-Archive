---
title: "Splash screen"
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by cooladi on 2007-06-14
i want to know how to install this particular splash screen for my ubuntu fiesty.
I tried the guide but couldnt get it.
[http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468&PHPSESSID=10c4a9041af5eb14e45226b1b039e728](http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468&PHPSESSID=10c4a9041af5eb14e45226b1b039e728)

---

### Post by nike984 on 2007-06-14
the main file for splash screen is '.so' type file and 
it should be copied into /usr/lib/usplash folder.

Assuming that it is already in the usplash folder,
Type these command in the terminal 

```
sudo update-alternatives --config usplash-artwork.so
```

this will show a list of splash screen in usplash folder,
choose the screen that you want, then update your system 
booting process by digiting in terminal

```
sudo update-initramfs -u
```

You're done :p

---

### Post by cooladi on 2007-06-14
thnks man

---

