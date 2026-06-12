---
title: "chown issues"
date: 2006-04-06
forum: Desktop Environments
---

### Post by CarbonPlexus on 2006-04-06
My files that I have on a seperate FAT32 partition are owned by root:root  I wanted to change the ownership to my name and group but when I use chown it says "operation not permitted" "failed to change ownership of ...."  I used chown with sudo figuring it'll see me as root and allow me to change it, but it's not. The strange thing is if I use sudo I can chmod the files and directories to rwxrwxrwx but even then it still won't let me change the owner or group.

it allows...
sudo chmod -R -v ugo=rwx [directory]  
and any variation of that

but not...
sudo chown -R -v [user]:[group] [directory]
sudo chown -R -v [user]: [directory]
sudo chown -R -v :[group] [directory]
sudo chown -R -v [user] [directory]

I even tried changing my username to be in the group 'root' hoping to get permission but the files don't seem to be able to be changed.  Can someone tell me what I'm doing wrong?

---

### Post by aysiu on 2006-04-06
You can't chown a Windows partition.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

