---
title: "mplayer and kubuntu do not mix."
date: 2005-04-16
forum: Desktop Environments
---

### Post by roffles on 2005-04-16
Hi,

I am trying to get mplayer to work with kubuntu and I am not having much success. I have it on 2 systems (one desktop, one laptop) and it does not work on either. I compiled it from source since I could not find a repo that had it, so maybe that's the problem. I know mplayer does work because I previously used MEPIS linux and it worked fine. 

Can someone help? One strange thing though, on my laptop if I do a sudo mplayer filename.avi it will play the file in fullscreen but I can't exit and if I ctrl+c out of it the whole screen messes up and I have to do a ctrl+alt+BS to restart X server. Not sure if this points to anything, could it be a permissions problem?

---

### Post by Pirate_Will on 2005-04-16
I had great problems with the apt version from: 

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

You could add the above line to your sources.list and it should be apt-able. I did that first but it didnt work properly for me and I eventually gave up with it.

I had a few initial troubles  compiling mplayer 
I got an error whilst compiling:
 /usr/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function
 `glXGetMscRateOML':
 : undefined reference to `XF86VidModeQueryVersion'
 /usr/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function
 `glXGetMscRateOML':
 : undefined reference to `XF86VidModeGetModeLine'
 collect2: ld returned 1 exit status
 make: *** [mplayer] Error 1

Turned out i was only missing this package   libxxf86vm-dev

It works pretty much fine now, I have a few sound issues, and playing DVDs takes up a lot of resources, but its bearable.

So what exactly is the problem?

---

### Post by roffles on 2005-04-16
[QUOTE=Pirate_Will]I had great problems with the apt version from: 

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

You could add the above line to your sources.list and it should be apt-able. I did that first but it didnt work properly for me and I eventually gave up with it.

I had a few initial troubles  compiling mplayer 
I got an error whilst compiling:
 /usr/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function
 `glXGetMscRateOML':
 : undefined reference to `XF86VidModeQueryVersion'
 /usr/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function
 `glXGetMscRateOML':
 : undefined reference to `XF86VidModeGetModeLine'
 collect2: ld returned 1 exit status
 make: *** [mplayer] Error 1

Turned out i was only missing this package   libxxf86vm-dev

It works pretty much fine now, I have a few sound issues, and playing DVDs takes up a lot of resources, but its bearable.

So what exactly is the problem?[/QUOTE]


I am at work right now but basically I can not compile it to use a gui (I think it may have to do with the package you mentioned above, since it mentioned it could not find some X11 libs). And after I compiled it I can run it, but it wont play anything, it says it cant initialize the video driver. the WEIRD thing is if I do a sudo mplayer it will play the video, except it corrupts everything when I try to close out of it and I have to restart the X server. So I don't know what is going on, really... is there some weird permissions that I have to change? It's weird that I can play video as root.

---

### Post by buldir on 2005-04-16
Sorry I can't help other than to say, I stayed away from mplayer from [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) and got it from the normal Ubuntu sources.  Here's my sources.list.  I have the [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) sources commented out...the only thing I grabbed from there was the win32codec package (stable) and the latest Adobe Acrobat package (testing).  My mplayer runs fine, plus the Firefox plugin.  Have you tried getting the mplayer package from the "official" Ubuntu repositories?  Why mess with compiling mplayer from source?


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe  
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

