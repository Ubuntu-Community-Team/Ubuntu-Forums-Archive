---
title: "Xorg to XFree86"
date: 2005-07-25
forum: Desktop Environments
---

### Post by KidAirbag on 2005-07-25
I recently installed Ubuntu for the first time. It's working well and I really enjoy it.

A problem I've been having, however, is that Xvideo wouldn't work with my video card under Xorg. I decided to switch to Xfree86. This immediatly fixed the problem. However after restarting the computer, X wouldn't load up. I was stuck with the console.
 
Is there a way to autoconfigure XFree86 in the same way that Xorg was configured when I installed Ubuntu? I'm working on a clean installation now, I haven't made the swith yet.

Thanks!

---

### Post by angkor on 2005-07-25
how about:

```
sudo dpkg-reconfigure xserver-xfree86
``` 

or something along that line.

---

### Post by KidAirbag on 2005-07-25
[QUOTE=angkor]how about:

```
sudo dpkg-reconfigure xserver-xfree86
``` 

or something along that line.[/QUOTE]

I switched over to XFree86, and attempted to configure it in the way you pointed out. I restarted and X still failed to start. I switched back to Xorg, configured it, and started X. Everything worked fine (except xvideo still doesn't work). I'm now back to where I started.

EDIT: It seemed that configuring XFree86 was still writing to the xorg.conf file. I copied this to the XFree86 config file and got it up and running. I just hope Xvideo won't die on me. Thanks for the help!

---

