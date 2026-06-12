---
title: "vlc 1.0rc - where? :)"
date: 2009-05-15
forum: General Help
---

### Post by Intrepid Ibex on 2009-05-15
I'd like to get vlc 1.0RC to my jaunty but I can only get the source with a configuration file from [[COLOR="Blue"]here[/COLOR]](http://www.videolan.org/mirror-geo.php?file=testing/vlc-1.0.0-rc1/vlc-1.0.0-rc1.tar.bz2) [[COLOR="Blue"](link from here)[/COLOR]](http://www.videolan.org/news.html#news-1). However when I do...: ```
./configure
```...I get so much errors that VLC 1.0RC probably wouldn't even run properly.

Why isn't the version 1.0RC on the repos?

---

### Post by BslBryan on 2009-05-15
Hello, Intrepid Ibex. :-) Nice name, by the by.

Well, have you tried to untar it, cd to the directory that you installed it in, then ```
sudo make install
```?

You might want to do that, and tell me how it goes.  

Best to you, and good luck. :-)

---

### Post by michy99 on 2009-05-15
The rc in the version number stands for "release candidate" which means it is not an official release yet. The errors you get probably refer to dependancies that need to bee installed. Post the error messages, and we'll see what you need to install to get it to work.

---

### Post by mc4man on 2009-05-15
Here is a launchpad ppa that has a 1.0 for jaunty (updated 

[https://edge.launchpad.net/~kow/+archive/ppa](https://edge.launchpad.net/~kow/+archive/ppa)

If you wish to build then 
```
sudo apt-get build-dep vlc
``` will get you almost all the deps

If you wished to build and not have your build packages and deps marked for autoremove then

```
sudo apt-get build-dep vlc -o APT::Get::Build-Dep-Automatic=false

```

note: a straight ./configure will not produce a very useful build (-read ./configure --help

---

### Post by Intrepid Ibex on 2009-05-16
Yes, I know that RC means Release Candidate and that is exactly why I installed it ;) (after creating this topic I remembered that I would of course get this from launchpad).

Also those errors where exactly about dependancies. There just was so many of them that I would have wanted to get the .deb package :/.

Anyways thanks for all and remember to read the signatures! Especially mine ^^.

**E:** If someone wants VLC 1.0RC, you can get it from [here]("https://edge.launchpad.net/~c-korn/+archive/vlc") (**OBS.** remember to add the pgp key too. Repositories need a validation).

---

