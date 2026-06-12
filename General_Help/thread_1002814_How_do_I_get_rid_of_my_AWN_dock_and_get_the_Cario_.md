---
title: "How do I get rid of my AWN dock and get the Cario dock?"
date: 2008-12-05
forum: General Help
---

### Post by PsychedelicWonders on 2008-12-05
I've talked with some people and seen some things and it seems the Cario dock is more advanced and has more special effects than my AWN.

So how do I successfully get rid of my AWN dock and intall the newest Cario dock?

I should also be able to drag and drop icons onto the Cario dock like i did with the AWN dock correct?

---

### Post by MedianMajik on 2008-12-05
To remove awn        'sudo apt-get remove avant-window-navigator
Another method is to load up Synaptic (under System) to search "avant-window-manager" and remove all related packages.  If you added to your source list when you installed awn, be sure to remove that as well.

Procedure For Installation of Cairo dock:-

Add the repository to System->Administration->Software Sources->Third Party Software->Add:
deb [http://repository.cairo-dock.org/ubuntu/dists/intrepid/cairo-dock/binary-i386/](http://repository.cairo-dock.org/ubuntu/dists/intrepid/cairo-dock/binary-i386/)  **I'm assuming you're using 32-bit Intrepid.  If I'm wrong please say so!  Always post exactly what version of Ubuntu you're using (best to add it to your signature)**

Click Reload.
Click here to install if you have apt-url installed with firefox and you added the above repository or:
Open up synaptic:
System->Administration->Synaptic and search for cairo-dock and cairo-dock-plug-ins then click install.

Once Installed you can access Cairo Dock via Applications->System Tools->Cairo Dock
Cairo-Dock has an update function so you will not need a repository or need to download it again

Here is the link I just copied that info from: [http://computrgeek.wordpress.com/2008/05/27/howto-install-cairo-dock-in-ubuntu/]("http://computrgeek.wordpress.com/2008/05/27/howto-install-cairo-dock-in-ubuntu/")
I've never used Cairo so this is where my knowledge on it ends (search google or the forum for lots more information).  Have fun!

---

### Post by DJ_Peng on 2008-12-05
There are some good uninstall instructions for AWN on their [support thread]("http://ubuntuforums.org/showthread.php?t=762363") here. The instructions he gives will also make sure you get all of the components removed.

---

### Post by PsychedelicWonders on 2008-12-05
So I take it this is a good move going from AWN to cario?

---

### Post by DJ_Peng on 2008-12-06
I can't say since I've never used Cairo. But then AWN works fine on my system. Hopefully someone will come along with a more informed answer, but like with most open source projects it's a matter of personal preferences. Whenever someone makes a recommendation based on their usage of an app your mileage may vary.

---

### Post by PsychedelicWonders on 2008-12-08
Do I need to remove AWN before installing Cario?

Does Cario have any 64 bugs I need to worry about?

AWN has worked pretty flawlessly for me.

Can I leave AWN installed and install Cario to see if I like it better before I remove AWN?

---

### Post by DJ_Peng on 2008-12-08
I don't think you need to remove AWN before installing Cairo but you definitely need to disable AWN before firing up Cairo. As far as the status of bugs in Cairo you should probably do a search to find the Cairo support thread. I was able to find some [community docs]("https://help.ubuntu.com/community/CairoDock") by running a search on [Uboontu search]("http://www.uboontu.com/").

---

### Post by PsychedelicWonders on 2008-12-09
I have 8.04 - 64.

So how would I get Cario for this version?

I plan on upgrading to 8.10.... should I do that first and then get Cario?

---

