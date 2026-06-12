---
title: "tomboy 0.10 and sshfs ?"
date: 2008-04-18
forum: Desktop Environments
---

### Post by jamaas on 2008-04-18
I'm attempting to get tomboy notes to sync to a server using sshfs.  I followed instructions and it gets as far as trying to connect to remote sever, gives error message.  When I look in the .tomboy.log file it says 

 [DEBUG]: Unexpected error calling sshfs.SaveConfiguration: Access to the path "/.............../.tomboy/sync-sshfs/test" is denied.

I've looked in this directory and the owner/group of this directory seems to change!  No idea how that could be but sometimes it is my username as both owner and group and others it is owner 1005, group 513.  I suspect this is the problem.  Any suggestions about how to set the owner/group to the correct settings, whatever they are and then keep them that way?

Thanks a bunch

Jim

---

