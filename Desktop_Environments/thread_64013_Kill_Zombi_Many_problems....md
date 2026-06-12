---
title: "Kill Zombi? Many problems..."
date: 2005-09-09
forum: Desktop Environments
---

### Post by cd-r80 on 2005-09-09
This Is grazy? I Have AMSN, it shows child process esd: zombi. I try to kill esd & Kill command changes to a zombi. And other kill = zombi... Gnomemeeting & Netmeeting does not work very well together, sound is horrible & other problems. Everyday I have been fixing something with this Hoary 5.04. It is now not going to be my Moms stable videophone. Windows ME is more stable than Ubuntu! If I log as a user and use gnomemeeting then log out and in as other user,  I cannot use Gnomemeeting because it is still running by the first user. Nautilus has a horrible renaming bug. It is very hard to rename some file. Huh!

---

### Post by amohanty on 2005-09-10
Ok a few peices of advise. if you have multiple problems, stating them on separate lines makes it more readable and thus more likely to be answered. Secondly try and post some background info, it goes a long way in understanding your problem.

1. Regarding the zombie methods:
before you kill anything, in terminal type:
ps ax 
and post the relevant process that you killed.
esd is the enlightenment sound daemon, you really dont need to worry about it.

2. Regarding gnomemeeting, I am not sure I fully understand your problem. 
- Are you trying to use gnomemeeting and netmeeting to setup a video connection? 
- I have experienced problems with gnonemeeting being used by multiple users on the same machine at the same time, but why are you trying to do that?

3. I think the nautilus renaming issue is still an open one, so cant help you there. If you want to rename stuff why not use the terminal? Or is this for a non-user? If so take a look at Roxie(?) I think thats what its called.

HTH
AM

---

### Post by cd-r80 on 2005-09-10
1. It was esd which I made my kills zombie. ps aux: kill zombie, esd zombie...
2. Gnomemeeting does not close when user logs out.
3. Gnomemeeting did not have the same sound codec as Netmeeting C.723. Or only for some quicknet cards. And sound was very bad.
4. I Had problems making videocalls to NetM. Don't know how to set right options. JUSt between two persons... And firewall was right set or Off.
5. Well. I can rename things with terminal, But I liked Nautilus appearance...
6. Perhaps I try Rox-filer.
7.Deleting .Gnome2/session file helped a lot my life.
8. I can manage with Ubuntu, but normal windows user does not yet.

---

### Post by cwaldbieser on 2005-09-10
[QUOTE=cd-r80]
8. I can manage with Ubuntu, but normal windows user does not yet.
[/QUOTE]
Like the tooth fairy or the unicorn, the normal windows user is a mythical beast.  Each individual approaches the use of personal computers from their own perspectives and experiences.

A little off topic, but I think the observation is worth mentioning.

---

