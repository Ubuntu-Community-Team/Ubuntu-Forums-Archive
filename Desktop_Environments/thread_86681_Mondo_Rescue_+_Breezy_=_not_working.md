---
title: "Mondo Rescue + Breezy = not working?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by redmoon on 2005-11-06
Hi,

I have updated to Breezy and cannot get Mondo Rescue to work (says something about Mindi not being installed properly). Can anyone provide a comprehensive explanation as to how I get it working so I can backup my drive please.

Thanks.

---

### Post by lexor on 2005-11-06
Its a bug if you search the forums you will see other posts about it. I tryed to use it a few days ago without any luck.

I did have some luck with Norton Ghost 2003, I booted up a floppy disk with network support to connect to a networkshare on the server, ran ghost from the server and dumped a image of the disk on the share, and have successfully restored from the ghost dump image.

I have read some posts that it is not wise to use ghost as it has problems reading linux partitions, But at least with dumping the whole disk I havent had any problems myself.

---

### Post by stevenospam on 2005-12-15
I got it working again by adding the debian testing package libraries to my apt sources.list.  I then installed the 2.04-7: i386 release and it all works.  I then deleted the debian testing from my sources.list.

---

