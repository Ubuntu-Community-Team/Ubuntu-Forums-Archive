---
title: "Beryl invalid signature"
date: 2007-03-16
forum: Desktop Effects &amp; Customization
---

### Post by fmaste on 2007-03-16
HELP!!
Since today when I update I get this:

W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures were invalid: BADSIG 3FF0DB166A7476EA Nicholas Thomas (Repository signing key) <root@lupine.me.uk>

I have previously installed beryl with no problems and also made updates day ago with no problems.
I tried to set again the key with this:

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

The beryl proyect page also tells me to execute this command.
I tried deleting the repos from the source list updating and adding them later and update again, the same with the keys but nothing!!

This are the repos
#Beryl
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

I search the forum and everyone seems to be updating to beryl 0.2.0 except me!
At least 0.2.0 is in the [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) repository
Help!!

---

### Post by PriceChild on 2007-03-16
Please remove your key from system>prefs>software sources.

Then try to add the key again.

Pricey

---

### Post by fmaste on 2007-03-16
> **PriceChild said:**
> Please remove your key from system>prefs>software sources.

Then try to add the key again.

Pricey

I already tried that!

May be the problem is related to
[http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
they both have the same key, I don't know!!
HELP!

---

### Post by chewearn on 2007-03-19
Have this problem been resolved?

Two days ago, I removed old beryl install and nvidia driver.  Then install the latest beta from nvidia using Envy.

Since then, have been trying to install beryl 0.2.0.  Keep having the same gpg error.

```
W: GPG error: http://ubuntu.beryl-project.org edgy Release: The following signatures were invalid: BADSIG 3FF0DB166A7476EA Nicholas Thomas (Repository signing key) <root@lupine.me.uk>

```

Thanks.

---

### Post by fmaste on 2007-03-20
In my case it was solved doing nothing!
I just got tired of trying and the next day it was working I don't know how.
Yesterday the same thing happened with the wine repository and now, (notice that I did no change) it is all working normally when I run the update manager. Same thing with the key that says "Ubuntu archive automatic signing key" 

So just be sure that you follow the installation HOW TO correctly and try again later, be sure that the HOW TO is up to date and the repositories already exist (enter with a web browser) and if you find something like the key archive (*.pgp) delete the old key and replace with the one that is supposed to be new.

---

### Post by chewearn on 2007-03-20
Thanks!  Today, it finally installed without error.  I didn't do anything differently, not sure what was wrong.

---

