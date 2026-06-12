---
title: "[SOLVED] Compiz fusion......"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by techno-mole on 2007-10-02
Hello people.

Ive got compiz fusion working (i used amaranths way of doing things) and it all works fine.
I know it is more stable this way than using the git way (least i think it was git) but when i last had it installed i had installed it using git and it ran fine, no problems.
so i want to install it that way again, because i can get all the extra plugins and such like, but im stuffed if i can find out how i did it last time (i had thought id written it down, but i cant find it now)
so basically can anyone point me in the right direction (i think it was from another website i installed it from last time) cheers.
if no one knows what im on about is it possible to get the extra plugins working with the stable version ? and what i would need to input to download and install them.
cheers.

---

### Post by overlord.gaurav on 2007-10-02
The git thing is called Fusion-Icon. Installing Fusion-Icon:

STEP 1
```
git clone git://anongit.opencompositing.org/users/crdlb/fusion-icon 
```

STEP 2
```
cd fusion-icon
```

STEP 3
```
sudo make install
```

---

### Post by techno-mole on 2007-10-02
i tried the commands you gave, and couldnt get them to work, im not sure thats what im after, i was trying to find the way i installed it last time (from trevinos repo i think) but its changed now.
ill shall have to do alot more sifting through posts and such like, cheers.

---

### Post by overlord.gaurav on 2007-10-02
Once you've done yourself with installation steps, do this:
Applications >> System Tools >> Compiz Fusion Icon.

---

### Post by techno-mole on 2007-10-02
step 1 - git clone git://anongit.opencompositing.org/users/crdlb/fusion-icon

result - git, the filemanager with GNU Interactive Tools, is now called gitfm.

If you are looking for git, Linus Torvald's content tracker, install
the cogito and git-core packages and see README.Debian and git(7).

This transition script will be removed in the debian stable
release after etch.

If you wish to complete the transition early, install git-core
and use (as root):
 update-alternatives --config git

Press RETURN to run gitfm

(if i hit return i get the following) 
GNU Interactive Tools 4.3.20 (i686-pc-linux-gnu), 16:31:59 Nov  9 2006
GIT is free software; you can redistribute it and/or modify it under the
terms of the GNU General Public License as published by the Free Software
Foundation; either version 2, or (at your option) any later version.
Copyright (C) 1993-1999 Free Software Foundation, Inc.
Written by Tudor Hulubei and Andrei Pitis, Bucharest, Romania

/usr/bin/gitfm: fatal error: `chdir' failed: permission denied.


the same happens if i do it as root.
but its not the icon i want, i want to install fusion using trevinos repo, but i cant seem to find it.
cheers

---

### Post by luisromangz on 2007-10-02
Another way to have the git version of Compiz would be to use Treviño's eyecandy repository. Compiz packages in that repository are compiled from the git source tree usually twice a week, enought to get all the new features and bug fixes, and some breakages, too :P

To use his repo, you should add this line to your sources.list:

deb [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) feisty eyecandy

---

### Post by techno-mole on 2007-10-02
ive got it installed, i used a method found - [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml) 
its similar to how i first installed it a while ago, i still cant find the snow plugin though.
cheers.

---

