---
title: "Lenny goes Stable this year"
date: 2008-02-10
forum: Debian
---

### Post by p_quarles on 2008-02-10
[http://lwn.net/Articles/267722/](http://lwn.net/Articles/267722/)
> Early April 2008
  Freeze of the essential toolchain

Mid of June 2008
  Freeze of the non-essential toolchain and all libraries
    The "non-essential toolchain" means things like debhelper, cdbs 
    and a big chunk of other things usually needed to produce binary
    packages.

Mid of July 2008
  Full freeze
    Please don't wait with uploads for the last day before the freeze,
    thanks.

September 2008
  Release lenny!
It's already pretty stable at this point, of course, but it will soon be official.

---

### Post by steveneddy on 2008-02-10
woo-hoo!

:roll:

---

### Post by p_quarles on 2008-02-10
> **steveneddy said:**
> woo-hoo!

:roll:
Well, it's exciting to me!

<finds a corner and cries self to sleep>

---

### Post by Whiffle on 2008-02-11
Sweet.  I'll get to choose between hardy, whatever is after hardy, and lenny.  If the one after hardy is anything like gutsy has been... i'll be using lenny...or hardy, or maybe even feisty still if they both fail to impress.  Or maybe I won't upgrade at all...I've got everything I want on this thing right now.

---

### Post by dptxp on 2008-02-11
I am waiting, waiting, and waiting for my first pure Debian. It is going to be Lenny.

---

### Post by kerry_s on 2008-02-11
lenny's pretty busy to, there's been updates everyday. :)

---

### Post by yabbadabbadont on 2008-02-11
So Lenny is the current "testing" version?  If you wanted to *always* use the current testing version of Debian, what would you put in your sources.lst?  Just replace "lenny" with "testing"?

Are there versions of cairo and libXft that have the new sub-pixel rendering patches for LCD monitors, or do you have to build them yourself?

---

### Post by kerry_s on 2008-02-11
> **yabbadabbadont said:**
> So Lenny is the current "testing" version?  If you wanted to *always* use the current testing version of Debian, what would you put in your sources.lst?  Just replace "lenny" with "testing"?

Are there versions of cairo and libXft that have the new sub-pixel rendering patches for LCD monitors, or do you have to build them yourself?

yeah, you could just change etch to lenny if you want to run a pure lenny. i run a mixed etch/lenny cause the etch kernels work better for me.

```

deb http://ftp.debian.org/debian/ etch main contrib non-free
deb http://ftp.debian.org/debian/ lenny main contrib non-free

deb http://security.debian.org/ etch/updates main contrib non-free
deb http://security.debian.org/ lenny/updates main contrib non-free

```

not sure on the font thing, heres the synaptic screen shots.

---

### Post by angryfirelord on 2008-02-11
> So Lenny is the current "testing" version? If you wanted to always use the current testing version of Debian, what would you put in your sources.lst? Just replace "lenny" with "testing"?
Yup. Just be careful when you upgrade and watch for any packages that might get removed.

> Are there versions of cairo and libXft that have the new sub-pixel rendering patches for LCD monitors, or do you have to build them yourself?
Depends, what version were those features introduced? You can see them here:

[http://www.debian.org/distrib/packages]("http://www.debian.org/distrib/packages")

---

### Post by notwen on 2008-02-11
currently running a lightweight gnome install on etch right now for my file server.  looking forward to lenny's stable release. =]

---

### Post by yabbadabbadont on 2008-02-11
@kerry_s and angryfirelord: Thanks for the info.

---

### Post by angryfirelord on 2008-02-11
> **yabbadabbadont said:**
> @kerry_s and angryfirelord: Thanks for the info.
Sure. :)

As far as Lenny's release schedule goes, one should never take that date seriously. Debian's releases are always delayed and I would be rather *shocked* if this one came out as they said. Not that being delayed is a bad thing (in fact, it's delayed for a good reason: bug fixing), but having an on-time Debian release is like having 3D Realms release Duke Nukem Forever. :)

---

### Post by odiseo77 on 2008-02-11
I'm using Lenny/Sid and except some xserver update which broke my 3D rendering (already fixed), I find it very stable. When it comes to Debian I'm always in the testing branch, so as soon as Lenny becomes stable I'll upgrade to testing :)

---

### Post by p_quarles on 2008-02-11
> **odiseo77 said:**
> I'm using Lenny/Sid and except some xserver update which broke my 3D rendering (already fixed), I find it very stable. When it comes to Debian I'm always in the testing branch, so as soon as Lenny becomes stable I'll upgrade to testing :)
Yeah, it's pretty bug free as it is. "Stable" for Debian has a different meaning than most destkop distros, hence the indeterminate development cycle.

I'll probably upgrade to the new Testing as well, and will leave Etch on my server until its end of life. So, Lenny going Stable actually means I won't be using it any more.

---

### Post by notwen on 2008-02-12
> **angryfirelord said:**
> Sure. :)

As far as Lenny's release schedule goes, one should never take that date seriously. Debian's releases are always delayed and I would be rather *shocked* if this one came out as they said. Not that being delayed is a bad thing (in fact, it's delayed for a good reason: bug fixing), but having an on-time Debian release is like having 3D Realms release Duke Nukem Forever. :)

LOL, so very true.  Most of these delays ensure the Debian release will be rock solid and normally that is the case. =]

---

### Post by voteforpedro36 on 2008-02-12
So will Etch be the new Sarge?

---

### Post by tturrisi on 2008-02-13
> **voteforpedro36 said:**
> So will Etch be the new Sarge?

No sarge is sarge, woody is woody, etch is etch, lenny is lenny.  The new testing will get a new name and sid is always sid.

---

### Post by angryfirelord on 2008-02-13
> **voteforpedro36 said:**
> So will Etch be the new Sarge?
When Lenny enters Stable, Etch will be moved into the Oldstable category and Sarge will be moved into the archives, where it will no longer receive any security updates. Then, a new name will be given to the testing branch and the cycle starts all over again.

---

### Post by mojoman on 2008-02-17
Good news, I suppose. I'm running Lenny now and it's rock solid. Still, I'm a bit surprised, it's not that long since Etch hit stable (or am I getting old and start losing perspective on time?). Anyway, in the end it'll be released according to the Debian schedule, i.e. when it's *ready* to be released. I think that's a pretty sound philosophy.

---

### Post by manmower on 2008-02-17
> **yabbadabbadont said:**
> Are there versions of cairo and libXft that have the new sub-pixel rendering patches for LCD monitors, or do you have to build them yourself?

No, unfortunately there are no such packages in Debian, not even in unstable. My guess is this has to do with the "freedom" of these patches still being contested.

I know I can't live without them. I wouldn't even consider using a distribution which doesn't provide them in some easy way anymore. :oops:

---

