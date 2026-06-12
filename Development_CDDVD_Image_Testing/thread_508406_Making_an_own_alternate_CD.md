---
title: "Making an own alternate CD"
date: 2007-07-24
forum: Development CD/DVD Image Testing
---

### Post by Maraujo on 2007-07-24
Hello everyone!

I'm working on making a custom alternate CD of Ubuntu 7.04. I'm having a bunch of problems doing it.

1.- First thing is that I don't find enough information about preseeding directives. I'm using this site at the moment:

[URL="https://help.ubuntu.com/7.04/installation-guide/i386/appendix-preseed.html"]

Specifically I'm really curious with this exact directive:
tasksel tasksel/first   multiselect ubuntu-desktop

¿Is this one reserved only to the Ubuntu tasks? 

2.- When on the Internet people speak about tasks in Ubuntu ¿Are they just metapackages? I have done my own one and I would like to add it to the ALT CD. ¿Is it possible to add it just after the ubuntu-desktop task? Example:

tasksel tasksel/first   multiselect ubuntu-desktop my-own-metapackage

Or I'm forced to use the pkgsel preseed directive.

**3.- Where can I find documentation about how the Ubuntu members make the ALT CD and what scripts or tools they use?**

4.- When I put 2 metapackages custom ALT CD makes weird things and starts downloading a debootstrap installation of Ubuntu from the Net and finally it boots up without X server. ¿Anyone has dealt with this issue?

5.- VMWare-Server and VIrtual-Box just work well in one out of three machines I'm using for this process:

[LIST]
[*]Host A is not even able to boot the iso. This is the oldest machine, so I'm guessing is just a RAM lack.
[*]Host B boots the isos. But it gets stuck when downloading the Release file from the archives ubuntu site. The point is that this happens even with the official ALT CD.
[/LIST]

I'm saying this just to know if someone has some hint why it's happening.

Thank you very much for your time and effort in advance.

Regards

---

