---
title: "Cannot login GDM Or terminal"
date: 2009-01-12
forum: General Help
---

### Post by tsardonix on 2009-01-12
Ok this is a new one on me.. 
I have a machine running ubuntu 8.10, 3 users (they are all me) been running for about 2 weeks now.

Today I was switching from 1 user to another and it stopped responding for a bit.   ok nothing unusual.  came back a bit later all looked ok.  started to do system update. Synaptic came up asked for pass. and it took it but it didn't. (it would usually tell me I typed it wrong or something or just work)
this time it didn't, it came back up and asked again. again it did the same thing so i tried my slightly different root pass did the same thing i tried a completely wrong pass and it told me it was wrong.  ok so I rebooted.  get to the GDM type user and pass starts to load gnome seconds later Back to the GDM ok tried other users same thing.  ok terminal time
get alt ctrl+f2  get a prompt.  user pass,...  yeah same thing starts to go then stops. back to the login.  tried off the wall user pass tells me its wrong.

Side note I was vnc'd to this same machine when this happened I could not do something from another machine got cups (installing a printer that was attached to another box) error thought it was the user I was in as so I tried to switch (may be a symptom.)  

I didnt failsafe kernel yet im doing this now.  will update if anything changes.  thanks in advance.

---

### Post by tsardonix on 2009-01-12
ok here is an update..  got into kernel failsafe was able to run dpkg (?)
and id did find some missing things and it appeared to have resolved them.
i also fsck'd the drive found a .3% issue ok it appears to have fixed.
then i choose the root prompt. it accepted my passwd for root.  so i rebooted.  back to GDM same issue. tried terminal, same issue.

thanks again.

---

### Post by lykwydchykyn on 2009-01-12
could be one of the partitions is full.  Go into maintenance mode, log in as root, and do:

df -h

If any of your partitions is full, clean it out.  Maybe you need to do "apt-get clean", since it messed up in the middle of package installation (might have filled up the drive at that point).

---

### Post by tsardonix on 2009-01-12
> **lykwydchykyn said:**
> could be one of the partitions is full.  Go into maintenance mode, log in as root, and do:

df -h

If any of your partitions is full, clean it out.  Maybe you need to do "apt-get clean", since it messed up in the middle of package installation (might have filled up the drive at that point).


Thanks for the information.  unfortunately no.  11 gig out of 112gig used.  did apt-get clean and autoclean (just in case)  nothing changes.

---

### Post by tsardonix on 2009-01-14
Ok So I was not able to uninstall gnome or GDM from failsafe kernel. I ended up formatting and reinstalling that machine.  thanks anyways.

---

