---
title: "dpkg error?"
date: 2009-04-10
forum: General Help
---

### Post by Stokenut on 2009-04-10
When trying to install a new piece of software or open the Synaptic Package Manager, I get the following error.

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I open up the terminal and get the following.

> root@stephen-desktop:~# dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0120' near line 19 package `linux-restricted-modules-common':
 EOF after field name `'

How do I fix this? It's left me unable to install programs.

Thanks.

---

### Post by Stokenut on 2009-04-10
I've got no idea whether bumps are allowed on this forum but I see no "bump topic" button so... bump?

---

### Post by overdrank on 2009-04-10
Hi and try the command with ```
sudo dpkg --configure -a
```
Also bumping once a 24 hr period is polite. :)

---

### Post by plucky on 2009-04-10
@overdrank

I think Stokenut already did that command > root@stephen-desktop:~# dpkg --configure -a


@Stokenut

I think you can delete the file that is giving you the problem ```
cd /var/lib/dpkg/updates/
ls
sudo rm <name of file>
sudo apt-get update
```

The first command takes you to the directory.
The ls command lists the files in the directory.
The sudo rm command deletes the file.
The last command updates your package manager.

Good Luck

---

