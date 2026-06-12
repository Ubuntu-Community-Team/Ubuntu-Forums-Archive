---
title: "Backup/Restore Question"
date: 2009-01-16
forum: General Help
---

### Post by drjonze on 2009-01-16
I posted my question in the following thread:[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087") but its an old one so I don't think I'll get a reply. 

In my question, I refer to using 'this method' to backup my system, that method is saving everything in a TAR file (which is what the above link is all about):

I have used this method before but the set up I had at the time was that my / and /home directories were on the same partition. I am going to be migrating my /home directory to a new partition. Will this method also work for this type of setup? (assuming that I'm restoring to the same setup, that I have run the back up after I have migrated my /home directory and all of my important files are already backed up to DVDs, just in case). In this case, would I exclude /home from the back up, seeing as if I were trying a new distro or upgrade, I would only be touching my / directory and not touching the home partition? If this is the case, any tips for backing up /home?

Also, when you are re-installing your system but have a seperate /home partition, will the Live CD know that you already have a /home directory and not create one in the / directory?

Thanks!

---

### Post by jnw222 on 2009-01-16
i can help with the liveCD

The liveCD WILL NOT detect that you have a /home partition and therefore, you will have to do three things

1. "edit partition" on the /home partition and set the mount point to /home 
2. make sure the /home partition is NOT SET TO BE FORMATTED
3 make sure u use the EXACT username and password

and for backing up /home, just copy the ENTIRE directory somewhere or use somethin along the lines 

dd if=/dev/(home partition) of=/backupofhome

---

### Post by drjonze on 2009-01-16
> **jnw222 said:**
> i can help with the liveCD

The liveCD WILL NOT detect that you have a /home partition and therefore, you will have to do three things

1. "edit partition" on the /home partition and set the mount point to /home 
2. make sure the /home partition is NOT SET TO BE FORMATTED
3 make sure u use the EXACT username and password


Thanks!

I'm so glad I asked. I was thinking that it would detect it. Again, 5 minutes spent consulting the forum has probably saved me an hour's worth of frustration.

I laugh when people say they don't want to use Ubuntu because there's no real support structure. I get better support from the forum than I have from any corporation.

---

### Post by jnw222 on 2009-01-16
hey that is what we are here for

we ask questions and answer others

---

