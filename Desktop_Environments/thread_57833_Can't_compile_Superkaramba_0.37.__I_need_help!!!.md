---
title: "Can't compile Superkaramba 0.37.  I need help!!!"
date: 2005-08-18
forum: Desktop Environments
---

### Post by muzza on 2005-08-18
I've tried to install Superkaramba to use Liquid Weather.  I was told that I needed Superkaramba 0.37 and that I would have to compile it  myself, and that this process was straightforward.

My feeble attempts to compile can be read  [at the end of this thread](http://www.ubuntuforums.org/showthread.php?t=51359) But I'm not getting any response, so I'm starting a new thread.

When I typed ./configure, there was always something missing, so I kept going to Synaptic, installed the missing bit, then ran ./configure again.

This went on for ages over a couple of nights.  There seemed to be an endless stream of missing bits. (I would have given up ages ago, but I think this is a good Linux learning exercise for me) (and I do have better things to do)

Anyway, each time I would get further down the 'configure' console, but now I'm stuck.  The last few lines of the console reads as follows.

[COLOR=Blue]checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for IceConnectionNumber in -lICE... no
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... configure: error: not found.
          Possibly configure picks up an outdated version
          installed by XFree86. Remove it from your system.

          Check your installation and look into config.log[/COLOR]

I've searched for libz, but there's nothing there, so I can't remove it.  I searched Synaptic and it comes up with 31 packages that begin with those 4 letters.

Why am I making this so difficult for myself.  All the searches I've done comes up with the same simple instructions. 
1. type; ./configure
2. type. make
3. type. sudo make install

This is my 3rd day trying to get this sorted.  Somebody PLEAAAASSSSE help me.

---

### Post by ltmon on 2005-08-18
I haven't tried myself, but I'm surprised that this is so hard. SK 0.37 is bleeding-edge, beta-release software so weird problems may come up from time to time.

Things you can try:

- The liquid weather home page still has older versions that work with the current stable SK available for download.  I use an older version (v. 6.2) and SK 0.36 (I think) and it works fine.  I don't think you're missing out on much.  [http://homepages.comnet.co.nz/~matt-sarah/](http://homepages.comnet.co.nz/~matt-sarah/)

- The Superkarama help forum is [http://sourceforge.net/forum/forum.php?forum_id=67470](http://sourceforge.net/forum/forum.php?forum_id=67470).  The people there may have more specialized knowledge about superkaramba, especially the version of libz (which incidentally is another name for libz, a file compression library) which is required.  It may turn out that you need to get hold of a newer version of this library, which may involve compiling it yourself also.

Cheers,

L.

---

### Post by Jeff Eklund on 2005-08-18
[QUOTE=muzza][COLOR=Blue]checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for IceConnectionNumber in -lICE... no
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... configure: error: not found.
          Possibly configure picks up an outdated version
          installed by XFree86. Remove it from your system.

          Check your installation and look into config.log[/COLOR]

I've searched for libz, but there's nothing there, so I can't remove it.  I searched Synaptic and it comes up with 31 packages that begin with those 4 letters.[/QUOTE]
 I'm having the exact same problem, but with other programs I try to compile. I start going through the ./configure-process and then they all come to that end. I would also like to see some way to fix that problem easily.

---

### Post by muzza on 2005-08-18
[QUOTE=Jeff Eklund]I'm having the exact same problem, but with other programs I try to compile. I start going through the ./configure-process and then they all come to that end. I would also like to see some way to fix that problem easily.[/QUOTE]

Thank God it's not just me.

I WANT to learn this stuff, but it's damned frustratingly unrewarding, ain't it?

---

### Post by skyboy on 2005-08-18
try installing this :
sudo apt-get install libzzip-dev

---

### Post by eMuNiX on 2005-08-18
You'll have to install a couple of things (not sure if the last in the list is really needed but threw it in for good measure as it would be useful in the future if nothing else)

```
sudo apt-get install build-essential automake kdelibs4-dev python2.4-dev kdebase-dev
```

Whilst trying to get this to work I also installed libzzip-devel but it didn't, on its own, get past the libz problem so it may or not be required (not going to do another fresh install today to try this out  :roll: )

During the config it did complain:-
"checking for libxmms... ./configure: line 43879: xmms-config: command not found
./configure: line 43881: xmms-config: command not found" 
but it continued on to create makefile and should install okay from there.

---

### Post by Jeff Eklund on 2005-08-18
Haha! I solved my problem by installing kdelibs4-dev! I tried libzzip among others but nothing seemed to do it. But then i picked kdelibs4-dev and installed all the required packages with synaptic and now everything is working like a charm!
Thanks a bunch!

---

### Post by muzza on 2005-08-19
I've got it.

Thank you Skyboy.
Thank you eMuNiX.
Congratulations Jeff Eklund...


...and thank you (K)Ubuntu forum.

---

### Post by Jeff Eklund on 2005-08-19
> **muzza]
Thank you Skyboy.
Thank you eMuNiX.[/quote]Yes, thank you.
[QUOTE=muzza]Congratulations Jeff Eklund...[/quote]Congrats yourself  said:**
> ...and thank you (K)Ubuntu forum.Couldn't agree more.

---

### Post by aftertaf on 2005-08-26
yeah... good one  :smile: 

after much pain and breaking of systems, i've decided to go kubuntu instead of debian...
every time i go unstable, the system does too... funny that.  :?
and i stumbled on this post cos it looks worth installing, and thanks for the guidance before i get started!!

---

### Post by ispmarin on 2005-10-31
Hello all...
I hoped, after so many congratulations I thougth that this will solve my problems. I am running a updated from hoary breezy badger and my open office installation is not working, complaining about the same libz. I have installed kde4libs-dev and libzzip-dev, but still not working. So, I say, Help!

Thanks!

Ivan

---

### Post by soxofaan on 2005-11-11
[QUOTE=Jeff Eklund]Haha! I solved my problem by installing kdelibs4-dev! I tried libzzip among others but nothing seemed to do it. But then i picked kdelibs4-dev and installed all the required packages with synaptic and now everything is working like a charm!
Thanks a bunch![/QUOTE]

I could get past the libz configure problem by just installing **zlibg1-dev** instead of that the whole bunch of kdelibs4-dev related packages.

---

