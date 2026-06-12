---
title: "Getting cinelerra to work on breezy?"
date: 2006-05-15
forum: Desktop Environments
---

### Post by zoiks on 2006-05-15
Hi...

I hope this is the right forum to post this...

I've followed the instructions on 
[http://cvs.cinelerra.org/getting_cinelerra.html#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.html#ubuntu)

to install cinelerra.  Yet, when I try to launch cinelerra from a terminal, I get simply "Illegal instruction" (after the GNU message) and it quits with no further messages or errors.  I am on a PIII runing Breezy, and I installed the i686 version of cinelerra.

I checked the logs in /var/log/ and found nothing.  Also, there's no --verbose or --debug options, so I can't tell what's going on.

I guess it could be a missing dependency, but I can't find a list of which libs to check for.

Any help or pointers would be greatly appreciated.
Thanks!

---

### Post by Sef on 2006-05-15
In the directions for cinelerra, it says this:

> Ubuntu packages

    Current instructions are for Ubuntu 5.10 (Breezy), 5.04 (Hoary) is not supported anymore because it would require backporting of too many dependancies. 

Looks like you will have to upgrade to Dapper to get it installed.

---

### Post by zoiks on 2006-05-15
The quote suggests the instructions should work on Breezy, which is what I'm running.   It didn't say I will have to wait for Dapper...

---

### Post by zoiks on 2006-05-16
Well, I got it to work.  I installed cinelerra 2.0 from this location

[http://socrates.if.usp.br/~liquid/pacotes/](http://socrates.if.usp.br/~liquid/pacotes/)

which I had found on some forum here at ubuntuforums.org.  In any event, after uninstalling cinelerra from the previous instructions, I installed this .deb file for i386 without a hitch, and cinelerra seems to run like a champ.  Still isn't recognizing some file formats but that may just mean I need to install codecs.  I tried some stuff like blurring video and using the "burning TV" effect, and they seemed to work great, though a bit slow to crunch on a PIII/750.

---

