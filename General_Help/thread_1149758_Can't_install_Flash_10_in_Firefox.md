---
title: "Can't install Flash 10 in Firefox"
date: 2009-05-05
forum: General Help
---

### Post by TheDasK on 2009-05-05
Hi everyone,

I'm having some problem with flash videos, sometime they load, sometimes they don't. Google (aka some random blogs) told me that the answer was upgrading to flash 10 ( I have 9.0 r999), so I went to Adobe and download the .deb file. the file runs and everything... but it doesn't do anything, i still have v9.0... So i went and download the tar.gz file, but when i try to put the .so file in the firefox plug-ins folder ( /usr/lib/firefox/plugins?), I don't have the rights...

Sorry for anything, I'm new and English is my second language...

---

### Post by Meson on 2009-05-05
As of 9.04, flashplugin-nonfree should be version 10. Are you installing from the repository? If it doesn't show you need to enable the multiverse repository in the "Software Sources" GUI

---

### Post by wpshooter on 2009-05-05
> **TheDasK said:**
> Hi everyone,

I'm having some problem with flash videos, sometime they load, sometimes they don't. Google (aka some random blogs) told me that the answer was upgrading to flash 10 ( I have 9.0 r999), so I went to Adobe and download the .deb file. the file runs and everything... but it doesn't do anything, i still have v9.0... So i went and download the tar.gz file, but when i try to put the .so file in the firefox plug-ins folder ( /usr/lib/firefox/plugins?), I don't have the rights...

Sorry for anything, I'm new and English is my second language...

Download the tar file to your /home directory/folder and then right-hand click on it and extract to here.  Then you need to use the terminal to move to the folder that the tar file was extracted to and then run the flash-installer program.  Run as sudo.  You will need to know the path for your browser/firefox (for instance mine is firefox-3.0.10), you will be prompted for this during the flash installation from the terminal.

Write back if you need further help.  I am at work now where I don't have a Ubuntu machine and I will check back here when I get home.

Good luck.

---

