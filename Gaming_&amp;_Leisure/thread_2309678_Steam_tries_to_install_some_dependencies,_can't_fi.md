---
title: "Steam tries to install some dependencies, can't find packages"
date: 2016-01-12
forum: Gaming &amp; Leisure
---

### Post by Joel_Gabriel on 2016-01-12
Hi folks,

I successfully got an ARM copy of Ubuntu 14.04 working on my Raspberry Pi 2. It came quite bare (namely, no GUI) so I installed lubuntu-desktop and a few other packages.

I wanted to see if Steam would work. I managed to use the .deb file, but now when I start it, Steam wants to install three packages:

  - libgl1-mesa-dri:i386
  - libgl1-mesa-glx:i386
  - libc6:i386

So after it tries to install these packages, it gets the following error:

```
Failed to fetch: hhtp://deb.playonlinux.com/dists/trusty/InRelease Unable to find expected entry 'main/binary-armhf/Packages' in Release file (Wrong sources.list entry or malformed file)

E: some index files failed to download. They have been ignored, or old ones used instead.

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package libgl1-mesa-dri
E: Unable to locate package libgl1-mesa-glx
E: Unable to locate package libc6
Press return to continue:
```

So, I tried to manually install the packages, using:

```
sudo apt-get install libgl1-mesa-dri libgl1-mesa-glx libc6 
```

But, when I do that, it says that all the packages are the latest version.

As a result, Steam doesn't launch. I assume it's because I'm using an ARM version of Ubuntu and it wants i386 versions of the packages?

---

### Post by maxinstuff2 on 2016-01-18
I am pretty sure that steam is x86 only.

As in, Valve's Steam client does not support or run on ARM architecture.

I guess you are trying to make your own SteamLink? I like it - but I think you're out of luck.
Incidentally, there is a change dot org petition to try to get Valve to do an ARM version of SteamOS:
[https://www.change.org/p/valve-corporation-streamos-lightweight-steamos-for-arm-platforms](https://www.change.org/p/valve-corporation-streamos-lightweight-steamos-for-arm-platforms)

EDIT: In addition to the above, it sounds like the custom OS that runs on the steamlink (that Valve sells for $50) is based on Android. It is not the full linux-based steamOS. (yes I know, Android is linux but you know what I mean)
Maybe they'll release the steamlink software at some point?

---

