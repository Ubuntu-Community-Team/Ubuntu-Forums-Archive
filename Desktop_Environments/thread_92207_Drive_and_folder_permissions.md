---
title: "Drive and folder permissions"
date: 2005-11-19
forum: Desktop Environments
---

### Post by vishnumrao on 2005-11-19
Recently installed Breezy on my AMd64 machine. Breezy does not allow me to copy anything from one folder to another even as superuser. How do I set permissions to allow write access to all drives?

Thanking you in advance,
Vishnu Rao.

---

### Post by frodon on 2005-11-19
It's just a problem in your fstab file, post it here and we will tell you how to modify it to get read/write access as a simple user.
To open the file : ```
sudo gedit /etc/fstab
```

---

### Post by vishnumrao on 2005-11-19
Fordon,

Please find my fstab as attachment.

Thanks,
Vishnu Rao.

---

### Post by frodon on 2005-11-19
Ok, i joined to this post a version of your fstab file which will work, just cut and paste and do a "sudo mount -a" or reboot if you don't see any change.

---

### Post by Maverick911 on 2005-11-19
This might help you. 
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by vishnumrao on 2005-11-19
Thanks frodon,

I now have rw access to all my drives. But there are some folders which are locked. How do I gain access to these folders? Am logged in as superuser. 

Thanks,
Vishnu Rao.

---

### Post by frodon on 2005-11-19
which folders ?
All the folders in your ubuntu partition (except your /home) need root rights to be handled for security reasons.
Could you give me more details ?

---

### Post by vishnumrao on 2005-11-19
Let me explain my situation. I downloaded vmware virtual player(.tar.gz) to my desktop and extracted them to the desktop. since i could not install it thought will move from desktop to another folder. The extracted folder is locked. And does not allow me to move it. What can I do?

---

### Post by frodon on 2005-11-19
Strange, however it's on your ubuntu partition so you can do a "chmod 777 the_repertory" to get full rights (or a chown) and then move it where you want.
If you want to learn more about terminal commands, read the Kyral's guide : [http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

---

