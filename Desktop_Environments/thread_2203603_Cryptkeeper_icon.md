---
title: "Cryptkeeper icon"
date: 2014-02-04
forum: Desktop Environments
---

### Post by p.callan on 2014-02-04
Saw a thread on Cryptkeeper icon but as the "fix" did absolutely nothing to fix the problem I am duplicating that thread.
[http://ubuntuforums.org/showthread.php?t=1791606](http://ubuntuforums.org/showthread.php?t=1791606)

Whitelisting All did nothing.

I've been looking around for solutions but I can't understand half of what is said half of the time, like here:
 [https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/571473](https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/571473)
I don't care how it works, I just need it TO work.

Alternatives to Cryptkeeper that are at least as easy to use are welcome. Heard of Truecrypt but this was not on SWC.

---

### Post by deadflowr on 2014-02-04
Cryptkeeper has turned hit or miss in terms of loading.
(Because of the indicator changes Ubuntu has brought to the panel.)
I have it, and on 12.04 it loads unquestionably, but on newer versions it loads when it wants.

Alternatively, look into [Gnome Encfs Manager]("http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html")

---

### Post by p.callan on 2014-02-07
I have 12.04 LTS and it does not load. I cannot open the software.
Will look into alternatives. Thanks.

---

### Post by deadflowr on 2014-02-07
In 12.04 you need to run this command
 ```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

That will set it to open in the panel.

This command doesn't(or can't) work on newer version, though.

---

### Post by JeQhdMD on 2014-03-25
Thanks deadflowr - - your suggestion to try _Gnome Encfs Manager_ works great on ubuntu 13.10.   

Was having lots of trouble running encfs/cryptkeeper, and also gpg/kgpg.   Both apps were misbehaving badly (for different reasons).  After adding the PPA (personal package archive) suggested in your link, installing & running Gnome Encfs Manager is simple and fast.   Kudos to the developers.

On something as important as encryption, when 2 out of 3 primary encryption tools (front-end gui managers) are broken since ubuntu 12.10, you would think Canonical would add this ppa automatically or provide the app in the standard repos.  I prefer not to encrypt my entire home directory, so this tool solved a lot of problems.

---

