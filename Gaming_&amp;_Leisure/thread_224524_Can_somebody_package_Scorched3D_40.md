---
title: "Can somebody package Scorched3D 40?"
date: 2006-07-28
forum: Gaming &amp; Leisure
---

### Post by &amp;)ky#)^ on 2006-07-28
I'd like to request that if anyone out there is running a Dapper amd64 system and can compile version 40 of scorched3d, can you please package a .deb file for us? I can't find one for the amd64 and compiling it is a pain for me with my current setup. Please? Through apt, we're all still on version 39.1 and it sucks since we can't play online. Thanks ahead of time.

Here's the source:
[http://www.scorched3d.co.uk/downloadssrc.php]("http://www.scorched3d.co.uk/downloadssrc.php")

---

### Post by Miguel on 2006-07-28
Hi bluej

There is a .deb in their site, [here](http://www.scorched3d.co.uk/downloads.php). Download it and install using dpkg -i and it should make the trick. If you need more help, don't hesitate to ask!.

---

### Post by &amp;)ky#)^ on 2006-07-28
The provided package from their website is for the i386 architecture.  I'm running the amd64 architecture.  Instant incompatibility.

I get this error:
```
dpkg: error processing Scorched3D-40-i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 Scorched3D-40-i386.deb

```

---

### Post by Miguel on 2006-07-28
I have no experience with 64bit architecture but try using the flag --force-architecture.

---

### Post by &amp;)ky#)^ on 2006-07-28
I've tried that.  It will install it, then, but I'd need to install all of the libraries and such that it depends on in the i386 architecture, which defeats the whole point of having a 64-bit system.  The game *can* be compiled on a 64-bit system.  I just don't have the libraries needed to *compile* it.  I have everything to run it.  So, I just need someone to compile it and package it for me.

---

### Post by Miguel on 2006-07-28
Hi again,

Are you experienced in compiling? I'm sure scorched3d is not difficult to compile, although it will have tons of lib*-dev dependencies. The first step should be
```

sudo apt-get build-dep scorched3d

```

It will ask you to install a few packages, which will surely be the ones needed to compile scorched3d 40. Does this help you? If not, we'll have to look for someone with a 64bit arch that compiles it for you (I'm not into cross-compiling)

After that, ./configure, make, sudo checkinstall (the dance, you know) should make the trick.

---

### Post by &amp;)ky#)^ on 2006-07-28
I'm kind of anal when it comes to keeping my system clean so I was hoping that I could avoid having to get all of those damn packages it needs for the libsdl1.2-dev dependencies just to turn around and remove them when I'm done, but I guess I have no choice.  Well, I don't have time right now because I should be sleeping so I'll try compiling it again tomorrow.

Hey, while we're on the subject, if there's anyone out there who really likes Scorched 3D, I think that Ubuntu (and Debian) could use a new person to manage the scorched3d packages.  It seems the guy who was doing it (Bartosz Fenski) has been MIA for about 4 months.  I sent him an email.  We'll see how it goes.  Until then, I'd love for someone to step up to the plate and manage this game's packages.  Just a thought.

---

### Post by HAARP on 2006-07-28
There's a new version? Holy crap, didn't know that.
Ok, I've installed the 40 i386 package now. When starting, I get this:
```
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

```
Could this be because I still have the 39.1 packages from the repos installed?
Since the package from the official site is named **scorched**, while the one from the Ubuntu repos is **scorched3d**

---

### Post by &amp;)ky#)^ on 2006-07-30
Can someone please package this for the 64-bit Ubuntu community?  We're missing out!

---

### Post by Kilz on 2006-07-30
> **bluej774 said:**
> Can someone please package this for the 64-bit Ubuntu community?  We're missing out!

You might want to make sure you have the [univers repoitory enabled in dapper]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") Because the [package site says there is a 64bit package]("http://packages.ubuntu.com/dapper/games/scorched3d") for this already. Its in the Universe, so its possible you dont have it enabled.

---

### Post by struess on 2006-07-30
roger that, but it doesn't seem version 40 is out there for us underprivileged '64 users.  on the plus side, 39.1 still warms my heart.

---

