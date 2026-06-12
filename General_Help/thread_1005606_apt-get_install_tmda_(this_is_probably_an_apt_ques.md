---
title: "apt-get install tmda (this is probably an apt question)"
date: 2008-12-08
forum: General Help
---

### Post by ezekieldas on 2008-12-08
Greetings --I'm a fedora/rh/centos -> ubuntu convert (for the time being). I'm experiencing some frustrations with apt. Specifically, I'd like to install TMDA using 'apt-get install tmda' but comes back with "couldn't find package" Then 'apt-cache search tmda' results in nothing. However, when I search packages.ubuntu.com I see there was a TMDA package for dapper, feisty, gutsy --but I'm running "hardy" 8.04. 

I realize I could install TMDA from source but I prefer package management. I also see something about "apt-get -t" which involves setting up apt pins but it isn't clear and I don't want to get more involved than I need to. 

Thank you,
-zeek

---

### Post by lovelyvik293 on 2008-12-08
TDMA is not the part of hardy anymore.
Check it:-
[https://launchpad.net/ubuntu/hardy/i386/tmda/1.1.12-0ubuntu1](https://launchpad.net/ubuntu/hardy/i386/tmda/1.1.12-0ubuntu1)

---

### Post by ezekieldas on 2008-12-08
> **lovelyvik293 said:**
> TDMA is not the part of hardy anymore.
Check it:-
[https://launchpad.net/ubuntu/hardy/i386/tmda/1.1.12-0ubuntu1](https://launchpad.net/ubuntu/hardy/i386/tmda/1.1.12-0ubuntu1)

Right, but how do I install (via the given package management, apt) something that isn't part of the current release. THAT is the question.

---

### Post by russo.mic on 2008-12-08
well, you should do a search for a DEB package.  Plenty of DEBs can be found just using google.  If not that, maybe you could find a repo to add to your /etc/apt/sources.list.

Then your only a sudo apt-get update away from management!

---

### Post by ezekieldas on 2008-12-08
> **russo.mic said:**
> ... If not that, maybe you could find a repo to add to your /etc/apt/sources.list.

I know about the sources.list entries but what do you mean by a repo? Could you provide an example of this? 

Cheers,
-zeek

---

