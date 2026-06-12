---
title: "Help. mount -t cifs terribly slow"
date: 2006-04-19
forum: Desktop Environments
---

### Post by anoveth on 2006-04-19
Hi.

I use cifs mount for sharing shared folder of windows XP Pro.
Unbuntu and Windows host are connected directly via hub.
It works well after mounted. But mounting itself takes 1-2 minutes terribly.
After mounted successfully, file transfer speed looks to be normal.

I used command as followings. nothing special.
mount -t cifs //nanoveth/D /media/cifs/nanoveth/D -o credentials=/etc/samba/smb.cred,iocharset=utf8

Can anyone explain possible reasons?

Thanks.

---

### Post by mlarsendk on 2007-02-28
I know this is old post, but I have same problem.
I mount CIFS shares via FSTAB. The shares gets mounted and is reported correctly when checking using mount command.

BUT! it takes several minutes before I can see the files!? (A ls command in /media/music shows "no files") If I wait 2-5 minutes, the files appear like magic!? No messages in /var/log/messages or dmesg.

Any suggestions are welcome!

---

