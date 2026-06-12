---
title: "Offline installer of applications"
date: 2009-03-31
forum: General Help
---

### Post by enigmatic28 on 2009-03-31
Hi All,

I would just like to ask if there is a way to create an off-line installer of the applications found in synaptic or from the repositories of the software providers.

**2 reasons for asking:**
1. I know that internet access can be found almost everywhere, but i would like to give the installer to someone who does not have an internet at his home (i.e. xbmc)


2. I don't want to re-download every packages over and over again when i decided to reformat my pc, i would just like to install the current release and update if necessary...

I know some softwares like skype already offer packages that works like an exe file which you can just double click and the package manager will do the rest.. this fuctionality i would like to do on the other softwares and store them or give them to freinds

Hope someone can help me or point me to a tutorial that can attain the said output...

Thank you very much....

---

### Post by cariboo on 2009-03-31
Have a look at this [howto]("http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/") by one of the former moderators.

Jim

---

### Post by hyper_ch on 2009-04-01
well, if you download software with the packager it the .deb files get stored in /var/cache/apt/archives.

All you need to do then is get those .deb and run them with
```

sudo dpkg -i package.deb

```

Of course, you'll also need to know if there are dependencies and install them also on other machines.

---

### Post by enigmatic28 on 2009-04-01
WOW!!! both answers were great!!!!

Thanks so much guys for the time... this helps SO MUCH!!!

---

### Post by EXCiD3 on 2009-04-02
[Keryx]("http://keryxproject.org") can do the trick as well. It takes care of doing most of the work for you and can run on any platform that can run python and wxWidgets this way you can get updates for packages, even on a Windows machine.

---

