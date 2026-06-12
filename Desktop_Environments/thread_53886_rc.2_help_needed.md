---
title: "rc.2 help needed"
date: 2005-08-02
forum: Desktop Environments
---

### Post by banditti on 2005-08-02
If I do a ls -l, I get the following:

lrwxrwxrwx  1 root root 23 2005-08-02 11:50 S20startupscript -> ../init.d/startupscript


I do I change that s20startupscript to s09startupscript?


Thank you in advance,

---

### Post by amohanty on 2005-08-02
Why do you want to do this again?

AM

---

### Post by banditti on 2005-08-02
I have to have this script load before GDM.

---

### Post by danns on 2005-08-02
sudo mv S20StartupScript S09StartupScript


just be sure you know what you are doing here and that StartupScript does not require a service that would be initialized prior to the script running.

---

### Post by banditti on 2005-08-02
Cannot move, no such file or directory.  I think it is a link of some sort.

---

### Post by banditti on 2005-08-02
I fat fingered it the first time.  Thanks!

---

