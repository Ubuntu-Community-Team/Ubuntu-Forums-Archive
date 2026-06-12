---
title: "Cluster / synchronize multiple motherboards with ubuntu desktop"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by iammeagain on 2007-05-14
:?: So i am totally naive when it comes to clusters netwroking etc. So more than one computer i get confused on what is possible and how to do it. 
What i want to do is take two motherboards and make them work together in one case. Its a project for school. The best case senario would be able to use Ubuntu, but my teacher said somethign about doing this with Free BSD. :-k Does anyone have any idea about how to go about this? thanx for any help at all

---

### Post by tutomlin on 2007-06-11
As far as I know you can't really just hook up two motherboards and have them work in sync.  First of all there are the logistic problems: ports on the back of the case for only one motherboard, psu only has one motherborad power connector, etc.  Second you need a way to connect the two boards for data transfer, and as far as I know networking is really the only way to do this.

I'd recommend just getting 2 cases and stripping one of them down to the bare essentials.  If you can get it to network boot  you can even skip the hard drive and cdrom. (i've never tried this but it is frequently recommended for very large clusters where tons of disk drives would be expensive)

Before you get into anything I'd check out:
the clustermonkey website: [http://www.clustermonkey.net/](http://www.clustermonkey.net/)
the OpenMosix website: [http://openmosix.sourceforge.net/](http://openmosix.sourceforge.net/)
and the Kerrighed website: [http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)

and try to get an idea of what you actually want to do with the system. (if you want to run your own code you'd be looking at the clustermonkey stuff, if you want simple process migration for load sharing you want the openmosix/kerrrighed stuff)

nb: OpenMosix is currently sitting on the 2.4 kernel series which does not play well with the x-server that comes with ubuntu.  Kerrighed does not have this problem but neither one is SMP safe so you can't use dual core processors (as far as I know)

Hope that helps

Tucker

---

### Post by iammeagain on 2007-07-21
yea, but i don't have the time to look into it now. The school year ran out before i had time to even start the project. I may try something similar in the future. Thanx for the help.

---

