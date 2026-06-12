---
title: "What's a backport?"
date: 2009-02-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by daveh551 on 2009-02-20
I am a computer veteran but a linux newbie.

Pardon the naive question, but what's a backport, and what goes into it, and, specifically, is it kernel specific?

I've installed Intrepid on my Dell Inspiron 1720, and the sound doesn't work. I've googled the problem and found dozens of responses that are all over the map, many of them contradictory.  One specifically specifically applied to the Inspiron 1720 and said the simplest solution was to install the Dell linux-backport-module, and gave a link to dell's support sites.  Well, the link is no good, but I found the following under their ubuntu/gutsy directory:

linux-backports-modules-2.6.22-14-generic_2.6.22-14.53_i386.deb 

Recognizing that it's from 2 versions before mine - my uname -r shows 2.6.27-11-generic - can I still use it, is it likely to work, and, most importantly, will it harm anything?

On a related note, the only thing they have on the dell site under the intrepid directory is a 1.8G reinstallation iso dated January 30.  I downloaded and burned it, but when I booted it, it came up with a warning that it would restore your entire computer to factory defaults and wipe out all data on your disk.  Since I have this computer set up to triple boot (Vista, XP, and Ubuntu) on several different partitions, and have a lot of work and personal data stored on it, wiping it out was not something I even wanted to risk.  Is there something I can do to restore that image just to my Ubuntu partition?

Thanks.

---

### Post by bapoumba on 2009-02-20
A backport is a repository where packages for version n+1 are "backported" to version n (dependencies versions and other things are adapted). You better stick to a tutorial for your own release.
In your case, you would be looking for Jaunty packages backported to Intrepid. Gusty is 3 release before yours.

If you look for answers on the internet, it is a good idea to place your release in the keywords.

Edit: Moved to Dell support. You may find better help here :)

---

