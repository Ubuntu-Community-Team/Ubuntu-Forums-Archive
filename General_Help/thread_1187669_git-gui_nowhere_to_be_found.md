---
title: "git-gui nowhere to be found"
date: 2009-06-14
forum: General Help
---

### Post by joshpennington on 2009-06-14
Hello-

I just upgraded to 9.04 from 8.10 tonight.  I am trying to load up git-gui to make sure it works but I am getting a message saying that it is not found.  It was installed and working correctly on my 8.10 install.

I tried removing and re-installing it, but it does the same thing.  Does anyone have any ideas why this could be happening?

Thanks

Josh Pennington

---

### Post by BobBobBoBob on 2009-08-02
Been there, done that.

For me, the solution was update my menu item for Git-GUI to have a command line of /usr/lib/git-core/git-gui, instead of just git-gui.

---

### Post by nilbus on 2009-11-14
The usage of the git-gui command has been replaced with
```
git gui
```

see [https://bugs.launchpad.net/ubuntu/+source/git-core/+bug/360848]("https://bugs.launchpad.net/ubuntu/+source/git-core/+bug/360848")

---

