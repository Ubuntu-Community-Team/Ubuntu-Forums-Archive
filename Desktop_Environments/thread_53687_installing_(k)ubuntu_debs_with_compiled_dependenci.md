---
title: "installing (k)ubuntu debs with compiled dependencies"
date: 2005-08-01
forum: Desktop Environments
---

### Post by EasterSunshine on 2005-08-01
hi, i'm new to kubuntu but i must say, its the best os on the planet. absolutely amazing job, (k)ubuntu team.

my problem is because i prefer running binaries that i have compiled myself over using sudo apt-get install to install precomiplied binaries. now, take for instance: i have successfully compiled and installed various packages, lets say atk, libtiff, libjpeg, and pango for example. now, i do not want to compile gtk+-2.0 for some reason and i would like to install thru kynaptic. kynaptic complains that i do not have atk, libtiff, pango, and libjpeg packages installed and requests that install the precompiled debs first.

so in short, is there a way to make kynaptic (or synaptic) aware of the packages i have compiled and installed myself rather than using the precompiled debs?

---

### Post by EasterSunshine on 2005-08-01
hmm, i guess i should also mention that i'm interested to know if there is somelike like kynaptic but instead of installing precompiled binaries, compiles binaries from source and installs those, taking care of dependencies and stuff.

i am on a slow old computer and i need to conserve my processor and my hdd. i read and heard that precompiled binaries take up more space and tend to run slower. i was like "whoa dude" when i first booted into kubuntu and found that many packages that i would have compiled myself were already installed.

i want to have as much of my kubnutu operating system compiled on my machine as i possibly can, without wasting so much time as to doing each package manually.

---

### Post by az on 2005-08-01
No, you cannot use stuff you compiled from source and integrate it into the package management system.  Well, you can, but you would have to make debian packages out of everything you compiled and you will probably bork your system.  Apt is there to keep you out of dependancy hell, and that is what you are going to be getting into.

Compiling packages by yourself takes up way more room than just installing the binaries.  No, they do not run all that faster if you compile them yourself.  Any further optimisation you make will not have a noticable impact on system performance.

So, in short, just use the packages in the repositories.

If you want to compile them from source and resolve dependancies, you can install source packages, but you will be using way more disk space and you will end up with exactly the same binary package as is in the repositories.

---

### Post by ltmon on 2005-08-01
You can actually integrate source compiled binaries into the pacage system using "checkinstall" (google for it), but I feel you'll be spending half your time mucking around with version numbers and patch levels and the like to get it all fitting together properly.  If you enjoy doing that kind of thing, go and help the Kubuntu dev team out :)

If you _really_ want to use your own source compiled binaries, I would recommend a source-based distro.  Gentoo is the most popular of these, and they often include optional binaries for big packages that would take days to compile yourself.

L.

---

### Post by EasterSunshine on 2005-08-01
thx for the advice. guess i'll continue to use kynaptic and sudo apt-get install

---

