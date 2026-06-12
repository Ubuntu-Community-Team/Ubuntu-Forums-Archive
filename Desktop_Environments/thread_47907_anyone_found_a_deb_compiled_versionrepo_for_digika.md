---
title: "anyone found a deb compiled version/repo for digikam?"
date: 2005-07-10
forum: Desktop Environments
---

### Post by arjay1 on 2005-07-10
Trying to install digikam under kubuntu - an absolute need since it is running on my wife's mepis setup elsewhere on our network and I need access to its functionality etc.  It is doing my head in - the usual million unmet dependencies because I can't find a source for apt-get.

Anyone found a deb repo with digikam and/or got other ideas about sourcing it?  Compiling it seems a nightmare from what I've read but I'll go that route if I have to with a bit of hand-holding!

TIA

---

### Post by JPatrick on 2005-07-10
digiKam is in the universe repository:
```

sudo apt-get install digikam digikamimageplugins digikamplugins

```

As mentioned before

---

### Post by arjay1 on 2005-07-11
Sorry - should have swung by and said thanks for the info.  I got sidetracked by my  more general thread on deb repositories.

I do appreciate your quick reply.

RJ

---

### Post by rosslaird on 2005-07-11
Digikam won't install on my system: dependency problems (with universe and Kubuntu sources enabled).

> The following packages have unmet dependencies:
  digikam: Depends: libimlib2-dev but it is not going to be installed
E: Broken packages

---

### Post by arjay1 on 2005-07-12
Ross - had the same problems but solved it with help from recent posts in this forum.  For what it's worth, here is how I did it:

1. Add the repos suggested in SGC's post in my thread  " Re: new to kubuntu - Question re deb repositories", in this forum.  Here is what my sources.list looks like now - note that I left the gb repos in and just added the us versions because I am not sure if they are the same.  I need help on that and will ask in the other post (still a newbie and all that):

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted 

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 

#### security
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#### universe
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe 

#### multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse


#### backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted 

#### kubuntu.org
deb [http://kubuntu.org/hoary-kde341/](http://kubuntu.org/hoary-kde341/) hoary-updates main 
# deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main 

Note also that the repos apt-get went to were the gb ones not the us - presumably because they are listed first?

2.  The apt-get I used was:  _sudo apt-get install digikam digikamimageplugins digikamplugins_ I think the same as the one in this post.

3.  That went fine and I also installed imlib-progs as suggested by apt-get. 

I'll attach my terminal's install output for you in case you want a line by line.

Hope this helps!

Richard

---

### Post by rosslaird on 2005-07-12
Thanks for the suggestions.
Unfortunately, they didn't work.
I added a couple of repos from your list (the backports, as I had all the others), but I'm still stuck.
(The gb/us repos will be mirrors of each other, and you are correct in surmising that you don't need both).

Ross

---

### Post by arjay1 on 2005-07-12
Sorry to hear that.  One advantage I may have is this is a clean install of kubuntu as I am just in the process of switching from simplymepis (because of poor digi camera support). This is one of the first installs I have implemented.  Maybe changes you have made elsewhere over time have upset the dependencies.  Thanks for the heads up on the gb/us repos - I'll simplify things there.

I hope someone with more expertise can help you out.

RJ

---

### Post by skyboy on 2005-07-13
add same problem, i downloaded all the deb package from 
[http://www.mpe.mpg.de/~ach/kubuntu/hoary/Pkgs.php](http://www.mpe.mpg.de/~ach/kubuntu/hoary/Pkgs.php)

and the did
sudo dpkg -i *.deb 
in the folder wher all the deb were.
when great
if something missing
sudo apt-get -f install

---

### Post by rosslaird on 2005-07-13
Nope, no dice.

I must have (and of course I've forgotten) installed some specific version of kde (3.4.1?) that's out of sync with the digikam packages. Eventually this will probably get worked out.
Thanks for trying to help.

Ross

---

### Post by skyboy on 2005-07-14
I also run KDE 3.4.1, but it is really important that you install all the package with one command, otherwise apt won't get it done and will find unmet dependencies.
Otherwise, install the rep from those links and 
sudo apt-get update && sudo apt-get upgarde
good luck

---

