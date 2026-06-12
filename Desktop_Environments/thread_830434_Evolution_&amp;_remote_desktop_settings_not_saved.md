---
title: "Evolution &amp; remote desktop settings not saved"
date: 2008-06-15
forum: Desktop Environments
---

### Post by BearWayne on 2008-06-15
Whenever I log off Ubuntu, whether I reboot or not, my mail server settings in Evolution are lost. This started after the Hardy upgrade. Likewise, my remote desktop sharing settings are lost.  For both applications, I have to re-enter the setup options.

For evolution, I have to set up my incoming and outgoing server settings, but not the passwords. I have to reenter my account information. All the files under .evolution are owned by me, and as far as I can see are all RW by me (there were thousands of files, so I didn't look at them all). I did notice that the passwords are kept under .gnome_private.

I don't know what to look at for Remote Desktop.

Does anyone have an ideas on how to resolve these 2 problems?  They seem similar enough that they could be linked.

Thanks,
Barry

---

### Post by BearWayne on 2008-06-16
It turns out that the .gconf directory was owned by root. Once I chowned it and its subdirs to my userid, the settings were saved.

---

