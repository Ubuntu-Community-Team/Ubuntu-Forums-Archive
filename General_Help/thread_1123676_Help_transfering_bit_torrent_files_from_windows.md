---
title: "Help transfering bit torrent files from windows"
date: 2009-04-12
forum: General Help
---

### Post by jomo56 on 2009-04-12
I have some bit torrent files I downloaded while using windows.I have recently installed ubuntu and would like to be able to seed them on this os.How do I do this?

---

### Post by lovinglinux on 2009-04-12
That depends on the torrent client you are using. Basically you need to copy the files you are seeding (content) from Windows to the location where you save downloaded content using the new client on Ubuntu, then add the corresponding .torrent files to the torrent client list and do a re-check. The client will compare the metadata in the .torrent file with the downloaded content and determine the status of the download, which will be 100%. Once it completes the re-checking, it will start seeding the files.

---

### Post by jomo56 on 2009-04-13
OK I'll give it a try.Tried each of those but not together.Thanks.Tried moving my files but there wasn't enough space in the file.How do you change the default file sizes?Each file size is only 2.3g.

---

### Post by jomo56 on 2009-04-16
Thanks for your help,it worked.One last thing though,I have some video files that are over 7gs and when I try to move them into a file it says there is only 2.3g available and you need 7.3g.How do I transfer these big files when every folder will only take 2.3g(Im assuming at one time)?

---

### Post by lovinglinux on 2009-04-16
> **jomo56 said:**
> Thanks for your help,it worked.One last thing though,I have some video files that are over 7gs and when I try to move them into a file it says there is only 2.3g available and you need 7.3g.How do I transfer these big files when every folder will only take 2.3g(Im assuming at one time)?

I guess you are talking about torrents with multiple files inside. The problem is that to download single files from a multiple file torrent you need to use full allocation, which means the client needs to reserve the space required by the entire torrent content in advance. So even if you download one file at at time, the client will still need 7Gb space to be allocated in advance. You could use compact allocation, which means the client would reserve the space on-demand. Problem is that you can't use compact allocation and select a single file from a multiple file torrent.

---

### Post by jomo56 on 2009-04-17
I already have these downloaded on windows(I have more then one) and when I try to move them into my Public folder(one at a time) on ubuntu I get a pop up that says only 2gs available.This happens no matter where I try to put them,Desktop,documents or any other folder.I don't think it's the folder size.Does ubuntu have a limit on file sizes you can move into folders?

---

