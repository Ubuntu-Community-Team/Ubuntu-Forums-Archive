---
title: "Lxde"
date: 2008-05-26
forum: Desktop Environments
---

### Post by Kowalski_GT-R on 2008-05-26
I added the apt repository in my sources list but I couldn't download/install over a 7.10 mini install system.

Any experiences yet?
Memory usage?

thanks,

Andre

---

### Post by joninkrakow on 2008-05-27
You do know that they recently changed the repo for this, don't you? I discovered this myself just the other day. I changed the lines in the sources.list to:
```

deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main

```

And I was able to install everything and it works.

As I said, I'm suggesting this, because that was what worked for me. :-)

-Jon

---

### Post by Kowalski_GT-R on 2008-05-27
that's exactly what I added to my sources list.

I have no time now, but if this thread starts to collect the experiences of others so far, I will post my hardware config and try to find a solution here...

thanks,

Andre

---

### Post by joninkrakow on 2008-05-27
[QUOTE=Kowalski_GT-R;5046685over a 7.10 mini install system.
[/QUOTE]

I just now caught the 7.10 part. You know, I don't remember when I "fixed" my repo links, but I had to upgrade to 8.04 before I got my install of LXDE to "take." Also, it's a complete Xubuntu install, not a mini. Oh, and a i386 install, not 64bit. 

As it goes, however, it's a bit lighter than xfce on my very ancient laptop. It certainly feels faster, but it's going to take some getting used to for me. I've kind of grown accustomed to icewm and xfce, and LXDE is a completely different beast. Some things I've grown accustomed to finding in certain places aren't there (configuring, etc.) However, I'm quite happy with its performance over xfce. Oh, one small bit is that I can't seem to change the window widgets (titlebar, button locations--I prefer them on the left, like on a Mac, not the right--I'm left-handed, and I just seems more natural to have them there--I remember upgrading to OSX and being delighted that _everything_ was on the left) ;-) 

So, other than some niggles, I can quite imagine LXDE being quite popular, especially on older systems.

-Jon

---

### Post by Kowalski_GT-R on 2008-05-27
sorry for being unprecise, I added the repos for the correct version of Ubuntu. Gutsy repos have been also set up, i used those.

thanks for the comments, i'm looking forward to triyng it out. Ubuntulite has been delayed for a while now...

cheers,

Andre

---

