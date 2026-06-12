---
title: "Ubuntu 9.10 Karmic Issues with libstdc++5 Fixed!"
date: 2009-11-12
forum: Desktop Environments
---

### Post by flyguy97 on 2009-11-12
All,

I know a lot of people using proprietary and/or older software are having problems with Ubuntu's decision to remove support for libstdc++5 in Ubuntu 9.10. As a open-source developer I faced a similar situation when I was trying to support a proprietary (but free) p2p video streaming client (see [http://code.google.com/p/sopcast-player]("http://code.google.com/p/sopcast-player")). I created packages for the 32-bit, 64-bit and lpia architectures of the libstdc++5 library as well as a 64-bit wrapper library for the 32-bit package called lib32stdc++5 (useful for running 32-bit apps on 64-bit platforms). Be advised, the lib32stdc++5 is only available on the amd64 platform, not the ia64 (although nothing is stopping you from downloading the source package and compiling for yourself). Please see [my PPA page]("https://launchpad.net/~jason-scheunemann/+archive/ppa") for instructions on how to install.

Cheers,
Jason

---

### Post by coldReactive on 2009-11-13
source for one arch may not compile on another. I've had that issue before.

By the way, make sure to tell people HOW to compile for a different arch and WHAT PACKAGES THEY NEED TO INSTALL. It's infuriating to compile and have 10+ packages you need to install extra, and each one has to be told to you by re-re-re-re-re-re making/configing the source.

---

### Post by flyguy97 on 2009-11-13
> **coldReactive said:**
> source for one arch may not compile on another. I've had that issue before.

By the way, make sure to tell people HOW to compile for a different arch and WHAT PACKAGES THEY NEED TO INSTALL. It's infuriating to compile and have 10+ packages you need to install extra, and each one has to be told to you by re-re-re-re-re-re making/configing the source.

coldReactive,

When I said install from source I should have been more specific. The source deb for lib32stdc++5 is pre-configured to also work on the ia64 platform, the dependency issues have already been sorted. Sorry for the confusion.

Cheers,
Jason

---

### Post by coldReactive on 2009-11-13
> **flyguy97 said:**
> coldReactive,

When I said install from source I should have been more specific. The source deb for lib32stdc++5 is pre-configured to also work on the ia64 platform, the dependency issues have already been sorted. Sorry for the confusion.

Cheers,
Jason

What if we want to compile it for i386 even though we're using amd64 and/or ia64?

---

### Post by flyguy97 on 2009-11-13
> **coldReactive said:**
> What if we want to compile it for i386 even though we're using amd64 and/or ia64?

coldReactive,

I am not sure what you are trying to do. In my PPA I have already put together the the i386 binaries for libstdc++5. lib32stdc++5 is strictly for 64-bit architectures, it is a compatibility layer between the 64-bit kernel and the 32-bit library. If you want to compile the libstdc++5 binaries yourself on a 64-bit machine I suggest you read up on pbuilder. pbuilder allows you to build packages for any version of Ubuntu and Debian on any architecture supported by your CPU (i386 is supported by amd64). In my opinion all packages should be built with pbuilder as it will guarantee a clean build environment if used correctly.

Cheers,
Jason

---

### Post by coldReactive on 2009-11-13
> **flyguy97 said:**
> if used correctly.

You're assuming that I know how to use it in the first place, correctly that is. Bad call on your part.

It's not really any concern of mine though, since I barely ever develop.

---

