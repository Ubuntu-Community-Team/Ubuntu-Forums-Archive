---
title: "error in synaptic package manager"
date: 2009-06-16
forum: General Help
---

### Post by fcuk112 on 2009-06-16
i am getting the following error in synaptic:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

any idea what i can do about this?

thanks.

---

### Post by michy99 on 2009-06-16
Try this:```
sudo rm /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
sudo apt-get update
```

---

### Post by fcuk112 on 2009-06-16
wow that seemed to do the trick, thanks very much!!!

any idea what was wrong?

---

### Post by 3rdalbum on 2009-06-16
The file was corrupted - it's rare, but it can happen. The first command deleted the file, the second command downloaded the table of contents for the repositories (which contains a fresh copy of the file you deleted).

---

### Post by billgoldberg on 2009-06-16
> **fcuk112 said:**
> wow that seemed to do the trick, thanks very much!!!

any idea what was wrong?

You removed the faulty file, the second commmand put a new one in.

---

### Post by PhilJames on 2009-06-19
Hi
I had the identical error so I followed the same solution ( substituting my distribution sources), unfortunately the problem wasn't resolved and came back with this error message
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ubuntu.mirror.rafal.ca_ubuntu_dists_jaunty-security_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Have you any idea what else I could try?

---

### Post by synapsys on 2009-06-19
```
sudo rm /var/lib/apt/lists/ubuntu.mirror.rafal.ca_ubuntu_dists_jaunty-security_universe_binary-i386_Packages
sudo apt-get update
```

---

### Post by PhilJames on 2009-06-19
OK I tried that one, and as you can see, not a positive result either
> rm: cannot remove `/var/lib/apt/lists/ubuntu.mirror.rafal.ca_ubuntu_dists_jaunty-security_universe_binary-i386_Packages': No such file or directory

.
I'll leave it a day or so, and if nobody else has any ideas I'll reinstall Ubuntu. The last resort of the clueless.

---

### Post by synapsys on 2009-06-19
Maybe try and remove everything like shown in this thread (at the end).

[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

Could be dangerous, but you're thinking about re-installing anyways.

---

### Post by PhilJames on 2009-06-19
That's the one
> sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
It worked like magic.
Thanks for that :D

---

