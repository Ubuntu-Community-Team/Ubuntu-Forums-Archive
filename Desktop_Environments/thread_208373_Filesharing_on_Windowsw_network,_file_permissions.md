---
title: "Filesharing on Windowsw network, file permissions?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by Boomy on 2006-07-03
I have my  Ubuntu machine networked to my iBook and a Windows PC. I can write files to my Mac from Ubuntu, but I can't write files to Ubuntu from any other machine, it says I don't have permission. How can I set it up so I can drop files into my Ubuntu machine? thanks

---

### Post by queenorych on 2006-07-03
That's an easy or a diffiuclt answer.  The one I'd suggest is to look at your /etc/samba/smb.conf file.  By default all home directories are readonly.  THis is probably your problem.  The file is fairly well commented, and a google of smb.conf should be sufficient for most purposes.

Good luck

---

