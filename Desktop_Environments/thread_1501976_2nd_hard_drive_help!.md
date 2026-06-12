---
title: "2nd hard drive help!"
date: 2010-06-04
forum: Desktop Environments
---

### Post by Slayn2034 on 2010-06-04
ok i have Ubuntu 8.04

i just installed a 1TB hard drive, its formatted fat32.
i've been hunting through these forums for the past 3 hours and have not found a straight answer.
i just simply want my user account to have the permissions to read write and execute from this drive,  the drive is internal.
its frustrating because everything i try doesnt work because when you mount the drive the ownership goes back to ROOT.
i just want to simply want to be able to drag and drop files.
am i missing a step or what?
i tried CHMOD
i've tried CHOWN
and i even adding lines to the fstab
but regardless everytime i mount the drive, permissions shift back to ROOT(and no i dont want to sign into root each time)
can somebody please give me a straight answer and i mean a straight answer...

---

### Post by 3Miro on 2010-06-05
Hardly an expert opinion, but here is what I have done in the past:

1. Create a mount point folder in the /media:
```
sudo mkdir /media/MyHDD
```
(you should change MyHDD to whatever you want)

2. Check the UUID number of your extra drive.
```
sudo blkid
```
You should get something like:
```
/dev/sda1: UUID="***" TYPE="ext4" 
/dev/sda5: UUID="***" TYPE="swap" 
/dev/sda6: UUID="***" TYPE="ext4" 
/dev/sda7: UUID="***" TYPE="ext4"
```

3. Edit the /etc/fstab file to have the line:
```
UUID=*** /media/MyHDD     fat32   defaults        0       2
```

4. Type
```
sudo mount -a
```

5. Now, while the disk is mounted, you should change the permissions as:
```
sudo chmod your_username:your_username /media/MyHDD
```

This is what worked for me. I know it is not the most straight forward answer, but I hope it helps. I guess this is one of those things that can be done in so many different ways that everyone has their own favorite one.

---

### Post by Barafu Albino Cheetah on 2010-06-05
If I remember it right, defaults in fstab doesn't allow users to write files. you should write defaults,user,users,exec. Read_[FONT=Courier New] man fstab[/FONT]_ for parameters.

---

