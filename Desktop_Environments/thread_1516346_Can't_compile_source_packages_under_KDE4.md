---
title: "Can't compile source packages under KDE4"
date: 2010-06-23
forum: Desktop Environments
---

### Post by anoknusa on 2010-06-23
Wanted to switch to Kubuntu and decided a clean install was the way to go.  Though the learning curve isn't too tough, I've hit a serious snag: When I try to compile a source package according to the similar instructions in each of the README files, I get the same error message;

_Instructions:_

 mkdir build
     cd build
     cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..         
     make
     su -c 'make install'
     kbuildsycoca4

When I run the 'cmake' terminal command, I get this spat at me:


CMake Error at CMakeLists.txt:3 (kde4_add_plugin):
  Unknown CMake command "kde4_add_plugin".


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!



What's the deal? I'm liking this KDE 4.4 setup, but if I can't install the improvements from kde-look.org I'm gonna be none too happy. Please, help!

---

### Post by 3Miro on 2010-06-23
Installing kubuntu-desktop will setup KDE 4.4 on your system from the tested repositories. You will also get updates (however with a few days delay compared to the official KDE).

kde-look.org contains themes and eyecandy and it doesn't require compiling anything. Also, many of the things on kde-look.org are for KDE 3 and will not run under KDE 4.4

---

### Post by anoknusa on 2010-06-24
> **3Miro said:**
> 
kde-look.org contains themes and eyecandy and it doesn't require compiling anything. Also, many of the things on kde-look.org are for KDE 3 and will not run under KDE 4.4


The "KDE Improvements" section of kde-look.org contains several add-ons to Dolphin, Plasma and the like that *do* require compiling; it's some of these packages I'm trying to set up.

SEE:



[http://kde-look.org/content/show.php/AudioThumbs?content=114885&PHPSESSID=463c81d36e3dcd6a88b7afd6da127cff](http://kde-look.org/content/show.php/AudioThumbs?content=114885&PHPSESSID=463c81d36e3dcd6a88b7afd6da127cff)

---

### Post by anoknusa on 2010-06-28
*bump*

---

### Post by ankspo71 on 2010-06-29
Hi,
You can get it from a PPA repository, which would be easier than compiling it from source. 

But first, Go to this link and download the i386.deb or amd64.deb package for audio-thumbs, then try to install it by clicking on the file. [https://launchpad.net/~samrog131/+archive/ppa/+packages](https://launchpad.net/~samrog131/+archive/ppa/+packages)

It should be installable as is without having to install any extra packages, but if not, you might have to add the PPA repository to your software sources if some of the dependencies are not met. If they're not met, open up konsole (terminal) and paste the following commands:

```
sudo add-apt-repository ppa:samrog131/ppa 
sudo apt-get update
sudo apt-get install audio-thumbs
```

Hope this helps.

---

### Post by anoknusa on 2010-06-29
Thanks alot for the help; I've got in goin' now.  A quick follow-up question: with regard to these neat little add-ons, is it generally a good idea to search for a developer ppa *before* I even think about compiling from source? Just how often do such simple products have ppa's?

---

### Post by ankspo71 on 2010-06-29
Hi,
It's just my personal preference. I can usually find what I need by searching Google using the search terms **packagename PPA**.

Sometimes I like to compile things for myself, but there are those times where once in a while I run into compiling problems (which might happen because the instructions are written for a different linux distribution (or for a different version of Ubuntu) or something. So it's nice to be able to find these PPA's, when there is no similar packages available in Ubuntu's own official repositories.

---

