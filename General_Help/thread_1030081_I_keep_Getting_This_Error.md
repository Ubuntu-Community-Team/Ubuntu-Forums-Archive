---
title: "I keep Getting This Error"
date: 2009-01-04
forum: General Help
---

### Post by overratedx on 2009-01-04
Hello everyone, I just installed Ubuntu a few weeks ago so I'm still getting used to it. Every time I try to open 'Synaptic Package Manager' I get this error: 
'E: dpkg was interrupted. you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.'
I was wondering if anyone could help me fix this so I could use Synaptic to install the programs I'm looking for? :confused:

---

### Post by adult swim on 2009-01-04
go to a terminal, applications>accessories>terminal and enter in 
```
sudo dpkg --configure -a
```
type in your password and hit enter.  this error is caused usually by an update being stopped and not finishing for some reason.  you should now be able to use synaptic again.

---

### Post by overratedx on 2009-01-04
Ok, I did that now a bunch of stuff has popped up, and I'm kinda confused.
I also tried opening Synaptic again and the error popped up again.
Would you mind explaining how to fix it?
Sorry for the hassel.

---

### Post by adult swim on 2009-01-04
you need to close down synaptic package manager while doing this.

did you do it like this?

from a terminal type in 
```
sudo dpkg --configure -a
```
hit enter
type in your password
hit enter
stuff should appear now.  copy that and paste it here!

---

### Post by overratedx on 2009-01-04
This time when I typed it in all it said was
'Setting up java-common (0.28ubuntu3) ...'

---

### Post by adult swim on 2009-01-04
if that didnt return any errors then you should be all set.  does synaptic work?

---

### Post by overratedx on 2009-01-04
Yes it does!
Thank-you for your kindness. =)

---

