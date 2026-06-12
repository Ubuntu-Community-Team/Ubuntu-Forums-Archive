---
title: "Enhanced CD or CD Extra"
date: 2006-08-26
forum: Desktop Environments
---

### Post by Corey on 2006-08-26
I'm trying to burn an Enchanced CD. A CD that has audio tracks followed by a data track in a seperate session. I cannot for the life of me get it to work though. The only program I've found that explicitly supports it is K3B but every enhanced CD I've burned has failed to finalize on the 2nd session resulting in just a plain audio CD that isn't finalized and no data. Nero for linux mentions Enhanced CD support but I can' find and instructions for how to do it or and obvious ways in the program. I think it just supports copying  an enhanced CD to another enhanced CD but not the creation of one from scratch. Bonfire doesn't appear to have working multisessions support yet, xcdroast requires SCSI emulation which I don't have setup and seems like a step backwards anway. I'll do it if I have to though. Gnomebaker doesn't have any clear way to accomplish this either. Has anyone sucsessfully made a Extra-CD in linux?

---

### Post by Corey on 2006-08-27
As much as I love GUI tools, I was able to do think with all command line tools and it worked! I used normalize to normalize the tracks. cdrecord to burn the audio tracks, mkisofs to make the data track and cdrecord again to burn the data track as a seperate session.

---

