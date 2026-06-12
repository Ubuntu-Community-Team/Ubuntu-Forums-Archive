---
title: "kde apps in gnome"
date: 2005-03-18
forum: Desktop Environments
---

### Post by 23meg on 2005-03-18
hi, 

this is my first post here; i've been enjoying the community in read only mode so far, but there's quite a lot of trouble and confusion on my side regarding Warty (which i've chosen over MEPIS) so i'll probably be asking things around quite a bit these days; i hope you all will bear with my newbieness..

anyway, i have a simple question to start with: i'm fine with running Gnome as a window manager, and actually would like to try Fluxbox and some other light managers after i get things working a bit steadier. i'm not mad about KDE, but there are some KDE apps that i want to run as well. Kubuntu would be overkill for this requirement, so i'd like to learn whether it's possible to just install the core KDE packages and not the whole thing without messing anything up for this purpose. if it's possible, which packages should i install over Ubuntu just for basic KDE application compatibility? 

thanks

m.

---

### Post by WW on 2005-03-18
If you just want to run a few KDE applications, you don't have to worry about finding what you will need in advance, since the apt system will take care of that for you.  Just install the applications that you want with Synaptic (or 'apt-get install', if you prefer the command line), and let the system find the dependencies that it needs.  That's how I installed k3b and kile, two KDE apps that I use regularly.

When I run them from the command line, I get lots of warnings that I assume occur because I am not running KDE, but the applications run fine.  I now have them in my Applications menu, so I don't have to see ugly warnings each time I start one them. :)

---

### Post by 23meg on 2005-03-18
wow thanks, i'll definitely give it a go. i hope digiKam works this way.

---

### Post by kkathman on 2005-03-19
23 meg you bring up a great issue. I have run KDE on other, unfortunately less stable distributions, and loved it. Its much easier to configure and more flexible. However, I've learned to configure Gnome now, and while not as flexible, I can get the job done.

Ive found alot of things about getting KDE on the system, but when I follow the apt stuff to install it, things go goofy. Be careful :)

Kork

---

### Post by 23meg on 2005-03-19
right; i've tried installing digiKam by downloading the .deb package and using

dpkg -i "package name"

but lots of unhandled dependencies occur. and apt-get cannot find it in the default repositories. is there any way of making Synaptic (or some other package manager) handle the dependencies of a single downloaded .deb file and set them up accordingly, or is it a must to direct it to a repository that contains the package? 

frankly i haven't been able to locate digiKam in .deb format in any repository either so i'm quite stuck as to what to do here.

---

### Post by ember on 2005-03-19
Have you added universe and multiverse repositories? I do have digikam in my list.

---

### Post by WW on 2005-03-19
I should have said that the KDE packages that  I have used are all available in ubuntu's "universe" repository.  I haven't tried installing any from other repositories.

---

### Post by 23meg on 2005-03-24
right; i've forgotten to add the universe repository.. 

i've installed digiKam, synaptic handled all the dependencies and it works fine, but the fonts in KDE applications appear far bigger than the gnome ones. where can i configure KDE to make them smaller?

thanks for the help so far!

m.

---

### Post by lao_V on 2005-03-24
If kcontrol has been installed as one of the dependencies (i doubt it) then you can change the font there. Alternatively, why not do a minimum kde installation and use KDE apps from KDE??

---

### Post by 23meg on 2005-03-24
thanks for the quick reply; no, kcontrol wasn't installed, but i'm installing it right now.

i really prefer GNOME over kde in just about every aspect, and i don't want to keep switching window managers or waste lots of disk space just for the few advantages of KDE. but there *are* some good KDE apps i want to use, and all is fine with running them in GNOME so far, except for this little quirk which it seems is fixable.

m.

---

