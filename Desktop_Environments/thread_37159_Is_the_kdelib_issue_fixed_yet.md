---
title: "Is the kdelib issue fixed yet?"
date: 2005-05-26
forum: Desktop Environments
---

### Post by buldir on 2005-05-26
[http://www.ubuntuforums.org/showthread.php?t=28837&highlight=kde+updates](http://www.ubuntuforums.org/showthread.php?t=28837&highlight=kde+updates)

---

### Post by jeremy on 2005-05-26
I don't know, but there is a new version of knetworkconf since the problem occured.

---

### Post by fdoving on 2005-05-26
[QUOTE=jeremy]I don't know, but there is a new version of knetworkconf since the problem occured.[/QUOTE]
 Hi.
Add 'deb [http://kubuntu.org.uk/](http://kubuntu.org.uk/) hoary-updates main universe' to your apt sources.

There is new kdelibs, kaffeine, and knetworkconf.

- Frode

---

### Post by philipacamaniac on 2005-05-26
[QUOTE=fdoving]Hi.
Add 'deb [http://kubuntu.org.uk/](http://kubuntu.org.uk/) hoary-updates main universe' to your apt sources.

There is new kdelibs, kaffeine, and knetworkconf.

- Frode[/QUOTE]

Are you sure these aren't in the Ubuntu.com hoary-updates archive? There are newer versions of knetworkconf and kdelibs for sure, but I don't know about Kaffeine (maybe because I already had a fixed version). I didn't know anything about adding a Kubuntu.org repo.

For all you (less-than-happy) Kubuntu users, devels are working actively on all the known problems, especially the ones we've mentioned here. See [http://www.ubuntulinux.org/wiki/KubuntuHoaryReleaseKnownProblems](http://www.ubuntulinux.org/wiki/KubuntuHoaryReleaseKnownProblems)

---

### Post by buldir on 2005-05-26
OK.  The new knetworkconf update may fix the problem...not sure.  I did see the script someone wrote to debug kdelibs.  If these updates aren't too critical, I'll just wait it out.  I learned my lesson a while back and always come to the forums first before updating anything.  Thanks to all for the latest scoop.

---

### Post by ltmon on 2005-05-26
I hadn't as yet updated my kdelibs due to the problems reported.  As I had some time today I grit my teeth and did:

1. Update knetworkconf
2. Update kdelibs

The updates took straight from kynaptic (using the default AU mirrors).

Upon relogin KDE gave me a "first start wizard" (which I quit immediately) and then I found many of my KDE settings had been nuked.  I had to re-add all my applets to kicker, reset the background, window decoration and splash screen.  In all about a 5 minute job given I know my way around the kde settings well enough.

So in answer to the original question... yes, but it's still a bit of a mess.

---

### Post by Frihet on 2005-05-26
Don't think so. I did another installlast night and messed it up with the post install update. Same problem.  Since it was a ne install, there was not too much effort required to fix it.

---

### Post by kleeman on 2005-05-26
deb [http://kubuntu.org.uk/](http://kubuntu.org.uk/) hoary-updates main universe
worked once universe was deleted. I had to run upgrade twice for some reason and after booting into kde the applets crahed in the panel and the background had changed. Apart from that things look fine...

---

### Post by Frihet on 2005-05-26
I just did another update/upgrade.  Kdelib was replaced.  It worked fine. Nothing broke.

---

### Post by ceti on 2005-06-02
Yeah, I reinstalled Kubuntu from CD and performed a general update. 
So far, it works fine.

---

