---
title: "kdelibs4 or kdelibs4c2a??"
date: 2006-08-29
forum: Desktop Environments
---

### Post by wombat20 on 2006-08-29
I've been trying to install the software for the Cherry Cymotion Master Linux keyboard, but the Package Installer says I need kdelibs4.  I appear to have kdelibs4c2a, but kdelibs4 is not an option according to Synaptic.

How can I get around this?

---

### Post by mlind on 2006-08-29
I guess it's a one of these weird package naming conventions. install kdelibs4c2a, that's package you're after.
Package **kdelibs** additionally provides kdelibs4c2a, kdelibs-bin and kdelibs-data.

---

### Post by wombat20 on 2006-08-29
Yes, but the package is already installed and not recognised by the installer - can I make an alias to it or something and if so, how?

---

### Post by mlind on 2006-08-29
> **wombat20 said:**
> Yes, but the package is already installed and not recognised by the installer - can I make an alias to it or something and if so, how?

Did you try installing **kdelibs** package also?

---

### Post by wombat20 on 2006-08-30
Oh, didn't know that I could.  It isn't listed in Synaptic.  What do I need to do to get it?  Would apt-get be easier?

---

### Post by mlind on 2006-08-30
> **wombat20 said:**
> Oh, didn't know that I could.  It isn't listed in Synaptic.  What do I need to do to get it?  Would apt-get be easier?

It's listed on synaptic for me. You can install it with apt-get/aptitude too if you wish.

