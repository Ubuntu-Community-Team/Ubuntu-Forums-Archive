---
title: "How do you speed up NFS mounts?"
date: 2005-07-12
forum: Desktop Environments
---

### Post by flak9 on 2005-07-12
I have a fairly large directory and it is pretty slow when I try to browse.  What can I issue to get faster browsing speeds.  (As fast as SMB browsing) 

I thought by issuing rsize=32768,wsize=32768 it would speed up and it did slighty.  Anyone have any other tips or tricks?

This is what I am using now.

```
sudo mount 192.168.0.252:/MP3 /home/ryan/Desktop/NShares/mp3 -o rsize=32768,wsize=32768
```

Thanks! :)

---

### Post by flak9 on 2005-07-13
I moved my rsize up to 64 and its still somewhat slow.  The server also pushes out at 64 max. Im stumped!?! :?

---

