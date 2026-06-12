---
title: "100% disk used root partition"
date: 2009-03-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by johnbarlow on 2009-03-28
I bought a dell minin 9 inspirion and I receive a message that I have no free space on my root partition. I bought a new external hard drive, how can I move the files from the small dell hard drive to my new external hard drive. They are attachments to the evolution mail system I have deleted.
John

---

### Post by pytheas22 on 2009-03-28
All of Evolution's files for your user account should be stored in a directory at ~/.evolution.  To access it, open your 'Home Folder' from the 'Places' menu, then press control-H to show hidden files.  With the hidden files visible, you should see a folder named '.evolution' (note the . ).  If you delete this folder or move it to your external hard disk, it should remove all of your email attachments and email stored in Evolution, along with all of your other Evolution settings (don't delete the folder unless you don't care about any email you currently have stored in Evolution).

Keep in mind that depending on how you go about deleting the .evolution folder, you will probably have to empty the trash before it actually disappears from disk and frees up the space.

---

### Post by Sir_Hellraiser on 2009-03-29
> **pytheas22 said:**
> All of Evolution's files for your user account should be stored in a directory at ~/.evolution.  To access it, open your 'Home Folder' from the 'Places' menu, then press control-H to show hidden files.  With the hidden files visible, you should see a folder named '.evolution' (note the . ).  If you delete this folder or move it to your external hard disk, it should remove all of your email attachments and email stored in Evolution, along with all of your other Evolution settings (don't delete the folder unless you don't care about any email you currently have stored in Evolution).

Keep in mind that depending on how you go about deleting the .evolution folder, you will probably have to empty the trash before it actually disappears from disk and frees up the space.
what if you dont use eveolution but get the same message

---

### Post by 3Miro on 2009-03-29
It depends on how you have partitioned your HDD. I think the default Ubuntu setting is to have a root partition /, swap and a home partition /home.

If you only have two partitions, then you this message means thta you have filled up your HDD. To verify use the df (disk free) command in the terminal. Then you need to move some files (such as maybe movies or mp3s) to another internal/external harddrive, burn them to CD/DVDs and delete them from the HDD to free up space.

If you have the default three partition scheme (df would also let you see the partitions), then it becomes a bit harder. First I should note that I find very unlikely that the / partition became full from regular usage. Then you will have to see if there are any big files that don't belong there, it is tricky because messing with files in /something can badly damage your system.

---

### Post by CatKiller on 2009-03-29
Run (Alt-F2) ```
gksudo boabab
``` That will show you where all your disk space is being used. I don't know how much space there is in the Mini 9, but there were some complaints a while ago that the log files were becoming extraordinarily large for some people. These would be in /var/log. You can generally delete these logs if you aren't interested in what they say, but I don't know if there was a solution to the log files becoming large in the first place.

You may find that all of the space is being used by your Home folder (unless it's changed recently the default is to have two partitions - on for / and one for swap) in which case you can just move your personal files to your external drive.

EDIT: The default configuration I mentioned was for the standard Ubuntu install. Perhaps Dell do things differently. If you do have a separate /home partition that still has plenty of space, and your / is full because of things that you want to keep, it is possible to use GParted to shrink your /home partition and increase the size of your / partition. It all depends on where the space is being used.

---

### Post by Sir_Hellraiser on 2009-03-29
i downloaded some app frostwire and then gnome 2 and one other along with some  mps from frostwire  i will give that a try when i get home today

---

### Post by lavy on 2009-04-03
Hy,

From shell run the following commands:

$ cd /var/log

$ du (shows space occupied by logs)

(if they take a lot of space, you can safely delete them. The logs can fill up all the space on the disk)

To fix the problem

$pwd
[COLOR="Red"](make sure you are in /var/log directory)[/COLOR]

[COLOR="Red"]Before you run the following command, be very careful that you are in the /var/log directory and not in / when you run this command, because you will delete all your files on /; you can verify that with the pwd command [/COLOR]

$ sudo rm -rf *.*   

Logs are now deleted. You should set up a cron job to delete them automatically.


Regards,

---

### Post by anjilslaire on 2009-04-04
> **3Miro said:**
> It depends on how you have partitioned your HDD. I think the default Ubuntu setting is to have a root partition /, swap and a home partition /home.

Actually, the default ubuntu install is everything but swap in a single partion, including home.

However, I don't believe the Mini 9 has a swap partition, as Dell offers an option with only a 4gig SSD.

I ran with the Dell OS for about an hour before wiping and loading x86 Ubuntu 810. Granted, I ordered mine with a 32gig SSD

---

