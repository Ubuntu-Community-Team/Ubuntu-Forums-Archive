---
title: "[SOLVED] When was Ubuntu first time installed?"
date: 2008-12-29
forum: General Help
---

### Post by el02 on 2008-12-29
I installed Ubuntu 8.10 sometime ago on my laptop.
Now I would like to find out when my Ubuntu was first installed on my laptop.

Is that possible, which log file can tell me this?

many thanks,
elinus

---

### Post by Sorivenul on 2008-12-29
syslog should tell you, but you won't need all of it:
```
sudo cat /var/log/installer/syslog | less
```
To exit the view, just type "q", without the quotes.

The date in syslog should be your install date. I'm currently working on a new setup, and my output begins with:
> Dec 26 05:49:31

---

### Post by sdennie on 2008-12-29
I don't know if logs are going to give you that information.  However, you can probably infer it by the timestamps on various things on your system.  For example, if you do an "ls -la" in your home directory, the oldest files you see are probably around the time you created your home directory (which is probably about the time you installed your system).

---

### Post by el02 on 2008-12-29
I think I am now convinced after seeing this entry from /var/log/installer/syslog

  Dec  8 14:41:37 ubuntu grub-installer: Installing GRUB to (hd0) as (hd0)...


Thank you so much Sorivenul & "vor"!

---

### Post by Sorivenul on 2008-12-29
Glad to help!

If your issue is resolved, please help others by marking this thread "Solved" using the "Thread Tools" link near the top right of the page.

Good luck!

---

### Post by Laestrygo on 2009-04-15
Just wanted to add that although Sorivenul's solution works and gives you the time of the installation it misses one little thing - THE YEAR ;)

To find it out try this:
```
ls -l /var/log/installer/
```

This way you can find that your system was originally installed back in 2007 ;)

```
ls -l /var/log/installer/
razem 980
-rw------- 1 root   root  28568 **2007**-10-26 02:19 casper.log
-rw-r--r-- 1 root   root 296528 **2007**-10-26 02:49 initial-status.gz
-rw------- 1 root   root 445873 **2007**-10-26 02:28 partman
-rw------- 1 syslog adm  211153 **2007**-10-26 02:49 syslog
-rw------- 1 root   root     15 **2007**-10-26 02:22 version

```

---

### Post by Sorivenul on 2009-04-15
> **Laestrygo said:**
> Just wanted to add that although Sorivenul's solution works and gives you the time of the installation it misses one little thing - THE YEAR ;)

Good catch, and nice addition.

---

