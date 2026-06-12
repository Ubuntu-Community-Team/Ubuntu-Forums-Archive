---
title: "Cannot mount hard drive/ibus error?"
date: 2011-02-19
forum: Desktop Environments
---

### Post by shenghaiknight on 2011-02-19
Hey guys,

I am dual booting windows 7 and kubuntu, and when I try to access my main filesystem where all my files are, a KdeSudo prompt pops up to authenticate. I type in my password correctly, and it gives me the following error message:

an error occurred while accessing '265.8GiB hard drive', the system responded:QInotifyFileSystemWatcherEngine:addPaths:
inotify_add_watch failed: No such file or directory QFileSystemWatcher: failed to add paths: /home/kevin/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon

It worked fine for about a day when I first installed it (yesterday), and now it suddenly gives me this. Can anyone help me out?

---

### Post by shaka_zulu on 2011-02-19
What did you do before that happened? Did you have any update or did you install something?

---

### Post by shenghaiknight on 2011-02-19
I don't think so...it just stopped working all of a sudden...

---

### Post by shaka_zulu on 2011-02-20
Did you try to unmount that partition manually first?

---

### Post by shenghaiknight on 2011-02-20
no I think I just booted up one time and it wouldn't mount. This happened at the same time that I stopped being able to access the user management setting in system settings. Maybe I did something to remove admin privileges? Is there a way to mount a hard disk as root?


EDIT:

I got this same thing when I tried to open okular to view an image. It opened fine, but this might give another clue?

okular 183732_10150111047764893_507674892_6121076_6116362_n.jpg 
okular(4474)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
okular(4474)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
okular(4474)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/kevin/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon

---

### Post by shaka_zulu on 2011-02-20
Do you maybe have Strigi/Nepomuk turned on? If i have understood you correctly you can see that partition but anytime you try to access its content you can't actually. Right? I had similar problem and just trying to recall the solution.

---

