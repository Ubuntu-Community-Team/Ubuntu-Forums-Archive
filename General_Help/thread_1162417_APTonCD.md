---
title: "APTonCD"
date: 2009-05-17
forum: General Help
---

### Post by mark.giblin on 2009-05-17
I would like this bit of kit to work but it is not.

The program runs, scans for installed pckages and takes about 2 minutes on my system and then crashes without offering any list of apps to backup as I want to make a LiveCD from what I have been reading, you use APTonCD to make a live CD of your fave programs and stuff and can run or install like the Ubuntu installer.

The problem is that the APTonCD that came as part of the install is as stated going belly up after the scan completes.

As I have downloaded many apps and librarys, I would like to back things up but I am stuck. 

So if this can be solved through the add/remove or package managers that would be great as this commandline stuff I just don't get right now because I am new to this Linux OS.

Cheers.

---

### Post by geirha on 2009-05-17
Could you run it from a terminal? It should hopefully output what is wrong there when it crashes. 

Applications -> Accessories -> Terminal, type in (all lowercase letters):
```
aptoncd
```

Do the same thing you tried last time it crashed, then copy the output from the terminal (or at least the last part where there hopefully is a descriptive error message) and paste it in a post here. Preferably enclosed in BB-code code tags.

---

### Post by mark.giblin on 2009-05-18
This is the output from the method you described to me> markgiblin@markgiblin-desktop:~$ aptoncd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
FATAL -> Failed to fork.
markgiblin@markgiblin-desktop:~$ 

Which means nowt ta me lad.

---

### Post by 4Orbs on 2009-05-18
I had the same problem, but found a cheezy way to make it work. I discovered that aptoncd crashes when I have too many packages in the apt cache. So I divided the process into two steps, on two cd's rather than one. First I copied half the .deb packages (from /var/cache/apt/archives) over to a storage partition, then deleted that 50% of the debs from the apt cache. Then I ran aptoncd on the remaining 50% of the debs in the cache and made the first cd. Then I deleted those debs after they were burnt to cd. Then I pasted the other 50% of the debs (that were removed previously) back into the (now empty) apt cache and ran aptoncd again, and created the second cd. As I said, cheezy, but now it works for me.

---

### Post by geirha on 2009-05-18
Found a bug report on it.
[https://bugs.launchpad.net/aptoncd/+bug/272509](https://bugs.launchpad.net/aptoncd/+bug/272509)

Apparently, the problem is that it consumes waaay too much memory.

---

### Post by Meow27 on 2009-05-18
backing up 300mb worth took more than 700mb on my machine i thing :/

---

### Post by mark.giblin on 2009-05-19
@geirha - does not do anything when I click the link. :(

I will look and see if any updates are on offer from the vendors site.

---

### Post by mark.giblin on 2009-05-19
Well thats not helpful at all.

> CD-based repository creator for packages downloaded via APT
Tool for the creation of a CD-based repository containing all packages downloaded via apt-get. Helpful for a post-installation on several machines or a simple backup method to re-install the system. After you've created the CD, you will be able to add it as a repository, as if it were an CD with addictional applications. The graphical interface will be enought, starting it via System -> Administration -> APTonCD menu entry. Or if you want, see the available command-line call methods by typing 'aptoncd --help' in the console.
For more information, visit [http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net) 

This is the error I got after downloading "The Latest" from the APTonCD site link, same as features in the above erro when I tried to install it.

The message 

[COLOR="Red"]Error: A later version is already installed[/COLOR]

So I am wondering how this can be. APTonCD website offers the latest and this version that crashes was part of the ISO file I downloaded from ubuntu website.

So someone at ubuntu must have made some changes to the source code...

---

### Post by geirha on 2009-05-19
The version on sourceforge is an old one, from 2007. AptOnCD used to be developed on sourceforge, but when it got added to the official ubuntu repositories, the developer apparently decided to only use launchpad.

The launchpad URL I posted doesn't work for you? I tested it myself, and it sends me right to that bug, so that's quite odd. Try going to launchpad.net and type in the bug number, 272509, into the search box. The first hit will be that bug.

---

### Post by mark.giblin on 2009-05-19
Tried doing that and the link I followed from the top of this forum page just ends in a blank page for me.

---

### Post by amay1283 on 2009-05-20
Hi! I am new to Linux and i would be grateful if u guys could help me out a bit. I took a backup of packages using aptoncd. When i restored it to a new installation it simply put the packages back in the cache(/var/cache/apt/archives). How do i go about installing all the packages without having to start installing them one at a time.

---

### Post by mark.giblin on 2009-05-22
I checked the launchpad site on this bug and this bug seems to have existed for a long time and nothing has been done to resolve this by whoever it is that sitting on their hands at Ubuntu.

I would have thought that this being a very important tool in Ubuntu that this would have been a priority back in hardy where it seems that this bug was introduced.

So when can the ubuntu people who have goofed up be putting things straight?

---

### Post by mark.giblin on 2009-05-22
> **amay1283 said:**
> Hi! I am new to Linux and i would be grateful if u guys could help me out a bit. I took a backup of packages using aptoncd. When i restored it to a new installation it simply put the packages back in the cache(/var/cache/apt/archives). How do i go about installing all the packages without having to start installing them one at a time.

Can you please start your own thread on your particular problem, this is a thread I started because APTonCD is crashing and your asking something completely different.

Thanks.

---

