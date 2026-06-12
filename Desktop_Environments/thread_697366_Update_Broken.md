---
title: "Update Broken?"
date: 2008-02-15
forum: Desktop Environments
---

### Post by Nevermind042 on 2008-02-15
For some reason, when I install "critical security updates" via the prompt on the Ubuntu top bar, the program opens, shows me 6 updates, then becomes unresponsive and does absolutely nothing until I kill it.

What are my options? Should I reinstall it? (how?)
Should I update manually? (how?)

I'm learning slowly here, guys! :(

---

### Post by erginemr on 2008-02-15
Hello,

What is the current state of your Ubuntu system? When you restart (or reset) your computer, does it freeze or continue to work normally?

---

### Post by RJ Hythloday on 2008-02-15
would this help? fixed adept for me in kubuntu
[quote author=dibl link=topic=3091380.msg115812#msg115812 date=1202998523]
There's a fancy "package manager" in the guts of your Linux system that Adept (and Synaptic) are designed to hide from you, while providing easy access to the application packages.

When there's a problem of the type you describe, you need to close Adept, open your Konsole, and enter the following:

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get install
```

```
sudo apt-get autoclean
```

This will normally straighten out the problem with the package manager, load and install any missing updates, and then clean out the cache.   :)
[/quote]

---

### Post by Nevermind042 on 2008-02-15
> **erginemr said:**
> Hello,

What is the current state of your Ubuntu system? When you restart (or reset) your computer, does it freeze or continue to work normally?

It works beautifully, except for this.

---

### Post by Nevermind042 on 2008-02-15
> **RJ Hythloday said:**
> would this help? fixed adept for me in kubuntu
[quote author=dibl link=topic=3091380.msg115812#msg115812 date=1202998523]
There's a fancy "package manager" in the guts of your Linux system that Adept (and Synaptic) are designed to hide from you, while providing easy access to the application packages.

When there's a problem of the type you describe, you need to close Adept, open your Konsole, and enter the following:

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get install
```

```
sudo apt-get autoclean
```

This will normally straighten out the problem with the package manager, load and install any missing updates, and then clean out the cache.   :)
[/QUOTE]

[[IMG]http://img223.imageshack.us/img223/7300/screenshotgu1.th.png[/IMG]](http://img223.imageshack.us/img223/7300/screenshotgu1.png)

After doing this, these 6 updates still only succeed at causing the update manager to become non-responsive.

---

### Post by Nevermind042 on 2008-02-15
I've found a workaround. Right clicking on the update icon and selecting "Install All Updates" works, but if I open up the graphical UI and use that button, the program stops responding.

---

### Post by erginemr on 2008-02-15
The command line counterpart of the update manager is:
```
sudo apt-get update
sudo apt-get upgrade
```
Maybe if you issue these commands from the terminal and install those six packages this way, you will have this bizarre bottle-neck cleared away.

---

