---
title: "Awn not working."
date: 2009-04-26
forum: Desktop Environments
---

### Post by djbushido on 2009-04-26
Okay, so I had Awn (avant-window-navigator) working in 8.10. Upgraded to 9.04 and it doesn't work. Here's the problem: ```
brad@BradXFCE:~$ avant-window-navigator
Traceback (most recent call last):
  File "/usr/bin/awn-applets-migration", line 21, in <module>
    import awn
ImportError: No module named awn

```While it looks stupid, I checked, and I'm using the same version of python. Any ideas? Also, display compositing is enabled.

---

### Post by djbushido on 2009-04-28
Still not working, any ideas? Help, please?

---

### Post by [SomeGuy] on 2009-04-28
I had the same problem with my friend's computer I am setting up. I think it's a problem with the fact that it's brand new. Wait for a while, the devs will probably release a new AWN version soon. I say downgrade back to 8.10...I had to. It was a pain, but oh well. Just back everything up on a separate partition or external hard drive, reinstall, figure out how to get the desktop back to the way you like it.

---

### Post by djbushido on 2009-04-28
I think it might have something to do with the Jaunty upgrade to 2.6.2. I'm compiling my own python (now that jaunty has bound to the new one, I think it's safe) and will post back the results.

---

### Post by djbushido on 2009-04-28
Nope, not python. Any other ideas? Also tried the launchpad ppa, that didn't work either.

---

### Post by Hichhiker on 2009-04-28
For what its worth, I had same issue and ended up uninstalling  all the packages (I had 0.3.1 version from Launchpad) first. Then upgrading to 0.3.2 packages in the official repo. Everything worked great after that.

-HH

---

### Post by djbushido on 2009-04-28
Did you get this same error though?
I tried that too, but it didn't work...

---

### Post by Hichhiker on 2009-04-28
> **djbushido said:**
> Did you get this same error though?
I tried that too, but it didn't work...

Don't remember exact error. Maybe not exactly the same. The issue I found in my case was that there were 2 competing sets of packages, once from Intrepid+Launchpad (end in -bzr). I had to un-install those before anything worked proper. Check in synaptic as to what packages are installed and which are not. (or via command line if you are so inclined)

-HH

---

### Post by djbushido on 2009-04-29
No, I didn't have conflicting packages.

NOTE: DO NOT COMPILE AND INSTALL YOUR OWN PYTHON VERSION!!!! THIS WILL MORE THAN LIKELY BREAK YOUR SYSTEM OR CAUSE ERRORS!!!! That being said, compiling my own python didn't work. Anybody know how to change default python version?

EDIT: Or if you feel you must, use "make altinstall"

---

### Post by djbushido on 2009-04-29
Bump again. Still having problems, need the help. Or another dock with the same effects. Gnome DO is already out.

---

### Post by djbushido on 2009-04-29
For people who also have this problem, can you guys do this: "python" then these commands: "import sys" and "sys.path".

---

### Post by djbushido on 2009-04-29
Sorry for all the posts. But this is all important.
Turns out that the new avant needs 2.6 for all the library stuff, however 8.10 used 2.5 and all of the links didn't get updated. So, to fix, try this:
```
sudo rm /usr/bin/python
sudo ln /usr/bin/python2.6 /usr/bin/python
```
Although I make no guarantees about this.

EDIT: Also make sure that /usr/share/python/debian_defaults points to 2.6 as the default version.

---

### Post by chrisj26 on 2009-05-20
did this get awn working again? [http://ubuntuforums.org/showthread.php?t=1164637](http://ubuntuforums.org/showthread.php?t=1164637) here is the issue i had.

---

### Post by djbushido on 2009-05-20
If you could add the awn repositories as stated above (pretty sure - if not, let me know), then install the *-trunk packages, that would be great.
Also, run this command in a terminal - "which python". This will tell me the execution directory of python, and also "python --version" which will tell me the version of python you are using (should be 2.6). WARNING!!! Do not compile your own python - this will cause many problems. Don't do it.

---

