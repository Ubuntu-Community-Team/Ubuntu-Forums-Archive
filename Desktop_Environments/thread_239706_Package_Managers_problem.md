---
title: "Package Managers problem"
date: 2006-08-19
forum: Desktop Environments
---

### Post by whistlerspa on 2006-08-19
I got a wierd message when attempting to install Kmail. It asked whetherr i wanted to install somethig to do with f-prot. I said yes and then the thing just hung. I had to kill the app but now I can't use either Add/ remove programs or Synaptic program manger as the y ask me to do the following

'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. '
 
When i do this from a terminal the following happens 

'Setting up f-prot-installer (0.5.21) ...
installing f-prot
Downloading file fp-linux-ws.tar.gz.md5 from ftp://ftp.f-prot.com/pub/linux/'

And then the terminal hangs indefinitely.:( 

Does anyone please know how to fix this?:(

---

### Post by editrix on 2006-08-21
f-prot is an anti-virus backend for KMail, which you probably don't need. It could be that the server is down. I don't know much about how to check whether an ftp server is actually alive.

You might want to try dpkg -r to remove the fprot that's partially downloaded file. **WARNING** I'm no expert on this. man dpkg gives info, but I'm not very good at deciphering it.

Sorry I can't be more help. If nothing else, I've bumped your post.

---

