---
title: "why is /tmp not a tmpfs"
date: 2009-05-28
forum: General Help
---

### Post by lavinog on 2009-05-28
I was noticing that /tmp is not a tmpfs. Why is that?

Also, what command can be used to determine what file system a file or folder is part of?

---

### Post by Coreigh on 2009-05-28
I would like to know this too. Just for curiosity.

About the second part; The simple answer is ```
df -h
``` This displays all the mounted filesystems. So once you know the path to the folder in question you can determine your answer. It would not surprise me to find out there is a command you can run and give it a specific folder or path and have more detailed information returned.

---

### Post by VMC on 2009-05-28
> **lavinog said:**
> I was noticing that /tmp is not a tmpfs. Why is that?

Also, what command can be used to determine what file system a file or folder is part of?

tmpfs is a memory file system file system that uses virtual memory. It saves hard drive usage. Found on all ram type usage. "/tmp" is a folder where temporary files are stored. 

You could, I suppose mount it on /tmp, like so :mount_tmpfs tmpfs /tmp

---

### Post by Brandon Williams on 2009-05-29
You wouldn't get much benefit from making /tmp a tmpfs, since there's almost nothing stored there. Virtually all of the items there on a typical Jaunty filesystem are either locks or sockets, which means that they only get used for access control. There's no content in the files and they require very little disk access, so you wouldn't get a big benefit from using tmpfs, but there's also no reason _not_ to use tmpfs. You could easily change this on your system with no ill effects.

---

### Post by lavinog on 2009-05-29
I have noticed that flash will use this space to store youtube videos when they are being played, so I wonder if there could be an issue if there is a lack of ram for the video to be stored.
I can see a benefit using tmpfs to reduce hd activity, but log files and such would have to be moved to tmpfs as well

---

### Post by Brandon Williams on 2009-05-29
Good point ... some software uses /tmp for large files, like firefox, which puts files there when it downloads them for you to open in some external application. That's a pretty good argument in favor of not using tmpfs for /tmp. You could limit some amount of disk activity by using tmpfs, but only if you also found a way to limit the use of /tmp such that it doesn't get filled up with large temporary files. With large files in /tmp, using tmpfs would not only cause disk activity but also take up space in RAM and/or swap space.

---

### Post by HavocXphere on 2009-05-29
I think /dev/shm would serve the same purpose. Thats where I dump temp stuff. Read somewhere that it even resizes dynamically.

Only downsided is that is gets wiped on reboot.

---

### Post by lavinog on 2009-05-29
> **HavocXphere said:**
> I think /dev/shm would serve the same purpose. Thats where I dump temp stuff. Read somewhere that it even resizes dynamically.

Only downsided is that is gets wiped on reboot.

The odd thing is that the only thing using /dev/shm is a 65M pulse-shm file (related to pulseaudio no doubt)

after reading the man page for mktemp, it says if TMPDIR is set then it will use that in place of /tmp
I am going to give it a try and see.
I am sure the difference will be small.
My df for /dev/shm is about 2G, I doubt I will encounter a 2g temp file.
I also think that as more users are going to ssd drives, minimizing wear will be more important.

---

