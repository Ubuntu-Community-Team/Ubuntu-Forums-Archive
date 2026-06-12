---
title: "Mounting logical partition in /home/user"
date: 2009-04-26
forum: General Help
---

### Post by dranger92 on 2009-04-26
Is there any way where i can mount a logical partition in /home/(user name) so that each user gets a new partition.

I first deleted all user accounts including usernames in home directory

Then i used root login and added these lines to fstab

/dev/sda5 /home/dranger ext3 nodev,nosuid 0 2
/dev/sda6 /home/scorncer ext3 nodev,nosuid 0 2

Then i created the user accounts using Users and Groups after reboot

But it does not work and i do not know where i went wrong
Can anyone help thanks in advance

---

### Post by Tim Sharitt on 2009-04-26
You will probably need to created the users with the partitions unmounted. 

Then copy the files and folders (be sure to copy the hidden files as well) in the newly created user directories to their respective partitions. 

You can then mount the partitions over the user directories.

---

### Post by Klaz168 on 2009-04-26
I'm not sure if I understand you correctly, how do u mean by each user gets a new partition?

If your trying to mount your drives so all users on system have access to it, then add 'users' to the options field.

---

### Post by dranger92 on 2009-04-26
> **Klaz168 said:**
> I'm not sure if I understand you correctly, how do u mean by each user gets a new partition?
I have 2 logical partitions and 2 users so i just want to move their respective folders inside the /home directory to their respective partitions.

---

### Post by dranger92 on 2009-04-26
> **Tim Sharitt said:**
> You will probably need to created the users with the partitions unmounted. 

Then copy the files and folders (be sure to copy the hidden files as well) in the newly created user directories to their respective partitions. 

You can then mount the partitions over the user directories.

Hey thanks very much it works:)

---

