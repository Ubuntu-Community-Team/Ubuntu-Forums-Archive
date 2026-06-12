---
title: "Why won't azureus get fixed?"
date: 2006-07-29
forum: Desktop Environments
---

### Post by dmb on 2006-07-29
Hey, im sorry to be kind of rude, but im wondering why azureus just won't get fixed and updated in the repositories. The version in the repositories is simply broken, and not useable at all. The simple fix is to use a slightly updated version of azureus from the actual azureus website. What I don't understand is why the maintainers of the ubuntu azureus package can't simply fix it, or at leaste update it to a version that works. Haveing a version that works but may be unstable is better than a version that doesn't work at all. Azureus is one of the most popular packages i'm assumming that is in the repositories, and i think it should be fixed.

Yes, i know, its a p2p app, but it can be used for leal purposes (which is what i'm doing)

Anyway, again sorry to sound rude, but this has to fixed, it is ruining the reputation of ubuntu for my friends.

---

### Post by GTvulse on 2006-07-29
Just a quick note: No matter how much you kick and scream about a distribution or application bug in the forums, all you are doing is venting steam or, worse, wasting your time. [If you want a bug solved you need to transmit the information through the correct channels]("http://www.ubuntu.com/support/bugs").

On the other hand, here in the forums you can find help of fellow users that have already fixed up the same or similar problems. I'll make as if you didn't write the above as a gripe, but as a very dense question: ¿How do I install Azurerus from the upstream developers? Well, there are many ways to skin a cat, you know, but this is how I did it:

1. Installed Sun's Java from the repos and made it the default with a "sudo update-alternatives --config java". (GNU GJC won't cut it since Azureus is using some Sun crypto libraries).

2. Downloaded Azureus in a zip file, uncompresses the file and moved the resulting directory (Azureus, I think) to a hidden name: /home/<myaccount>/.azureus-bin

3. Right clicked on the desktop to create an aplication launcher that launches "/home/<myaccount>/.azureus-bin/azureus" and added an icon by changing the default path to /home/<myaccount>/.azureus-bin and selecting the logo.

4. Dragged a copy to the menus panel. Click on icon, launched azureus, installed AZCVSupdater, intalled all the updates (which include a new SWT runtime), and got a good behaving azureus.

---

### Post by dmb on 2006-07-29
[https://launchpad.net/distros/ubuntu/+source/azureus/+bug/41813](https://launchpad.net/distros/ubuntu/+source/azureus/+bug/41813)
This bug has been here for a while.

---

### Post by droogy on 2006-08-19
> **dradul said:**
> 4. Dragged a copy to the menus panel. Click on icon, launched azureus, installed AZCVSupdater, intalled all the updates (which include a new SWT runtime), and got a good behaving azureus.

Can you expand on the details of these steps... I can't install the cvsupdater and the updates are not accepted.  Do I have to change permissions somewhere?

---

### Post by droogy on 2006-08-19
My problem was that azuerus was trying to update files in the /opt/azureus directory... I had installed from automatix.

I ended up installing the latest azureus 2.5 RC and putting it in the /home/user/.azureus directory. then it automaticaly updated to the correct directory... any ideas why it installed to opt directory?!

---

