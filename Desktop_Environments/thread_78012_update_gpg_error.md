---
title: "update gpg error?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by rplantz on 2005-10-17
When I run System -> Administration -> Update Manager I get GPG errors.

I then ran apt-get update and got:
```

W: GPG error: http://us.archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```

How do I correct the problem that gave these errors?

(The suggested solution is also known as "chasing your tail.")

Bob

---

### Post by cytoplasm on 2005-10-17
Just wiped my 5.04 install and re-installed 5.10 and I'm getting the same errors when I runt [FONT="Courier New"]sudo apt-get update[/FONT].

---

### Post by dustigroove on 2005-10-17
[quote=rplantz]When I run System -> Administration -> Update Manager I get GPG errors.[/quote]

As of 10 minutes ago I started getting these same errors. I'd just suggest trying it again a bit later... I'm sure whatever is goofed in the repos will be fixed fairly quickly.

---

### Post by Dr. Nick on 2005-10-17
I get them still, also some packages wont install, I bet the repos are just getting  pounded and hopefully will be fixed soon

---

### Post by dustigroove on 2005-10-17
Per cytoplasm in the thread [here]("http://www.ubuntuforums.org/showthread.php?t=78033")...

[QUOTE=cytoplasm]Remove the "us" references in the URL within the sources.list file and then run update again.  It will then work correctly.[/QUOTE]
Worked well for me, thanks cyto.

---

### Post by wezza on 2005-10-17
Just remove the files in /var/lib/apt/lists/ then wait a few minutes and do apt-get update again.

---

