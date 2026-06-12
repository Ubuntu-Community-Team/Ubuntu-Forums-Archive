---
title: "Problem Compiling/installing FF1.5.0.2"
date: 2006-04-17
forum: Desktop Environments
---

### Post by presentt on 2006-04-17
Hello,

I've been trying to install Mozilla Firefox 1.5.0.2 by following the instructions posted [here,]("https://wiki.ubuntu.com/CompileFirefoxNewVersion?highlight=%28firefox%29") but I've run into some problems when attempting to complete the command
```
make -C firefox-bin/browser/installer/
``` on step 4.

I've made some changes to steps 1-3, as follows:[LIST=1]
[*]I substituted 1.5.0.2 for 1.5.0.1 wherever applicable
[*]I changed my processor architecture to pentium4 in the .mozconfig file
[*]I cd'd to /mozilla before entering ```
make -f client.mk build
```  Otherwise, the command would not run.[/LIST]For me, the client.mk file was not in the default directory, but in the ~/mozilla directory.

I looked at the man page for make -C, and it looks to me like it is relying on "the user's configuration file." I'm not sure if I have a configuration file, or how to make one. This is the first time I've tried compiling something on my own; previously, I've used apt-get.

Because of an apparantly different directory scheme (for some reason), I tried running the troublesome command while in the ~/mozilla directory as ```
make -C /broswer/installer/
``` and in the ~/mozilla/browser directory as ```
make -C /installer/
```. Nothing worked.

Can someone help me get FF1.5 running from this point?  Thanks a lot.

---

### Post by aysiu on 2006-04-17
Is there any reason you want to *compile* it instead of just *installing* it?

This script will install Firefox 1.5.0.2 for you:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by presentt on 2006-04-17
[quote=aysiu]Is there any reason you want to *compile* it instead of just *installing* it?[/quote] 
Haha, no.  The compilation of FF was just the first thing I came across.  Thanks for the script.

---

### Post by presentt on 2006-04-17
Thanks a lot, the script ran perfectly, and v1.5.0.2 is up and running flawlessly.  All of my bookmarks, extensions, etc. carried over as well.

Just curious, though, why wouldn't the compilation work correctly?  What was I doing wrong, and how can I fix it so that when I *do* need to compile something, I will be able to do so?

Thank you.

---

### Post by aysiu on 2006-04-17
[QUOTE=presentt]Thanks a lot, the script ran perfectly, and v1.5.0.2 is up and running flawlessly.  All of my bookmarks, extensions, etc. carried over as well.[/quote] Good to hear.

> 
Just curious, though, why wouldn't the compilation work correctly?  What was I doing wrong, and how can I fix it so that when I *do* need to compile something, I will be able to do so? No idea. I don't really compile software. I usually just use stuff available in the repositories.

---

