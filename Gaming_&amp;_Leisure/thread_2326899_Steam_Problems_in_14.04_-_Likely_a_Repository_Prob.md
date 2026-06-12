---
title: "Steam Problems in 14.04 - Likely a Repository Problem"
date: 2016-06-05
forum: Gaming &amp; Leisure
---

### Post by MiscJax on 2016-06-05
After reinstalling steam because it was not working, it pops up with this when I try to open it:

```
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386

```

Which prompts this to come up:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  Unable to find expected entry 'restricted/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  Unable to find expected entry 'restricted/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/trusty/InRelease  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://ppa.launchpad.net/wine/wine-builds/ubuntu/dists/trusty/InRelease  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'partner/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch http://archive.canonical.com/dists/trusty/Release  Unable to find expected entry 'partner/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libc6 libc-bin initscripts locales tzdata


Package libgl1-mesa-glx:i386 is a virtual package provided by:
  libgl1-mesa-glx-lts-wily:i386 11.0.2-1ubuntu4~trusty1 [Not candidate version]


Package libgl1-mesa-dri:i386 is a virtual package provided by:
  libgl1-mesa-dri-lts-wily:i386 11.0.2-1ubuntu4~trusty1 [Not candidate version]


E: Package 'libgl1-mesa-dri:i386' has no installation candidate
E: Package 'libgl1-mesa-glx:i386' has no installation candidate
E: Package 'libc6:i386' has no installation candidate

```

Which then brings up the following error message:

"You are missing the following 32-bit libraries, and Steam may not run:libc.so.6"

I've been seeing the first part of the error message, where it fails to find things and suggests an error with sources.list, quite a bit recently, and have tried (with a friend with more Linux knowledge than I have) to fix it without success.

---

### Post by oldrocker99 on 2016-06-05
It does look like repository errors. Go to Software Sources, and ping the servers and pick the fastest one. I have had great success with tripadvisor.com as a source, but your mileage may vary.

---

### Post by MikeCyber on 2016-06-06
Install proprietary drivers AMD/Nvidia etc.

---

### Post by MiscJax on 2016-06-06
> **oldrocker99 said:**
> It does look like repository errors. Go to Software Sources, and ping the servers and pick the fastest one. I have had great success with tripadvisor.com as a source, but your mileage may vary.
I can't open Software Sources. In the software center, the Software Sources option is disabled.

> **MikeCyber said:**
> Install proprietary drivers AMD/Nvidia etc.
I have an Intel graphics card though...

---

### Post by oldrocker99 on 2016-06-07
> **MiscJax said:**
> I can't open Software Sources. In the software center, the Software Sources option is disabled.
Try this:```
sudo apt-get install synaptic
```
Under Settings/Repositories, you'll be able to ping the repositories, and pick a better and faster one.

> I have an Intel graphics card though...

**ALL** Intel drivers are open source.

---

### Post by MiscJax on 2016-06-08
> **oldrocker99 said:**
> Try this:```
sudo apt-get install synaptic
```
Under Settings/Repositories, you'll be able to ping the repositories, and pick a better and faster one.



**ALL** Intel drivers are open source.
I already have synaptic, though I wasn't aware that it's possible to ping repositories with it.

---

### Post by deadflowr on 2016-06-08
You're errors are caused by the fact that it is looking for wrong architecture.
1386 is not an arch.
the correct arch is  i386 small letter I, not number 1.
So you need to remove the 1386 arch,
to do so use the command
```
sudo dpkg --remove-architecture 1386
```
then run a quick
```
sudo apt-get update
```

hope it helps

---

### Post by MiscJax on 2016-06-10
> **deadflowr said:**
> You're errors are caused by the fact that it is looking for wrong architecture.
1386 is not an arch.
the correct arch is  i386 small letter I, not number 1.
So you need to remove the 1386 arch,
to do so use the command
```
sudo dpkg --remove-architecture 1386
```
then run a quick
```
sudo apt-get update
```

hope it helps
That solved the problem I was having, yes. Thank you!

However, when I try to run Steam it still asks to install the same packages. Instead of what came up before, this comes up:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.6)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```
After checking for them with synaptic, I was able to find unity-control-center, libcheese-gtk23, and libcheese7, the latter two of which I have the most recent version. The rest of the packages, including the ones it asks to install, don't show up in synaptic.

---

