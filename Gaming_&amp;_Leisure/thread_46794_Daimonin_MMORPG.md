---
title: "Daimonin MMORPG"
date: 2005-07-06
forum: Gaming &amp; Leisure
---

### Post by RadixLecti on 2005-07-06
Has anyone tried Daimonin. I've been checking around their [homepage](http://web2.168180.vserver.de/index.php) , and it looks pretty nice. I haven't had the time yet to install and test, does anyone know if it is worth playing?

---

### Post by TorQ on 2005-07-10
I've played it a few times and enjoyed myself.  Its quite a bit like your standard roguelike I guess.  The only problem  is that it can be terribly laggy at times.  I haven't run it on linux but I think its worth checking out.  If you decide to do so let us know how the install goes!!

---

### Post by RadixLecti on 2005-07-11
Well, now I've tried installing Daimonin, and I haven't gotten further than  sh ./configure

```
~/daimonin/client/make/linux$ sh ./configure
checking build system type... configure: error: cannot guess build type; you must specify one
```

I haven't found a solution to my problem in the daimonin forums, and have failed to find one on my own. I'm stumped.

I've followed the [installation guide](http://www.daimonin.net/modules.php?op=modload&name=phpWiki&file=index&pagename=Source%20Client%20Install) , installed the libraries stated in the guide (I hope the "make" installed on my system is compatible with the GNUmake suggested in the installation guide), and... well, it doesn't work.  And I don't know why. That probably says more about my linux savvy than I want to let on... ;)

---

### Post by gryphius on 2005-08-15
well.. I've got the same problem! Does anyone know how to make it work?

---

### Post by Mirith on 2005-11-24
I'm trying to do it now, and i'm getting the same problem.  On the daimonin i saw someone suggest for OSX using sh ./configure --build=ppc for the power pc.  If anyone knows the abbreviation for the normal x86 pc, i think it might work.

---

### Post by mondi0924 on 2005-12-12
I got past the ./configure part . In my case the gnu compiler wasn't installed  so I installed it and ran ./configure again. it went ok .

though I encountered more errors when compiling began. 

Is there a binary package for this game? anyone?

---

### Post by hod139 on 2005-12-13
I decided to try this game out after seeing your post about it.  I downloaded the source and installed the dependencies mentioned on their website: "... before you continue with this guide you'll need the SDL, SDL-mixer and SDL-image dev packages".
The specific names for ubuntu are:
libsdl1.2debian
libsdl1.2-dev
libsdl-image1.2-dev
libsdl-mixer1.2-dev

Also, make sure you have all the tools required to build from source: build-essential

```

sudo apt-get install build-essential libsdl1.2debian libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev

```

Then I extracted the tar:
```
 tar -zxvf daimonin_client-BETA3-0966.tgz 
```
and changed to the source code
```
 cd /daimonin/client/make/linux 
```
and typed
```

sh ./configure
make
make install

```
Everything built (with lots of warnings but no errors)
and then still following the install guide I did:
```

cd ../../..
cd client-BETA3-0.966
./daimonin

```
and the game launched.

I don't know if it is worth playing yet, but hopefully this helps you get it up and running.

---

### Post by mondi0924 on 2005-12-16
cool it works! I was lacking the build-essentials...

---

### Post by hod139 on 2005-12-16
[QUOTE=mondi0924]cool it works! I was lacking the build-essentials...[/QUOTE]
Glad you got it working!

Let me know what you think of the game.  Personally, I was unimpressed.

---

### Post by mondi0924 on 2005-12-16
I saw the screenshots before hand so I wasn't expecting it to be graphically pleasing. but I was expecting it to run smoothly . unfortunately its laggy so I didn't get to explore the game deeper. I would rate it 5/10

---

### Post by TheRingmaster on 2006-12-17
> **hod139 said:**
> I decided to try this game out after seeing your post about it.  I downloaded the source and installed the dependencies mentioned on their website: "... before you continue with this guide you'll need the SDL, SDL-mixer and SDL-image dev packages".
The specific names for ubuntu are:
libsdl1.2debian
libsdl1.2-dev
libsdl-image1.2-dev
libsdl-mixer1.2-dev

Also, make sure you have all the tools required to build from source: build-essential

```

sudo apt-get install build-essential libsdl1.2debian libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev

```

Then I extracted the tar:
```
 tar -zxvf daimonin_client-BETA3-0966.tgz 
```
and changed to the source code
```
 cd /daimonin/client/make/linux 
```
and typed
```

sh ./configure
make
make install

```
Everything built (with lots of warnings but no errors)
and then still following the install guide I did:
```

cd ../../..
cd client-BETA3-0.966
./daimonin

```
and the game launched.

I don't know if it is worth playing yet, but hopefully this helps you get it up and running.
how do you uninstall this package???

---

### Post by pgatrick on 2006-12-17
'make uninstall' :) Of course if there is no rule for uninstall or such, then you'll have to remove the files by hand.. A good reason to use such program as checkinstall rather than make install, then it's just dpkg -r whatever. :)

---

### Post by TheRingmaster on 2006-12-17
> **pgatrick said:**
> 'make uninstall' :) Of course if there is no rule for uninstall or such, then you'll have to remove the files by hand.. A good reason to use such program as checkinstall rather than make install, then it's just dpkg -r whatever. :)
all the files are in the main daimonin folder on the desktop...right?

---

