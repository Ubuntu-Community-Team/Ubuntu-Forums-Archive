---
title: "Ubuntu free software"
date: 2009-10-27
forum: Desktop Environments
---

### Post by sk8trf on 2009-10-27
ubuntu free software, i just installed ubuntu 9.10 RC on my computer i still have no internet access on it and none of my free software can be downloaded for some reason. it cant be because of the internet because i also have it on a laptop and i have the same problem. Im thinking maybe its because its just the RC?

---

### Post by earthpigg on 2009-10-27
nah, it's probably because everyone and their mother is downloading/installing the RC right now, so the ***primary*** ubuntu servers are slammed.

system -> admin -> software sources -> download from -> other -> select best server

will test all the server mirrors (copies of the primary server) and find the fastest one from your specific location at this particular moment in time. two weeks before and after any new ubuntu release, it's not a horrible idea to run that once every day or two before trying to install anything from the repos.

---

### Post by sk8trf on 2009-10-27
so when you do go to applications>ubuntu software center, it runs that software off mirrors online, see i thought it was kind of like gentoo with portage, it was all right there on your system and you had no need for the internet at all

---

### Post by earthpigg on 2009-10-27
be sure to let us know if you still have problems after doing that :D

---

### Post by sk8trf on 2009-10-27
well i dont think its cause the server because when i click on it to install it just says not available in current data, it says that on both my computer which has no internet yet(but thats another thread lol) and my laptop which has working internet. The ubuntu software center isnt like portage in gentoo where all the software is right there on your system rather than having to retrieve it from the internet?

---

### Post by JBAlaska on 2009-10-27
There are some basic packages available on the LiveCD, like build-essential so if you have to compile a driver to access the Internet you can.

You need to have "Installable from CD-ROM/DVD" checked in software sources, then with the LiveCD in your drive you can use the term to apt-get install.

But yes for major packages you will have to have inet access

---

