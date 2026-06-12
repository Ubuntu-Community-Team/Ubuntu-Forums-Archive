---
title: "Can't install ZSNES"
date: 2007-07-14
forum: Gaming &amp; Leisure
---

### Post by NEMESIS0744 on 2007-07-14
I'm trying to install ZSNES, So, I open a a Terminal type "sudo apt-get install update"- Succesful, but the when I type"sudo apt-get install zsnes" , it gives me this 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zsnes has no installation candidate
Please Help!!!!!

---

### Post by rye_ on 2007-07-14
you can only install applications in the manner you described above that are available from the repositories.

I believe zsnes is not.

try getdeb.net for additional debian packages, including zsnes.

Ryan

---

### Post by BoyOfDestiny on 2007-07-14
> **NEMESIS0744 said:**
> I'm trying to install ZSNES, So, I open a a Terminal type "sudo apt-get install update"- Succesful, but the when I type"sudo apt-get install zsnes" , it gives me this 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zsnes has no installation candidate
Please Help!!!!!

What version of Ubuntu?

Anyway, try going to system -> administration -> Software sources. Make sure all the little repositories are checked (especially the one with the word universe)

at that point you can try
sudo apt-get update
sudo apt-get install zsnes

Or if you prefer gui methods, zsnes should be Add/Remove or you can go to system -> Adminstration -> Synaptic Package Manager and install it.

That should do it :)

Or go with what the above poster suggested and just download the getdeb package (it's for feisty)

[http://www.getdeb.net/app.php?name=ZSNES](http://www.getdeb.net/app.php?name=ZSNES)

The plus is the newest version is already in the repos for the next Ubuntu release.

---

### Post by NEMESIS0744 on 2007-07-14
I tried the deb package but it is the wrong architecture, I need the package for PowerPC.

---

### Post by BoyOfDestiny on 2007-07-14
> **NEMESIS0744 said:**
> I tried the deb package but it is the wrong architecture, I need the package for PowerPC.

I see... Unfortunately, zsnes doesn't work on the PPC architecture. Perhaps they will resolve this, as zsnes has some x86 specific asm, in time it may be converted to portable C or whatever. 

Try snes9x instead I guess... Although I haven't run it in ages, it's a good choice I think.

---

### Post by NEMESIS0744 on 2007-07-15
Thats what I am currently running but has a Distorted sound that bugs me.

---

### Post by DoktorSeven on 2007-07-15
> **NEMESIS0744 said:**
> Thats what I am currently running but has a Distorted sound that bugs me.

I've always had issues like this with snes9x.  Just a bug in the program, I suppose.  

You'll just have to hope for a PPC port of zsnes, unfortunately.

---

