---
title: "Removing flightgearsdl"
date: 2007-11-13
forum: Gaming &amp; Leisure
---

### Post by Smbrandes on 2007-11-13
Greetings unto all,

   I ran into a bizarre problem that is most difficult. Essentially, i managed to install a flightgearsdl.rpm while trying to sort out some other dependency problems. In any event , the flightgearsdl.rpm led to a new problem, which appears unsolvable (an openal failure of some sort), so I thought to install flight gear through synaptic, which is probably what should have been done the first time, however upon attempt to remove the flightgearsdl package or whatever you call it through the use of the terminal or any other method I can think of, which mind you is not too many as this whole linux thing is still a bit new to me, it failed.  In any event, the linux structure is still a little hazy. I think in windows I would have rather easily dispatched such a problem but that is simply a matter of experience there.  LInux is still yet a bit more fiddly, but  generally in a good way.
   So synaptic produces this result E: /var/cache/apt/archives/flightgear_0.9.10-2ubuntu1_i386.deb: trying to overwrite `/usr/share/man/man1/fgfs.1.gz', which is also in package flightgearsdl

So I am totally, stumped. This has been a frustrating app to try to get run. Hope someone has some solution that would be useful.

---

### Post by Smbrandes on 2007-11-13
Hello,

   First find the offensive package using " sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_list" which will put a list of packages in your home folder. 
  Second "sudo apt-get remove xxxx" where xxxx is the package.

---