(You're not building the package manually are you? Then you would need to install -dev packages too. If not then ignore this.)

---

### Post by wombat20 on 2006-08-30
I wonder why it's not listed for me... could I be missing some repos?  Surely it would be in the same one as kdelibs4c2a?  I'll have a fiddle around and check when I get home.

No, I'm not building the package, it came on the disc.

Thanks for your help on this.

---

### Post by mlind on 2006-08-30
I'm not sure.. Package is on **main** and **dapper-security** repositories

```

$ apt-cache policy kdelibs
kdelibs:
  Installed: (none)
  Candidate: 4:3.5.2-0ubuntu18.1
  Version table:
     4:3.5.2-0ubuntu18.1 0
        500 http://security.ubuntu.com dapper-security/main Packages
     4:3.5.2-0ubuntu18 0
        500 http://archive.ubuntu.com dapper/main Packages

```

---

### Post by wombat20 on 2006-08-30
Well, I have much the same, actually...

```

:~$ apt-cache policy kdelibs
kdelibs:
  Installed: 4:3.5.2-0ubuntu18.1
  Candidate: 4:3.5.2-0ubuntu18.1
  Version table:
 *** 4:3.5.2-0ubuntu18.1 0
        500 http://security.ubuntu.com dapper-security/main Packages
        100 /var/lib/dpkg/status
     4:3.5.2-0ubuntu18 0
        500 http://archive.ubuntu.com dapper/main Packages

```

Which all looks fine, but the package specifically wants **kdelibs4**, which I can't find anywhere.  I could install kdelibs4-dev or kdelibs4-doc, but i'm guessing they won't do.   Doing the same with kdelibs4 gives me (none) and (none).

Is there a way I can force it to install or trick it into using the base **kdelibs** library?

---

### Post by mlind on 2006-08-30
> **wombat20 said:**
> 
Which all looks fine, but the package specifically wants **kdelibs4**, which I can't find anywhere.  I could install kdelibs4-dev or kdelibs4-doc, but i'm guessing they won't do.   Doing the same with kdelibs4 gives me (none) and (none).

Is there a way I can force it to install or trick it into using the base **kdelibs** library?

kdelibs is basically the same than kdelibs4 package
[http://packages.debian.org/stable/libs/kdelibs4](http://packages.debian.org/stable/libs/kdelibs4) (check changelog link at the bottom of the page, you'll notice actual name of the package).

Try to install kdelibs package. It should do it.
(btw. Is this package you're installing for Dapper?)

---

### Post by wombat20 on 2006-08-30
I already have kdelibs installed for some reason it's not recognised as being basically the same thing as kdelibs4.

Is there some clever way I can rename/alias/trick it into using it?

The package is for Debian - thought it was the closest thing, the rest are rpm

Thanks again for your continued help!  :)

---

### Post by mlind on 2006-08-30
Can you provide a URL where I could check out this package, or is it from some media like install CD? What's the name of the package?
It's possible to create meta package (that depends on kdelibs package) to possibly satisfy the install requirements, but I'd rather rebuild it.

---

### Post by wombat20 on 2006-08-30
Yep, have attached it to this message.

---

### Post by mlind on 2006-08-30
I'm sorry to say that there's no easy way to get that package installed on Dapper :(
There's at least 8 libraries which have been obsoleted (or removed), so this package would need a rebuild or some sort of very ugly hack which would probably make things extremely unstable.

I suggest to either
[LIST]
[*]Find a binary package which is compiled for Dapper (from vendor's website)
[*]Find a source package and compile it on Dapper (from vendor's website)
[*]Try out [kmflcomp]("http://packages.debian.org/unstable/utils/kmflcomp") which should provide same functionality as keyman
[/LIST]

---

### Post by wombat20 on 2006-08-31
Okay, well thanks anyway.

I wrote to Cherry asking for a Dapper package and referencing this thread, so we'll see what happens.

kmflcomp doesn't want to install as libkmflcomp seems to need libc6 which I already have, but it doesn't see it... oh well.

---

### Post by wombat20 on 2006-09-07
It appears the source code is available here, but I've yet to delve into Linux programming, despite being a Windows programmer, so I'm not sure what to do with it.

[http://support.cherry.de/download/KeyMan_source.tar.gz](http://support.cherry.de/download/KeyMan_source.tar.gz)

---

### Post by mlind on 2006-09-07
> **wombat20 said:**
> It appears the source code is available here, but I've yet to delve into Linux programming, despite being a Windows programmer, so I'm not sure what to do with it.

[http://support.cherry.de/download/KeyMan_source.tar.gz](http://support.cherry.de/download/KeyMan_source.tar.gz)

It looks like this tarball already contains Debian packaging information, but requires some additional build dependencies. I'll upload the packages for you once those are ready.

---

### Post by mlind on 2006-09-07
This package looks more than fishy to me, so have some caution when you're installing it.. I didn't test it myself, but it seemed to build fine. I'd test it on a safe environment first.

[http://www.freefilehoster.com/uploads/1157654080keyman-1.0.0_dapper.tar.gz](http://www.freefilehoster.com/uploads/1157654080keyman-1.0.0_dapper.tar.gz)

---

### Post by wombat20 on 2006-09-07
Thanks very much for going to the effort of sorting this out.  Would like to learn how to do this one day.

But how do you mean, fishy?  Buggy?  Possibly unstable?  Likely to break things?  Containing malicious code?  The package installer seems to like it, but requires libglade and libxerces - looks fine, but I haven't installed it yet.  I guess I should make a testbed in a separate partition.

The source came straight from the Cherry.de website, although I'd guess it's just a port from windows.

---

### Post by mlind on 2006-09-08
> **wombat20 said:**
> Thanks very much for going to the effort of sorting this out.  Would like to learn how to do this one day.

But how do you mean, fishy?  Buggy?  Possibly unstable?  Likely to break things?  Containing malicious code?  The package installer seems to like it, but requires libglade and libxerces - looks fine, but I haven't installed it yet.  I guess I should make a testbed in a separate partition.

The source came straight from the Cherry.de website, although I'd guess it's just a port from windows.

Package didn't contain copyright or license information, and I doubt it's been widely tested. It didn't compile on Dapper before I gave +rw permissions to all files (some were read-only), and quite many build dependencies needed to be added to get the package compile.

Just my 2 cents. Package is probably fine and I'm just being paranoid :)

---

