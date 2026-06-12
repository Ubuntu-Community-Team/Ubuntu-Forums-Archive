---
title: "search option in software center not available"
date: 2015-02-10
forum: Desktop Environments
---

### Post by Qwopy on 2015-02-10
Using the new LTS i just downloaded. 
Booted to try ubuntu to recover some data off an infected machine.
wanted to install ClamAV
checked in "Ubuntu Sfotware center" cant find a search bar.
Has it been removed or what? thousands of packages but no way of searching them.
so i did an apt-get install clamav
i can update my clam defs with freshclam but I still cant start it with

 $ clamav ->command not found.
$ apt-get install clamtk -> Unable to locate package clamtk

totally stuck, but my main issue is "_Why is there no search in the software center?"_
makes no sense to me. i know the name of somthing but cant get it.

---

### Post by ajgreeny on 2015-02-10
Have you updated the sources with **sudo apt-get update**?

---

### Post by monkeybrain20122 on 2015-02-10
Works here. See screenshot.

Can't really answer your question since I don't use the Software Centre. But I suggest using synaptic instead, it is much faster and has more features. The USC tries to replicate the 'app-store' feel but frankly I find it bloated and lacking in functions. The only thing that is available in the USC but not synaptic is paid software, but I don't have those.

The first thing I do after a new Ubuntu installation

```
sudo apt-get install synaptic gdebi
```

gdebi is for installing a .deb by right clicking. By default clicking a .deb would bring up the Software Centre but with gdebi I would finish installing before the USC is up and running. With these two I have no use for the Software Centre 

P.S. Why do you think you need to run an Av in Linux which detects Windows virus??

---

### Post by v3.xx on 2015-02-10
> **ajgreeny said:**
> Have you updated the sources with **sudo apt-get update**?

Also a good idea to do a upgrade.
```
sudo apt-get dist-upgrade
```

---

### Post by ajgreeny on 2015-02-10
I'm with monkeybrain20122 and never use USC; I find it a waste of time and far too dumbed down so I also always use synaptic for these activities.  I've been using Ubuntu, or a derivative since 2005, when synaptic was the default package manager and USC did not even exist,so I admit I know how to use it, and it can be a bit intimidating for new users, but persevere with it and you will find it invaluable.

---

### Post by deadflowr on 2015-02-11
Even without a search bar you can still look for an app by strolling through categories.
Long-winded approach but always an option.

that said, seems something more is afoot than a mere botched software center.
(if apt-get install throws out an error for a  well-established package like clamtk being not found.
Perhaps a repo is not enabled.
I would agree with the above to run a quick apt-get update, and see if any errors crop up.
I would also make sure that the universe repo is enabled.
(clamav is in the main repo, but clamtk is in universe.)

Also, I do not think there is any such command as clamav, by itself.
The most I can remember is freshclam and clamscan.
Maybe if you install clamav-daemon running clamav does something...

---

