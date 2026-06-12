---
title: "Can't get Ubuntu to update"
date: 2006-03-13
forum: Desktop Environments
---

### Post by Kiotie on 2006-03-13
I have installed Ubuntu on 2 PCs now and the 1st one had an active net connetion at time of install and pulls updates as they are available just fine.  My 2nd PC was not connected to the net at time of install and for some reason when I use the update manager it does a query and says everything is up to date when I know that it isn't as I used the same disc for both installs.

I'm sure if I were to re-install w/ a net connection it would correct the problem but I'm guessing there has to be a better way.  An optioning issue or something.

Thanks,
Kiotie

---

### Post by IGNIZ on 2006-03-13
system-> administration -> network ?

---

### Post by Kiotie on 2006-03-13
My 2nd PC does have a web connetion.  I used that path (system->administration->networking) to set it up a few days ago.  I can bowse the web, get email, post in this forum etc.  The issue is it won't pull any new updates.

I looked on the PC that is working and copied /etc/apt/sources.list and pasted it into the one that is not updating as the two sources.list files were different then rebooted.

Still no good.

Any other ideas?

---

### Post by htinn on 2006-03-14
You then did "sudo apt-get update" right?

---

### Post by Zelut on 2006-03-14
In my experience if the computer can't find a network connection during installation it comments out the update lines in the sources.list file.  Take a look at that & see if thats the problem.

You can edit the /etc/apt/sources.list file with your favorite editor (and make sure the deb & deb-src lines aren't commented out) or you should also be able to do this thru Synaptic with Settings > Repositories > Add.

---

### Post by Kiotie on 2006-03-14
Ahhh Yes!!  It was the sources.list file.  I corrected the rem'd statements and rebooted.  Now it pulls all the update packages.

Thanks everyone!!

---

