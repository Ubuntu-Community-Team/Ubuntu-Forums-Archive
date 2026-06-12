---
title: "&lt;_&lt; I dislike compiz fusion..."
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by Hickler on 2007-10-30
I've recently upgraded to Gutsy and made the change from Beryl to Compiz Fusion. I was excited at first because I've heard of all the hype about it. But I was disappointed. First of all, there was no settings manager that I could see, so I installed one. But, once again I was disappointed, it wasn't nearly as good or as customizable as the Beryl manager, not to mention as user friendly. I've searched through the settings manager trying to find something as simple as how many sides I want for the cube, but I couldn't find any settings options for that. So I guess I'm asking if there are any instructions on how to install Beryl for Gutsy or is it the same as Feisty?

Thanks for listening.

---

### Post by Hexxagon on 2007-10-30
Just choose the number of Desktops, and the Cube will have 3, 4 ore more sides...
I never worked with beryl, but that sounds logical to me...

---

### Post by Zorael on 2007-10-30
ccsm isn't as well-polished as beryl-manager was, but there's **plenty** you can customize in it. And as mentioned, the way to set the number of cube sides is to set the number of horizontal virtual desktops accordingly.

It isn't possible to have an option to set "number of sides on cube" anymore, since there are additional plugins now (aside from the cube) that deal with handling virtual desktops. Like Expo, Desktop Wall, etc which can all have virtual desktops aligned vertically, something that is mutually exclusive with cubes.

---

### Post by kregg on 2007-10-30
I know they've got rid of the exposé thing, which I'm pretty annoyed about, but that doesn't bother me too much, since I'm running VirtualBox, and if I have compiz, everything goes downhill from there really.

---

### Post by Zorael on 2007-10-30
> **kregg said:**
> I know they've got rid of the exposé thing, which I'm pretty annoyed about, but that doesn't bother me too much, since I'm running VirtualBox, and if I have compiz, everything goes downhill from there really.

That functionality can be found in the Scale plugin, I think?

---

### Post by Hickler on 2007-10-30
Okay, there is plenty to customize but I find Beryl much easier. Oh, are we talking about the same settings manager? In terminal you type "compiz-settings" and at the top of the settings window it says "Compiz configuration". Anyways, my question still stands, "Can Beryl be installed on Gutsy?" 

Thanks for the comments.:)

---

### Post by Zorael on 2007-10-30
You type ccsm and it says CompizConfig Settings Manager. :)

Beryl can probably still be installed, but it's not supported. Treviños repository probably still has it for Feisty, might work still. I've had some bad experiences with that repository so I won't recommend it.

Anyway. Add to your sources.list:
```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Then do
```
$ wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
$ sudo aptitude update
$ sudo aptitude install beryl
```

---

### Post by k0rfain on 2007-10-30
the compiz manager is ccsm, what exactly did you see in beryl? it was more bulky.. Compiz has more features and it isnt as bulky as beryl. if you dont like compiz why not just disable the desktop effects?

---

### Post by cprofitt on 2007-10-30
> **Hexxagon said:**
> Just choose the number of Desktops, and the Cube will have 3, 4 ore more sides...
I never worked with beryl, but that sounds logical to me...

Can I have a dodecahedron or even a Icosahedron?

---

