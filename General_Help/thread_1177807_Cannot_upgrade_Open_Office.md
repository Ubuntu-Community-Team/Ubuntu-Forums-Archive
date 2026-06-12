---
title: "Cannot upgrade Open Office"
date: 2009-06-03
forum: General Help
---

### Post by ratcheer on 2009-06-03
I am following the instructions at ubuntumanuals.org to upgrade Open Office from 3.0 to 3.1. I cannot get past the first steps.  I added the Third-party repository in Software Manager and it gave several errors, mostly to the effect that maybe the repository is not valid, anymore. But I continued and tried to import the PGP key. I find the file I created and click OK, but it does not add it. There are no error messages or warnings of any kind, but nothing is added.  What am I doing wrong?  Thanks, Tim

---

### Post by salvachn on 2009-06-03
Same thing happened to me last week, just try
```

sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

```
If that doesn't work, uninstall current version of oOo and then install the newer ones in Synaptic (the newer version must be available after the update).

---

### Post by ratcheer on 2009-06-04
Thanks, salvachn. I will try that.

I also found another topic on wilderssecurity forum that gives a script to upgrade OO. I am going to look at that, first. If it works, I will post that method, too.

Tim

---

### Post by fooman on 2009-06-04
try this:

[http://ubuntuforums.org/showthread.php?t=987181](http://ubuntuforums.org/showthread.php?t=987181)

hope it helps.

---

### Post by ratcheer on 2009-06-04
Ok, to make a long story short, the PGP Key posted in the instructions I had been trying to follow was somehow garbled. It looked the same, but when I got the key from the repository site, it imported on the first try. Then the upgrade to OO 3.1 ran in just a few minutes.

All is well.

Tim

---

