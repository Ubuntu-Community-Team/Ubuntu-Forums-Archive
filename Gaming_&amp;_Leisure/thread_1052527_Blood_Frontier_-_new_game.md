---
title: "Blood Frontier - new game"
date: 2009-01-27
forum: Gaming &amp; Leisure
---

### Post by electrogeist on 2009-01-27
Release Candidate was just issued today (Jan 27) with a scheduled release date of about a week.  It also hit slashdot today... so their server, including website, documentation, and the main server for reporting game servers is pretty much down right now.

Download for FREE from either:
[LIST]
[*][http://bloodfrontier.com/](http://bloodfrontier.com/)
[*][http://sourceforge.net/project/platformdownload.php?group_id=198419](http://sourceforge.net/project/platformdownload.php?group_id=198419)
[*]release candidate filename is: bloodfrontier-B1-RC1-linux.tar.bz2
[/LIST]

Unzip it.  You can double click the downloaded file and drag "bloodfrontier" folder to your home directory

There is a 32-bit binary and the source code to compile your own.  I am trying to use the binary...
```
$ cd ~/bloodfrontier
$ ./bloodfrontier.sh
```

It might run if you are 32-bit, but I have 64-bit Ubuntu 8.04 and got the following:
[INDENT]*  bin/bfclient: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory *[/INDENT]

So I used Cappy's getlibs script[LIST]
[*][http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
[/LIST]```

$ getlibs ~/bloodfrontier/bin/bfclient
libSDL_image-1.2.so.0: libsdl-image1.2
The following i386 packages will be installed:
libsdl-image1.2
Continue [Y/n]? y
Downloading ...
Installing libraries ...
[sudo] password
```

Tried again and it worked ...sort of.  No sound.  Lotsa warnings "failed to load sample:" and "unregistered sound:" continues to fly by during gameplay.  No errors saying that sound failed to initialize or anything though.   

It was a 32-bit ogg vorbis dependancy or two:
```
$ getlibs -p libvorbis0a
$ getlibs -p libvorbisfile3 
```
The first one (libvorbis0a the main lib) didn't do it alone, but after installing libvorbisfile3 the sound works. I already had the 32-bit libsdl-1.2mixer

---

### Post by RichardLinx on 2009-01-28
I saw this on Slashdot today as well. It looks like It could be a really good game. I'll have to give it a try sometime. I would give It a go now but I'm bandwidth limited in my area so I can't download it right now.

---

### Post by binbash on 2009-01-28
Umm homepage is empty?

---

### Post by hikaricore on 2009-01-28
> **electrogeist said:**
> **It also hit slashdot today... so their server, including website, documentation, and the main server for reporting game servers is pretty much down right now.**
[COLOR="White"]-[/COLOR]
> **binbash said:**
> Umm homepage is empty?

---

### Post by Carpentr on 2009-01-28
Homepage posted is empty , but this one isn't. 

[http://bloodfrontier.com/](http://bloodfrontier.com/)

---

### Post by hikaricore on 2009-01-28
You lot really don't pay attention do ya.

You linked the exact same website without the www prefix...

---

### Post by qreeves on 2009-01-28
> **hikaricore said:**
> You lot really don't pay attention do ya.

You linked the exact same website without the www prefix...

Actually they're one of the few paying *extra special* attention. [http://bloodfrontier.com/]("http://bloodfrontier.com/") is correct, www. is not :)

As for the O.P. try installing libsdl-1.2mixer (and you may quite possibly need to append "alsa" to that). Failing that, make sure ogg vorbis support is available (dependencies of dependencies?).

---

### Post by electrogeist on 2009-01-28
> **qreeves said:**
> Actually they're one of the few paying *extra special* attention. [http://bloodfrontier.com/]("http://bloodfrontier.com/") is correct, www. is not :)

As for the O.P. try installing libsdl-1.2mixer (and you may quite possibly need to append "alsa" to that). Failing that, make sure ogg vorbis support is available (dependencies of dependencies?).

I'll update my original post with that url correction. 

I did fix the sound!! It was a 32-bit vorbis dependancy or two:
[INDENT]$ getlibs -p libvorbis0a
$ getlibs -p libvorbisfile3 [/INDENT]

The first one (libvorbis0a the main lib) didn't do it alone, but after installing libvorbisfile3 the sound works.  I already had the 32-bit libsdl-1.2mixer

Now I have to run out and do something but will play later...

Thank you for joining the community to make this your first post!

---

### Post by qreeves on 2009-01-29
> **electrogeist said:**
> I'll update my original post with that url correction. 

I did fix the sound!! It was a 32-bit vorbis dependancy or two:
[INDENT]$ getlibs -p libvorbis0a
$ getlibs -p libvorbisfile3 [/INDENT]

The first one (libvorbis0a the main lib) didn't do it alone, but after installing libvorbisfile3 the sound works.  I already had the 32-bit libsdl-1.2mixer

Now I have to run out and do something but will play later...

Thank you for joining the community to make this your first post!

Great to hear, you can thank a Gentoo user that came a little earlier to our IRC channel who had the same problem and solved it. I made a note to remember it, as I don't use Linux on my desktops.

Enjoy playing Blood Frontier, we enjoyed making it :)

---

### Post by Vadi on 2009-01-29
Hm, a tad too much magic to get it to work properly on a 64bit ubuntu for me. I'll wait 'till they have a better solution.

Looks quite nice though.

---

### Post by zmjjmz on 2009-01-29
Got it installed.
It's pretty fun, kinda like OpenArena but with less physics.

---

### Post by crazyfuturamanoob on 2009-01-31
I downloaded it, but pre-compiled binaries couldn't run because of incorrect linking or something.

Had to recompile them from source, and then it worked.


This is a good start for a good game. But I didn't like it.

Weapons feel powerless, they don't have recoil, anims suck.

If these things would get fixed then I'd just love it:
[list]
[*]Much more recoil for all weapons
[*]Faster reloading (shotgun, sniper)
[*]Better reloading/shooting animations
[/list]

---

### Post by eragon100 on 2009-01-31
Cool, let's hope some players actually start playing it online! It's a very cool game and the graphics are nice!

---

### Post by rv65 on 2009-02-07
How do I compile this game? I have compiled other programs but just wanted to make sure. The readme doesn't mention it though.

---

### Post by crazyfuturamanoob on 2009-02-07
> **rv65 said:**
> How do I compile this game? I have compiled other programs but just wanted to make sure. The readme doesn't mention it though.
Pre-compiled binaries didn't work so I had to do this to get it working:
> 
cd <bloodfrontierdirectory>/src
make
cd ..
rm bin/bf*
cp src/bfclient bin
cp src/bfserver bin


---

### Post by charlieg on 2009-02-13
> **crazyfuturamanoob said:**
> I downloaded it, but pre-compiled binaries couldn't run because of incorrect linking or something.

Had to recompile them from source, and then it worked.


This is a good start for a good game. But I didn't like it.

Weapons feel powerless, they don't have recoil, anims suck.

If these things would get fixed then I'd just love it:
[list]
[*]Much more recoil for all weapons
[*]Faster reloading (shotgun, sniper)
[*]Better reloading/shooting animations
[/list]
No point reporting the wishlist here.  It's an open source project - contact them and let them know, details are on the website!

---

### Post by Vadi on 2009-02-28
Ubuntu .debs: [http://www.getdeb.net/app/Blood+Frontier](http://www.getdeb.net/app/Blood+Frontier)

Gave it a try - the graphics are quite nice actually, but there was nobody to play with online.

---

### Post by binbash on 2009-03-01
> **Vadi said:**
> Ubuntu .debs: [http://www.getdeb.net/app/Blood+Frontier](http://www.getdeb.net/app/Blood+Frontier)

Gave it a try - the graphics are quite nice actually, but there was nobody to play with online.

Thanks i am downloading right now

---

### Post by BigSilly on 2009-03-01
What's the single player game like?

---

### Post by Vadi on 2009-03-01
Default bot skill is tough! I had to lower them to be able to compete.

Then again I'm too use to Savage 2's melee (or the curved arrow path), my sniping skills aren't great :)

---

### Post by Sealbhach on 2009-05-02
This is pretty good, I just tried it in Jaunty 64 and it runs very well.


.

---

### Post by Arand on 2010-06-06
This game has now been forked into Red Eclipse ( [http://www.redeclipse.net](http://www.redeclipse.net) ) and all active main developers and community has left BF which is as of now pretty much dead.

More info (by the now lead developer of RE, Quinton Reeves) available at [http://www.quadropolis.us/node/418](http://www.quadropolis.us/node/418)

And (by the initiator the original BF, Anthony Cord): [http://www.bloodfrontier.com/](http://www.bloodfrontier.com/)

Red Eclipse has not had an official (pre-) release yet, which will happen, in due time...

I've started doing some preview builds of the SVN version for ubuntu in my PPA: [https://edge.launchpad.net/~arand/+archive/redeclipse](https://edge.launchpad.net/~arand/+archive/redeclipse)
PLEASE DO READ the information at the PPA page, any complaints should be directed initially at ME (don't pester the RE devs about what is likely a packaging/delay problem on my behalf), thanks, enjoy.


- arand

---

### Post by ShiftSide on 2010-06-06
Can't find a download for red eclipse?

---

### Post by Rytron on 2011-02-28
> **ShiftSide said:**
> Can't find a download for red eclipse?

```
sudo add-apt-repository ppa:itachi-sama-amaterasu/redeclipse-client; sudo apt-get update; sudo apt-get install redeclipse
```

How can I change my name in Red Eclipse?

---

### Post by Arand on 2011-02-28
> **Rytron said:**
> How can I change my name in Red Eclipse?The config file lies in ~/.redeclipse so either rewrite it in-place or delete the directory and clear all configurations.

I also supply some packaging over at: [https://edge.launchpad.net/~arand/+archive/redeclipse](https://edge.launchpad.net/~arand/+archive/redeclipse)

- arand

---

### Post by Rytron on 2011-02-28
Thank you Arand. RE is an incredible game. The makers did a superb job.

---

