---
title: "Undefined symbols using OSS ati-driver: mismatching driver-files?"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by warjowuch on 2007-04-21
Hi folks. A highly technical question here:
Beryl/Compiz does not work for me, even though nearly everything is setup correct.
3d works ppracer works, glxgears works... but almost. It turns real slow, but gives good-correct frame-rates.
It gives me the following error:

libGL: XF86DRIGetClientDriverName: 5.2.0 r200 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
libGL error: dlopen /usr/lib/dri/r200_dri.so failed (/usr/lib/dri/r200_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: r200_dri.so
libGL: XF86DRIGetClientDriverName: 5.2.0 r200 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
libGL error: dlopen /usr/lib/dri/r200_dri.so failed (/usr/lib/dri/r200_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: r200_dri.so

while the driverfile is there. But there seems something wrong with the symbols in it. Now it seems that this has something to do with not-matching versions of X/Mesa/ati-driver (I use the open-source one). Yes, I reïnstalled the ati and mesa-glx/dri several times.

Now, what versios of X, Mesa and ati driver packages do you all use, and should these files really be from mesa, and not from x.org or the oss ati-driver?

I see this issue from this page, section 'Userspace setup'
[http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)

And, how to fix this, by changing symbols (and how?), or reïnstalling certain packages?
Serious technical support would be appreciated

---

### Post by lqyjzmms on 2007-04-23
I'm stuck at the same point. After looking at [http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting), I went to this forum, and I found this thread by searching for ```
undefined symbol: _glapi_add_dispatch
```

My card is  an ATI Technologies Inc RV350 [Mobility Radeon 9600 M10], and I want to get direct rendering to use Google Earth e.g.

Please keep us updated if anyone has found a solution.

---

### Post by lqyjzmms on 2007-04-23
I have been able to solve this issue by uninstalling any fglrx related packages.

Google pointed me to [this page]("http://www.mail-archive.com/slug@slug.org.au/msg61012.html")

---

### Post by warjowuch on 2007-04-23
Hi, thanks for your suggestion.
THat's weird. I have *completely* uninstalled the fglrx-package (via completely remove option in synaptic). What more packages should I uninstall? But, I will take a look once more, though still it seems to me this is not the solution. Let's wait until this evening, am at work now...

What where the steps you took? And, google earth does seem to run on my machine, ppracer also, but not good, according to this bug: [https://bugs.launchpad.net/ubuntu/+source/ppracer/+bug/99359](https://bugs.launchpad.net/ubuntu/+source/ppracer/+bug/99359). I think these are related to eachother.

---

### Post by lqyjzmms on 2007-04-23
I used aptitude, searched for every package containing fglrx in its name, and purged it, i.e. uninstall plus remove all config files.

The packages were
fglrx-amdcccle_8.36.5-1_i386.deb
xorg-driver-fglrx_8.36.5-1_i386.deb
fglrx-kernel-source_8.36.5-1_i386.deb
and perhaps one more.

Google Earth runs now, but it is much too slow to be usable on my machine. Google Earth worked fine (fast) with the fglrx drivers, but I had other issues, e.g. I could not open a second X server instance.

---

### Post by warjowuch on 2007-04-26
How did you do this, I can't find this package
fglrx-amdcccle_8.36.5-1_i386.deb
here, the other ones are allready 'completely removed'

Now I tried reInstalling restricted modules, maybe that will help.

But untill that is tried, no luck yet!

Thanks for your help though!

BTW: google earth runs fine here...? Do you also have the same problems as I have with ppracer, or is it just not accelerated?

---

### Post by lqyjzmms on 2007-04-26
The fglrx-amdcccle package is not included in the Ubuntu repositories. Before switching back to the open source radeon drivers, I had installed the current version of ATI's fglrx drivers, using the file AMD/ATI is distributing on their website. This includes the fglrx-amdcccle package. So if you just installed fglrx from the Ubuntu repositories, you most probably never had the fglrx-amdcccle package.

I've never used ppracer, so I can't tell you anything about it. Does glxgears still give you the same error message?

---

### Post by warjowuch on 2007-04-26
Ah, I installed it from the repos. :-) Thanks for your Ideas! glxgears does indeed still give the same error message after export LIBGL_DEBUG="verbose" Stupid thing...
Hope this will solve, I'd really like to play ppracer normally again and to enjoy beryl or so.

---

### Post by lqyjzmms on 2007-04-26
I just went to packages.ubuntu.com and searched the contents of feisty packages for /usr/lib/dri/r200_dri.so, the file mentioned in your error message. It belongs to the package libgl1-mesa-dri. Did you already try to reinstall libgl1-mesa-dri?

---

### Post by warjowuch on 2007-04-27
yeah, I did it several times. No effect... On the link in my first message is more information, however it is difficult to follow the advice for me.
Smart way by the way, to find out to which package the file belongs!

---

### Post by halfgaar on 2007-04-28
Hi, I'm a friend of Warjowuch, and I'm poking around his computer with SSH while he's not there (and ejecting his CD drive while I'm at it :)). I was kind of confused by this problem, until I did "locate libGL" (after "updatedb"). It revealed that besides the libGL* files in /usr/lib, there are also libGL files in /usr/X11R6/lib, which belong to no package. They weren't (hard) links to the ones in /usr/lib, and were of different size. One of the files even belongs to the user he normally uses, as opposed to root. It would appear he's been creative :). Running "ldd /usr/bin/glxgears" showed that the version in /usr/X11R6/lib indeed takes precedence over the one in /usr/lib.

I'll leave it to him to remove the files, run "ldconfig" and restart X when he gets home. The rest checks out (no xorg-driver-fglrx, matching versions of libgl1-mesa-glx and libgl1-mesa-dri and xserver-xorg-video-ati are present, all of them intact), so the problem should be solved.

Just thought I'd mention it here, for reference.

---

