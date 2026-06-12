---
title: "Cinnamon install directory?"
date: 2015-05-18
forum: Desktop Environments
---

### Post by mattig89ch on 2015-05-18
Hidy ho all,

I'm using the Cinnamon Desktop Environment, and the text color is a really dark grey.  Making it hard to read the icons.

I found a solution where you have to manually tell the default theme to make the text white instead of black.
[http://forums.fedoraforum.org/showthread.php?t=300371](http://forums.fedoraforum.org/showthread.php?t=300371)

But it says I have to find the install directory for the cinnamon UI, and I have no idea where that is.  Does anyone know where the default installation directory is for cinnamon?  Or where to find that info?

---

### Post by Vladlenin5000 on 2015-05-19
Nowhere it says you need to "find install directory for the cinnamon UI". As a matter of fact, it merely points to a specific directory where a certain file should be created. A moot point anyway, unless you're running Fedora and if so the forum you linked is a better avenue for your search.
So, without further info about your system I strongly advise against proceeding with whatever you're doing/trying to.

---

### Post by mattig89ch on 2015-05-20
oh, I see.  Sorry,  didn't realize that was a fedora specific forum.

Basically, the dark grey of the text for the cinnamon UI makes it very difficult to read the text of the desktop icons.  I wanted to change them to a color that was easier to read, white was just the example.  And this is a virtual machine I'm experimenting with, so I could delete it tomorrow and not be disappointed.

As such, rooting around and messing with system settings is great practice and won't harm anything.

---

### Post by vasa1 on 2015-05-20
You may find more users and more guidance here: [http://forums.linuxmint.com](http://forums.linuxmint.com).

---

### Post by buzzingrobot on 2015-05-20
The directory referred to at Fedoraforums is > ~/.config/gtk-3.0  which is more or less universal. The OP can add that fix, log out and in, and see what, if anything, changes.  Worse comes to worse, remove it.  

I'll guess Nemo has to have control of the desktop for this.

---

### Post by mattig89ch on 2015-05-21
wow, so there is a ~ directory.  lol, i'm learning more about this OS every day.

Thanks for the help all, I'm going to add that line into the document and see what happens.

---

### Post by buzzingrobot on 2015-05-21
> ~ is shorthand for that user's home folder.  I.e., User Bob's folder will be /home/bob, and user Sammy's folder will be /home/sammy/.  Linux is multi-user, meaning any number of users can have an account on a single system, using it simultaneously if they wish.  

The shell program -- Bash -- that executes in the terminal understands '~' and expands it correctly.

Something like "/config/gtk', without the '~', points to the '/' directory, where there probably is not a 'config/gtk' directory and where you probably don't want one. (Note that although the '/' directory is often referred to as the 'root' directory, it is actually the beginning of the file system hierarchy and all other directories are 'inside' it.  There is an actual 'root' directory located as '/root'.  A bit confusing, but the usage is about 40 years old and isn't going to change.)

---

### Post by mattig89ch on 2015-05-21
Wow, has ot been 40 years of life for Linux?  I though linux cam to be in the mid 90's

---

### Post by buzzingrobot on 2015-05-21
Unix had been around for 40 years or so, give or take.

---

### Post by Vladlenin5000 on 2015-05-21
Linux is 20 something years old but, as usual, it wasn't built from scratch, as new "thing". We're all constantly sitting on the shoulders of giants. The giant here is Unix which has been around since the time when The Rolling Stones were young so, yeah, a long time ago.

---

### Post by mattig89ch on 2015-05-21
wow, thats awesome.  I know a tiny bit about linux history, but I didn't know Unix was around for 40 some odd years.

I have to look up what it was first used for.

Oh, and I went ahead and created the file, and copied and pasted the text from the OP (see?  I'm learning).  The folder was already there, and it worked!  now my cinnamons desktop text is a nifty shade of white.

If only I could get people to respond to my likewise open post like you guys responded here.  Many thanks for the help all!

---

### Post by Vladlenin5000 on 2015-05-21
Sorry, I don even know what that is...

I'm glad we were helpful with this one though. If you're satisfied then you can use the thread tools to mark this one as solved, so others may benefit.

---

