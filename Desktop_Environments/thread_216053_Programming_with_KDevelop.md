---
title: "Programming with KDevelop"
date: 2006-07-14
forum: Desktop Environments
---

### Post by SPlutard on 2006-07-14
I can't get code to compile in KDevelop. The output when I try to build C++ code is:
> Exited with Status: 2

For a java program, it's:
> cd/home/lucas/docs/Docs./Programming/Java/javatest && ant dist -buildfile build.xml -quiet
/bin/sh: ant: command not found
Exited with status: 127

Before I upgraded to DD, I asked about the same problem, and was told:
> 
You need to install some packages to be able to compile. For C, you need:

Code:
sudo apt-get install build-essentialFor Java, you need:

Code:
sudo apt-get install j2sdk1.4

But... that didn't help. Those files wouldn't have been overwritten during the upgrade, right? Any thoughts on what's going on? I would look up the error numbers, but the help section isn't working for some reason - that's for another thread....

---

### Post by SPlutard on 2006-07-14
NOTE: I didn't notice that there was a Programming forum - would it be possible for a moderator to move this there? I'm terribly sorry!

---

### Post by asimon on 2006-07-15
The missing "ant" problem should be solvable by installing the package 'ant'.

The output of your failing C++ compilation is not very informative. Maybe this will bring some more information about what's going wrong. From the [KDevelop FAQ](http://www.kdevelop.org/mediawiki/index.php/FAQ):
```
Why don't I see the compilation error messages?

If during compilations you notice some valuable information is
missing in the Messages Output View window, it may be that the
level of message detail is set too low. Right-click in the window
and select another detail level from the context menu.
```

---

### Post by SPlutard on 2006-07-15
> **asimon said:**
> The missing "ant" problem should be solvable by installing the package 'ant'.

Like this?
```
sudo apt-get ant
```

---

### Post by utnubu001 on 2006-07-15
have u got gcc binutils cpp and libc?

---

### Post by SPlutard on 2006-07-15
I don't know - how can I find out? 

Sorry, but I'm pretty new to Linux so I'm a bit low on experience.

---

### Post by asimon on 2006-07-15
> **SPlutard said:**
> Like this?
```
sudo apt-get ant
```
No, it's
```
sudo apt-get install ant
```
;-)

---

