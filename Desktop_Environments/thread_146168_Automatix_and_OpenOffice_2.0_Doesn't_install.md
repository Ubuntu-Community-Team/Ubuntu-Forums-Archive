---
title: "Automatix and OpenOffice 2.0: Doesn't install"
date: 2006-03-17
forum: Desktop Environments
---

### Post by arthur on 2006-03-17
And the worst part:
I first got rid of the default 1.9.29 version of OO.

Tried installing using Automatix,
tried using apt-get,
tried using synaptic

All I get is:
[B]E: /var/cache/apt/archives/openoffice.org2-core_2.0.1-0breezy1_i386.deb: failed on buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/openoffice.org2-writer_2.0.1-0breezy1_i386.deb: failed on buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/openoffice.org2-calc_2.0.1-0breezy1_i386.deb: failed on buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/openoffice.org2-base_2.0.1-0breezy1_i386.deb: failed on buffer_write(fd) (10, ret=-1)[/B]

---

### Post by arthur on 2006-03-18
Additional problems. 
Using
[B]
[TERMINAL CONSOLE][/B]
Issue command:
apt-get remove openoffice*

Error message *(not a literal English translation):*
Maybe you would like to execute `apt-get -f install' to correct it:
The following packets have unresolved dependencies:
  python-uno: Depends: openoffice.org2-core (> 2.0.1) but will not be installed
E: Unresolved dependencies. Try 'apt-get -f install' with no packets (or specify a solution).

Have also tried

dpkg --configure -a

and

apt-get clean,

with no results whatsoever (no change, no error message)

*********************************************************
Using
**[SYNAPTIC]**
I marked both packages for complete removal:

Error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I executed that command, to no avail (nothing happened).

NOTHING WORKS, I can find no way in the world to remove openoffice...math and python-uno, so 

NO OPEN OFFICE 1.9.29
NO OPEN OFFICE 2.0.1

Can anybody help?:cry:

---

### Post by arthur on 2006-03-18
Somebody else mentions the problem here:
[http://nightfox.wordpress.com/tag/freeopen-source/](http://nightfox.wordpress.com/tag/freeopen-source/)

but I can figure out how to reproduce their instructions.

---

### Post by arthur on 2006-03-18
Well, I did a complete re-install of 5.10 (my partition layout was way off ...)
Now I am back with a fresh new one, have used Automatix again (I like challenges), and everything works like a charm.

My theory?
Available free space in my PREVIOUS "/" partition: 100 MB.
Would that be the culprit?
I guess so :p 

Do blame my clumsiness, but I do hope this might help other people in similar situations.

---

### Post by MakubeX on 2006-05-31
[QUOTE=arthur]Somebody else mentions the problem here:
[http://nightfox.wordpress.com/tag/freeopen-source/](http://nightfox.wordpress.com/tag/freeopen-source/)

but I can figure out how to reproduce their instructions.[/QUOTE]

Just saw the trackback recently.. (Btw, that's my blog.)

Are you pertaining to this entry?

[http://nightfox.wordpress.com/2006/02/04/doing-things-over-and-over-again-is-over/](http://nightfox.wordpress.com/2006/02/04/doing-things-over-and-over-again-is-over/)

Never tried Automatix. (it's just too automatic for me) heehee

---

