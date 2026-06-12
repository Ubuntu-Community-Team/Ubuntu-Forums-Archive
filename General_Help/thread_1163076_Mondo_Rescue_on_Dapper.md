---
title: "Mondo Rescue on Dapper"
date: 2009-05-18
forum: General Help
---

### Post by eoindubh on 2009-05-18
I will preface this by saying that I have some experience with Linux but not a lot. Due to staff cuts I have had to take over the management of the Linux servers as well as the MS stuff. 
 
I have a SubVersion server on Unbuntu 6.06.2 that has been using Mondo Rescue for some years now. The last weekly system backup failed because it was unable to remove the previous weeks .iso files. 
 
When the backup is complete the .iso image are FTPed to a Samba share on a Windows server and burned to DVD. When the next weekly backup starts, the old .iso files are deleted from the directory on the Unbuntu server and the backup is run. I got a message that the .iso files were unable to be deleted this week because they are read-only file systems. I cannot delete, rename or overwrite them. CHMOD will not touch them.
 
How do I get rid of the old .iso files so the backups will run again?
 
Thanks

---

