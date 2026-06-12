---
title: "S1 vs S3 suspend in ubuntu 8.10"
date: 2009-03-06
forum: General Help
---

### Post by grafxalien on 2009-03-06
I recently installed ubuntu on a computer I am using as a media server.  I would like to start saving some power, so I want the server to go into suspend when idle, then come on when something tries to access the media.  The computer went into S3 suspend fine, but WAN didnt work.  I switched my bios to use S1 instead of S3 standby because any network activity should be able to bring it out of S1.  However, now that I switch to S1, the "suspend" option is completely gone from ubuntu.  If i switch the bios back to S3, "suspend" reappears in ubuntu.  Any ideas?

thanks

---

### Post by kanikilu on 2009-03-06
Someone more knowledgeable will correct me if I'm wrong, but I don't think you can wake a computer up just by trying to access data on it.

You can look into something like Wake-On-LAN, but I gave up trying to get it to work on my network...

---

### Post by grafxalien on 2009-03-06
in windows you can wake a computer from S1 from lan.  To wake from S3 you need to send a special packet to the computer i think

---

### Post by grafxalien on 2009-03-07
anyone?

---

### Post by Lack Thereof on 2009-04-08
I am also very interested in getting S1 suspend on my desktop, because my bios doesn't support S3 at all.  I can't get suspend in my shutdown menu, just hibernate (which doesn't work, but that's another thread).

---

