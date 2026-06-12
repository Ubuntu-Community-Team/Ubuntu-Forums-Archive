---
title: "why is Ubuntu sagemath so old?"
date: 2010-03-05
forum: Education &amp; Science
---

### Post by memilanuk on 2010-03-05
Hello all,

I'm kinda curious about something... the current version of sagemath is something like 4.3.x... vs. the installed version that is in the Ubuntu repositories which is more like 3.0.x.  Even if a person downloads the 'current' version of sagemath separately, there appears to be an installed c++ lib that is out of date and needs to be downloaded separately and linked in.

I'm not very 'up' on the process for poking (politely) the package maintainers to get them to update packages in a timely manner... any suggestions?  Is that big of a lag (3.0.5 - mid 2008 - to current 4.3.3) normally considered acceptable in Ubuntu?

Monte

---

### Post by nateperson on 2010-03-05
Short answer, for why its that version and not a newer, is because that's the version that is in the Debian repositories, and Ubuntu is based off of Debian.  

Long answer has to do with the process of getting packages into Debian repositories and updating them and dependencies and their packages and updating them and politics and testing, that I don't even want to try to understand...

It is apparently in the [works]("http://wiki.sagemath.org/debian/sage-4.0.x-in-experimental"), so there is a plan to update it, but no clue on their time table...  and as you can see, the responsibility of updating it to a later version is with Sagemath, rather than Debian....

---

### Post by memilanuk on 2010-03-05
Well, that would be one explanation why sagemath is so unusually old for an Ubuntu package.  

Given that if you download the Virtualbox image of Sage for Windows... it's actually running *Ubuntu* inside the image... it doesn't seem like it should be something that would be necessary to wait on Debian to get the cork out to update things...

Since it (sage) does appear to be tied to Debian for the time being... I wonder if  there would be any possibility of getting it moved to the *volatile* repository used for things that being hopelessly out of date would negatively impact the functionality.

That there are plans inside Debian to 'update' Sage to 4.0.2 sometime in the near future... when the upstream package is already @ 4.3.x... isn't as much of an improvement as I'd hoped for.

Thanks for the info, though.

Monte

---

### Post by ratcheer on 2010-03-05
I am running Sage 4.3 on 9.10, and I don't recall having to install any special libraries for it. I did get it directly from the Sage web site, though.

Tim

---

### Post by memilanuk on 2010-03-05
Dang.  Took me a bit to re-find it...

