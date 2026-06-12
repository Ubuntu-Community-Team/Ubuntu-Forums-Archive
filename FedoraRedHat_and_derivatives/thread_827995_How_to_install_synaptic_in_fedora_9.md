---
title: "How to install synaptic in fedora 9?"
date: 2008-06-13
forum: Fedora/RedHat and derivatives
---

### Post by sharks on 2008-06-13
How to install synaptic in fedora 9?

---

### Post by Golem XIV on 2008-06-13
Well, if you can't find it using Yum I guess you'll have to compile it from source which you can get from the [Synaptic web page]("http://www.nongnu.org/synaptic/").

<edit> Note that Fedora uses RPM packages, while Synaptic is for DEB packages.  I don't know if Synaptic will work properly on a RPM based system.  Check their web site for documentation. </edit>

---

### Post by schallstrom on 2008-06-13
The right place to ask Fedora specific questions would be a [Fedora forum]("http://fedoraforum.org/").

---

### Post by Joeb454 on 2008-06-13
Why would you want Synaptic in Fedora? Personally I'd suggest using Yum :)

---

### Post by igknighted on 2008-06-13
> **Joeb454 said:**
> Why would you want Synaptic in Fedora? Personally I'd suggest using Yum :)

Yum is a command line interface, while synaptic is a GUI interface.  There is a version of synaptic (and apt4rpm) that can be used with Fedora 9, but it really hasn't been maintained for some time and isn't very good.  You would be better served by getting used to packagekit, because it will likely replace synaptic in Ubuntu in the not too distant future.

---

### Post by samwyse on 2008-06-14
Have you tried yumex? It's in the repos.

---

### Post by izanbardprince on 2008-06-29
PackageKit is what is used in Fedora 9, and it kicks Synaptic's butt.

Actually, yum kicks apts butt too, it's a lot easier to recover from an update that breaks your system with yum than it is with apt, apt will just tell you "You have the latest package!" (NO! Really? Hadn't noticed!)

Yeah, there is an apt-rpm and a Synaptic that kind of works and isn't well maintained, but why?

---

