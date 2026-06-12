---
title: "Gnome-Do 0.8.0 and the Dell Mini 9"
date: 2009-01-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by emnii on 2009-01-30
I'm having a hell of a time getting Gnome-Do 0.8.0 to install on my Dell Mini 9 running Dell Ubuntu Netbook Remix. I've followed the steps listed in the Gnome-Do wiki for installing on Hardy and it just keeps installing gnome-do version 0.4.0.1.

Then I tried building it from the source. After endless headaches trying to get the dependencies sorted out, it craps out on ./configure with an error indicating a missing makefile.in.in and I'm not quite sure what that means. If I run make, it'll start but then craps out with another error.

Has anyone with a Mini 9 gotten Gnome-Do 0.8.0 running and have any pointers?

---

### Post by ugm6hr on 2009-01-30
Haven't done this, but 0.6 is in the PPA for lpia architecture:
[http://ppa.launchpad.net/do-core/ubuntu/dists/hardy/main/binary-lpia/Packages](http://ppa.launchpad.net/do-core/ubuntu/dists/hardy/main/binary-lpia/Packages)

Is this the How-to you are using?
[http://do.davebsd.com/wiki/index.php?title=Installing_Do#8.04_.28Hardy.29](http://do.davebsd.com/wiki/index.php?title=Installing_Do#8.04_.28Hardy.29)

Looks like 0.8 is only available on Intrepid:
[http://ppa.launchpad.net/do-core/ubuntu/pool/main/g/gnome-do/](http://ppa.launchpad.net/do-core/ubuntu/pool/main/g/gnome-do/)

I'm afraid the dependency issue may be due to the version of Gnome installed in Hardy.

The list of dependencies for 0.8: [http://ppa.launchpad.net/do-core/ubuntu/dists/intrepid/main/binary-lpia/Packages](http://ppa.launchpad.net/do-core/ubuntu/dists/intrepid/main/binary-lpia/Packages)

These are not available in the main repos for Hardy:
libglib2.0-cil (>= 2.12.1)
libgtk2.0-0 (>= 2.14.1)
libgtk2.0-cil (>= 2.12.1)
(possibly others too - I got bored of checking the dependencies!)

---

### Post by emnii on 2009-01-31
Yes, that was the How-to I was following. If I get all the dependencies sorted out, would it work? Or would I still be stuck because of the older version of gnome?

---

### Post by kpmoore on 2009-02-28
I'm having the exact same issue. Has anyone found a way to resolve it?

---

### Post by armandh on 2009-02-28
install 8.04.1 or 8.10

I had trouble getting stuff to work with the "dell ubuntu light"
NO trouble with out of the box Ubuntu on the mini 9 save the one CL to get sound and remapping the "full screen" to the "windows" button. of course you have to get your own flash and [www.medibuntu.org](www.medibuntu.org)

add compiz manager and the cube rocks & rolls.

---

### Post by sirebral on 2009-02-28
If a dependency is 8.10 and you don't have it then you then you can't run it.  The new kernel in 8.10 adds some features to Ubuntu.

Plain and simple.

I'll run a test install and tell you what version I get.

---

### Post by sirebral on 2009-02-28
This made me stop:
```
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  gnome-do gnome-do-plugins libnotify0.4-cil 
```

Looks like all you can get without using 8.10 is Gnome-Do version 0.6.1.0.

---

