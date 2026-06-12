---
title: "Upgrading to Ubuntu 7.10 failed.. Server issues?!"
date: 2007-11-11
forum: Dell  Ubuntu Support
---

### Post by franny on 2007-11-11
OK. ... First of all, I have been searching the forum for discussions about Ubuntu 7.10 upgrade and also as on a Dell computer and also as on a Dell Inspiron E1705  with zero results for all and I cannot believe that::  
[COLOR="Blue"](#1)[/COLOR] no one at all has posted anything on the new Ubuntu release 
[COLOR="DarkOrchid"](#2) [/COLOR]no one with a Dell laptop has upgraded to gutsy 7.10 yet 
[COLOR="Magenta"](#3) [/COLOR]no one has posted anything here on the Dell forum about upgrading, etc.
Is this an issue due to the forum's search engine's abilities or has no one really upgraded and/or posted on this subject yet?

As a Dell Inspiron E1705  user with self installed Ubuntu 7.04 I have been frustrated by a number of issues plaguing Dell computers specificall, i.e: WIFI trouble, the hibernate option will not 'wake up', and printers that can't print, to name a few. Even after loading the live cd version from the My Little Ubuntu Guide website (specially configured to work with Dells) there have still been problems.

So, even with no results on the Ubuntu forum search for discussion on the subject(s) I decided the news about Gutsy Gibbon from direct2dell.com was encouraging enough to be brave the upgrade  on my own. 
But once again, I am frustrated.

I have tried 2 times to upgrade as per instructed via update manager but both times it has failed. 
**The error reads:**

[COLOR="Red"][B]Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'[/B][/COLOR]

Has anyone else tried this and if so, what was your experience?
Any advice?
waiting patiently.  [-o<... more of less..  f

PS. I seem to be striking out today. Where is every one? Wake up and try Gutsy Gibbon 7.10 with me.  And post something about it.
Thanks ya'll.

---

### Post by natehall on 2007-11-11
This post talks about it: [http://ubuntuforums.org/showthread.php?t=588033](http://ubuntuforums.org/showthread.php?t=588033)
I tried upgrading my 1420 laptop and only got a terminal screen after running the download. (I did a factory restore) The thread above seems to have a solution but I'm happy with the current state of my machine and I'm going to wait a few months to let all the bugs get worked out first.

---

### Post by hiikeeba on 2007-11-12
Actually, I did a search for updating a Dell Inspiron 1420 and found lots of reasons not to upgrade yet.  Does anyone know when Dell will release an image?

---

### Post by seaq on 2007-11-12
franny the problem you've got is not related to dell or a failed upgrade process..

What you should do is to disable via synaptic or upgrade-manager the wine and the medibuntu repo.

Probably you've got automatix installed.

Just disabling those and you'll be fine.

---

### Post by Dellfan on 2007-11-12
All your failures are with additional packages. I would suggest verifying that the servers are still live and that they have 7.10 packages available. You may not need all of the mediabuntu stuff, with 7.10. I have Wine running on 7.10 and it works fine. Not sure where I pulled it from (away from my notebook and can't check).

I would also suggest just upgrading the core, and getting it working before dealing with additional packages that you are getting from "3rd party" repositories. Easiest way to do this is to edit your sources list and comment out all non Canonical repositories.

7.10 certainly works great with a 1505, with Nvidia graphics and Intel wireless. The upgrade to Tribe 3, Beta and now the 7.10 went well. Have suspend & hibernate working, after a small amount of tweaking. Wireless is solid.

---

### Post by wrongo on 2007-11-13
in case you don't know what one of the other posts is talking about, i think this is how to do what they are saying:

SYSTEM
 >ADMINISTRATION
   >SYNAPTIC PACKAGE MANAGER
     >SETTINGS
      >REPOSITORIES
       >THIRD PARTY SOFTWARE (?)

---

### Post by cmccauley on 2007-11-13
Hi,

I've been using gutsy since not long after the repos were opened. I dist-upgraded from Feisty and had the usual run of problems with graphics cards etc. The original machine was an Inspiron 8600 (had been running Hoary before Feisty) but I'm now on a 1720 (I also have an Inspiron 9300 running Gutsy just fine). Throughout all of those releases, I've found support from other Dell users (though not always on Ubuntu)

I mention all of this just to reassure the original thread author  that there are a large number of Dell users who have been using Linux for many years - I switched full time to Linux back in 2004 having dual-booted for some years - and who are happy to share their experiences. Just remember though that not all of them are on Ubuntu (that's good) but that if Gentto, Red Hat, Suse users are running happily on Dell hardware then Ubuntu will too.

On a last happy note, when I received my Inspiron 1720 a few weeks back, the first thing I did was to run the Gutsy Lice CD. I was really surprised that wireless and graphics settings worked out of the box. The only minor frustration was remembering how to install the requisite DVD playback drivers. This is a small "price" to pay for a solid and free OS.

Chris

---

