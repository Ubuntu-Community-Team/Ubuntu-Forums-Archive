---
title: "how import data from old Kmail in Kontact?"
date: 2005-06-12
forum: Desktop Environments
---

### Post by Olflo on 2005-06-12
how can i use my user-specific settings like the folders i created and the old mail archives as well as the data in my old kadressbook in a brandnew install of Kontact under Kubuntu 5.04?
Is there a way to import data and settings from an older Installation on a separate machine running KDE 3.1. ?

---

### Post by oakhilltop on 2005-06-12
I'm having problems also. I backed up my ~/Mail directory before installing kubuntu. I untarred my backup and kmail is complaining that it can't read my folders. Either permissions or invalid maildir format.

I'm not sure if my previous kmail was mbox or maildir. kmail has a default setting for the type, so I changed it to mbox and tried again. It still complains and mentions maildir, even though the default is mbox.

Its pretty poor when an application can't read in the data that was backed up for the previous version.

Has anyone else seen this? I'd really like to get my email back.

Thanks

---

### Post by oakhilltop on 2005-06-12
Well, forget that last post   :roll: 

I did a rm -rf ~/Mail and untarred my backup again and it worked this time.

I don't know what I screwed up before.

Steve

---

### Post by Olflo on 2005-06-13
alright.
If I get that right, it means I  need to copy several files from my old .kde/share/apps and corresponding subfolders to the new ones, and everything will be in place..
thanx

---

