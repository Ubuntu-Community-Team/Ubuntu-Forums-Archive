---
title: "Req. Kaffeine 0.7.1 &amp; amaroK 1.3.6"
date: 2005-11-26
forum: Closed Requests
---

### Post by noigeaR on 2005-11-26
Kaffeine 0.7.1 fixes some crashes and improve general stability over version 0.7 in Breezy. Kaffeine 0.7.1-1.2ubuntu1 is in Dapper right now. 
amaroK also has a newer version in Dapper, 1.3.6 instead of the "half-official" 1.3.5 from the Kubuntu homepage and the quite old and buggy 1.3.1 in breezy.

It would be very nice for us Kubuntu users to have this backported if possible, thanks :KS

---

### Post by donar73 on 2005-11-26
I'm not a **K**ubuntu user ;) , but I'd also like to see Amarok 1.3.6 in the backports.

---

### Post by drolyk on 2005-11-26
+1 here

P.S.: I want it to be backported becouse I`ve got problems with amarok from dapper. I think my problem related to missing version of some libs...

---

### Post by abandoned_hussam on 2005-11-27
The kaffeine 0.7.1 from breezy backport would really help. The kaffeine 0.7.0 in breezy crashes when you exit or open a second file. 
All these crashes were fixed in dapper, so this backport would really help a lot people.

---

### Post by thumper on 2005-11-28
Just to keep this at the top of the list.

Another me too for both kaffeine and amarok.

---

### Post by strikeforce on 2005-11-29
I have an ubuntu desktop so I'll try it later tonight from a chroot I'll make up of kubuntu-breezy.

Obviously jdong will beat me to it :)

---

### Post by strikeforce on 2005-11-29
This is what I get for amarok
> 
: Build-Depends dependency for amarok cannot be satisfied because no available versions of package kdelibs4-dev can satisfy version requirements
I couldn't resolve build dependencies by myself. I'll drop you to a shell
(backports)marc@ubuntu:~/ubp-compile-temp/amarok-1.3.6$ exit
OK, continuing the build...
***Building...
dpkg-buildpackage: source package is amarok
dpkg-buildpackage: source version is 2:1.3.6-1ubuntu3
dpkg-buildpackage: source changed by Jonathan Riddell <jriddell@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: kdelibs4-dev (>= 4:3.5-rc2) libtunepimp2-dev (>= 0.3.0-2.1)
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Build FAILED... 768
Do you want to rebuild w/o dep checks, or get a shell? [Y/s/n] ?s
(backports)marc@ubuntu:~/ubp-compile-temp/amarok-1.3.6$ apt-cache show kdelibs4-dev | grep Version
Version: 4:3.4.3-0ubuntu1
(backports)marc@ubuntu:~/ubp-compile-temp/amarok-1.3.6$ apt-cache show libtunepimp2-dev | grep Version
Version: 0.3.0-2ubuntu7


Kaffeine bar one hickup built fine and I'm unsure about the running of it. Due to being in a chroot.

---

### Post by abandoned_hussam on 2005-11-30
Any news on kaffeine 0.7.1 backport?
OK, I backported kaffeine 0.7.1 
If anybody wants it or knows where I can place them, please contact me.

---

### Post by noigeaR on 2005-12-05
at least kaffeine 0.7.1 seems to build fine for some people so how about an official backport?

---

### Post by SlugO on 2005-12-06
So what's going on with backporting Amarok anyways? Nobody interested?
This is a **very** popular application and versions above 1.3.0 have been out there for ages... >_<

So why isn't anything happening? :confused:

---

### Post by noigeaR on 2005-12-07
amaroK 1.3.7 is now available from kubuntu.org
[http://kubuntu.org/announcements/amarok-1.3.7.php](http://kubuntu.org/announcements/amarok-1.3.7.php)

---

### Post by abandoned_hussam on 2005-12-10
Ok, we have amarok 1.3.7

I already backported kaffeine 0.7.1 for my personal use. 
But we have kaffeine 0.7.1 officially backported. This would help many people and it fixed all the crashed from breezy's kaffeine 0.7.0.

---

### Post by abandoned_hussam on 2005-12-17
Sorry for double posting but is it still possible to get an official kaffeine 0.7.1 backport?
I've already done my own backport for this and it fixes tons of crashes from breezy's 0.7.0.
Thanks is advance.

---

### Post by jdong on 2006-01-02
Both have been sent to James.

---

### Post by noigeaR on 2006-01-02
thanks a lot! :D 

i think the new kaffeine version will make many users happy! the one currently in breezy is so buggy, it shouldn't be in a stable release in the first place...

---

### Post by MichaëlVD on 2006-01-03
Did we just get another amaroK update? The "about amaroK" still says 1.3.7, but I'm quite sure I just 'aptgraded' it. What happened?

---

### Post by jdong on 2006-01-03
Yes, Backports developer Martin Meridith (Mez) worked with KUbuntu's Jonathan Riddel to loosen build deps such that an amaroK backport of 1.3.7 could be done.

---

