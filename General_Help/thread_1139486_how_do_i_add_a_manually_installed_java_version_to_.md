---
title: "how do i add a manually installed java version to my path?"
date: 2009-04-27
forum: General Help
---

### Post by Polygon on 2009-04-27
I am using jaunty, and the 64 bit version of java is not in the repos, so i had to install it manually

the browser plugin works (i had to do a symlink) but other programs (eclipse) say they can't find any java virtual machine.

sudo update-alternatives says there are no javas to configure....

so how do i add my manually installed java install to my path so everything can see it?

i installed it to  /usr/lib/jvm/jre1.6.0_14/

---

### Post by c0kr3x on 2009-04-27
hi polygon you may try this:

[http://rioastamal.net/2008/10/tutorial-how-to-install-java-on-ubuntu-linux/]("http://rioastamal.net/2008/10/tutorial-how-to-install-java-on-ubuntu-linux/")

---

### Post by jespdj on 2009-04-27
> **Polygon said:**
> I am using jaunty, and the 64 bit version of java is not in the repos, so i had to install it manually
Huh? The 64-bit version of Sun Java 6 (update 13) including the new 64-bit Sun Java browser plug-in **is** in the repository. What makes you think it isn't?

Install it with:
```
sudo apt-get install sun-java6-plugin
```

---

