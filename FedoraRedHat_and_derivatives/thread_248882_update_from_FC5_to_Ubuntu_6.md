---
title: "update from FC5 to Ubuntu 6"
date: 2006-09-01
forum: Fedora/RedHat and derivatives
---

### Post by sharkdiver on 2006-09-01
Hi all,

I'm thinking of trying out Ubuntu 6 because I'm tired of constant upgrades (which has left my system in a mess that yum cannot sort out), as I'm running Fedora Core 5 currently.
However, I have lot's of downloaded files and programs that I've installed manually off of the web (and some are installed in non-default places), so I'd like to mess with my hard drive/partitions as little as possible. I run LVM and dual boot Win XP (not by choice).

Hw can this be done as easily as possible, and what should I think about?

Cheers,
/sharkdiver

---

### Post by patwack on 2006-09-01
i doubt it can be done as the two distros are so different, best off just backing up any stuff you really need to keep and doing a clean install

---

### Post by SoundMachine on 2006-09-01
> **sharkdiver said:**
> Hi all,

I'm thinking of trying out Ubuntu 6 because I'm tired of constant upgrades (which has left my system in a mess that yum cannot sort out), as I'm running Fedora Core 5 currently.
However, I have lot's of downloaded files and programs that I've installed manually off of the web (and some are installed in non-default places), so I'd like to mess with my hard drive/partitions as little as possible. I run LVM and dual boot Win XP (not by choice).

Hw can this be done as easily as possible, and what should I think about?

Cheers,
/sharkdiver

Copy them with the full path to wherever you can save them, use parted or whatever, copy them back after you are done, there is no other way that will work (this means all of the files, from /usr/local/bin to /etc and so on)

If i were you i'd just make a list, make sure there are no debs and simply download and reinstall what i needed using make-kpkg instead of the standard make.

---

### Post by sharkdiver on 2006-09-02
Ok, thanks guys. Another reason to migrate to Ubuntu is the user community, which you guys proved yet again.

I was hoping for a quick fix, but maybe I'd better take the bull by the horns and backup everything and make a clean install.

cheers,
sharkdiver

---

### Post by ferd on 2006-09-02
I've done exactly this over the last few days. It is my experience that it is easier to install and configure U6 than fc5. My biggest problem was getting lm_sensors configured but I was able to do it by typing "sensors-detect in this forum's search box and finding the correct script. Often having the correct repos loaded is the solution to the problem of "how can I find ?." As for performance, U6 is faster to load web pages through Firefox and loading apps seems about the same. Good luck and enjoy.  :cool:

---

