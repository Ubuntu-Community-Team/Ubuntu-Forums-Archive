---
title: "Creating an Apt CD"
date: 2005-01-12
forum: General Help
---

### Post by saBrEwolf on 2005-01-12
Hi people,

I am trying to create a cd of packages that people like for example gstreamer-lame and totem-xine. I'd like to keep this simple and easy to use (as in add cd repository on synaptic) as I want to distribute this at a LUG along with ubuntu.

Could someone explain to me how to do this as I've searched round the debian help archives but can only find how to create server repositories.

Any help would be greatly appreciated.

---

### Post by Juergen on 2005-01-12
IMHO you just need to run dpkg-scanpackages to create a Packages.gz and then burn this with your packages on CD.

Synaptic bombs if I try to add such CD to the package sources, but if I edit sources.lst manually, it works.

If you want a 'real' repository you can try apt-move to copy your download-cache to a local repository. 
But it seems apt-move doesn't know the ubuntu repository structure with multiverse etc. and creates Packages.gz only for main, even if it copies all packages. 
So you have to run dpkg-scanpackages anyway.

---

