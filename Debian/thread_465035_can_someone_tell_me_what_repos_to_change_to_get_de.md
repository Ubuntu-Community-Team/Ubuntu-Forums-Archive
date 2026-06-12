---
title: "can someone tell me what repos to change to get debian unstable from etch?"
date: 2007-06-05
forum: Debian
---

### Post by syxbit on 2007-06-05
i've tried searching everywhere, and from what i understand, there are no downloads for either unstable or testing.
i'd like a permanently unstable OS, as that way, it'll just keep getting upgraded forever.
it annoys me that when a new program comes out (like thunderbird 2.0) you have to wait till the next ubuntu to get it (obviously, i can often either compile, or find a .deb of it, and i don't mind doing this for a few progs, i don't want to have to do it all the time)

so, i have etch on my system, can somene tell me the REPO's i need to get unstable?
thanks a lot

---

### Post by plb on 2007-06-05
just edit /etc/apt/sources.list and change etch to unstable...it should look something like this in the end:

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) unstable main contrib non-free
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) unstable main contrib non-free

after that just apt-get dist-upgrade

---

### Post by syxbit on 2007-06-05
i only need those 2 things in myy sources.list for everything to upgrade?

---

### Post by Bachstelze on 2007-06-05
How is your sources.list like, currently ?

---

### Post by syxbit on 2007-06-05
deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib
deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) unstable main
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) unstable main


it started with stable, so i just renamed to unstable

should i delete it all, and put in the repos plb mentioned?

---

### Post by Pobega on 2007-06-05
Just putting "unstable" in place of Etch should be enough. If you're going to use Sid though, I advise you to install apt-listbugs.

---

### Post by syxbit on 2007-06-05
i do want the newest stuff
i'd heard that unstable wasn't too buggy
testing is safer i hear.
i'm guessing i'd just replace stable/unstable with "testing"

---

### Post by tturrisi on 2007-06-05
You are better off backing up your data & reinstalling using the net-install iso, which will give you the option to install stable, testing or unstable.  Else you may end up with broken packages and other issues doing a dist-upgrade.  Besides, you'd have a cleaner system that uses less disk space.

---

### Post by Pobega on 2007-06-06
> **tturrisi said:**
> You are better off backing up your data & reinstalling using the net-install iso, which will give you the option to install stable, testing or unstable.  Else you may end up with broken packages and other issues doing a dist-upgrade.  Besides, you'd have a cleaner system that uses less disk space.

Upgrading a Debian system isn't as risky as updating Ubuntu, since the packages are closer in timespan to each other.

I'd advise you to dist-upgrade into testing first though, and then into unstable. The transition should be much easier that way.

---

### Post by juxtaposed on 2007-06-06
> I'd advise you to dist-upgrade into testing first though, and then into unstable. The transition should be much easier that way.

I just dist-upgraded from etch to sid an hour or so ago and it worked fine.

---

### Post by FuturePilot on 2007-06-06
How do you get testing? I don't want to go all the way to sid.

---

### Post by Pobega on 2007-06-07
> **FuturePilot said:**
> How do you get testing? I don't want to go all the way to sid.

Just use testing in your sources.list instead of stable, and run (As root or through sudo) *apt-get update && apt-get dist-upgrade*.

---

### Post by syxbit on 2007-06-08
i just installed fron the net install version, but was never given the option to choose either sid or lenny
unless i missed something?

---

### Post by plb on 2007-06-08
Don't worry about it, just do as I said earlier in the post...trust me..I've been using Debian for a couple of years now and have always done it that way...no need to install sid via cd. Upgrading will work like a charm.

---

### Post by deanlinkous on 2007-06-09
testing builds are here
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

