---
title: "Unable to download or update software"
date: 2009-05-22
forum: General Help
---

### Post by LoreleiR on 2009-05-22
I'm very new to Ubuntu, I've been using windows for as long as I've been able to use computers and I'm completely lost when it comes to fixing Ubuntu problems.

When I try to install updates from the update manager I get an error message that says: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Also when I try to download things such as Adobe flash I get an error message that reads: 
"Only one software management tool is allowed to run..."

I've tried everything I could think of, but like I said, I'm very unfamiliar with Ubuntu and the way it works.

Any help would be appreciated, thanks!

---

### Post by taurus on 2009-05-22
If you have an update manager window open, close it first.  Then, open a terminal and run

```
sudo dpkg --configure -a
```
And if you want to install all those codecs and plugins, install the ubuntu-restricted-extras package.  That would install flash, java, and among other things.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by 73ckn797 on 2009-05-22
> **LoreleiR said:**
> Also when I try to download things such as Adobe flash I get an error message that reads: 
"Only one software management tool is allowed to run..."

You can only have one Synaptic running at one time. Close everything else then go to Synaptic and install the programs.

---

