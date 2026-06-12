---
title: "help!  fonts keep reseting..."
date: 2011-03-24
forum: Desktop Environments
---

### Post by nerdy_kid on 2011-03-24
I use Kubuntu, and I don't like Ubuntu's font with KDE.  So, I changed it in systemsettings.  However, for some reason every now and then the font reverts to Ubuntu.  Anyone have any idea why this might be happening?  Where is the config file that dictates the system font? Maybe I could just remove write permissions for an ugly fix.

---

### Post by ankspo71 on 2011-03-24
Hi,
> Where is the config file that dictates the system font?
The offending settings file might be ".kderc" so check your home folder for a hidden file called .kderc. Right click on the file, select properties, then select the permissions tab, and make sure the file is owned by you, not root. 

If it is owned by root, then use the following command to gain ownership of the file:
```
sudo chown yourusername:yourusername ~/.kderc
```

Open the file up with your text editor and check to see which font it has listed in the settings. If it says the font is Ubuntu then this would be the file that is causing your fonts to revert to Ubuntu. If the .kderc file only contains font information, then it is safe to delete (or you can simply rename the file as a backup like ".kderc-backup"). 

Now configure your fonts again, then restart and see if the problem ever comes back.
Hope this helps.

---

### Post by nerdy_kid on 2011-03-24
> **ankspo71 said:**
> Hi,

The offending settings file might be ".kderc" so check your home folder for a hidden file called .kderc. Right click on the file, select properties, then select the permissions tab, and make sure the file is owned by you, not root. 

If it is owned by root, then use the following command to gain ownership of the file:
```
sudo chown yourusername:yourusername ~/.kderc
```

Open the file up with your text editor and check to see which font it has listed in the settings. If it says the font is Ubuntu then this would be the file that is causing your fonts to revert to Ubuntu. If the .kderc file only contains font information, then it is safe to delete (or you can simply rename the file as a backup like ".kderc-backup"). 

Now configure your fonts again, then restart and see if the problem ever comes back.
Hope this helps.

great, thanks!

The file is owned by me, and only contains font relevant info.  I checked the /root/.kderc file as well, and its set to the font of my preference.  I'm going to go and track down the master kderc, probably in /usr/ somewhere.  Thanks for the info :)

---