[http://ubuntuforums.org/showthread.php?t=1343590&](http://ubuntuforums.org/showthread.php?t=1343590&)

---

### Post by haraldschilly on 2010-03-06
> **nateperson said:**
> and as you can see, the responsibility of updating it to a later version is with Sagemath, rather than Debian....

Recently there was once again [a discussion about that]("http://groups.google.com/group/sage-devel/browse_thread/thread/29ee9e1d4efdeda2") and actually we want to get "sagemath" removed from ubuntu's repository for more than one year ...

---

### Post by Adam Redwine on 2010-03-06
> **ratcheer said:**
> I am running Sage 4.3 on 9.10, and I don't recall having to install any special libraries for it. I did get it directly from the Sage web site, though.

Tim


I've been getting my netbook up to speed on ubuntu in the last few weeks.  I've had sagemath on my desktop since before you could get the package from synaptic so I was happy to see it as an option now.

Sadly, when I installed it with apt-get, almost nothing worked!  I saw the notice about the other library and tried half-heartedly for a few minutes to fix it.  After a while though, I just downloaded the source code from the website and recompiled.  Much to my delight, everything (even 3d graphing) worked right off the bat.

As a non-techie generally (or at least as a reluctant techie) I highly recommend that people in charge refrain from posting packages that don't work.  If it works on most Debian installs, fine, but if it doesn't generally work on Ubuntu, let people know that they can get a newer version of the package elsewhere.

---

### Post by memilanuk on 2010-03-06
The bit that slays me is that apparently sagemath has never made it into mainstream Debian, if I'm reading that other thread right.  Looks like it's only in unstable/sid, and a 2+ year old version at that (talk about an oxymoron!).  

At least the fact that it's being discussed on the sage-devel list gives me a little hope...

Again... given that the Windows 'version' is literally Ubuntu 9.10 (I looked in the /etc/apt/sources.list file) running as a virtual appliance... it would seem that a lot of the work _may_ already be done - something I didn't see mentioned at all on the devel list?

---

### Post by haraldschilly on 2010-03-09
> **memilanuk said:**
> ... something I didn't see mentioned at all on the devel list?

I'm not sure what you mean. If our build farm doesn't crash, we release ubuntu 9.10 binaries for 32+64 bit for every sage release here: [http://sagemath.org/download-linux.html](http://sagemath.org/download-linux.html) ;)

Extract it anywhere where you have write access and start it as your own user (i.e. no sudo!). It only creates files in $HOME/.sage/ i.e. you can extract it system wide for all users, too. Building from source should work just like that, except that it takes some hours ... :popcorn:

But that has nothing to do with packaging for debian/ubuntu, because this requires to split up the whole well tested thing in many small components, reuse existing packages that are available (i.e. maxima) and make sure that they work together.

Especially, we still don't know how to remove an outdated package from the ubuntu repository and the sagemath package itself should have been gone for more than a year...

---

### Post by nateperson on 2010-03-09
> we want to get "sagemath" removed from ubuntu's repository for more than one year ...
Well, the difficulty ya'll are encountering is only bit surprising...  :)  From what I've heard about assorted processes. 

Maybe as a stop gap of sorts, it would be easier to could get the package description changed with a disclaimer and/or qualifier till ya'll are able to get it removed or replace it with updated ones? Either way, good luck in your efforts.

---

### Post by memilanuk on 2010-03-09
> **haraldschilly said:**
> I'm not sure what you mean.
At this point, I'm not sure either.  I think I'd been doing my browsing/downloading on waaaay too little sleep... 

> Extract it anywhere where you have write access and start it as your own user (i.e. no sudo!). It only creates files in $HOME/.sage/ i.e. you can extract it system wide for all users, too. 

Ya know... I'd swear I did that already.  In fact, I deleted the same package by the same name to do it again, just out of morbid curiosity.  This time... after it did the bit about coding system paths or whatever... it came right up with zero problems (so far) and I have the notebook interface running in a browser window as I type this... ?  Definitely not the experience I had several days ago, and as I said, I'd downloaded the same file - i.e. same name - but from a different mirror?  

Weird, but it's working now.



> Especially, we still don't know how to remove an outdated package from the ubuntu repository and the sagemath package itself should have been gone for more than a year...

Dunno.  Seems like you are caught in a loop... Ubuntu references Debian unstable, Debian doesn't sound too concerned about it because it *is* unstable... unless you can put some pressure on the Debian package maintainer for sagemath, I don't see how else you would be able to divorce yourself from the whole Debian -> Ubuntu relationship.

---

### Post by haraldschilly on 2010-03-10
> **nateperson said:**
> Maybe as a stop gap of sorts, it would be easier to could get the package description changed with a disclaimer and/or qualifier ...
ok, and how to do that? where can somebody submit a remove request? nobody of us has any insight where to go to do anything with the ubuntu packages...

if you know how to do it, please go ahead ;)

---

### Post by nateperson on 2010-03-10
I would, if I could, but I don't even know who to contact to ask who to contact, other than to maybe post a question in one of the development area's.    I'm just a punter and a fan, who's just starting to wade into scientific computing and linux...

---

### Post by PC_load_letter on 2010-03-21
Sorry to resurrect an old thread (a week old, yay) but IMHO I think there is no point in keeping sagemath in the repos. At the rate SAGE is evolving, and changing, it will be a headache just sorting out the dependencies. 

The downloaded latest version of SAGE from the home page includes everything it needs and it's up to date, ok it's huge (400+MB), but I think it'll more productive to d/l it given the way and the rate SAGE is developing. And of course it still works perfectly. You just download the compressed file, uncompress it (explodes to 1.6GB), then launch SAGE by running the script inside, that's it!  

And given that there are now Ubuntu & Debian specific versions of SAGE, I think there is nothing major to gain by keeping it in the repos.

---

