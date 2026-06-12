---
title: "Unable to close explorer window in top left hand corner of desktop screen"
date: 2014-06-30
forum: Desktop Environments
---

### Post by archp2009 on 2014-06-30
I am currently getting a reduced size file manager window whenever I log into Xubuntu 14.04.  [http://s727.photobucket.com/user/archp2008/media/Screenshot-14-06-30-085635PM.png.html](http://s727.photobucket.com/user/archp2008/media/Screenshot-14-06-30-085635PM.png.html)
I cannot close this window. It was not always there.  Is there a way to get rid of this?

---

### Post by Toz on 2014-06-30
That's the whisker menu. Its blank because its displaying the search results for "updater" - which there are none. Whats interesting (other than the fact that it's displaying on login) is that the desktop icons are sitting on top of it.

Lets try clearing your sessions cache first. Go to Settings Manager >> Session and Startup >> Session tab >> and click on "Clear saved sessions". Then log out and back in again to see if its gone.

---

### Post by archp2009 on 2014-07-01
Thanks for the reply.  On second thought it does not appear at login as I though but immediately after searching for updater which is usually the first thing I do.  I have 10 different distros installed so I still can't remember the location of software updater for each one, so typically I type in updater and that finds it for me.  Clearing saved sesssions did not get rid of it, but I think restarting will, until I type in update or updater and then it comes back again.  I need to memorize how to find Muon updater for Xubuntu so I don't need to type updater. No, once the whisker menu comes up, even restarting does not get rid of it.  The fist time I booted into Xubuntu today it was not there, though, only after I started looking for the updater.  Perhaps a cold start will get rid of it.  I will try a cold start.

---

### Post by Toz on 2014-07-01
> **archp2009 said:**
> I need to memorize how to find Muon updater for Xubuntu so I don't need to type updater.
Xubuntu doesn't use Muon updater, I believe thats the KDE updater. Xubuntu has a software updater and its located in the Settings Manager - unfortunately a search in the Whisker Menu won't bring it up.

---

### Post by archp2009 on 2014-07-01
Thanks for this.  Evidently I am thinking about another Ubuntu distro.  The old memory is not getting any better.  Regarding the cold start, even that did not get rid of the whisker menu.  It is still there.

---

### Post by archp2009 on 2014-07-01
Right clicking on the top left corner icon on the whisker menu and choosing desktop settings allowed me to choose the desktop without the whisker menu. It appears that what is happening is that I am seeing a screen capture of the desktop with the whisker menu.  It is only an image not the menu itself.  I wonder why this keeps happening.  I am using a customized desktop background with the name of the distro printed on the lower right corner so I'll know which one I am in.  I don't know where the new imsages with the whisker menu included are coming from.

---

### Post by Toz on 2014-07-01
Go to Settings Manager >> Desktop. There you can select another background image as well as identify where the current image is coming from.

---

