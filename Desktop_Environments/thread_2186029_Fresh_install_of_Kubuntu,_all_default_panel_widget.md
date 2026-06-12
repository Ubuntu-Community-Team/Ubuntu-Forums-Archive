---
title: "Fresh install of Kubuntu, all default panel widgets are missing"
date: 2013-11-05
forum: Desktop Environments
---

### Post by scottbomb on 2013-11-05
I normally use Xubuntu but thought I'd take a look at the current Kubuntu. In installed 13.10 into its own partition. Oddly enough, everything is missing from the panel. No Kicker, no clock, not even something to show the various buttons for open windows (Task Manager). I was able to add all of these manually but it seems very strange that they weren't already there. I double checked the MD5, reinstalled, and got the same issue. I also tried this with 13.04 and it too behaved the exact same way. 

I'm also having trouble getting the Dropbox icon to appear on the panel. I added the Notifications widget but that didn't help. 

FWIW, this is a 6-core AMD machine with 16 GB RAM and two monitors.

Is there a particular package against which I should file a bug?

---

### Post by SeijiSensei on 2013-11-05
Out of curiosity, is your home directory in the new Kubuntu partition, or are you sharing a /home with your other installation?  Try moving /home/username/.kde to .kde.old then logging out and in.  Kubuntu will build a new default configuration.  Any different?

---

### Post by scottbomb on 2013-11-05
No, each partition has its own /home. I renamed that file like you suggested and I was right back to where I was after installation, with a completely blank panel except for the Activity Manager and Panel Toolbox icons. I renamed the file back to .kde and for some reason, all my customizations were gone so I had to re-do them.

---

### Post by QIII on 2013-11-05
Hello!

Just for giggles and grins, could you tell us what happens if you add a new default panel?

---

### Post by scottbomb on 2013-11-05
It actually created the panel correctly like it should have in the first place! Awesome, thanks! I wonder if the fact that I'm using two monitors (one over the other with only one panel at the bottom of the main monitor) had something to do with it.

---

### Post by QIII on 2013-11-05
I have three monitors with just the one panel and I don't have this problem.  So I don't think it's that.

Let's give the machine a reboot and see if the new panel survives intact.

---

### Post by scottbomb on 2013-11-06
Yes, it survived the reboot. Thanks!

Other than that, I must say that Kubuntu is looking great! I may end up switching from Xubuntu, we'll see.

---

