---
title: "Rsync Help..."
date: 2005-05-14
forum: Desktop Environments
---

### Post by ryan.overton on 2005-05-14
I am backing up my server remotely with Rsync using this command, to a usb hd I have at my house.

rsync -azotv --rsh="ssh -l root" --progress--delete .xxx.xxx.xxx:"/path/on/remote/system" /path/on/local/system


the question I have is:

Once this backup is done...what is the command to keep both server in sync, constantly?  Or.. should the connection break, modify the files that only have been changed or written to since the first backup?

---

