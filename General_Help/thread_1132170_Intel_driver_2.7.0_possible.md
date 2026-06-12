---
title: "Intel driver 2.7.0: possible?"
date: 2009-04-21
forum: General Help
---

### Post by peterson_espacoporto on 2009-04-21
Hello,

I'm experiencing the famous performance regressions on intel hardware (Jaunty) =( The only thing I didn't do was to downgrade to 2.4 - I'm using UXA now and it is a *bit* better =)

I was just thinking: would Ubuntu run if I upgraded to 2.7 driver instead of downgrading? And also, is there any PPA to do so or I need to build the driver?

Thanks in advance =) :)

---

### Post by imwithid on 2009-04-29
I have been trying to install the new driver to no avail for the last couple of days. I've tried to follow the intel site ([http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)) as well as a step by step guide ([http://www.graphics-muse.org/wp/?p=314&cpage=1](http://www.graphics-muse.org/wp/?p=314&cpage=1)), however, I am still very much a beginner and either receive an error at some point (xorg-macro version >=1.1.3 required error) or I cannot follow (the intel site is far too general).

Has anyone succeeded in installing this driver?

---

### Post by monkeyKata on 2009-04-29
> **peterson_espacoporto said:**
> Hello,

I'm experiencing the famous performance regressions on intel hardware (Jaunty) =( The only thing I didn't do was to downgrade to 2.4 - I'm using UXA now and it is a *bit* better =)

I was just thinking: would Ubuntu run if I upgraded to 2.7 driver instead of downgrading? And also, is there any PPA to do so or I need to build the driver?

Thanks in advance =) :)

Hello.  I had pretty bad performance regressions using a laptop with intel graphics as well.  I didn't mess with UXA but downgrading to 2.4 fixed the problem and restored the performance I had from Hardy.  I posted about it here:

[http://ubuntuforums.org/showthread.php?p=7132612#post7132612](http://ubuntuforums.org/showthread.php?p=7132612#post7132612)

Also, adding the greedy heuristic option to the xorg.conf file fixed the horribly choppy background fade effect.  I now see why they implemented this, as it looks nice when it runs smoothly as it's supposed to.  They mention how to do it in the release notes here under the section on Intel graphics regressions:

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

I know I'm not responding to what you asked, but in case you can't use the newest driver, I just wanted to say that, for me, reverting to the old really helped.  I'm curious, too, if anyone has had any luck upgrading to the new driver, if it can be found in a third-party repository somewhere, if it clears away the performance issues... so +1.

---

### Post by imwithid on 2009-05-14
Thanks for the help anyhow. I tried the regression and I found it made no change and in some cases lowered the performance (but not significantly). I guess it's back to 8.04 or wait for 9.10. Other than the video problem, I like the performance of Jaunty. I guess patience is twice "blest", or is that mercy (Merchant of Venice).

---

