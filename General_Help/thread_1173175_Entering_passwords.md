---
title: "Entering passwords"
date: 2009-05-29
forum: General Help
---

### Post by nengracia on 2009-05-29
I have issues I wish you could help with...

I'm the sole owner and user of my desktop and it's quite annoying that everytime I mount a drive, install updates, partition a drive, etc., Ubuntu is always asking for my password.

Is it possible that I can override entering passwords everytime I do something administrative?

Need help. Thanks.

---

### Post by _Purple_ on 2009-05-29
You can add the tasks you want to do without entering password by adding them to the sudoers file. Check this thread for details:
[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

---

### Post by whoop on 2009-05-29
> **_Purple_ said:**
> You can add the tasks you want to do without entering password by adding them to the sudoers file. Check this thread for details:
[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

Although I wouldn't get too comfortable with that. Typing in your password reminds you of what you are doing can have a negative impact on your system... Quite useful if you had a couple of drinks, when you are tired, distracted etc.

---

### Post by _Purple_ on 2009-05-29
> **whoop said:**
> Although I wouldn't get too comfortable with that. Typing in your password reminds you of what you are doing can have a negative impact on your system... Quite useful if you had a couple of drinks, when you are tired, distracted etc.

True. Sorry, I missed the part where the OP mentioned about running all the administrative commands without password. For security reasons it is not advisable to run all the administrative tasks without password, specially install packages and partitioning. However, partitions can be mounted without the password by adding it to fstab file.

---

