---
title: "Stupid ftp Question"
date: 2006-01-13
forum: General Help
---

### Post by darkFlame on 2006-01-13
As a fairly new linux user, I have a question that I'm sure a lot of you veteran folks could answer in a heartbeat. I've tried on a few occasions to use the ftp command to upload files to my personal ftp server running on a WinXP box using the FileZilla server. The linux ftp command behaves as expected and works without issue, but when I try to open or read from the files while in XP, they seem corrupted; I can't decompress zip files and photos come out all mangled. Is this a usual flaw in trying to transfer files from ext3 to ntfs or is there maybe something weird with my ftp server or ubuntu installtion? Transferring files has always worked perfectly between two Windows boxes, by the way.

Thanks in advance.

---

### Post by kostkon on 2006-01-13
Maybe because you try to upload binary files as text (ASCII). I mean you don't specify that before you upload your files. Type *binary* to set the file transfer mode to Binary and then try again with *put*.

---

### Post by professor_chaos on 2006-01-13
I wouldn't think this would be a function of linux, or the ext3 format. I have seen files become corrupted when the wrong type is used (binary or ascii). if your using the ftp command in linux, you can try the -d or and -v options for more information on the transfer. You can also try a GUI based ftp program like gftp. It is located in the repository.

---

### Post by Azion on 2006-01-13
It's probably what the lads said.
Set it to binary and see if it works.

---

### Post by darkFlame on 2006-01-13
See, I knew it was something riduclously simple. :) 
Thanks guys, really appreciate it.

---

