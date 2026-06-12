---
title: "/ with no more room + deleting issues...  PLEASE HELP"
date: 2009-01-08
forum: General Help
---

### Post by jdm2 on 2009-01-08
I haven't been using this machine for a while. I don't have access to it at this moment. So I know it will be hard to help me with what I need to know, but I appreciate all the help that you can give me. 

The machine is a desktop that was installed with ubuntu 6.06 desktop version and the teacher has upgraded it to ubuntu 8.04 desktop version. 

I know I haven't been on for a while, so if this is the wrong place to post this question I'm sorry. 

The machine is being used as a file sever. It has 2 hard drives in it. One is the main filesystem and the other stores all of the students work on it. 

The main hard drive with the filesystem on it has run out of room. I backed up the backups that were on it. The backups were around 6 gbs total. I backed them up and then deleted them, but for some reason it didn't free up space. 

I need to know what to do in this case. I was using sudo nautilus when I deleted it. I checked under root to see if it was in the .Trash folder and I didn't see it. 

Any ideas???

Thanks for the help. 

P.S. If I can't get it fix tomorrow we are planning on using a program to backup the system to cds then putting in a new hard drive and then using the cds to restore it. Do you see a problem with that? Thinking of using modo rescue. 

Thanks for the help.

---

### Post by bodhi.zazen on 2009-01-08
First thing that comes to mind is that the deleted backups are in the trash, either your users or root's.

---

### Post by jdm2 on 2009-01-08
I check both root and the user trash folder.  I didn't see anything in either of them.

---

### Post by mssever on 2009-01-08
The best tool I know for finding out where all your disk space has gone is baobab. Give it a whirl.

---

### Post by jerome1232 on 2009-01-08
du is also great for figuring out where all the space has gone.

```
sudo du -hx --max-depth=1 /
```

---

### Post by albinootje on 2009-01-09
> **jdm2 said:**
>  The main hard drive with the filesystem on it has run out of room. I backed up the backups that were on it. The backups were around 6 gbs total. I backed them up and then deleted them, but for some reason it didn't free up space. 

In the past I've seen "df" behaving a little strange after a disk had been completely full. 
A reboot (.. yes :( ) can make things clearer for df.

Places to check for loads of taken disk space :
```

sudo du -sh /var/log
sudo du -sh /tmp
sudo du -sh /var/tmp
sudo du -sh /var/cache/apt/archives   (sudo apt-get clean is a good idea)
sudo du -sh /root

```

Did you check ~/.Trash and ~/.local/share/Trash for your user and root ?

---

### Post by albinootje on 2009-01-09
> **mssever said:**
> The best tool I know for finding out where all your disk space has gone is baobab. Give it a whirl.

In Intrepid (and Hardy too I think) baobab is called "Disk Usage Analyser" in the menu.

---

### Post by jdm2 on 2009-01-09
I only check the .Trash folder for root and the user.  I will check the other places tomorrow.  I did install xdiskusage and used that.  I said / was 100% and the high, beside the mount point for the second hard drive was the modules folder with 13%.

---

### Post by jdm2 on 2009-01-09
I found where the files are at.  They are in /root/local/share/Trash

The only thing is that I don't have permission to delete them.  

I using sudo nautilus to view them and it won't let me delete them  I says I have the right to delete and create folder, but I try to apply the permission for read and write and it won't stay.  

Any ideas???

---

### Post by albinootje on 2009-01-09
> **jdm2 said:**
> I found where the files are at.  They are in /root/local/share/Trash

The only thing is that I don't have permission to delete them.  

I using sudo nautilus to view them and it won't let me delete them  I says I have the right to delete and create folder, but I try to apply the permission for read and write and it won't stay.

Can you try shift+delete on the files and/or directories that you want to delete ?
Be careful, shift+delete does bypass any trash.

---

### Post by mssever on 2009-01-09
> **jdm2 said:**
> I found where the files are at.  They are in /root/local/share/Trash

The only thing is that I don't have permission to delete them.  

I using sudo nautilus to view them and it won't let me delete them  I says I have the right to delete and create folder, but I try to apply the permission for read and write and it won't stay.  

Any ideas???
Time to get the big guns out. Open up a terminal and type:```
sudo rm -rf /root/local/share/Trash
```If you still get errors, post the results of ```
ls -lh /root/local/share/Trash
```Feel free to post just a representative snippet if the listing is long.

---

### Post by jdm2 on 2009-01-09
> **mssever said:**
> Time to get the big guns out. Open up a terminal and type:```
sudo rm -rf /root/local/share/Trash
```If you still get errors, post the results of ```
ls -lh /root/local/share/Trash
```Feel free to post just a representative snippet if the listing is long.

Thanks for the help.  I did something like the rm command.  I don't have the actual command in front of me, but it had that in it.  It got rid of the files.  Right now I'm doing mondoarchive to create a backup of the whole system.  Thanks for the help.  

P.S.  Thanks I didn't know about the shift + delete feature.

---

