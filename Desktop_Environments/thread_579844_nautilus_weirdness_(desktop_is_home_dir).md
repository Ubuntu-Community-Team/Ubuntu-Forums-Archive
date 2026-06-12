---
title: "nautilus weirdness (desktop_is_home_dir)"
date: 2007-10-18
forum: Desktop Environments
---

### Post by Jussi Kukkonen on 2007-10-18
This is a weird one: nautilus acts like I had set the gconf key *desktop_is_home_dir* to true, but I haven't.
 * files from my home directory fill the whole desktop
 * setting *desktop_is_home_dir* to false or true does absolutely nothing
 * restarting nautilus does not change things

Background: This is a fresh Gutsy install, but I've copied the contents of my home dir from my old computer onto this one... 

Any hints?


EDIT: Also, clicking Places->Desktop opens /home/jku (my home directory). It looks like my desktop folder is defined to be /home/jku instead of /home/jku/Desktop.

---

### Post by Sabretooth on 2007-10-20
Hi man, this is the exact problem that's happening to me. I discovered it some time ago, as an after-effect of another problem. [Thread's here](http://ubuntuforums.org/showthread.php?t=581498). Be sure to share your solution if you find one!

---

### Post by tonywhelan on 2007-10-20
> **Sabretooth said:**
> Hi man, this is the exact problem that's happening to me. I discovered it some time ago, as an after-effect of another problem. [Thread's here](http://ubuntuforums.org/showthread.php?t=581498). Be sure to share your solution if you find one!


See this link for a suggested fix (which worked for me).
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/154037](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/154037)

---

