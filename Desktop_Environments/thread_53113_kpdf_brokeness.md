---
title: "kpdf brokeness?"
date: 2005-07-30
forum: Desktop Environments
---

### Post by kLy on 2005-07-30
Hi

Could someone verify this for me?

Please see if you can download and then open:

[http://ifarchive.org/if-archive/infocom/compilers/inform6/manuals/designers_manual_4.pdf](http://ifarchive.org/if-archive/infocom/compilers/inform6/manuals/designers_manual_4.pdf)

With me, it opens up a window where you can see all the pages, but they just have the big black "X" across all of them (like they were still busy being rendered). This goes on indefinitely. If I close kpdf, it does close, but there's still a process for it hogging up 100% of CPU. Can anyone verify this for me?

Certain files just seem to be buggered for me :( kghostview can view it (though it's not got the goodness of kpdf), and I've also got a gentoo kde 3.4.1 install with kpdf working with that file. So it shouldn't be a problem with kpdf 3.4.1?

thanks

---

### Post by SGC on 2005-07-30
I got the same thing with kpdf 3.4.2

---

### Post by GeneralZod on 2005-07-30
Verified here (3.4.0) with the exact same systems.  Please file a bug report at bugs.kde.org, including the URL - I'm sure the developers will like a nice, reproducable test case to play with :) Or does it look like this is a Kubuntu-specific bug...?

---

### Post by kLy on 2005-07-30
thanks guys!

I don't think it's an upstream or kpdf problem tho. Like I said, I tried it on a gentoo box and it worked perfectly. I wonder what could be broke?  :-? 

Perhaps one of the libraries that kpdf uses? That would perhaps explain why it happens with all the versions of kde we have here? I'll search bugs.kde.org as well as try xpdf 3.0 (which kpdf is based on afaik).

I'll file it on bugzilla.ubuntu.com too.

Thanks!

---

### Post by kLy on 2005-07-30
yip... works perfectly with xpdf too

---

