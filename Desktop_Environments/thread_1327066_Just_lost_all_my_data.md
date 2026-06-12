---
title: "Just lost all my data"
date: 2009-11-15
forum: Desktop Environments
---

### Post by Melcar on 2009-11-15
Okay, something really messed up just happened to my main desktop running Kubuntu Karmic.  I was just changing some folder locations in the "About Me" manager (the Music, Documents, and Downloads folders to be specific) and after I hit *Apply* I got an error message about the location not being valid.  After that I noticed that part of my desktop had reverted to the default colors and icons, and when I went into my Home folder none of my data was there anymore.  In fact, nothing was there anymore.  The entire thing had reverted back to its original state (as if I had just installed Kubuntu) with all my data and applications gone.  Yes gone; I can't find them anywhere and my partition is 100GBs bigger (the exact amount of stuff I had already installed).  
Needless to say I'm raging right now and have no idea what happened.  It's not the HDD I'm sure as I always check its SMART status.  Anyone have any idea what happened?

---

### Post by kellemes on 2009-11-15
You have used your filemanager/terminal to check if stuff is really not in /home/<yourusername>?
Guess you did..

Don't see how stuff can magically disappear to be honest..
At least I'd stop using the system and mount it from a livesystem, so at least you won't destroy accidentally deleted data and you can start restoring it..

---

### Post by UbuntoJO on 2009-11-15
have you looked in nautilus under home>users>?

sounds like it's there somewhere.

---

### Post by Zorael on 2009-11-15
> **UbuntoJO said:**
> have you looked in nautilus under home>users>?
The thread has a [COLOR="RoyalBlue"]**[kubuntu]**[/COLOR] tag. :3

Regarding what you're experiencing, I opened up About Me and had a try myself.

Some of the values pointed to my home folder, though I'm 100% positive I had changed them before, shortly after installation (during Karmic betas). For instance, my Documents path was pointing to /home/zorael. Setting it to the correct directory, /main/documents, I get a dialog window;
> The path for 'Documents' has been changed.
Do you want the files to be moved from '/home/zorael/' to '/main/documents/'?
Obviously, saying 'yes' here would move my entire home to my documents directory.

I imagine you answered yes and your home is now somewhere in your (new) Desktop/Documents/Downloads/Movies/Pictures/Music directory.

This should perhaps be filed as a bug, to save users from themselves when the paths point to home. It *did* do as instructed, but I'm not sure why the values would be unset/set to home to begin with. I guess a case can be made for there to be a sanity check before asking to move the files, so that it doesn't try to move home.


**edit**, from #kubuntu-devel;
```
[12:56] <apachelogger> zorael: bugs.kde.org
[12:57] <apachelogger> zorael: also, IIRC none of the default locations points to $HOME, so the only way this could happen is by users poking around in the config or by a very long upgrade path (probably starting before 8.04)
[13:08] <zorael> apachelogger: In my case the config file was tampered with before account creation (/etc/xdg/user-dirs.defaults). The paths I pointed them to were on a different partition (/main), so perhaps at some boot it failed to mount and went crazy? *shrug*
[13:14] <apachelogger> *shrug* that user-dirs stuff is magic to me :)
```
[bugs.kde.org](http://bugs.kde.org) here.

---

