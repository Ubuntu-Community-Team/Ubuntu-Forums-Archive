---
title: "How do I remove everything installed with netbook remix?"
date: 2009-04-30
forum: General Help
---

### Post by zorkerz on 2009-04-30
Im running Jaunty and wanted to try out the Ubuntu netbook remix. So I installed it through synaptic. I think its pretty cool and has potential but I always run into problems. Most annoyingly to many of my settings for the classic desktop got changed so that I could not switch between the classic desktop and remix desktop satisfactorily. So eventually I decided to uninstall it.

Here is my problem. A whole bunch of programs got installed with ubuntu desktop remix but where not uninstalled with it. 

Would somebody open synaptic and tell me all the programs that are marked for installation when they select ubuntu desktop remix.

---

### Post by gamewolf on 2009-04-30
I was tempted with doing this also. Netbook Remix is build on the Atom processor, which is pretty much only included in netbooks. It runs into problems when not on the Atom processor.

As for removing it, you may have to chroot into it from knoppix or ubuntu live cd and use aptitude to remove it and reinstall ubuntu-desktop.

Good luck!

---

### Post by zorkerz on 2009-04-30
Hmm I never uninstalled the ubuntu desktop and I have removed the ubuntu-netbook-remix package itself. Its just that all the other packages installed with it have not been removed.

---

### Post by Brandon Williams on 2009-04-30
Open aptitude in a terminal, navigate to ubuntu-netbook-remix, and press Enter to look at the details of ubuntu-netbook-remix.

Now, down-arrow to the line that says 'Depends'. Press 'M', which will mark all of the packages in the Depends list as having been automatically installed. The ones that are only installed because ubuntu-netbook-remix depended on them will be marked for removal.

Now go down to 'Recommends' and press 'M' again.

Finally, press 'g' to review the list of packages to be removed and then press 'g' again to perform the actual removal.

---

### Post by zorkerz on 2009-05-01
Thanks a lot Brandon. Solved my problem and finally got me to begin learning how to use aptitude.

---

