---
title: "How to completely remove all previous Evolution settings"
date: 2009-05-05
forum: General Help
---

### Post by cajunaggie on 2009-05-05
I recently reinstalled Jackelope and set up two separate partitions for my filesystem and my /home locations, as a back-up procedure.

When reconfiguring Evolution I restored from my back-up files. After that, whenever I tried to use Evolution calendar, Evolution froze. I deleted the calendar, but it still shows up in Evolution.

Long story short, after much experimenting and frustration, I'm trying to completely remove all my previous Evolution settings and start from scratch. However, even after uninstalling Evolution with the purge settings and removing the folder in my /home location, I still see calendars and account settings from before and I can't seem to edit them in Evolution. Is there a conflict in having separate partitions or is there a back-up file somewhere that I can't find?

---

### Post by mpcengineering on 2009-05-06
I have also wanted to start from scratch with evolution and haven't been able to find any way to make the software forget its previous setup like you.

However I have just run across [this]("http://www.samlesher.com/tag/delete-evolution-settings") page.  Seems to have done the trick for me, and to keep all my local mail I did a backup of settings first which effectively archives the entire .evolution directory including the local mail boxes.  You can then expand the archive and import just the relevant mailbox files back into evolution to restore all your old mail.

You do of course have to recreate some things afresh such as signature, mail filters and so on, but this isn't a big deal.

---

