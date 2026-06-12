---
title: "Menu freeze with Cinnamon on 13.04"
date: 2013-09-13
forum: Desktop Environments
---

### Post by polt on 2013-09-13
Hi!

I had big problems trying to set up Cinnamon on Ubuntu 13.04.  I used this repository:

```
ppa:gwendal-lebihan-dev/cinnamon-stable
```

But had problems because of unmet dependencies:

```

The following packages have unmet dependencies:
 cinnamon : Depends: libgjs0-libmozjs185-1.0
E: Unable to correct problems, you have held broken packages.

```

But I was able to overcome these using aptitude.

Then my computer would freeze on the login screen unless I did CTRL+ALT+F1 and after logging in at the command line, did a dist-upgrade.  After that, Cinnamon worked pretty good except that any time I opened the menu it would completely freeze everything.

Has anyone had similar problems or know how to fix them?

Thanks!

---

### Post by SuperFreak on 2013-09-13
This is how I installed cinnamon.Did you install nemo?

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon nemo
```

---

### Post by SuperFreak on 2013-09-13
I gooogled this solution:
> This is a relatively easy fix, at least an easy one to try! :) It appears you have a broken dependency/package, an easy fix.

Do this:

sudo apt-get clean && sudo apt-get update
It should fix your broken packages error, then you can run the sudo apt-get install cinammon command to install it!

Good Luck!

[http://http://askubuntu.com/questions/291495/cinnamon-not-installing-in-ubuntu-13-04]("http://http://askubuntu.com/questions/291495/cinnamon-not-installing-in-ubuntu-13-04")

---

### Post by polt on 2013-09-14
I totally tried all of the simple google solutions, and that's how I found the one of installing aptitude.  apt-get clean doesn't help.  And yes, I have also installed nemo.  Ultimately, I got Cinnamon installed, the problem is opening the menu crashes the whole computer.  I've probably just tweaked my distro too much and maybe a fresh install and then a new attempt to install Cinnamon would work.  But I'd rather not do that if you know what I mean :)

---

### Post by polt on 2013-09-16
Well, I did a fresh reinstall of Ubuntu 13.04 and that fixed a lot of my problems.  You don't even need to add the Cinnamon repository if Raring is installed correctly.  Good luck everyone else!

---

