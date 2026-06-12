---
title: "Best way to start xfce when using NX or X2Go"
date: 2010-10-31
forum: Desktop Environments
---

### Post by luma on 2010-10-31
Hi everyone,

I noticed that when using NX or X2GO if I start xfce4 using /usr/bin/startxfce4 it looks different and not as "pretty" then the console.

How can I start XFCE using something like X2GO or NX and have it look the same as if I booted it up using a monitor.

thanks!

Luma

---

### Post by rolkau on 2010-11-02
In NX, chose "Unix CDE" as Desktop to start XFCE. In x2go, try starting the program /usr/bin/xfce4-session

---

### Post by luma on 2010-11-06
Thanks for the reply.

I have done as you say in NX and I get an error: cannot run 'cdwm' please ensure the requested app is in the system path and that you have credentials to execute it.

in X2Go (and NX) running /usr/bin/xfce4-session gives me the same plain version of XFCE and not the same one that is on the console.

thanks.

Luma

---

### Post by yaztromo on 2010-12-31
Does anyone know a fix for this?

I'm trying run an NX server on a xubuntu machine and I get the cannot rum cdwm message. It worked fine on Lucid.

---

### Post by yaztromo on 2011-06-25
Sorry to bump an old thread but I'm still lost with this one.

I really need to get nx server working on my Xubuntu 10.10 laptop but I run into the "cannot rum cdwm" problem.

---

### Post by HunterZ on 2011-09-27
Posted a fix/workaround here:

[https://answers.launchpad.net/ubuntu/+question/157817](https://answers.launchpad.net/ubuntu/+question/157817)

---

### Post by maxadamo on 2012-07-06
> **luma said:**
> Thanks for the reply.

I have done as you say in NX and I get an error: cannot run 'cdwm' please ensure the requested app is in the system path and that you have credentials to execute it.

Luma

Come on, come on, come on ... I can't really believe:
# cd /usr/bin
# ln -sf xfce4-session cdwm

---

