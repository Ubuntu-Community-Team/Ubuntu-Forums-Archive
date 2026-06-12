---
title: "compiz settings manager won't load in gutsy"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by spooky1 on 2007-11-01
I just upgraded(twice) to gutsy from feisty. The first time, compiz was running perfectly and Imade no changes before beforehand. After the upgrade, I couldn't get the settings manager running, I saw a post which said you should unistall compiz before the upgrade. I reinstalled feisty, removed any compiz I could find, then upgraded again. Same problem again. Has anyone encountered this and found a fix? Do I need to add a new repository for my compiz download?Some of the effects are working, it's runnining in my process list, but when I click on the settings manger nothing happens, so I can't customize anything.

Any help is much appreciated...thanks:

---

### Post by Jose Catre-Vandis on 2007-11-01
Have you checked that ccsm is properly installed?
```
sudo apt-get install compizconfig-settings-manager
```
it is not installed by default in Gutsy

---

### Post by Zorael on 2007-11-01
And if it's there and still won't start, try purging *everything*, then reinstall and see if it improves. I understand this is a common issue for upgraders who've used Treviños repository.

```
$ sudo apt-get **purge** compiz* libcompiz* emerald* libemerald*
```

---

### Post by spooky1 on 2007-11-01
I reinstalled according to the first post, no change. If I purge all compiz and reinstall, I I would be reinstalling from the same repository. Can anyone post some reliable repository sources for me to add?  
thanks

---

### Post by Zorael on 2007-11-01
Er, well, the official ones? :>

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

And you don't need the 'Beryl' repository offered there.

---

### Post by spooky1 on 2007-11-01
problem solved,thanks for the help guys

---

