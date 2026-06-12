---
title: "Where do I get Phonon 4.4.3?"
date: 2010-11-17
forum: Desktop Environments
---

### Post by t_echtenkamp on 2010-11-17
I'm trying to build KDE, following the guide here:

[http://techbase.kde.org/Getting_Started/Build/KDE4](http://techbase.kde.org/Getting_Started/Build/KDE4)

and I got to the section to build kdebase/runtime. I got kdebase from the git repository and when I tried to run cmakekde, I got this error message:


   * Phonon (4.4.3 or higher)  <git://gitorious.org/phonon/phonon.git>
     Phonon library
     STRONGLY RECOMMENDED: Required for playing audio and video throughout KDE

My version according to 'apt-cache show libphonon4' is "Version: 4:4.7.0really4.4.2-0ubuntu1". So I tried to get phonon from the git repository, build it, make, make install, and that worked, but I still get the same error as before. To me it looks like the version I got from the git repository is 4.4.0, but I'm not sure. (I ran 'git clone git://gitorious.org/phonon/phonon.git phonon')

I don't know where to go from here... If the version in the git repo isn't the right version I don't know where to get it. One thread that I found mentioned something about using tags/kdesupport-for-4.5 but I it appears that phonon isn't in kdesupport at all anymore. help? I'm lost.

---

