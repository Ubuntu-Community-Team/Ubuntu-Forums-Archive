---
title: "&quot;Cannot install all available updates&quot;"
date: 2006-08-02
forum: Desktop Environments
---

### Post by jkh107 on 2006-08-02
I clicked on the icon in the notification area to install the latest updates and it brought up the following message:

> Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

The following updates will be skipped:
totem

Would someone mind explaining what this means in simple terms? And what exactly will happen if I do "sudo apt-get dist-upgrade"?

---

### Post by zorkerz on 2006-08-03
I also get this message.  when i entered "sudo apt-get dist-upgrade" into the terminal I got this response.  
>  The following packages have been kept back:
  totem Also the "Mark All Upgrades" button in the package manager does not find any new packages to upgrade
Does anyone know what is going on here? What needs to be removed? Or maybe has totem been replaced by another package?
Possibly some packages haven't been added to the repos yet.
elias

---

### Post by dr k on 2006-08-03
In synaptic, find totem, right click and selct mark for upgrade.  For me it removed totem-xine and added totem-gstreamer.

I might add that by removing totem-xine I can no longer play divx files.

---

### Post by zorkerz on 2006-08-03
In the past totem-gstreamer was not as functional as totem-xine.  Do i want to upgrade?  Has gstreamer improved or am I going to lose some functionality?  Seams odd that an upgrade would make me loose functionality.
elias

---

### Post by dr k on 2006-08-03
so, to get divx playback working, i had to remove totem-gstreamer, which also took totem and ubuntu-desktop with t.  after those three were remoed, i reinstalled totem-xine, and it was all back to normal.

---

