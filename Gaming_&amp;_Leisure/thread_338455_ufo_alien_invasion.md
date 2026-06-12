---
title: "ufo alien invasion"
date: 2007-01-14
forum: Gaming &amp; Leisure
---

### Post by Choad on 2007-01-14
i have some repos with this game in it added, but there is a missing dependency

ufoai: Depends: libasound2 (> 1.0.12) but 1.0.11-7ubuntu3 is to be installed
E: Broken packages


where can i get that package from? cheers

---

### Post by _simon_ on 2007-01-14
Try these:

[http://packages.debian.org/unstable/libs/libasound2](http://packages.debian.org/unstable/libs/libasound2)
[http://packages.debian.org/unstable/libdevel/libasound2-dev](http://packages.debian.org/unstable/libdevel/libasound2-dev)

---

### Post by cilynx on 2007-01-14
The game you're trying to install needs a newer version of the asound libraries than are in the system repository you're using.  What version of Ubuntu are you using?

To answer the above:  while this solution will work, it is adding more "unofficial" packages to the mix, opening the user up for more problems down the line.  In my experience, it is better for folks to stay within the Ubuntu framework as much as possible until they're comfortable enough to solve dependencies on their own.  No harm intended.  I use your type of solution all the time on my own systems.

---

### Post by Choad on 2007-01-14
well i took it from feisty before i read your response

it depended on libc6

libc6-feisty installed without complaining of dependency problems, only to give up and scream half way through.

paniced for a bit, but i found the "sudo dpkg -i --force-downgrade" command and was saved by installing the edgy one again

yep, im running edgy. edgy has libasound2 1.0.11, and it requires libasound2 1.0.12

if i add those repos, am i not just going to be in the same position as before, depending upon a later version of libc6, which in turn depends upon a later version of something else....

---

### Post by Perfect Storm on 2007-01-14
Yes, you will. As I see it you have 3 options here:

1. Hack the libasound.deb package from feisty

2. compile the libasound

3. Install Feisty (still in development stage)

---

### Post by Choad on 2007-01-14
option 2 wouldnt update apt tho, so apt would still think i am running .11, so ufoai wouldnt install

unless i misunderstand...

---

### Post by Perfect Storm on 2007-01-14
If U.F.O. isn't a .deb file there's no problem running option 2

---

### Post by dolny on 2007-01-30
I'm running Edgy and had the same problem. Used the packages _simon_  suggested and everything went great. It works, great game for multiplayer.

---

