---
title: "Problem running program from menu"
date: 2006-01-29
forum: Desktop Environments
---

### Post by tgcUbuntu on 2006-01-29
I recently compiled VLC from sources and am able to run it from the command line: vlc
It runs ok. I then added a menu item for VLC using the Alacarte Menu editor. However when I click on VLC in the menu nothing happens. I think I've run down the problem. The shared libraries that VLC is using are all in /usr/local/lib. When I create symbolic links to all the *.so libraries that VLC uses in the /usr/lib directory I can then click on the VLC menu item and have VLC run.

I know that the LD_LIBRARY_PATH variable controls this from a Terminal but it doesn't have any effect from the menu selections.

So the question is: How do I get the system to look in the /usr/local/lib directory without having to go and create the symbolic links in /usr/lib?

---

### Post by RAOF on 2006-01-29
You should be able to edit (as root) /etc/ld.so.conf, and add /usr/local/lib to it.  Then run "sudo ldconfig" and it should update the cache that ld uses to identify where shared libraries are.

---

### Post by tgcUbuntu on 2006-01-30
Thanks a lot, that did the trick!

---

