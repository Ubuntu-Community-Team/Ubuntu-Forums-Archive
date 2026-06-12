---
title: "Broke Firefox, attempted fix and failed"
date: 2008-08-28
forum: Desktop Environments
---

### Post by Tzimisce on 2008-08-28
Recently my computer locked up (a rare occurance) while I was toiling away on Firefox. When I rebooted and opened firefox to get back to work, it asked if It should restore last settings... yes... when it loaded it loaded a blank page. All the bookmarks were gone (and I couldnt add/change anything). The interface was all pretty much missing and it locks up the computer after several minutes of use. I tried using ubuntu website's walkthrough to install the Mozilla version in the /opt/ directory and firefox runs fine now when i start it using 'gksudo firefox' any other method of opening it reverts it back to the ruined version. Is this something that has been heard of, is easily fixed etc.?

(note: i picked desktop environments because I wasn't sure where this would go, and the problem seems to be with the interface)

---

### Post by ajgreeny on 2008-08-28
For the moment, rename your hidden .mozilla folder in your home folder as .mozillaold (press Ctrl+H if hidden files do not show) and restart FF.  It should start up OK, but without your bookmarks etc etc.  Now you can try copying back the files and folders from your old .mozilla folder one by one to the new one.  Something may upset FF again, and you may have to live with that, but you may be able to get back most of your old profile if not all of it.

---

### Post by Tzimisce on 2008-08-28
> **ajgreeny said:**
> For the moment, rename your hidden .mozilla folder in your home folder as .mozillaold (press Ctrl+H if hidden files do not show) and restart FF.  It should start up OK, but without your bookmarks etc etc.  Now you can try copying back the files and folders from your old .mozilla folder one by one to the new one.  Something may upset FF again, and you may have to live with that, but you may be able to get back most of your old profile if not all of it.

Thank you very much, I never thought of the hidden folders. This fixed it for the time being, I imported my backup bookmarks (from html as the backup/restore never works for me) and will just do everything else from scratch. Highly appreciate it now I can get back to work. 

+1

---

