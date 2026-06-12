---
title: "fglrx + XGL = holy crap!"
date: 2007-09-02
forum: Desktop Environments
---

### Post by bohsocks on 2007-09-02
Running Feisty, I just installed fglrx for my ATI cards so I can run XGL (and Compiz).

Initially when I did it, XGL just gave me the "10 seconds" error.  I decided to brick the whole idea, and uninstalled fglrx.  XGL was still there... and opened... but it would lock up quickly.

I decided to see what would happen if I installed fglrx and tried again.  Remarkably, it opens, but this is the result:

[http://www.bohsocks.com/stuff/Screenshot-3.png](http://www.bohsocks.com/stuff/Screenshot-3.png)

That's pretty messed up.

What can I do to remedy this problem?

---

### Post by Donkinator on 2007-09-06
I get the same problem with my ATI X600 card, mobility radeon. using feisty, and having a mess of problems getting the thing to work with the updated ATI driver. XGL and fglrx are having a mess of issues. It is definitely an ATI driver problem, because I can run compiz in Gnome without XGL or fglrx. It's not exceptional quality but will work, and the textures aren't quite up to my standards, but remember they are software driven...not hardware. I did have the new ATI driver working in XGL using fglrx with Compiz once before on this machine...but had to redo my partition and can't remember what I did before >.<. I do know I installed compiz from repos too, not self compiled. I've been trying to work this one out for a week now, hopefully I'll have an answer soon.

---

### Post by mcduck on 2007-09-07
My Mobility Radeon X1600 works just fine with XGL using fglrx drivers from Feisty's repositories.

You could try using the repository fglrx package instead of installing the latest version.

---

### Post by Jouke74 on 2007-09-07
Yep I agree use the restricted drivers option under your administration menu. This will install the Ubuntu FGLRX driver (older version) and some additional files. Afterwards it will run fine with XGL (X1600Pro) here. Be warned, if you get a black screen after the first boot with FGLRX, just reboot again. Things will be adjusted in Xorg.conf.

Do not forget to get rid of the new drivers!

---

### Post by kellemes on 2007-09-08
> **bohsocks said:**
> Running Feisty, I just installed fglrx for my ATI cards so I can run XGL (and Compiz).

Initially when I did it, XGL just gave me the "10 seconds" error.  I decided to brick the whole idea, and uninstalled fglrx.  XGL was still there... and opened... but it would lock up quickly.

I decided to see what would happen if I installed fglrx and tried again.  Remarkably, it opens, but this is the result:

[http://www.bohsocks.com/stuff/Screenshot-3.png](http://www.bohsocks.com/stuff/Screenshot-3.png)

That's pretty messed up.

What can I do to remedy this problem?

You don't have your driver installed like it should..
Please look at /var/log/Xorg.0.log

---

