---
title: "Using the file manager as a root user"
date: 2009-02-07
forum: General Help
---

### Post by DarkTxS on 2009-02-07
Hello everybody~

I've got Ubuntu 8.10 and XAMPP is installed on it. The file transferring on XAMPP is done by a regular FTP Client. It's installed in the /opt/lampp directory. Now, I would like to know if there's any option that I can use, paste, copy and edit files from XAMPP directory without using the FTP Client (Just root users can do it). I've installed XAMPP on my Eee PC as well, and there I use Xandros OS. I found there an option to use the file manager as a root user, so I could edit files directly through the XAMPP directory (without using the FTP Client).

I'd be glad to know if there's any way to do this in Ubuntu (:
Thanks a lot.

---

### Post by AlexBellisBrown on 2009-02-07
using the terminal: sudo nautilus

This will launch nautilus with root capibilities. Allow you to move files and folders. etc. Be carefull. You can mess up the system if you move something you shouldnt.

---

### Post by SuperSonic4 on 2009-02-07
Use gksudo since nautilus is a GUI app ```
gksudo nautilus
```

---

### Post by DarkTxS on 2009-02-07
Alright, got it done. And when I want to cancel it I just close the file manager, right?

Thanks again (:

---

### Post by SuperSonic4 on 2009-02-07
> **DarkTxS said:**
> Alright, got it done. And when I want to cancel it I just close the file manages, right?

Thanks again (:

Yes that's right

---

### Post by DarkTxS on 2009-02-07
Works very well! Thank you (:

---

### Post by AlexBellisBrown on 2009-02-07
Mark as solved? ;)

---

