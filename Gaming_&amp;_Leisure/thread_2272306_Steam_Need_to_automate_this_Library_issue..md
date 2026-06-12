---
title: "Steam Need to automate this Library issue."
date: 2015-04-05
forum: Gaming &amp; Leisure
---

### Post by divxclub on 2015-04-05
Hello guys, I am a huge fan of Linux and Steam and Ubuntu and everything that has to do with Linux world but I have to admit I am not good at code and command line. So when something happens most of the time I am completely useless and need to search for stuff for hours and hours before I get somethign done. Some time ago Steam simply stop working for me and no matter what I do on all of my machines steam asking me to install library but when I do, Ubuntu telling me no such library available. Now here is the question, because it has been over a year with exactly same problem I have to say this is not a bug or temporary thing that will be fixed but something that just not working good. Example.

A computer with Ubuntu 14.04.2 64bit, Nvidia GPU and Steam. On very first load Steam is asking me to install library files and it fails. Why ? I mean clean system, nothing touched first program to install is Steam and problem right away. Most people will say I do not need this, Windows here I come and I hate this. Back in a day everything worked out of the box now it is not. I was thinking this is a bug and gave Steam 3 months, same thing nothing works, another 3 months 14.04.02 (I was using original 14.04) still nothing. Then someone told me to use "alternative" library ppa and stuff started to work. Now I am on brand new system and AGAIN I need to struggle to install simple program. I mean why things are not being fixed ? I am doing something wrong ? How could I, I just installed Steam from official site, no guide from Steam that if you have let's say 14.04.2 64bit you need to do something in advance it just installs. Can anyone explain me do they know that when they say:

```
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386

```

I will give you an error. I mean there is not way around this. Now average user without any guide from steam will say , "well this thing is not working" . because after saying "sure Steam install missing packages" you get this:

```

...........................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.6.0~git20150318.27bf37ba-0ubuntu0ricotz~trusty)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue:

```


Now what ? Alternative library files or some unknown repositories ? Why we're strugle to install simple application, is there something that could be done ? Include this files with Steam may be ? Or have Ubuntu include this library files with original installation ? I am asking today for simplisity and solid performance. When in 1998 for a first time I install Red Had it was premitive, yes but I never looked back, I always had Linux installed and unless I had to use Windows I always put Ubuntu as my main OS.

I am sure there are "fixes" and "guides" but why do we need all this ? Can system be a bit more automatic ? Why in the world you're asking to install library when you know in advance that it wont be installed or this is new ? (it's not it's been happening for some time now). I am just upset because high end system with latest version of Ubuntu can't install simple application or a game.

Now with all that, is there a SOLID guide that we can stick so everyone can see it with how to install Steam on x64 Ubuntu 14.04.2 ++++++ that will work because sure thing I don't see this problem going away in near future. Untill then where do I get this missing library files ?

Thank you guys !

---

### Post by ian-weisser on 2015-04-05
The system is already thoroughly automatic *when a user doesn't muck it up*.

I have mucked up my system many different ways over the years, sometimes deliberately.
It's much harder now than it used to be, but it's still possible.

Example:
> **divxclub said:**
> **libgl1-mesa-glx**:i386 : Depends: libglapi-mesa:i386 (= **10.6.0~git20150318.27bf37ba-0ubuntu0ricotz~trusty**)
You seem to have installed a non-Ubuntu version of libgl1-mesa-glx. It seems to be causing the problem.
Perhaps you were trying to improve performance, or install some driver.

Uninstall it, and reinstall the original version for your release of Ubuntu.

---

### Post by oldrocker99 on 2015-04-06
^ He's right. When my system has gotten borked, it has **always** been as a result of something *I* did. Otherwise, it is amazing just how mature and (mostly) error-free an unborked GNU/Linux system is.

---

