---
title: "Pan Newsreader problem"
date: 2009-05-15
forum: General Help
---

### Post by PhilB on 2009-05-15
Upgraded to Jaunty last week, and everything has been very good until yesterday.
Basically the news reader Pan was in the middle of updating one of the groups when I lost power briefly. On rebooting, Pan fired up as if it was a new install-no subsribed groups, let alone scores/killfiles etc. Strangely the .Pan2 folder is intact in my home directory, complete with all the groups/headers and so on.
I have tried copying this to a backup folder and deleting the newly created files before copying the old ones back in, but so far no joy. 
Short of starting again from scartch with the gruops has anyone got suggestions for restoring my old settings?

---

### Post by whoop on 2009-05-15
> **PhilB said:**
> Upgraded to Jaunty last week, and everything has been very good until yesterday.
Basically the news reader Pan was in the middle of updating one of the groups when I lost power briefly. On rebooting, Pan fired up as if it was a new install-no subsribed groups, let alone scores/killfiles etc. Strangely the .Pan2 folder is intact in my home directory, complete with all the groups/headers and so on.
I have tried copying this to a backup folder and deleting the newly created files before copying the old ones back in, but so far no joy. 
Short of starting again from scartch with the gruops has anyone got suggestions for restoring my old settings?

Do you have ext4 by any chance? Might be due to delayed allocation. In that case there's not allot of chance of recovery.

---

### Post by PhilB on 2009-05-15
> **whoop said:**
> Do you have ext4 by any chance? Might be due to delayed allocation. In that case there's not allot of chance of recovery.

No, I decided to stick to ext3.

---

### Post by PhilB on 2009-05-15
Well I decided to bite the bullet and start from scratch. Went to get the first groups headers and hey presto, there were the old headers too.
Seems that Pan had simply lost my subscribed groups list.

---

