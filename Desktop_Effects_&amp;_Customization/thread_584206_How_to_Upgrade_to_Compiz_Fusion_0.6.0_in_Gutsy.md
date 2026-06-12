---
title: "How to Upgrade to Compiz Fusion 0.6.0 in Gutsy?"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by Quickdood on 2007-10-20
Hello,

I am wondering if it is possible to upgrade to compiz fusion 0.6.0 in gutsy.  I was using that version when I was using feisty and I don't like being back at 0.5.2.  Anyone know of a tutorial or can write down a few steps  on how to upgrade fusion in gutsy?  or have any advice at all?

Thanks!

---

### Post by qamelian on 2007-10-20
If you are using Gutsy, you already have compiz-fusion 0.6. Below is the result of running apt-cache policy compiz in the terminal of a freshly installed Gutsy with no third party repos installed.

```
compiz:
  Installed: 1:0.6.0+git20071008-0ubuntu1
  Candidate: 1:0.6.0+git20071008-0ubuntu1
  Version table:
 *** 1:0.6.0+git20071008-0ubuntu1 0
        500 http://ca.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by Quickdood on 2007-10-20
Your right I must have been using an SVN version. I guess Trevino's version was a little ahead of 0.6.0.  Anyone know how to get the SVN version?

---

### Post by forteller on 2007-10-21
But how can that be? Compiz Fusion 0.6.0 was [released today](http://smspillaz.wordpress.com/2007/10/21/compiz-fusion-060-is-released/).

---

### Post by qamelian on 2007-10-21
> **forteller said:**
> But how can that be? Compiz Fusion 0.6.0 was [released today]("http://smspillaz.wordpress.com/2007/10/21/compiz-fusion-060-is-released/").

If you check the output in my post above, you'll see that the version in the Gutsy repos is a snapshot of the git repositoiry for the project as of October 8, 2007. So, it isn't a final release, but it is close enough for most users.

---

### Post by jham on 2007-10-21
> **qamelian said:**
> If you are using Gutsy, you already have compiz-fusion 0.6. Below is the result of running apt-cache policy compiz in the terminal of a freshly installed Gutsy with no third party repos installed.

```
compiz:
  Installed: 1:0.6.0+git20071008-0ubuntu1
  Candidate: 1:0.6.0+git20071008-0ubuntu1
  Version table:
 *** 1:0.6.0+git20071008-0ubuntu1 0
        500 http://ca.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status

```

That's version 0.6.0 of **compiz**, not **compiz-fusion**. Compiz is now at version 0.6.2 and compiz-fusion is at version 0.6.0. Gutsy ships with compiz-fusion 0.5.2.

---

### Post by Hobo2021 on 2007-10-21
If understand correctly, compiz-fusion is essentially comprised of the compiz-fusion plugins...which are plugins for compiz, which is why you'd get 0.6.0 version for compiz, and 0.5.2 for compiz-fusion.

---

### Post by missingno on 2007-10-21
I just found out about the new Compiz Fusion release about 30 minutes after getting [whichever version ships with Gutsy] working, and headed straight here to find out how to update. It sounds like there's a lot of impressive new features, I can't wait to see.

---

### Post by Hobo2021 on 2007-10-21
I was successful in compiling it (at least I think I was), you'll need to install the dev packages for compiz, if you get the error

```

ranlib /usr/local/lib/compiz/libanimation.a
ranlib: could not create temporary file whilst writing archive: No more archived files

```

Just make the /usr/local/lib/compiz directory, that worked for me. I also recommend using checkinstall to make a deb package for it for easier uninstallation/upgrade.


Edit: Also, I forgot the exact wording of the error, but if you get an error about not finding "text.h" when installing the plugins-extra, (well first make sure you installed plugins main) copy text.h from /compiz-fusion-plugins-main-0.6.0/include source  to  /usr/include/compiz

---

### Post by hotweiss on 2007-10-24
Did anyone find a debian package?

---

### Post by nikoPSK on 2007-10-25
this worked for me [http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html]("http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html")

hope it helps!:)

---

### Post by QuacoreZX on 2007-10-30
I tried the guide, it ended up messing up Compiz entirely for me, even after doing make uninstalls from source and reinstalling from synaptic.  x_x

---

### Post by Sephoroth on 2007-10-30
Ditto.

---

### Post by Zorael on 2007-10-30
My fingers tremble and I want to try it out because I'm weak like that, but I keep telling myself to be content with my stable, normal C-F.

I tried three different install scripts that grab the git sources, but all of them fail with unintelligible errors at some point in the process.

wtb backport .deb :(

---

### Post by nikoPSK on 2007-10-30
screw compiz 0.6 for the moment guys. It's terribly slow. Even on my 1 gig RAM 2 GHz processor and nvidia GeForce 7200 GTX card. Just wait for an official .deb

---

