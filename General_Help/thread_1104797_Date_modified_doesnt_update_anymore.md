---
title: "Date modified doesnt update anymore"
date: 2009-03-24
forum: General Help
---

### Post by Dr_Snapid on 2009-03-24
I have an FTP backup server based on ubuntu desktop.

I used to be able to open nautilus and it would show me each user's folder plus it's date modified column. The column showed the datestamp of the most recently edited file in the folder.

If the user had successfully backed up last night it would show the date modified as early this morning or now if the upload was still happening.

Since updating to Gutsy, the Date Modified column doesnt seem to update. If I look inside the folder, the files have newer date modified timestamps, but the folder view is no longer showing me the date of the 'most recently modified' file within.

Can I fix this?

---

### Post by Dr_Snapid on 2009-03-24
I think this is bacause ubuntu changed to use gamin instead of fam for monitoring files and folders.

Can I go back to fam? When i go to apt-get it, it says it's going to remove a whole bunch of stuff, including ubuntu-desktop so I cancelled.

I really need these folders refreshing their modified times!

Please help, anybody?

---

### Post by dcstar on 2009-03-25
> **Dr_Snapid said:**
> I think this is bacause ubuntu changed to use gamin instead of fam for monitoring files and folders.

Can I go back to fam? When i go to apt-get it, it says it's going to remove a whole bunch of stuff, including ubuntu-desktop so I cancelled.

I really need these folders refreshing their modified times!

Please help, anybody?

My fully-patched 8.04 system updates the folder access time if something directly in that folder changes - but not something another level down (and it uses gamin).

---

### Post by Dr_Snapid on 2009-03-25
Thanks davis,thats good to know. I'd like to know if I can go back to FAM, before I updated, this was working perfectly. I wish I hadnt updated now, but I needed to get to the LTS version.

---

