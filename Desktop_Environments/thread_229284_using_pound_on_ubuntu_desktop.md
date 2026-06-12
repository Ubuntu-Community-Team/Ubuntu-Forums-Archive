---
title: "using pound on ubuntu desktop"
date: 2006-08-04
forum: Desktop Environments
---

### Post by teh_chris on 2006-08-04
i am trying to get pound ([http://www.apsis.ch/pound](http://www.apsis.ch/pound)) to work on my ubuntu desktop.

in case this sounds retarded (running a reverse proxy on a desktop distro) i'll get to the long story about why i decided to do this after i post my questions (in order of easiest to do to the hardest):

1) is there a package for pound already made for ubuntu that i can use?  i was not able to locate a page with packages listed like they are on the debian website, if such a page exists i will gladly consult it from now on.

2) i tried installing the most recent debian package for pound and got an error that libssl-1.9.7 is not installed, however if i look in /usr/lib i have libssl-1.9.8.so there.  is there a way i can either run both libraries at the same time, or pass the library path to 1.9.8.so to the .deb installer?

3) i tried compiling from source and i got all sorts of compiler errors about not being able to create executables.  if anyone is interested i can post the log.

why would anyone do something so complicated:

i am using vmware server to run a few servers off one machine instead of on a handful old junk PC's.  the vmware console requires an Xserver and the only distro they support other than redhat is ubuntu.

this is all run out of my house, strictly low end (dynamicDNS on a cable modem, very little traffic).  i have my emulated windows 2003 server all set up and hosting IIS and pop3 mail.

now i want to add a LAMP machine to the mix, only i have just 1 dynamically assigned IP and only one port 80.  this is where pound comes in to play.  it is a pretty simple and light weight way to host multiple web servers on one IP and port.

so that is my story and my problem, thanks in advance for any help or guidance anyone can offer.

---

### Post by teh_chris on 2006-08-04
bump

---

