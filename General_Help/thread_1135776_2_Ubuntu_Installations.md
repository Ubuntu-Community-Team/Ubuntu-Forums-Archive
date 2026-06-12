---
title: "2 Ubuntu Installations"
date: 2009-04-24
forum: General Help
---

### Post by bnshrdr on 2009-04-24
Currently I have Jaunty running on 2 separate partitions.  One of them is my general use partition, and the other one is my development partion, which I use for build/compiling/programming and other things.

The problem is there are some shared setting between the two and I want them completely separate.  They both share /home and /usr/local, but that is it.  It remembers things like what is on my panels, network settings, etc.  How can I make one distinguishable from the other?

---

### Post by jsowoc on 2009-04-24
It is likely that you will run into a problem sooner or later. The binaries for various programs go into /usr/local, but the corresponding config files go other places. If/when a program updates itself in /usr/local, it should update its config files (stored elsewhere). If you share /usr/local between two installs that get updated independently, that's asking for trouble. You should have a separate /usr/local for each install.

The second thing, is that your panels are stored in your /home. If you share /home between the two installs, any changes that get written to the config files in /home automatically get applied to both places.

Ideally, you should have two completely separate installs, with two separate /home, /usr etc (everything can be under /). You would then make a partition /common, in which you would keep all your "common" files that you want accessible from both installs.

To "fix" this, you need enough room in the "/" of each install to copy over the contents of /usr/local and the config files (i.e. /home without your personal files).

---

### Post by bnshrdr on 2009-04-24
Ok, thank you, that clears it up.

---

