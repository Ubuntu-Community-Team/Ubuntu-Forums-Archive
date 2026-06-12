---
title: "Problems Installing/Uinstalling Matlab"
date: 2009-06-13
forum: General Help
---

### Post by nmaster on 2009-06-13
I tried to install Matlab using the given.  When I try to uninstall it by deleting the files, the files don't go away.  I'm not sure what is happening.  I gksudo nautilus so that I can delete the directories, but no disk space is freed up.  I can't see the directories, but they are clearly taking up space.  Whats worse is that I've tried installing twice, so now twice the space is taken up.  I'm using wubi with about 17GB.  I was at about 7-8GB before I tried this, but now I'm at 789MB of free disk space.  Where are the files? Why aren't they being removed?  Can anyone help me out?

---

### Post by nmaster on 2009-06-13
Okay so I found an answer.  I found the files in  /root/.local/share/Trash using gksudo nautilus. ([https://answers.launchpad.net/ubuntu/+question/52686](https://answers.launchpad.net/ubuntu/+question/52686)).  I was able to delete them so now I'm actually at 13GB available.  

I'm happy doing this, but can anyone explain why?  Is there something about gksudo or nautilus that I don't know?  It seems that because I deleted files as root, they went to a different Trash.  I'd really like to learn about this.

Thanks for taking the time to read!

---

### Post by mc4man on 2009-06-13
deleting files as root is no different in that regard as deleting as a user, by default the files go to the trash. Root has it's own trash which makes sense.

And like for a user a delete command can be added to root's right click options, though for most it would be safer not to enable

---

### Post by michy99 on 2009-06-13
When deleting files in nautilus, if you want to completely delete them instead of sending them to the trash, hold down the shift key and press the delete key. Make sure you really want them gone because they will be.

---

### Post by nmaster on 2009-06-13
Yeah thanks, I've figured those things out.  I guess I got a little crazy and posted a thread before I had exhausted other options; I was panicing.  Thanks for the responses though.

---

