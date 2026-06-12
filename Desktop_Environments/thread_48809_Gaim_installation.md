---
title: "Gaim installation"
date: 2005-07-13
forum: Desktop Environments
---

### Post by Yoshiassasin on 2005-07-13
I am pretty new to linux, so even if I act like a total idiot, bare with me. I downloaded the source for gaim in hopes to use it over kopete. I used the command

$tar -xvf

to uncompress the file and install it. I then used 

./configure

and then

make

But whenever I come to make, it always has an error stating

make: *** No targets specified and no makefile found.  Stop.

When I look through the uncompressed files, I find makefiles, but they are all makefile.am, makefile.in and makefile.mingw. What more am I supposed to do to be able to install Gaim? Or is there some kind of program to do this?
Thanks

---

### Post by jasmuz on 2005-07-13
Hello there!
Wouldnt it be easier if you just ran from the console a :

sudo apt-get install gaim

That would be so easier for you than compiling.

---

### Post by Yoshiassasin on 2005-07-13
I tried that, but it says it couldn't find the package. I thinkit's because Kubuntu doesn't come with Gaim. But thanks anyways.

---

### Post by funkydan2 on 2005-07-14
[QUOTE=Yoshiassasin]I tried that, but it says it couldn't find the package. I thinkit's because Kubuntu doesn't come with Gaim. But thanks anyways.[/QUOTE]
 What does your "/etc/apt/sources.list" look like?

Run "cat /etc/apt/sources.list" and paste the output here.

---

### Post by skyboy on 2005-07-14
Probably your configure diidnt succeed !! check out the output of configure
does it say, "now you can make ??" at the end

---

### Post by Lord Illidan on 2005-07-14
My suggestion to you is read the Ubuntu Guide at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) , add the extra repositories and install gaim like this:

sudo apt-get install gaim

That's all.

---

### Post by tea_man on 2005-07-14
easiest way would just to install it from kynaptic just do a search for it(need to be online to install it) - i did that last night along with a bunch of other installations and it works just fine! kopete doesnt work with my msn so i needed gaim

---

### Post by f1dave on 2005-07-15
Or if you want another alternative, add extra repositories from the guide and:

sudo apt-get install amsn

---

### Post by Yoshiassasin on 2005-07-15
Well, I've decided to go to Ubuntu because It already comes with Gaim and is less of a hassle. Thanks to all of you who tried to help me though.

---

### Post by tea_man on 2005-07-16
clicking on a check mark box and pressing a button is a hassle??:P i just had the raw install - went directly into kynaptic and it installed beautifully along with a bunch of other packages that i thought would be handy - i like kde/kubuntu looks better on my older dell monitor. the gnome/ubuntu with 1024x768 60hz refresh rate hurt my eyes for some reason but in kubuntu it looks more crisp and detailed and yet its at the same settings and refresh rate... wierd but anywho good luck with ubuntu!:)

---

### Post by matva on 2005-07-17
[QUOTE=tea_man]clicking on a check mark box and pressing a button is a hassle??:P i just had the raw install - went directly into kynaptic and it installed beautifully along with a bunch of other packages that i thought would be handy - i like kde/kubuntu looks better on my older dell monitor. the gnome/ubuntu with 1024x768 60hz refresh rate hurt my eyes for some reason but in kubuntu it looks more crisp and detailed and yet its at the same settings and refresh rate... wierd but anywho good luck with ubuntu!:)[/QUOTE]
 I started with ubuntu, but gnome didn't do much for me. I switched to kubuntu this morning, and found kopete to be a disaster (kept crashing). Kynaptic installed gaim with no problems.
Anyway, i think you should reconsider. Don't give up so easily:p

---

