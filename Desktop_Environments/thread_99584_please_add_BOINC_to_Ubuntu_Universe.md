---
title: "please add BOINC to Ubuntu Universe"
date: 2005-12-05
forum: Desktop Environments
---

### Post by ChrisC on 2005-12-05
Hello all -

I would love to be able to run a pure synaptic/apt/deb Ubuntu system, with all apps installed from the official Ubuntu archives.  Life is just so much easier that way.

BOINC is one of the very few programs that I can't install that way.  Either I have to compile it:

   [http://boinc.berkeley.edu/compile.php](http://boinc.berkeley.edu/compile.php)

or I have to add a non-Ubuntu archive:

   [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org)

Searching the forums here, someone else asked this and the reply was to add it to:

   [https://wiki.ubuntu.com/UniverseCandidates](https://wiki.ubuntu.com/UniverseCandidates)

Alas, I just spent 20 minutes getting my login here to work (stale, password resets, etc.) and I just don't want to plow into another 20 minutes of climbing the Wiki acct creation / login / editing learning curve (possibly with failure waiting for me at the end of it all).

Can someone either add it there, or tell me that it's already been done and I'm missing it, or that there's a "better" archive than the one above?  Thanks!

---

### Post by ChrisC on 2005-12-07
Drat.

---

### Post by ChrisC on 2005-12-08
OK, so lacking a response,  I tried adding to my sources.list :

   deb [http://pkg-boinc.alioth.debian.org/](http://pkg-boinc.alioth.debian.org/) ./

and Synaptic bitched on startup with "Couldn't stat source package list".  I NOW know that it just does that the first time you add a source (right?), but didn't figure that out before the next step.  I did some more searching and was led to try:

   deb [http://pkg-boinc.alioth.debian.org/debian](http://pkg-boinc.alioth.debian.org/debian) sarge main

which I then loaded into Synaptic and then downloaded and installed boinc-client.  It seems to have installed OK.  I had to go past the "not authorized" package warnings.

However, boinc-manager was not installed.  According to [http://wiki.debian.org/BOINC](http://wiki.debian.org/BOINC) , it "is not available for DebianSarge because of a missing build dependency (wxWidgets 2.6)."  That warning was added to that wiki page on Nov. 5th, so I guess I'm hoping that it's not true anymore and there's a workaround.  There is an option to run boinc_cmd in terminal mode, but it looks impossibly complex for me.

Now, I'm teetering right on the edge of my abilities here ... not sure of the pitfalls of messing with a Debian Sarge package in Ubuntu, not sure if I should try to pursue the wxWidgets problem, not sure if should be on this path at all.  I DO know that I want to get this computer to work SO BAD.

Can someone please help me get BOINC going on Breezy?  Surely I can't be the only one to want to do this on Ubuntu.

---

### Post by RAOF on 2005-12-08
You could use instead the testing (Etch) or unstable (Sid) repositories.  I'd suggetst the Sid ones:

deb     [http://pkg-boinc.alioth.debian.org/debian](http://pkg-boinc.alioth.debian.org/debian) unstable main non-free
deb-src [http://pkg-boinc.alioth.debian.org/debian](http://pkg-boinc.alioth.debian.org/debian) unstable main non-free

Uninstall your current client first, then add the above to your sources.list, and install the client from there.

---

### Post by ChrisC on 2005-12-08
I bumped the repository entry up from "stable" to "testing", and indeed boinc-manager is now listed.  However, after marking boinc-client and boinc-manager for installation, I promptly received these warnings:

  Depends: libcurl3 (>=7.15.0-1) but 7.14.0-2ubuntu1.1 is to be installed
  Depends: libidn11 (>=0.5.18 ) but 0.5.13-1.0 is to be installed
  Depends: libssl0.9.8  but it is not installable
  Depends: libstdc++6 (>=4.0.2) but 4.0.1-4ubuntu9 is to be installed
  Depends: lsb-base (>=3.0-6) but 3.0-1ubuntu8 is to be installed

Which all sounds serious enough that I'm not about to try to upgrade all of these on my plain vanilla Ubuntu system and possibly break everything in sight.

Has anyone ignored these warnings and found that it worked anyway?  libssl being "not installable" sounds serious to me.  Anyway, it's all far over my head, which takes me back to the thread title:  please add BOINC to Ubuntu Universe :)

---

### Post by RAOF on 2005-12-09
You should try the "unstable" repositories before you give up.  True to wierd naming dynamics, "unstable" is more likely to be stable than "testing".  Plus, Ubuntu is based upon a (sort-of recent) snapshot of "unstable", so it's more likely to work with "unstable" than "testing".

In fact, I think that one of the better ways of getting one of the Masters of the Universe to put BOINC in Universe is to ask, and say that the "unstable" packages work ;)

Edit: upon checking, it seems that the packages from the "unstable" repository should work on Breezy.

Edit again:  I have successfully installed boinc-client & boinc-manager from the unstable repository.  This is actually on Dapper, so it's not guaranteed that it'll work on Breezy too, but it looks like the dependencies are satisfied by Breezy libs.

---

### Post by holomate on 2005-12-09
[QUOTE=RAOF]You could use instead the testing (Etch) or unstable (Sid) repositories.  I'd suggetst the Sid ones:

deb     [http://pkg-boinc.alioth.debian.org/debian](http://pkg-boinc.alioth.debian.org/debian) unstable main non-free
deb-src [http://pkg-boinc.alioth.debian.org/debian](http://pkg-boinc.alioth.debian.org/debian) unstable main non-free
[/QUOTE]

Assuming these are the unstable reps, then I too receive the messages already described. This was the same problem I encounted while trying to compile source, the libraries are unavilable under breezy? (complete n00b... or at least enough of one to not understand this)

---

### Post by ChrisC on 2005-12-09
RAOF, thanks for the advice, but I tried it in unstable mode and got the same warning as I described in my previous post.  Are you saying that if I just blow past the warnings (without upgrading any of the dependencies) it'll all work out OK?

---

### Post by RAOF on 2005-12-11
Aaah, sorry.  I haven't booted into my Breezy install for some time.  It works on Dapper, though ;)

You won't be able to push through those messages.  They're errors, not warnings; you won't be able to install whatever it is that is depending on those packages.

---

### Post by Limulus on 2005-12-12
If you use:

>  deb [http://pkg-boinc.alioth.debian.org/debian/](http://pkg-boinc.alioth.debian.org/debian/) unstable non-free
deb [http://pkg-boinc.alioth.debian.org/debian/](http://pkg-boinc.alioth.debian.org/debian/) stable main
in Breezy, you'll get boinc-client (5.2.5-1sarge2) and boinc-manager (4.72-2)

Please see [http://ubuntuforums.org/showthread.php?t=96930](http://ubuntuforums.org/showthread.php?t=96930) (ChrisC posted in that thread and I've been putting my notes there)

---

### Post by Limulus on 2005-12-12
[QUOTE=ChrisC]Searching the forums here, someone else asked this and the reply was to add it to:

   [https://wiki.ubuntu.com/UniverseCandidates](https://wiki.ubuntu.com/UniverseCandidates)

Alas, I just spent 20 minutes getting my login here to work (stale, password resets, etc.) and I just don't want to plow into another 20 minutes of climbing the Wiki acct creation / login / editing learning curve (possibly with failure waiting for me at the end of it all).

Can someone either add it there, or tell me that it's already been done and I'm missing it, or that there's a "better" archive than the one above?  Thanks![/QUOTE]
I added it the other day, BTW :)

---

### Post by ChrisC on 2005-12-12
And he's right, it works!  Thanks, Limulus.

I mind using non-apt installer scripts a lot more than I mind going to an unstable or even experimental version of software.  It's still managed within the apt world ...

---

### Post by Limulus on 2005-12-13
**Update:**
```
deb http://pkg-boinc.alioth.debian.org/ubuntu/ breezy universe
```
in Breezy will get you boinc-client (5.2.13a-1ubuntu1) and boinc-manager (5.2.13a-1ubuntu1)

More details on [http://ubuntuforums.org/showthread.php?t=96930](http://ubuntuforums.org/showthread.php?t=96930)

---

