---
title: "Synaptic (package manager problem)"
date: 2008-07-27
forum: Desktop Environments
---

### Post by Len Tyree on 2008-07-27
Synaptic package manager stopped working.  Gives error, e.g. dpkg was interupted . You must manually run 'dpkg --configure -a' to correct the prolem.  So on terminal I managed to get an AFS screen up, but do not know what it wants.  Nothing in the help menu helps.
The Synaptic was working fine the day before yesterday.
Am running 'hardy heron 8.04' on desktop, 256 megs ram, 80 gigs hard drive, 2.66 GHTZ speed.
Need to get my Synaptic back up and runing ---- PLEASE HELP.
Thanks, Len Tyree.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by coffeecat on 2008-07-27
Open a terminal and:

```
sudo dpkg --configure -a
```

You need to preface the command with sudo to get adminstrator rights. It will ask for your password. Don't worry - the password is going in! The appearance of nothing happening when you type in your password is a security feature, not a bug.

You might find this helpful reading: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Len Tyree on 2008-07-28
PROBLEM SOLVED. (But Don't know how??)
Thanks John for the assistance.  Got my Synaptic back.  I had already done the 'sudo dkpg --configure -a' bit and it sent me to the AFS screen where I did not know what it wanted.  (After becoming a superuser).  Anyway, I clicked on Software sources, clicked on Universe and Multiverse applications; lo and behold, the synaptic package manager popped up??  Any I will still check out the url you passed to me.
Thanks again, len Tyree.

---

### Post by Len Tyree on 2008-08-19
Thanks to coffeecat.

---

