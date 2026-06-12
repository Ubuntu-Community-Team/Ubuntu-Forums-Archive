---
title: "programming required for writing music in Ubuntu?"
date: 2006-07-24
forum: Desktop Environments
---

### Post by 1002285 on 2006-07-24
I tried to find programs for writing music in Ubuntu, and found that musescore could be good (because it is said to be similar to Sibelius and Sibelius is sth I like).
But I need to compile it, and this leads me to things like qt and gcc, and qt page suggests that I need to learn programming in order to use qt.
Is it really that hard? Are there good forums or guides available?
I have looked at ubuntustudio.org, but it seems too difficult for me and seems to  be not quite meant for people like me (I don't so much care for recording or making the computer to play music, I mostly want to write scores).

And another question related to the subject - is there a program that would work in Ubuntu and would open .sib files?

---

### Post by Hanj on 2006-07-24
You only need to learn programming if you want to write your own software. When you download the source code for a program, all you have to do is compile it to make a program that you can run (someone has already done all the programming for you ;) ). 

Almost all programs you download as source packages under Linux can be installed by opening up a terminal and typing these commands:
```

./configure
make
sudo make install

```

However, if you haven't done any compiling before you are probably missing some packages which you will need to install first (using Synaptic package manager for instance). One such package is the one called "build-essential". I can't tell you exactly which other packages MuseScore needs (as I have never used it), perhaps you can look in the README or INSTALL files that came with the package and find out?

Also, keep in mind that a program that has no pre-compiled binaries for download and a version number of 0.2 might be under heavy development and may be very buggy/incomplete.

---

### Post by 1002285 on 2006-07-24
I was sure it could not be that hard :), but it's still difficult to understand for me.
[http://mscore.sourceforge.net/requirements.php](http://mscore.sourceforge.net/requirements.php)
this is the page that tells me that qt is a requirement and also gcc, and that "You _must_ compile MuseScore with the same compiler you used to compile QT".
Does that mean build-essential won't be enough?
[http://sourceforge.net/project/showfiles.php?group_id=109430](http://sourceforge.net/project/showfiles.php?group_id=109430) is the download page - I will probably need the tar file I guess.
Do I need to download the source to a specific location in order to use the codes you gave? Are the codes really like that or do I need to add the filename and location somewhere?
Thank you for your answer.

---

### Post by Hanj on 2006-07-24
You will most likely need the qt development files, which can be installed using Synaptic. I would guess the package you need is called libqt4-dev. It seems you also need libfluidsynth-dev. Once you have installed those and build-essential, download mscore-0.2.tar.bz2 and save it somewhere, let's say /home/user. Then extract the archive (right click on the file and select extract). 

Now open up a terminal (Accessories > Terminal) and type *cd /home/user/mscore* or whatever the directory is called. cd stands for "change directory" so that's just like double clicking on a folder. Now that you're at the right place, type *./configure*, *make* and then *sudo make install* to install it.

If you need some more packages you will get error messages when you try to compile - just post them here and hopefully someone can make something out of them.

---

### Post by 1002285 on 2006-07-25
Thank you, I'll start trying. (I would have started yesterday if I had got the email notification about your answer - I guess this does not work all the time).
I guess I don't need to compile anything else than musescore itself, if you're right, because qt and fluidsynth can be installed with synaptic. Thank you very much, and if I get more problems, I'll post again.

---

### Post by 1002285 on 2006-07-25
I did install libqt4-dev with Synaptic, but configure command gave me this as the last line:
configure: error: need qt >= 4.0.1
What could be the right package, or should I download qt source and try compiling it?

---

### Post by Hanj on 2006-07-25
That's very strange. If you installed libqt4-dev, you shouldn't get that error. I'm at a loss here, maybe someone else can help?

By the way, are you sure MuseScore is the best program for your needs? I don't know much about this kind of software myself, but I found a program called Rosegarden in the ubuntu repositories (i.e. it can be installed with Synaptic), which seems much more finished. Perhaps it could be worth a try?
There's also one called Denemo which seems a little less feature-rich.

---

### Post by trent dillman on 2006-07-25
I'd check Synaptic for qt related packages. Also, you may have to install gcc-3.4, and set an environment variable:

```
export CC=gcc-3.4
./configure
make
make install
```

---

### Post by 1002285 on 2006-07-25
Thanks, I will have to try Rosegarden and I had even already found it but for some reason I wanted to see this MuseScore thing, too, so I will go on trying, I guess, and see how far I can succeed.
I have done ./configure, make and sudo make install with qt source, by now, but I don't really know how to see if it is actually installed and working. May-be trying with musescore again will show me.

---

### Post by aysiu on 2006-07-25
I haven't tried these, but *musixtex*, *noteedit*, and *opustex* are in the Universe and Multiverse repositories.

---

### Post by 1002285 on 2006-07-25
> **Hanj said:**
> That's very strange. If you installed libqt4-dev, you shouldn't get that error. I'm at a loss here, maybe someone else can help?
.
I got the same error after compiling qt, which seemed to get on without any errors.
And I do have gcc 4.0.3-1 installed.
Maybe it's musescores problem at the moment?
Anyway, I guess I might give up for some time on this program and see other options like RoseGarden.
I wanted to see MuseScore because it was said to be similar to Sibelius. But I guess I can always look at sth else.

---

