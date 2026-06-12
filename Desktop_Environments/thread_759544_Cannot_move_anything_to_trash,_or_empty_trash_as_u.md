---
title: "Cannot move anything to trash, or empty trash as user"
date: 2008-04-19
forum: Desktop Environments
---

### Post by konungursvia on 2008-04-19
I thought I'd wait a few weeks, for this to be fixed, but it hasn't in the last month. I'm runninig 64-bit hardy, most things work fine, but whenever I use nautilus or thunar to delete something, I get a pop-up box saying the file(s) cannot be moved to the trash, Skip, Delete, Delete All, Permanently are the options. In short, as my regular user, it seems no apps have permission to write to the trash folders. I am also unable to empty the trash (or was a month ago). Am I the only one? Thanks in advance team.

---

### Post by Thanoulis on 2008-04-19
Maybe your *~/.Trash* directory has only root access...
Try to write in a terminal:
```
sudo chmod 666 ~/.Trash
```

---

### Post by say2sky on 2008-04-19
> **konungursvia said:**
> I thought I'd wait a few weeks, for this to be fixed, but it hasn't in the last month. I'm runninig 64-bit hardy, most things work fine, but whenever I use nautilus or thunar to delete something, I get a pop-up box saying the file(s) cannot be moved to the trash, Skip, Delete, Delete All, Permanently are the options. In short, as my regular user, it seems no apps have permission to write to the trash folders. I am also unable to empty the trash (or was a month ago). Am I the only one? Thanks in advance team.

The trash directory was ~/.trash but now in 8.04 version it is moved to .local/share/Trash/. So check the user permissions on it and all parent directory perhaps you can find the cause for your problem.

---

### Post by konungursvia on 2008-04-20
Combining your two instructions worked! Ty

---

### Post by mockdeep on 2008-04-26
I'm having the same problem but your solution doesn't seem to be working (although there is certainly a possibility that I might be doing something wrong).  My permissions look like this for .local:

drw-rw-rw-  3 mockdeep mockdeep   4096 2008-03-10 19:54 .local

even so when I try to change to the directory it says "Access Denied" and I am still unable to send files to the trash bin.  I tried changing the permissions for .local/, .local/share/, and .local/share/Trash/

Any help would be much appreciated.

---

### Post by mockdeep on 2008-04-26
Ok, got it missed the -x

---

### Post by konungursvia on 2008-05-04
Actually I jumped the gun. I thought it was fixed when I could now empty the trash. However, I did the chmod to the trash and still can't actually move anything to it. Strange, isn't it? I think it has to do with starting at RC5.

Is this the right set of permissions?

drwxr-xr-x 3 peter users 4096 2008-03-24 11:32 /home/peter/.local/share/Trash/files

---

### Post by konungursvia on 2008-05-04
...

---

### Post by frediE on 2008-06-25
soo i everything working fine on boot disk but i can not delete files on my second storage disk.  if i sudo nautilus, then root is able to.  however it creates this funky .Trash-0 directory....

is that an id or something?

i used to have to make .Trash-user and that would work but it broke in Hardy.


i bet we can get this if we all try...   :-)

---

### Post by frediE on 2008-07-03
ok i got it working.  looks like it is a combination of the folder name and the security permissions.

so lets say you have a user bob.  bob's user id is 1001 (root is 0).

create a folder on the root of the drive .Trash-1001
    so you would now have /.Trash-1001

then set the owner to bob
    sudo chown -R bob:bob .Trash-1001

then set the permissions for only bob.
    sudo chmod -R 700 .Trash-1001

this seemed to fix it on the the computers i has issues on.  good luck.  :-)

---

### Post by konungursvia on 2008-07-06
Thanks for the info, Fredie. Didn't work for me though. Where exactly on the root did you create the directory?

---

### Post by frediE on 2008-07-06
you caught me off guard for a second there...  :-)

root is / and i have my large hard drive mounted in /media/BIGDRIVE
i couldn't delete files from BIGDRIVE without created the .Trash-1001 file first.

so i made the the following folder /media/BIGDRIVE/.Trash-1001

also note looks like there are two folders under .Trash-1001 (guessing they are important.
    \files and \info

let me know if this works or if you have any other questions... i am glad to help.  :-)

---

