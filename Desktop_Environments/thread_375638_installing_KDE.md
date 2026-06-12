---
title: "installing KDE"
date: 2007-03-04
forum: Desktop Environments
---

### Post by woopud on 2007-03-04
I'm trying to install KDE using the following method but get this:

```
woopud@woopud-desktop:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: digikam but it is not going to be installed
E: Broken packages
woopud@woopud-desktop:~$ 


```

---

### Post by aysiu on 2007-03-04
Dependency errors usually stem from conflicting repositories.

**Step 1**: Get a fresh repositories list by following [these instructions](http://www.psychocats.net/ubuntu/sources)

**Step 2**: Install KDE with these commands: ```
sudo aptitude update
sudo aptitude dist-upgrade
``` More details, including screenshots, [here](http://www.psychocats.net/ubuntu/kde).

---

### Post by kenl100 on 2007-03-04
When I try those suggested commands, nothing happens.   I just get prompted for the aptitude password, enter it, and nothing happens.  No errors, nothing.  I've tried each command and several of the variations suggested.  Any ideas?

---

### Post by aysiu on 2007-03-04
Sorry. I gave you the wrong instructions. It's not ```
sudo aptitude update
sudo aptitude dist-upgrade
``` It's ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

