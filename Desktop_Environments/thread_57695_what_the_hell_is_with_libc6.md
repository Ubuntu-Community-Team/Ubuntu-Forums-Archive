---
title: "what the hell is with libc6"
date: 2005-08-17
forum: Desktop Environments
---

### Post by enfact on 2005-08-17
I noticed so many problems on my system and now others as i look throught the forums with libc6. Many different programs need this, Ubuntu has their ubuntuized version and other program you may try to install wont install with their version. Now if you install backports and install the regular version, then more things start screwing up and eventually apt-get/synaptic goes insane and wants to uninstall basically tons of core libraries and parts whenever you want to install new software. Is this a well known issue? I'm hoping so, and if so are there any fixes to this. I really dont like (im not sure if its neccessary) ubuntu's custom versions of files. The main problem with installing software in linux (which's is linux's major problem desktop wise) right now is people using tons of different versions of libraries and versions, why not make it even more complicated...... I may be missing something but complicating the package system more seems to me to be going the opposite way of where linux needs to go.

Rant over.

---

### Post by az on 2005-08-17
Binary packages are made from source code.  The interface for all open source software is the source code. 

Libc6 is the library of C code that was used to build the binary package from the source.  If the package was not built for ubuntu, you cannot use that package, but you can compile it for yourself.  You probably can find itin the backports repository, which is what it is for.

---

### Post by enfact on 2005-08-17
my question was WHY do they use a custom libc6, especially because it is a widely used library... I would think its obvious that having a custom library of a base linux lib, especially for anything doing with C isnt the best idea. I understand how the packages work. I should correct myself thought, my problems were only with packages, whether it was through kynaptic/synaptic or downloading and dpkg'ing deb files no packages would get past this problem. Compiling programs worked much better.

Thank you much for taking the time to reply also :)

---

### Post by enfact on 2005-08-17
Also, for my problems is there any solutions you would suggest for getting the ubuntuized version installed for what programs need that and then regular libc6 for what programs require that and have them live happily ever after? I have seen errors from different programs stemming from this library, Should i reinstall both or one and how do i go about that safely?

---

### Post by az on 2005-08-17
Well, since libc6 is ever-changing.  You cannot say that everybody will always use this one version and never use anything else.  You cannot pick and chose what version you use, either.  You can only use one version on your system.  

Ubuntu tracks debian Unstable.  Whatever version of libc6 is being used at the time of the package fereze for release is what you will get.  That is why it is different from other debian packages made for other distributions.  Sarge was release after Hoary, and so it's libc6 is more recent.  Breezy will have a more recent version than sarge when it is released.

To not upgrade your libc6.  If you did, do not downgrade it.  That is all I have to say about that.


What does

sudo apt-get -f install 

tell you?  (post the result so that we can fix any problems you currently have)

---

