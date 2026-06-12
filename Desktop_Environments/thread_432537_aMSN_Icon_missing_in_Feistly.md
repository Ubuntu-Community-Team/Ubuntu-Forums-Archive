---
title: "aMSN Icon missing in Feistly"
date: 2007-05-04
forum: Desktop Environments
---

### Post by netsurfau on 2007-05-04
Before writing this I did try a search and amsn came up in a wide number of different forum
subjects in here so, posting in D/Top Environments seemed a good choice.


I went to the aMSN forums for help on this first but, they weren't able to help.
None of the "fixes" suggested worked.

Since upgrading to Feisty, the amsn icon that usually lives next to the clock (in top right
corner) has disappeared.  Was working fine until upgrade.  To make sure it would work
properly I re-installed amsn from the Applications \ Add/Remove installer, using the Ubuntu
configured version.  This has made no difference.

Any ideas.  I don't know where to go to contact the team who actually put the various 
packages in the "Add/Remove" together.

---

### Post by aysiu on 2007-05-04
File a bug report:
[https://bugs.launchpad.net/ubuntu/+source/amsn](https://bugs.launchpad.net/ubuntu/+source/amsn)

---

### Post by netsurfau on 2007-05-04
Have now filed a Bug Report & guess will wait to see result.  Doubt it will receive a very
high priority though.

In meantime if anyone finds a fix for this please let me know.  There seems to be a number
of people with this issue.

---

### Post by eduardoska on 2007-05-19
I worked it out changing this

Try changing images $YOUR_SKIN/pixmaps/amsn{,mask}.xbm with those ones from the default skin, and tell me if it works.

You can find amsnmask.xbm by searching it on your computer and then you copy it to your skin folder under .amsn. You can copy it to other skins folders for some time saving when changing skins.

From
[http://amsn-project.net/forums/viewtopic.php?p=18911]("http://amsn-project.net/forums/viewtopic.php?p=18911")

:)

---

### Post by netsurfau on 2007-06-26
Sorry for delay in getting back to you.  I'm studying full time and this had to be pushed down the priority 
list untill I'd got my assignments finished & exams over for end of semester.

I have tried what you suggested - without success.

Even tried working around issue by installing extra skins & changing from default skin - same result.

Still no icon in near clock & unable to "minimize to tray".

Anyone else have an idea on how I might be able to sort this one out?

---

### Post by Rippy on 2007-08-08
Does your amsn window minimize itself whenever you click the top bar (don't know the exact word for it, but the bar that contains the minimize and close buttons etc)? If so, I've got the same problem, if not, then obviously I've got something else.

---

### Post by netsurfau on 2007-08-11
Sorry, I don't have that particular problem.

---

