---
title: "Sudo setuid error"
date: 2009-02-04
forum: General Help
---

### Post by fearful on 2009-02-04
I did something really stupid when I moved my home to a separate partition.

sudo chown -R benjamin:benjamin /

meaning I changed the owner for everything in my / folder not just /home

Now everytime I try and use the sudo command I get the following error:
sudo: must be setuid root

How can I rollback this action?

---

### Post by khelben1979 on 2009-02-04
Are you able to create a root account on that system? 

As root there would be no trouble of doing anything you want without using the sudo command. I know that there exist no root account in Ubuntu since it compromises security, but I have heard that you have the possibility in creating one.

---

### Post by geirha on 2009-02-04
sudo won't work anymore for security reasons. You'll have to fix this either from recovery mode, or from a live CD.

From recovery mode, running ```
sudo chown -R root:root /
sudo chwon -R benjamin:benjamin /home/benjamin
```

might enable you to get a somewhat usable system, but many files should be owned by other system users and/or groups, and many programs will either not work, or work differently than before if their files have gotten a different ownership. You have to identify each such file and set the ownership accordingly. It will be a time consuming process at any rate, but it is possible.

The quickest solution, as I see it, is to back up all data and reinstall, but if you do want to attempt to repair the damage, we may be able to help you further.

---

### Post by binbash on 2009-02-04
i agree with geirha and I suggest reinstalling the OS

---

