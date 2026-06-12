---
title: "KDE4 Display Manager"
date: 2008-05-03
forum: Desktop Environments
---

### Post by dmsynck on 2008-05-03
Hi all,

I installed Ubuntu 7.10 several months back, then recently upgraded to 8.04. Last night I decided that I would like to add KDE also, so I installed the kubuntu-kde4-desktop metapackage. Everything installed fine, but I noticed that after I changed the display manager from gdm to kdm-kde4, logout takes you to a black screen rather than back to the login. This happens from both Gnome and KDE4. So I switched the display manager back to gdm and now it works fine. Has anyone else seen this or have a fix for it ?

---

### Post by Xiong Chiamiov on 2008-05-03
Why, oh why did you install KDE4?  I suppose, since you're a GNOME user, you haven't heard that a large majority of KDE users hate KDE4, and are using 3.5.9 until 4.1 comes out.  So please, don't judge KDE by 4.  It's incredibly buggy and much less customizable.

That said, is everything fine when you use the gdm login screen, but log in to KDE?

---

### Post by Zorael on 2008-05-03
KDE4 is very much a work in progress, yes. :>

As for kdm-kde4 and similar packages remaining, you could try this in a terminal to get rid of everything rhyming with kde4. I can't guarantee stuff though.
```
$ sudo aptitude purge ~nkde4
```
And, of course, '**sudo dpkg-reconfigure kdm**' if KDE and '**sudo dpkg-reconfigure gdm**' if Gnome to set your default window manager.

---

### Post by dmsynck on 2008-05-03
Thanks for the info. I can see why the majority of KDE users dislike KDE4. It seems very buggy. Yes, everything works fine when using gdm and actually I went ahead and installed kubuntu-desktop so now I have KDE3, but also have a bunch of duplicate KDE apps in the menus, one for KDE3 and one for KDE4. I guess I can work through Synaptic and remove the apps referencing KDE4. 

Thanks again

---

### Post by capink on 2008-05-05
```
sudo aptitude markauto ~i~nkde4 kubuntu-kde4-desktop --schedule-only
```

Now, run aptitude in simulation mode to see what packages it would remove.

```
sudo aptitude install -s
```

Examine the output of this command carfelly, if you spot a package you would like to keep you can reverse the previous step by running the command:

```
sudo aptitude keep-all
```


Otherwise you can run the command without the -s switch:

```
sudo aptitude install
```

---

