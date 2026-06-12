---
title: "NWN + All Expansions - Easy Installation Instructions?"
date: 2007-04-27
forum: Gaming &amp; Leisure
---

### Post by Lotsapoppa on 2007-04-27
Hello, everyone.

First off, yes I know this topic has been discussed on the forum, but the information jumps from being newbie speak to more advanced users.

I, myself, am new to Ubuntu, and one of the many tests I am running to see if it ready for me to deep-6 Windows and get hip with Ubuntu, is the game test.

Is there, that anyone knows of, easy to follow, step-by-step instructions on how to install the Windows PC version of Neverwinter Nights (PLUS) all of the expansions?

If so, please point me to it!  

Much thanks in advance from a newbie n00b.

---

### Post by cogadh on 2007-04-27
I would start with a general how-to on Wine before jumping right into a particular game, if you are eventually looking to move away from Windows entirely. If you understand Wine better, installing almost any Windows app becomes much easier.

That being said, the Wine documentation is terrible (IMHO). As you say, it jumps very quickly from n00b speak to Linux-ese. But if you are patient and read through the docs while installing something simple, it will be helpful. Start at [http://www.winehq.org/](http://www.winehq.org/) with the user documentation, then spend a lot of time Googling answers to specific errors you may encounter.

---

### Post by Josey on 2007-04-27
this game runs natively so don't worry about wine

---

### Post by cogadh on 2007-04-27
Interesting, I didn't know that. I did just find this:
[http://news.softpedia.com/news/HOWTO-Play-Neverwinter-Nights-on-Linux-39615.shtml](http://news.softpedia.com/news/HOWTO-Play-Neverwinter-Nights-on-Linux-39615.shtml)

It may prove helpful.

---

### Post by Josey on 2007-04-27
run this with the original nwn cd's
[http://icculus.org/~ravage/nwn/donotlinktomyfiles/nwn_129_final.run](http://icculus.org/~ravage/nwn/donotlinktomyfiles/nwn_129_final.run)

then the sou expansion installer
[http://icculus.org/~ravage/nwn/donotlinktomyfiles/shadows_of_undrentide.run](http://icculus.org/~ravage/nwn/donotlinktomyfiles/shadows_of_undrentide.run)

then hotu installer
[http://icculus.org/~ravage/nwn/donotlinktomyfiles/hordes_of_the_underdark.run](http://icculus.org/~ravage/nwn/donotlinktomyfiles/hordes_of_the_underdark.run)

then download the latest patch
[http://files.bioware.com/neverwinternights/updates/linux/168/English_linuxclient168_xp2.tar.gz](http://files.bioware.com/neverwinternights/updates/linux/168/English_linuxclient168_xp2.tar.gz)

extract the patch to your nwn directory and overwrite existing files.
you'll have a 'nwn' file in the directory that runs the game.

btw... for me nwn runs smoother in ubuntu than in xp :)
and the good news is that you wont ever have to install it again if you just backup the folder you installed to.

---

### Post by Lotsapoppa on 2007-04-27
This is all great information, folks!  Thanks!

But, If someone would be so kind as to hold my hand a bit on this, I'd appreciate it.

So...step 1:  Put in the first CD.

Step 2:  ?

This is the kind of information I am missing and need, if it's possible.  I certainly don't want anyone to spend too much time on this, as I am sure there are more interesting topics to comment on.  But, as a newbie, these kind of instructions (the step by step ones) would be most beneficial.  

Anyone, out of the kindness of their heart, care to take a stab at writing step by step instructions?

Thanks!

---

### Post by Josey on 2007-04-27
the .run files above are like .exe's in windows... if you run them installation program will start.

basically step 2 is download and run the first file I linked to.

step 3 ... put in sou cd and run the second file

ect...

---

### Post by Lotsapoppa on 2007-04-27
OK. Thanks, Josey.

Do I put the CD in and THEN run the "Run" file?

Or do I copy all the contents of the CD to a directory and then run the "RUN" file in the directory I copied all the content to?

Please excuse my confusion, as my native OS environment [read: Windows] has made me rather stupid.

---

### Post by the8thstar on 2007-04-29
Hmm... I tried with NWN Diamond but it didn't work. Is there a .run file that is specific to the Diamond version somewhere?

---

### Post by leech on 2007-04-29
Check the How To I wrote in the forums (Link in my sig) it works with both the Platinum and the Diamond edition (though I personally only own the Platinum and haven't tried it with the Diamond)

Leech

---

### Post by the8thstar on 2007-04-29
It does work with Diamond too.

---

### Post by Extreme Coder on 2007-04-30
I'm not sure about Diamond/Platinum, but here is how I got my original game to work:
1) Go to [http://www.liflg.org/?catid=6&gameid=65](http://www.liflg.org/?catid=6&gameid=65)
2) Download the installers you need ( probably the first 3 files there, if you want SoU and HotU to work)
3) Download the latest updates for your language ( same here, all 3 files of any language if you want SoU and HotU)
4) Put CD in CD-Rom.
5) Run first installer, then the second two.
6) Run the updates.

That's it, I think. But you probably would better ask someone else before doing it, I'm not that sure...

Extreme Coder

---

### Post by Lotsapoppa on 2007-04-30
What is the difference between the original game and the Diamond/Platinum releases?  Why are there different installation paths?

---

### Post by Josey on 2007-04-30
> **Josey said:**
> run this with the original nwn cd's
[http://icculus.org/~ravage/nwn/donotlinktomyfiles/nwn_129_final.run](http://icculus.org/~ravage/nwn/donotlinktomyfiles/nwn_129_final.run)

then the sou expansion installer
[http://icculus.org/~ravage/nwn/donotlinktomyfiles/shadows_of_undrentide.run](http://icculus.org/~ravage/nwn/donotlinktomyfiles/shadows_of_undrentide.run)

then hotu installer
[http://icculus.org/~ravage/nwn/donotlinktomyfiles/hordes_of_the_underdark.run](http://icculus.org/~ravage/nwn/donotlinktomyfiles/hordes_of_the_underdark.run)

then download the latest patch
[http://files.bioware.com/neverwinternights/updates/linux/168/English_linuxclient168_xp2.tar.gz](http://files.bioware.com/neverwinternights/updates/linux/168/English_linuxclient168_xp2.tar.gz)

extract the patch to your nwn directory and overwrite existing files.
you'll have a 'nwn' file in the directory that runs the game.

btw... for me nwn runs smoother in ubuntu than in xp :)
and the good news is that you wont ever have to install it again if you just backup the folder you installed to.

Did you try this and it didn't work?

---

### Post by Lotsapoppa on 2007-04-30
Josey,

That is correct.  It did not work.

When I went to run NWN, it gives me a bash error cannot find file or something like that.

The installation went fine (no problems reported).  But when it came to the last step, to actually start the game, nothing happens.  

Suggestions?

---

### Post by Josey on 2007-04-30
This is the file I start the game with...

```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
# If you do not wish to use the SDL library included in the package, remove
# ./lib from the LD_LIBRARY_PATH
export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
export LD_LIBRARY_PATH=./lib:./miles:
  cd "/home/user/game/neverwinter"
  ./nwmain $@
  exit $? 
 
```

post yours

also post the exact output you get when run from terminal.

---

### Post by Lotsapoppa on 2007-04-30
OK, Josey, I'll do just that.

I'll try to post the information this evening.

Thanks again for sticking with me on this!

---

### Post by the8thstar on 2007-05-01
I gave up on NWN because of the weird colors given by the new Intel drivers while in play. I know that there is a fix for this (downgrading the drivers to 6.10 OS level), but I'm honestly fed up with all this tinkering. I'm just going to play NWN in windows XP until someone figures out a way to write a .run file for the Diamond edition.

That's my opinion.

---

### Post by Lotsapoppa on 2007-05-05
OK, Josey.  Here's what I have so far.

I have installed NWN and the two expansion.  As far as errors go during the installation, this is all I got:

setup.data/preinstall.sh: 3: Syntax error: "(" unexpected
Checking for required files

PASSED: ambient directory exists
PASSED: data directory exists
PASSED: music directory exists
PASSED: override directory exists
PASSED: miles directory exists
PASSED: nwm directory exists

When I run the "nwn" file, I get the following:

cyrus@linux:~/nwn$ sh nwn
Failed to initialize graphics.
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
cyrus@linux:~/nwn$ 

Here is a copy of what is in the nwn file:

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH

./nwmain $@


Any help you can offer would be great!

---

### Post by Josey on 2007-05-05
try this

```
sudo aptitude install libgtk1.2
```

then try running 'nwn' again

---

