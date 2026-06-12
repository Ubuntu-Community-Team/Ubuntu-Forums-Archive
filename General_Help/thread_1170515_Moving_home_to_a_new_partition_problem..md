---
title: "Moving /home to a new partition problem."
date: 2009-05-26
forum: General Help
---

### Post by aldav on 2009-05-26
I recently installed ubuntu on a virtual machine. I decided to install using a virtual disk of 10 GB, and partitioned the disk to create /home, / and swap partitions. After installation of the OS and a lot of apps, / partition went out of space. I decided to create another virtual disk, moved the swap and /home partitions to it, and resize / partition to fill the entire old virtual disk of 10 GB. I proceeded according to these steps:
1. Create the new virtual disk.
2. Format the new swap partition
3. Format the new partition in which /home will be located
4. Move /home to the new partition using cp command.

When I log using the console, everything is fine. The new virtual disk is mounted on /home, so no problem. The problem comes when I try to log using KDE. Then I get two error messages:

1. Could not update ICEauthority file /home/alfredo/.ICEauthority

2. There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256

And it stays frozzen. Any ideas?

---

### Post by Alekz_ on 2009-05-26
Did you update the /etc/fstab file?

If you've changed a mounting point, you probably need to 'fix' the file!

---

### Post by drs305 on 2009-05-26
For the first problem, it may be due to permissions. When you copied your $HOME, did you use the "-p" switch. That preserves all the original permissions. Check the permissions of the .ICEauthority file. Mine is 600.
```
sudo chmod 600 $HOME/.ICEauthority
```

---

### Post by aldav on 2009-05-26
Yes, I did change /etc/fstab. I wasn't using -p when copying. Did it again using -p and it worked! Thanks a lot.:D

---

