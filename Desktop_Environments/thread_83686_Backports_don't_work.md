---
title: "Backports don't work"
date: 2005-10-29
forum: Desktop Environments
---

### Post by SmellyLlama on 2005-10-29
Hi,

I recently installed the Breezy Badger. Of course, I want to be able to stream and watch movies of all kinds, so I tried to install mplayerplug-in. Therefore I added the backports repository to my /etc/apt/sources.list.
However, when I run apt-get update, it complains that it can't find those repositories. I have tried several mirrors.

On a side note, why on earth is the "Repositories" dialogue in synaptic removed?

---

### Post by Xian on 2005-10-29
The Breezy Backports repo is not in operation. However, if you follow the [Ubuntu FAQ Guide](http://help.ubuntu.com/starterguide/C/faqguide-all.html) you can get the application that you want and other multimedia packages. Specifically, in this case you need to enable the multiverse repo.

For example, here is the mplayer plugin information:

```
$ sudo apt-cache policy mozilla-mplayer
mozilla-mplayer:
  Installed: (none)
  Candidate: 3.05-1ubuntu1
  Version table:
     3.05-1ubuntu1 0
        500 http://us.archive.ubuntu.com breezy/multiverse Packages
```

---

