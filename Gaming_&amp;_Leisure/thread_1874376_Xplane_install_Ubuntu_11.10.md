---
title: "Xplane install Ubuntu 11.10"
date: 2011-11-02
forum: Gaming &amp; Leisure
---

### Post by dbwrobel on 2011-11-02
Hello!

I've been trying to install Xplane 9 based on the tutorials provided on the xplane website for linux and am getting the following error:

error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory

I tried to trace back to the Mesa gl libraries and they seem to be installed (I also located libGLU.so.1 on my system). Has anyone come across the same issue?

(I'm also using the most recent NVIDIA driver, 285.13).

Thanks!

---

### Post by Perfect Storm on 2011-11-03
Are you using 64-bit system?
Where was the lib located?
Try ldd the binary for more output.

---

### Post by nehalem on 2011-11-17
Since dbwrobel never got back to you I hope it's ok that I jump in here as I'm having the same issue. I actually have very little familiarity with installing xplane 9, but the need has come up.

The box that I'm attempting to install on has 8gb of RAM so installing the 64bit version seemed intelligent enough, is it possible to install xplane 9 on this configuration (using 32 bit libs) or should I revert to the 32 bit install?

I'm getting the same error and unlike dbwrobel haven't located the LibGLU library to link against. I'm using the proprietary nvidia drivers as this box has a pretty good nvidia card that I would like to run the software on.

Thanks in advance for any help you can lend.

---

### Post by Perfect Storm on 2011-11-17
Install **libglu1-mesa:i386** and see if it helps.

---

### Post by dbwrobel on 2011-11-17
Hey, sorry for the long delayed reponse...I had tried several other distros and finally managed to get it going on RHEL 6 out of all of them. Although I could not get any audio to work on it. Also of note, was that I was able to get it working under Ubuntu 10.04.3 LTS (again with no audio though).

Anyway, yes I was running a 64 bit version of Ubuntu (11.10) and from what I remember I think the file was under /usr/lib (at least I think). I will likely be reinstalling again as I setup another RHEL 6 system to be used as a simulator and am getting a segmentation fault on this one.

---

### Post by Perfect Storm on 2011-11-17
in Ubuntu 11.10 a simple installing of libglu1-mesa:i386 package should do it.

Otherwise a run **ldd** on the binary to check up on the x-plane dependencies.

---

### Post by dbwrobel on 2011-11-18
Also, to add to my previous post...I think the problem with not being able to install/run sometimes stems from using the binary provided nvidia (if using them directly from the site); at least that is the case with the rhel based distros I tried...if using drivers from the repos I didn't have any issues (with the exception of no audio still).

As Artificial Intelligence said though, other than the driver issue, it should work by simply installing the 32-bit libGLU.

---

### Post by paulororke on 2012-01-05
> in Ubuntu 11.10 a simple installing of libglu1-mesa:i386 package should do it.

Brilliant.  That resolved my dependency issue on 11.10 ATI/AMD, at least to the point where I can run the installer.

I had been pulling my hair out trying to get the x-plane 10 demo installed.

Too bad it won't actually run...

After launching x-plane 10 demo I get a window warning that I don't have the sound drivers, the window flickers an on launch I get:
```

XIO:  fatal IO error 14 (Bad address) on X server ":0"
      after 3817 requests (3817 known processed) with 46 events remaining.

```

Maybe the issue is a lack of hardware acceleration.  I'll add a decent card and try again and then spend the time getting the sound drivers in place.

---

### Post by 1clue on 2012-01-05
Mine works fine right out of the box. I must have had that lib already loaded.  **Edit:** XP9 that is, not XP10.

---

