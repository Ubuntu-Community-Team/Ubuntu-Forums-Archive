---
title: "Fix: NWN and Intel Graphics Problems"
date: 2007-04-29
forum: Gaming &amp; Leisure
---

### Post by JNowka on 2007-04-29
WARNING: The following has the potential to break your install if done incorrectly. I would suggest reinstalling the drivers for feisty that would be affected first so that you have them in your archives. This way you have a way to fix a mistake if you are kicked to the command prompt later on.
 
Steve0921 states that this fix for NWN will break Beryl.
 
First, this is supposed to be a way in order for those of us using the Intel video card, to be able to play Neverwinter Nights without the bright screen, off colors, problems that we are having. This is an issue that only effects the Feisty releases. This problem was not caused by the Ubuntu developers, it was caused by a fix to the mesa drivers, by the people that maintain them.
 
What I have found is that we need to regress the mesa drivers to the previous version in order to play NWN correctly. 
 
How do we get the drivers? From the Edgy repositories. Here are some links to the ones I downloaded.
 
[libgl1-mesa-dev]("http://mirrors.kernel.org/ubuntu/pool/main/m/mesa/libgl1-mesa-dev_6.5.1%7E20060817-0ubuntu3_i386.deb")
[libgl1-mesa-dri]("http://mirrors.kernel.org/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_6.5.1%7E20060817-0ubuntu3_i386.deb")
[libgl1-mesa-glx]("http://mirrors.kernel.org/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_6.5.1%7E20060817-0ubuntu3_i386.deb")
[mesa-common-dev]("http://mirrors.kernel.org/ubuntu/pool/main/m/mesa/mesa-common-dev_6.5.1%7E20060817-0ubuntu3_all.deb")
[libglu1-mesa]("http://mirrors.kernel.org/ubuntu/pool/main/m/mesa/libglu1-mesa_6.5.1%7E20060817-0ubuntu3_i386.deb")
[libglu1-mesa-dev]("http://mirrors.kernel.org/ubuntu/pool/main/m/mesa/libglu1-mesa-dev_6.5.1%7E20060817-0ubuntu3_i386.deb")
 
For each computer you could potentially have other mesa drivers also installed that I didn't. To check your drivers, type in the following into a terminal:
> dpkg -l | grep mesaP.S. the l is a lower case L
 
Grab only the packages you need from above. If you need other packages as well goto packages.ubuntu.com and search for the packages that you need.
 
Once you have the packages that you need, open up the terminal, and goto the directory that you downloaded the files to and type:
> dpkg -i *debThis is assuming that you have no other .debs in the directory that you don't want to have installed.
 
If you get an error when you try to install the packages to the effect as unable to copy over this file because it belongs to mesa-common-dev, just type "dpkg -i *deb" again and this should fix your problem.
 
Once this is done, you should be able to play Neverwinter Nights without the graphics problems that we have been experiancing
 
P.S. you will have some files state they are upgradeable. If you upgrade the files, then you will lose the fix and will once again be unable to play NWN.

---

### Post by hoyaabc on 2007-04-29
I installed all by synaptic.
I didn't have 3 of them
but nothing changed.

you talking about vary bright when you enter NWN after making chr?

---

### Post by JNowka on 2007-04-29
First off you can not install these by Synaptic.  If you do then you will be doing nothing but installing the drivers over themselves.  What you need to do is download the packages I have linked to because these are a lower version than those found in the feisty repos.  I actually am getting these from the edgy repos.  There was a bug that crept into the updated mesa drivers that is causing these errors.  Please download the packages I linked to and install them via dpkg and post here again.

---

### Post by steve0921 on 2007-04-29
Hey thanks!

This worked perfectly for me. I was too scared to fool around with downgrading (it's bad enough that upgrading sometimes breaks things) until hearing that it can be done successfully.

NWN looks so beautiful now after playing for a few hours with busted graphics.

---

### Post by JNowka on 2007-04-29
No problem man.  I am glad that it worked out for you.  Enjoy! :)

---

### Post by steve0921 on 2007-04-29
Oops, I have to qualify my previous statement slightly: it works perfectly for nwn.

I just turned beryl back on (I use metacity when running nwn) and it doesn't like using the old mesa. The screen goes all white. I suppose I could downgrade those packages too, but I feel that's just the beginning of a snowball.

Now I just need to decide which I like more, beryl or nwn. ](*,)

---

### Post by hoyaabc on 2007-04-29
I didn't read your last commant. that was my fault.
so this is about downgrading.
I will try. thank you.

---

### Post by JNowka on 2007-04-30
> **steve0921 said:**
> Oops, I have to qualify my previous statement slightly: it works perfectly for nwn.
 
I just turned beryl back on (I use metacity when running nwn) and it doesn't like using the old mesa. The screen goes all white. I suppose I could downgrade those packages too, but I feel that's just the beginning of a snowball.
 
Now I just need to decide which I like more, beryl or nwn. ](*,)
 
Ouch, that sucks.  I will make sure I inform people of this in the First post.  Sorry about that.

---

### Post by madjr on 2007-06-28
I got a better fix than going backwards.

Why not go forward and use the new version found in gutsy is more compatible and works with beryl (or you can wait some time till gutsy is out of beta). This also works for warzone 2100

:popcorn:

instructions:

open console and type:
```
dpkg -l | grep mesa
```

You will see the packages you already have installed, now we want to get a newer version of mesa (6.5.3) at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

in the search box select "**Gutsy**" and type in the file you need one by one and download.

Example: libglu1-mesa
the download page for gutsy is [http://packages.ubuntu.com/gutsy/libs/libglu1-mesa](http://packages.ubuntu.com/gutsy/libs/libglu1-mesa)

now go down and choose your "**Architecture**"
am using 32bit so i clicked on **i386**
select a mirror and download.

It will now ask you for dependencies, so search and download every dependency (downloaded one by one all dependencies will take time but is more secure if you know what you are doing)

If you get a broken dependency message just go in sypnatic -> status -> broken dependencies. Now remove these and you wont have more dependencies problems (some other installed files may also be deleted but you can easily add them afterwards so save them in a text file so you can add them later)

well to sum it up i downloaded 12 files for my system (including some library dependecies it was asking for):

ii  libgl1-mesa-dri                            6.5.3-1ubuntu1                         A free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx                            6.5.3-1ubuntu1                         A free implementation of the OpenGL API -- GLX runtime
ii  libglu1-mesa                               6.5.3-1ubuntu1                         The OpenGL utility library (GLU)
ii  mesa-common-dev                            6.5.3-1ubuntu1                         Developer documentation for Mesa
ii  mesa-utils                                 6.5.3-1ubuntu1                         Miscellaneous Mesa GL utilities

and some libraries:
tzdata_2007f-3ubuntu1_all
libxdamage1_1.1.1-3_i386
libstdc++6_4.2-20070626-0ubuntu1_i386
libgcc1_4.2-20070626-0ubuntu1_i386
libc6_2.5-11ubuntu1_i386
libc6-dev_2.5-11ubuntu1_i386
gcc-4.2-base_4.2-20070626-0ubuntu1_i386


Am lazy so just search by using the name of the file before the underscore "_" not with ubuntu version stuff ;)

---

