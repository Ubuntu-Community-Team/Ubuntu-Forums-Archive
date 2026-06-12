---
title: "update killed my desktop"
date: 2005-05-16
forum: Desktop Environments
---

### Post by giosico on 2005-05-16
i ran update and when kde restarted it went into a wizard and then my desktop was reconfigured ... the clock was missing ... and there were about 5 applet fail messages.

Any ideas?

---

### Post by Calgarian on 2005-05-16
Were you trying a 3.4 update? I got into the same problem and found that I had a partial 3.4 install. It was a mess and actually did a re-install. Fortunately I had a current backup of my data.

---

### Post by giosico on 2005-05-16
Good question.  I have no idea and thought ubuntu would handle data better ... I have no idea how to back up a desktop config ... nor what update gets done when one does a sudo apt-get update .... wont make that mistake again ... its been years since I ran linux and things have not changed that much ... well with the exception of how easy LAMP was to install ...good work ubuntu

---

### Post by rudiz on 2005-05-16
Right click on the Panel and >Add to Panel>.......Make your choices for the apples/applications/Special Buttons........to install the missing applets etc

---

### Post by giosico on 2005-05-16
Thanks for all of your help.

I guess I was looking for something more to fix the damage ... no have to manually fix the desktop ...

Yes is did update KDE to 3.4 ... so this thread could be considered a "bug" report of as such ... that if you run default kubuntu install and then do apt-get upgrade and which grabs kde 3.4 is will kill most of the desktop settings ... as least that is my experience of it ... it did keep my quick launch apps to use a ms term

SOLUTION: Create a new user ... that gets you a nice default desktop config.

Thanks for all your help.

---

### Post by philipacamaniac on 2005-05-16
Kubuntu has KDE 3.4 on the CD... The upgrade is some KDE libraries that happen to somehow bork everything.

This thread shows you how to fix it: [http://ubuntuforums.org/showthread.php?t=32166](http://ubuntuforums.org/showthread.php?t=32166)

Basically, you have to force the installation of the kdelibs-data package, which kills all your settings. To counter that, simply make a backup copy of /home/$username/.kde

---

### Post by giosico on 2005-05-16
Thank you so much for taking the time to reply.  You dont have 5 cups of ubuntu for nothing! :-)

---

