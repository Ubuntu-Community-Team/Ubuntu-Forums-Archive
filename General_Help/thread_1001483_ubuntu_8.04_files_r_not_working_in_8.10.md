---
title: "ubuntu 8.04 files r not working in 8.10"
date: 2008-12-04
forum: General Help
---

### Post by sreedhar001 on 2008-12-04
ubuntu 8.04  files r not working for 8.10 

 all files corrupted  plzz reply mee
 i installed skype in 8.04 
 same setup installed in 8.10 saying coruppted .. plzz tell me the reason adnd tell me  ansswer plzzzz

---

### Post by sreedhar001 on 2008-12-04
saying wrong architeure   wat  shall i do

---

### Post by SIGTERMer on 2008-12-04
are you sure the files are corrupted and it's not the permissions/owner issues?

---

### Post by sreedhar001 on 2008-12-04
say that  wrong  architecutee 1 386.deb

---

### Post by DieB on 2008-12-04
pls give more information - try to describe what u did and  what your purpose was.

we will then might be able to help u.

---

### Post by sreedhar001 on 2008-12-04
> **DieB said:**
> pls give more information - try to describe what u did and  what your purpose was.

we will then might be able to help u.



ok sir 
 here the details..

last two days i used  ubuntu8.04  .i iinsatlled all softwares like skype.gyachi.all.    .deb  files

 today  i insatlled  ubuntu 8.10  x64  amd.386

so that that when i trying to instlled those files.deb files saying   wrong architecture "386"  

 this is the error i getting 

 help me out sir

---

### Post by sreedhar001 on 2008-12-04
is that  8.04  files  will work in 8.10 ????//////

---

### Post by SIGTERMer on 2008-12-04
try downloading software packages that matche your operating system. if your using a 64bit edition (8.10), and you used to use a 32bit edition (8.04), then there might be compatibility issues.
try re-installing those packages using apt-get or synaptic. or download the packages from the web (but make sure that they match your operating systems type i.e. x64)
i hope this helps :)

---

### Post by DieB on 2008-12-04
you mean downloaded *.deb-files? 
well it pretty much seems like u changed the basis of your system (from classical 32-bit to 64-bit) - so u will have to get the 64-bit-versiones.

hope that might be a clue

---

### Post by m.srivathsan on 2008-12-04
No Fears,

Google for "getlibs", download and install it.  It installs 32-bit (thunk) libraries.  Then install Skype using the following cmd:

dpkg -i --force-all <skype>.deb

You should be able run Skype smoothly after this.

But I am having a problem.  My Webcam worked under Hardy Heron (8.04) but is not working after I upgraded to 8.10 and all the latest updates / patches.  So be forewarned.

Cheers,
Watson

---

### Post by m.srivathsan on 2008-12-04
Oops,

I think I missed one more step.  I guess you need to run getlibs against the executable (Skype in our case) to download the dependent librarires.  Anyways, the instructions are there in the "getlibs" page itself

Cheers,
Watson

---

