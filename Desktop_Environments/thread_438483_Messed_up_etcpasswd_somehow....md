---
title: "Messed up /etc/passwd somehow..."
date: 2007-05-09
forum: Desktop Environments
---

### Post by necromantula on 2007-05-09
I was in SSH, wanted to look at all the installed accounts (its a server me and my friend run, its at his house)
i typed "vi /etc/passwd" and looked around
somehow,  i changed "root::-1:0:root:/root:/bin/bash" to "ro:-1:0:root:/bin/bash"
i thought i couldnt actually edit this without using sudo to get root...
Any ideas how to fix it? i think i am logged onto Gnome, but i dont see how i could edit this file now without being able to sudo/gksudo...
Help please?

---

### Post by taurus on 2007-05-09
You need to boot into recovery mode from GRUB menu or from a LiveCD.

---

### Post by necromantula on 2007-05-09
Would the Ubuntu 7.04 cd work? it booted live for the install...
and also, what would i do to fix it? change the line back to the old one?

---

### Post by taurus on 2007-05-09
Any LiveCD would work as long as you can boot from it.  Assuming / is on /dev/sda1, open a terminal and do

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/etc/passwd
```
and change it back to what it was before.

---

### Post by necromantula on 2007-05-09
Thanks, i knew the basic commands, this is just the first time ive managed to fry my linux to need to do this.

---

