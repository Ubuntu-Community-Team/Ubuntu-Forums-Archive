---
title: "Replacing all uses of GKSU with KDESU?"
date: 2008-04-15
forum: Desktop Environments
---

### Post by Igtenio on 2008-04-15
This probably sounds like a stupid question, but I was wondering if there was any way for all the calls for privilege escalation could use KDESU instead of GKSU, including applications with it "hardcoded" and without removing its' dependencies?

I run KDE on a regular Ubuntu install, since I'm not too keen on Kubuntu itself. I mostly prefer KDE apps except for a few specific ones, such as the Network Manager and Update Manager.

But I dislike GKSU itself. The biggest reason is because it's just so horribly disruptive; with KDESU, if it pops up, I can finish doing what I'm currently doing, and then get to it. With GKSU, it's like a metaphorical kick in the pants, just completely derailing my line of thought. While some folks may like that in-your-face attitude of it, I'm not one of them.

First, I tried removing GKSU through apt-get. Except...it has a fair number of dependencies it'd take, including Update-Manager. Now, mind you, Update Manager isn't so vital to me that I'd have major issues living without it, since it doesn't do anything that "apt-get update" doesn't, but it's a nice convenience, so I'm searching for alternatives.

My next thought was a bit extreme, so I haven't implemented it yet, but it seems sound in theory. Which would be to make a link to the KDESU program named as the GKSU program, so things calling on it are automatically sent to KDESU. However, I could see syntax problems potentially getting in the way, so before I try it, I'd like to see if there isn't anything else I could do.

The reason I'm wanting something global is because, while looking through my KDE menu, I saw that some programs, like Update-Manager, don't seem to specifically have a GKSU prefix; they just call on it whenever they're run, leading me to think that between that and that it gets removed when you try to uninstall GKSU, it's hardcoded. So something which just routed all GKSU calls to KDESU would be smashing.

---

### Post by rahearn on 2008-04-16
Try running gksu-properties from the command line and setting grab mode to disable.  That might be the behavior you're looking for.

---

### Post by roachk71 on 2008-04-16
Thanks for that bit of advice. I've been wondering whether or not that behavior could be configured, as well. :KS

---

### Post by aysiu on 2008-04-16
Couldn't you symlink *gksu* to *kdesu*? After all, *gksudo* is just a symlink to *gksu*.

---

### Post by roachk71 on 2008-04-16
Not sure if this would work too well, but I'd probably edit my .bash_profile, placing an alias directive near the beginning. I've done this in DSL, and it worked wonders.

Ex.: [I]alias gksu=kdesu
       alias gksudo=kdesu

[/I]etc.

---

### Post by Igtenio on 2008-04-16
I did what rehearn suggested, and that's exactly what I was looking to disable. I figured it was just a part of GKSU you had to deal with, but with it turned off, I don't have an issue with GKSU staying.

Thanks.

---

