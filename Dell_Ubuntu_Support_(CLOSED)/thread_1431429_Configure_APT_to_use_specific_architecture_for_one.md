---
title: "Configure APT to use specific architecture for one repository?"
date: 2010-03-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mr_Cynical on 2010-03-16
That might sound like an unusual request for a Dell Mini, but hear me out! I've installed Chrome on my Mini (partly because it loads pages faster, but mainly because its interface uses less screen space, than Firefox), but the problem is that with LPIA defined as the architecture for APT, it can't retrieve updated versions from the Google repository (which has i386, but not lpia). The i386 version of Chrome works fine (it's what's in the original download Deb), so what I need to do is tell APT to look for packages in binary-i386 rather than binary-lpia, for that repository only. Is this possible?

---

### Post by mikewhatever on 2010-03-18
Last time I checked, the installation of Chrome also added a repository for it. You can also customize Firefox to increase the amount of space for content. I you want to try, take a look at 'Compact Menu 2' and 'Fission' add-ons.

---

### Post by Mr_Cynical on 2010-03-18
> **mikewhatever said:**
> Last time I checked, the installation of Chrome also added a repository for it.

It does, and that's my problem. It will only update via the repository (unlike for example Opera, which, IIRC from using it on an EeePC before, updates via its own mechanism), and APT is looking for an lpia release in the repo which (obviously) isn't there.

---

### Post by mikewhatever on 2010-03-18
I may be wrong here, but doesn't apt look for version changes of .deb packages in the repositories it has? 
package-1.23-ubunut01.deb -> package-1.23-ubuntu02.deb And if that's the case, why should it care for architecture?

---

