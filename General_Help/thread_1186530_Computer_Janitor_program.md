---
title: "Computer Janitor program"
date: 2009-06-13
forum: General Help
---

### Post by miggerish on 2009-06-13
I opened this program and it shows me a long list of files that it thinks I should clean up/remove.  I wanted to know if it is safe to trust this program and delete the files listed?  I am running Jaunty 9.04.

---

### Post by suresnjain on 2009-06-13
Just don't do so.Janitor can crate problems for you.Better to use Ubuntu Tweaks.It is  safer.I tried Janitor,landed in a soup.So, be safe.

---

### Post by doas777 on 2009-06-13
computer janitor is safe in that it does exactly what you tell it to. that said however, it can be misused to make undesirable changes. if you tell it to do somthing stupid. for instance, for most of my boxes, the only thing it shows, is a third party app that I use and trust. no point in removing it, as i would have to reinstall it again.

---

### Post by cariboo on 2009-06-13
If you are going to use Computer Janitor read what it says very carefully, there have been a few incidents where the user didn't read waht was on screen and remvoed software that was needed to start up the desktop. Make sure anything you want to keep has the check mark removed.

Personally I prefer opening an Applications-->Accessories-->Terminal and typing:

```
sudo apt-get autoremove
```

The above command removes unneeded dependencies and archived packages in /var/cache/apt/archives, and just to be sure everything is removed, in the same terminal type:

```
sudo apt-get clean
```

---

### Post by rajeev1204 on 2009-06-13
You need to use it with caution.It lists so many programs at first,you may get impatient and remove a lot of applications.

---

