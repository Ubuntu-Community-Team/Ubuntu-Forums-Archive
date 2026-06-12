---
title: "Need to reduce the size of my install"
date: 2009-03-25
forum: General Help
---

### Post by joeman500 on 2009-03-25
Hi,

I have Ubuntu 8.10 in a Virtual machine. The problem is that the hard drive file is almost 6GB and I have only installed a few medium sized programs (mySQL server, Netbeans). I really need to fit the machine onto a single DVD. There also needs to be some other files on the DVD so i need to get the hard drive file down to about 4GB.
Does anybody have any ideas on how i can do this please?
I'm an intermediate user in Ubuntu.
Kind Regards
Joe

Edit:
forgot to mention that I am using VMWare Workstation

---

### Post by JohnFH on 2009-03-25
You have many options depending on what you need the DVD for.

1. Use tar to compress what you have already.  After compression, it will probably fit on one DVD.

2. Use a dual layer DVD.

3. You didn't mention what host OS you use, and hence if you use VirtualBox to host your VM.  If so, then I think you can change the hard drives to be dynamic in size which might reduce the size.  (EDIT: Ignore that, since you are using VMWare).

4. Try removing the following to cut down the size: OpenOffice, old kernels.  Also use localepurge to get rid of unused locales.

---

### Post by kanikilu on 2009-03-25
If you've updated and installed packages, you can quickly and easily reclaim some disk space with ```
sudo apt-get clean
```

---

### Post by joeman500 on 2009-03-25
Hi guys,
Thanks for your replies.
JohnFH:
1. Im using windows so i'm in the process of zipping up my VM, its going to take twenty minutes. I am going to be using this for my final year project demonstration, i'll see how long it takes to unzip, but this could be out the question as the examiner probably wouldnt want to wait 20 minutes for it to unzip (but I will time it, if its less than 5 minutes then I could probably get away with it).
2. It needs to fit on a standard DVD as some of the computers are old at university.
3. Im using XP as host and they have the same at university.
4. I removed OpenOffice previously, it got rid of a few hundred megs! :) localepurge also just remove about 500 megs
Thanks for your reply!
kanikilu:
I will give it a go after the zipping has completed. Thanks

The one thing that concerns me though - a clean install is 2.3GB and i've hardly done anything and it seems to have put on 3.5GB. Just wondering where all that has gone to.

---

### Post by joeman500 on 2009-03-25
kanikilu:
Unfortunately that did nothing. I might have ran it a few months back and not installed anything since. 
I'm down to 5.4GB.
It took 6 minutes to unzip. Which is ok, but not great when I have to demo the project.
Does anybody else have any ideas where this extra space has come from or how to get rid of it?

---

### Post by kanikilu on 2009-03-25
I can't think of anything else that will be "quick and easy", but if you haven't already, open Synaptic, go to Status > Installed to view all installed packages. Then go to Edit > Preferences > Columns and Fonts and make sure "Installed Size" is checked and click Apply and OK.

Now you can sort your installed packages by size and start going through the largest and purging if they aren't necessary (you'll have to determine that though).

Also, if you want a "map" of your disk usage in a GUI, try baobab or filelight.

Lastly, you said this is for a demo of some sort, right? If so, do you have any user data that is related to that? Maybe you could move that user data to a USB flash drive and use a combination of the DVD and the flash drive?

---

### Post by joeman500 on 2009-03-25
Thanks kanikilu, that was very helpful.
I've decided to just start from scratch with the VM. Something has obviously gone majorly wrong. I had a clean Ubuntu VM install so i added all the programs that I needed in that and its come up to 3.5GB. So I am happy with that, but i will have to export my Database and configuration files, but at least it will be under 4GB.
Thanks for all your help anyway guys!

---

