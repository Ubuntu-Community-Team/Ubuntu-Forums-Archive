---
title: "Cannot add users in setup or after?"
date: 2005-12-19
forum: General Help
---

### Post by starscream1 on 2005-12-19
I have just installed ubuntu onto a laptop dual booting with windows XP. The hard drive has 1 NTFS partition for Windows XP and has an ext3 for ubuntu, a swap partition and a fat32 partition I want to use for emergencies and as an OS share. However, I mounted the fat32 panel as /home could this be why I have the following problem:

While installing ubuntu it came to the add users and passwords bit of the installation. It allowed me to assign a root password but when I added a non-administrative user it would not let me. It allowed me to add a name, username, password and password confirmation but then went back to ask for a name for the new user and went into a loop. I had to skip this part of the installation or I could not install ubuntu. 

So...I finally got it installed and could not log into ubuntu from the gnome gui as root (which is the only user in ubuntu so far)

I tried booting in failsafe mode and at the prompt typed "adduser username admin" but it just said that the username I was trying to add was not present and did not seem to create one. I also tried to add the admin group again.

I am now going to try a final effort of adding a different user group other than admin and try adding users. If this does not work I am going to try reinstalling and mounting the fat32 partition as /windows instead of /home to see if that works.

Before I reinstall ubuntu can anyone tell me a solution to my problem as I dont want to have to reintall as it seems ok other than having no users to log on with.

Any help appreciated.

Also does anyone know the real reason why this situation has occurred.

Thanks,

John

---

### Post by arctic on 2005-12-19
If you want to use Linux, you CANNOT install its apps or /home on a FAT or NTFS partition. Linux partitions MUST be ext2, ext3, reiserfs, reiser4, xfs or jfs! I recommend to set up ext3 or reiserfs as /home.

---

### Post by starscream1 on 2005-12-19
so if I do not assign /home a partition will ubuntu automatically use a part of the  main linux ext3 partition I created?

Also could this be why I cant add users?

---

### Post by arctic on 2005-12-19
If you do not assign a special partition for /home, it will be placed in /root filesystem. But I discourage from doing that due to security reasons. What you could try to do (If you think you are already up to the task) is to boot into rescue mode and edit the /etc/fstab file from the command line, using an editor like nano or vi or emacs. Uncomment the /home partition entry, then save the file. Now reformat the drive you want to use as /home partition in ext3 format and change /fstab again so it uses the right partition number and filesystem entries. I know, tempting for newbies. If you are not up to the task, do a reinstall. After all it doesn't take so long.

---

