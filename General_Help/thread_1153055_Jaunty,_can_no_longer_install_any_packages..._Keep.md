---
title: "Jaunty, can no longer install any packages... Keep getting this error::"
date: 2009-05-08
forum: General Help
---

### Post by DJSchmidty on 2009-05-08
dpg: parse error, in file '/var/lib/dpkg/available' near line 26942 package 'powermgmt-base':
'Depends' field, reference to 'udev' : version contains ')'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A Package failed to install. Trying to recover:
dpg: parse error, in file '/var/lib/dpkg/available' near line 26942 package 'powermgmt-base':
'Depends' field, reference to 'udev' : version contains ')'


(Sorry, don't know how to but that in 'code' on this forum yet..)

Anyways, so yea i'm trying to install thunderbird, wine, everything straight from the repos, and this keeps happening...  Any suggestions??

---

### Post by BslBryan on 2009-05-08
Hello, DJSchmidty. :-)

Can you tell us what command you're trying to run before you get that message?

---

### Post by DJSchmidty on 2009-05-08
Ok, well... i'm not really running a command in a terminal or anything, i'm just trying to add/remove programs... then once I click the check mark on the program i want and hit apply, it will download the files, but when it goes to install, then I get that error message, and after a warning window will pop saying that the program did NOT install...

(Thanx for the super quick reply btw!!!)

---

### Post by BslBryan on 2009-05-08
Hmmm...  Maybe it's postfix.  

First, could you close all open windows, run this:
```
sudo dpkg-reconfigure -a 
```

and then try to add the program again?

Also, no problem.  :-)

---

### Post by DJSchmidty on 2009-05-08
Hmm, did that but in the terminal, after I enter my password, i get this:

dpkg-query: parse error, in file '/var/lib/dpkg/available' near line 26942 package 'powermgmt-base':
'Depends' field, reference to 'udev' : version contains ')'
/usr/sbin/dpkg-reconfigure: acl is not installed

---

### Post by kanikilu on 2009-05-08
Try this from a terminal:
```
sudo dpkg --clear-avail; sudo apt-get update
```

*Make sure Synaptic is not running when you do this, or you'll get an error about not being able to lock the administration directory.

---

### Post by DJSchmidty on 2009-05-08
and just after I typed that, the update manager popped up saying there are updates, and when I hit 'install updates', I get an error window says 'update is complete' "not all changes and updates succeeded" when I hit the details, the terminal window underneath shows the same errors in my first post....

Ohhhhh boy....

---

### Post by BslBryan on 2009-05-08
This is very strange.  

Maybe a postfix error?

Before I give instructions, what do you think, kanikilu?

---

### Post by DJSchmidty on 2009-05-08
Wow!! Did the trick!!

Super thanks to you brotha!
Was able to both update my machine with all 4 recent updates, and install wine! Gonna try a few more programs too, thinderbird etc...

Yep, that works too!! Super, thanks again!:guitar:

(BTW, what caused this??)

---

### Post by BslBryan on 2009-05-08
It was caused by your cache being corrupted, but the commands we gave fix that. :-)

What ended up working for you, out of curiosity, and how did you manage to make it work, as I thought both of our commands were spitting out errors?

---

### Post by DJSchmidty on 2009-05-08
inputting this one

sudo dpkg --clear-avail; sudo apt-get update

in the terminal fixed it right away..
Thanx again, I hope either of you can help me with my next question, which i'm going to post right now...

---

