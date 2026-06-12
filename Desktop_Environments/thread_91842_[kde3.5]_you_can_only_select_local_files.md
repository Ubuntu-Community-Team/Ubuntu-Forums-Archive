---
title: "[kde3.5] you can only select local files"
date: 2005-11-18
forum: Desktop Environments
---

### Post by stoeptegel on 2005-11-18
Yesterday i wanted to get my wallpaper refreshed, but kde thought otherwise, have a look at this:
It says: You can only select local files. What the... i can't get any more local than home can i?
[[IMG]http://img496.imageshack.us/img496/3217/wallpaperbug6dn.th.jpg[/IMG]](http://img496.imageshack.us/my.php?image=wallpaperbug6dn.jpg)

If anyone has a thought about this please let me know.

---

### Post by bin on 2005-11-18
The file seems to be in /home/..... rather than /home/user-name/......

Normally you would not have access to that.

in light

bin

---

### Post by stoeptegel on 2005-11-18
The files are in /home/user/.
Since i upgraded to kde3.5 all files in in my /home/user/ directory that are touched via system:/ are in system:/home/. I thought that was a new kde3.5 feature.(?)

---

### Post by bin on 2005-11-18
That IS interesting - I can see that if it were a feature of 3.5 it would effectively be trying to hide from you the fact that you are in a dir under home - a bit like a root jail sort of thing. That could make sense if it stopped users drilling up past /home/user, but I'd have thought it would be better publicised.

Out of curiousity how does it show a new file creted in you user dir??? Just being nosey really - I don't really want to hose my system again until 3.5 is a little further up the release road....

in light

bin

---

### Post by stoeptegel on 2005-11-18
[QUOTE=bin]
Out of curiousity how does it show a new file creted in you user dir??? 
[/QUOTE]

Hmm konqueror just show me the files when i klik to system:/home, and all files are chowned by me so it's something freaky i guess. I have planned a fresh install this weekend so it's not so bad.

---

### Post by GoldBuggie on 2005-11-18
Try to use the normal /home/$USER directory.

The documentation about system:/ is practically none and I've found it to be highly non working. Haven't gotten a real answer from anyone if this is going to be fixed or not, nor if it is some configuration that one is missing. The same problem was present in the beta releases.

So until it works use the standard pathname

---

### Post by stoeptegel on 2005-11-19
Thanks :)
The funny thing is, even the real pathname didn't work a few days back, it gave me another error... but today it works. I hope it stays working.

---

### Post by oobuntoo on 2005-11-19
[QUOTE=stoeptegel]Thanks :)
The funny thing is, even the real pathname didn't work a few days back, it gave me another error... but today it works. I hope it stays working.[/QUOTE]


I had this problem after fresh install of Breezy. Upgrading to kdebase 4:3.4.3-0ubuntu4 and kdebase-kio-plugins 4:3.4.3-0ubuntu4 solved the problem.

---

