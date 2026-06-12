---
title: "If a package in the Hardy repos isn't in the Jaunty repos will it still work?"
date: 2009-06-02
forum: General Help
---

### Post by DiscipleRayne on 2009-06-02
I'm going to be upgrading to Intrepid and Jaunty eventually, and I was wondering... I have no choice, where I live, but to connect to the internet via dial up. I use AOL, because I've yet to find another dial up provider that has as far as I can tell 24 hour session limits, and allows you to hold a continuous connection without ever nuking your account. I use penggy to connect to AOL. Penggy is not in the Jaunty repositories, does this mean it doesn't work with Jaunty? Or that they just didn't put it on the repositories? I'm not sure how that works! Thanks in advance!

---

### Post by Sef on 2009-06-02
> Penggy is not in the Jaunty repositories, does this mean it doesn't work with Jaunty? Or that they just didn't put it on the repositories?

It would not be advisible to try to download from Hardy because likely something will break and it would bring down your system.   The didn't put it in for any number of reasons which I will not hazard a guess on.

---

### Post by anaconda on 2009-06-02
The safest way is to compile it yourself

ANd if you want you can also try to install it froom hardy:s repositories.

Installing from older versions (hardy) repositories is not as dangerous as installing from newer repositories... 

eg. if you would install something from 9.10: s repositories you might get lots of dependencies from 9.10 and then your system would be a mixture of 9.04 and 9.10 And if you would get any problems they would be wery difficult to fix (you would propably have to upgrade completely to 9.10) 
But installing from OLDER repositories is not as dangerous, because if you encounter problems you can uninstall that program and "upgrade" to 9.04.. Where you already are.. And it wouldn't install older versions of dependencies you already have....

---

### Post by DiscipleRayne on 2009-06-02
Thanks a lot guys. I don't mean to sound like an idiot, using AOL and all, but I'm a developer and where I live I have absolutely no choice but dialup. Since I'm a developer I have frequent, long downloads. On other services, sessions limits around around 4 hours and they usually suspend you for staying online more than 17 hours on average in a 30 day period. AOL has none of those, so it's the only service I can use. Until I find another service like it, and I don't think I ever will, I'll have to stick with AOL until I move or something. If Penggy ends up not working with Jaunty, I'll have to stick with 8.04 until 2011, or switch back to windows and that might just break my heart. :(. Hopefully if I end up having to stick with 8.04 until '11, by then I'll have moved somewhere I can get wireless internet. I'm trying to be optimistic but I'm honestly horrified at the fact that Penggy might not work with newer versions of Ubuntu.

I'm thinking they might not have added it after Hardy, just because it's so old, and not many people uses it. That's possible right?

---

### Post by dcstar on 2009-06-02
> **DiscipleRayne said:**
> I'm going to be upgrading to Intrepid and Jaunty eventually, and I was wondering... I have no choice, where I live, but to connect to the internet via dial up. I use AOL, because I've yet to find another dial up provider that has as far as I can tell 24 hour session limits, and allows you to hold a continuous connection without ever nuking your account. I use penggy to connect to AOL. Penggy is not in the Jaunty repositories, does this mean it doesn't work with Jaunty? Or that they just didn't put it on the repositories? I'm not sure how that works! Thanks in advance!

I have used multiple packages from earlier releases without any problems **provided** they install without any dependency issues.

The only real way to find out is to go to this site, download the .deb and try to install it - you will soon find out if it installs and then you can try and run it:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by stuart.reinke on 2009-06-02
A little off topic, but have you looked at Wild Blue for your internet access? It's high speed via satellite. Supposed to work everywhere.

---

### Post by DiscipleRayne on 2009-06-02
> **stuart.reinke said:**
> A little off topic, but have you looked at Wild Blue for your internet access? It's high speed via satellite. Supposed to work everywhere.

Sure have. For one, I don't think they support Linux, for any various stupid reasons. And two, as of now, I can't really afford it, but I'll find out if they support Linux, and if so, that's certainly something I'll try to work out.

---

