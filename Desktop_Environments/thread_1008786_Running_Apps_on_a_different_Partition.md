---
title: "Running Apps on a different Partition"
date: 2008-12-11
forum: Desktop Environments
---

### Post by llanitedave on 2008-12-11
Due to some very lame actions on my part, I ended up having to reinstall 8.10 on a separate partition from the original installation.  This happened after I had already downloaded tons of applications into my first installation.

The older installation is still there, residing in a downsized partition, although my old username appears to not be valid any more.  I don't want to have to go through the hassle of downloading and installing those applications all over again.

My choices seem to be to either move the application folders over to the current Filesystem, or to somehow gain access to run them from the old.  I can see a bunch of the apps in my old  /usr directory -- for example, I can get to the Bluefish application icon and double click on it -- but it doesn't load or run, and doesn't give me any fail message.

I'm a bit intimidated by the idea of bringing the applications over to the new Filesystem, since their critical files are scattered through several different folders.

Is there a way to master this short of wiping out the old partition and reinstalling everything from the repostories again?

BTW, I was given the option of importing from the old partition when I installed, but I declined, worrying that the corrupted stuff would get imported along with the stuff I wanted, and would put me in the same boat all over again.  Now I'm wondering if there's a way to do a more limited set of imports after the fact.  That would make things so much easier!

---

### Post by psusi on 2008-12-11
Unless the packages are still in the apt cache ( /var/cache/apt/archives ) of the old system, you will have to download them again.

---

### Post by llanitedave on 2008-12-11
Yes, they all seem to be in that directory, as package icons.  Right clicking on a package gives me as first option 'Open with GDebi Package Installer"'.

So, should I copy them to my current partition and install them using that method?

---

### Post by MedianMajik on 2008-12-11
> **llanitedave said:**
> Yes, they all seem to be in that directory, as package icons.  Right clicking on a package gives me as first option 'Open with GDebi Package Installer"'.

So, should I copy them to my current partition and install them using that method?
  GDebi is the standard installer for debian packages.  You don't need to worry about it.
  On the corruption issue I plead the 5th.  I don't want to give my opinion on something I'm unfamiliar with.  I would recommend looking into some backup solutions (googling rsynch will get you started) to prevent this hassle in the future.

---

### Post by llanitedave on 2008-12-12
The corruption issue was just me uninstalling the network manager when I was trying to install other apps.  I lost access to the internet, and for some reason I couldn't get my install disk to act as a source to reinstall the individual package.  So I had to do a total reinstall.

---

### Post by psusi on 2008-12-12
Just double click on the packages to install them.  No need to copy first.

---

### Post by Vantrax on 2008-12-12
sudo dpkg -i *.deb run inside that folder should chain install them all without needing to click them individually.

---

### Post by llanitedave on 2008-12-12
Thanks, Vantrax.  I'd installed a few packages for testing, but those with dependencies all chose to download them from the repository rather than using the ones that were sitting right next to them in the directory.  Would the -i option prevent that?

---

### Post by vloris on 2008-12-12
No, the -i is just a shortcut to --install. But it might help because the *.deb argument expands to all those files, so dpkg will install them all at once and if the mentioned dependencies are there too, dpkg won't complain about them.

---

### Post by llanitedave on 2008-12-13
Thanks to all those who responded.  The sudo dpkg -i *.deb did the trick!

---

