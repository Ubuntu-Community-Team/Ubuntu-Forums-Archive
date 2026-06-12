---
title: "Cannot change file permissions, tried everything obvious"
date: 2008-12-03
forum: General Help
---

### Post by 1awesomeguy on 2008-12-03
I am cutting and pasting all files from one external hard drive to the other. Many of these files were originally Windows files.

The process was going smoothly, until I hit some 10-20 files that will not copy over. These files are owned by root. I have tried the following to no avail:

1. "gksudo nautilus" to change file permissions and try to copy the file.
2. "sudo chmod 777" and "sudo chown"
3. reading the chown manual and searching all over Google

Does anybody know what may be happening here and how I can fix it?

Thanks in advanced!

---

### Post by Junkieman on 2008-12-03
hello, ive had the same problem. try changing the file owner to yourself:

```
chown yourname filename
```

Edit: sorry i know you've tried chown, but could you perhaps past the command and any resulting messages here for us?

---

### Post by 1awesomeguy on 2008-12-03
Thanks for the reply. The command goes through without any error messages as if it worked, but when I check the file I see it has not worked. Also, the file still has the same problem when being copied.

Here is the exact error message I receive when trying to copy the file:

> Error while copying "favicon.ico".
There was an error copying the file into /media/ella/eve-bk-2008-12-02/Docs/Websites(about06-2007)/- Backups/2007-05-18/PWebsite.info.
Error opening file: Permission denied

I get the same message for all the files I try to copy.

---

### Post by Lightstar on 2008-12-03
A friend of mine is having the exact same problem, for him it's a folder, I'd also like to know the solution if you, or anyone here finds it.  

His problem is with a .wine folder, when he tries to run wine programs it comes with some error that /.wine isn't owned by him.. then he changes the ownership to him (doesn't give any errors for ownership change), retries.. same thing.. the folder went back to ownership root.

---

### Post by falcon61102 on 2008-12-03
One thing you can try if you've tried all the terminal commands is opening nautilus with sudo and then editing the perferences while in that window.  To do so, open nautilus:
```
gksudo nautilus
```

Right click on the folder with the files that you want to copy and click on Properties.

Then click the permissions tab and you should see Owner at the top.  If your user name is there, then just click below that where it says Folder Access and select Create and Delete Files.

If your user name is not there then you need to chown it you first:
[code]chown USERNAME /LOCATION[code]

Make sure that you use the folder instead of the filenames and then go back to the properties in Nautilus and change that.

---

### Post by tjandracom on 2008-12-03
if it is a folder then you might want to use -R parameter to include all the files inside it.

```
sudo chown -R yourname:yourgroup /foldername 
```

or

```
sudo chmod -R u+rw,g+rw /foldername 
```

---

### Post by deadowl on 2008-12-03
why not just give others read/write permissions as root and create a copy in which your user is the owner if you can't figure it out the other ways?

---

### Post by 1awesomeguy on 2008-12-03
Thanks everybody for your ideas. It has already been more than I would have thought of, but I am still in a bind.

> **tjandracom said:**
> if it is a folder then you might want to use -R parameter to include all the files inside it.

```
sudo chown -R yourname:yourgroup /foldername 
```

or

```
sudo chmod -R u+rw,g+rw /foldername 
```

I did this:

```
chris@emily:~$ sudo chown -R chris:chris '/media/Black/Docs/Websites(about06-2007)/- Backups/2007-05-18/PWebsite.info'
chris@emily:~$ sudo chmod -R u+rw,g+rw '/media/Black/Docs/Websites(about06-2007)/- Backups/2007-05-18/PWebsite.info'

```

and the same thing happened. No error messages but the permissions did not change.

> **deadowl said:**
> why not just give others read/write permissions as root and create a copy in which your user is the owner if you can't figure it out the other ways?

I tried this, but I am unable to give anyone else permissions to the file nor copy the file. Good idea though.

---

### Post by deadowl on 2008-12-03
Try:
```
chris@emily:~$ sudo chown -R chris:chris '/media/Black/Docs/Websites(about06-2007)/- Backups/2007-05-18/PWebsite.info'
chris@emily:~$ sudo chmod -R ugo+rw '/media/Black/Docs/Websites(about06-2007)/- Backups/2007-05-18/PWebsite.info'

```

I don't know if you can actually separate permission levels by commas, but historically I've I've just put ugo+rw

---

### Post by bibleman on 2008-12-03
I don't know if it would help but you could change to the actual root user with
```
sudo su -
```
Then you could try using some of the commands you did before but without the sudo part. Windows has messed permissions on me before but I was always able to fix them as root.

---

### Post by tjandracom on 2008-12-03
[QUOTE="deadowl"]I don't know if you can actually separate permission levels by commas[/QUOTE]
yes you can, i always do that.

[QUOTE="1awesomeguy"]No error messages but the permissions did not change.[/QUOTE]

Is the owner changed?
Maybe you want to try login as root in terminal and do that again to see if it is a problem with your current user not having sudo privileges.

---

### Post by 1awesomeguy on 2008-12-04
> **tjandracom said:**
> yes you can, i always do that.



Is the owner changed?
Maybe you want to try login as root in terminal and do that again to see if it is a problem with your current user not having sudo privileges.

No, the owner did not change and sudo does work with other applications. What I assume is happening is that the owner is changed and then immediately does back to root. That is what happened when I tried to change the owner using gksu nataulis.

Anyone have any other ideas that may help? At this point I am pretty much open to anything.

---

### Post by Junkieman on 2008-12-04
this is some mystery. so we determined that changing the owner to root doesnt work. have you tried copying as root?

```
sudo cp -R source destination
```

you said you're copying from/to external drives, out of curiousity, what type of file systems are they?

---

### Post by 1awesomeguy on 2008-12-13
> **Junkieman said:**
> this is some mystery. so we determined that changing the owner to root doesnt work. have you tried copying as root?

```
sudo cp -R source destination
```

you said you're copying from/to external drives, out of curiousity, what type of file systems are they?


I was copying from an ntfs external hard drive (with files from Windows XP) to a ext3 one. I also tried moving the files from the first external hard drive to my Ubuntu desktop (a third ext3 hd), but has the same problem.

In the end, I was not able to fix the problem and gave up and reformated the ntfs drive to ext3.

Thanks everybody for all the help though.

---

### Post by Junkieman on 2008-12-15
> **1awesomeguy said:**
> I was copying from an ntfs external hard drive (with files from Windows XP) to a ext3 one. 

strange, i did the same this weekend, vista+ntfs to ubuntu+ext3, no problems. maybe something with ntfs storing extra stream info.

i did notice you tried changing the permissions on the mounted media, perhaps you cant change the owner/permissions for ntfs file systems?

---

### Post by bibleman on 2008-12-16
I have a similar setup where I backup to an external drive that is formatted ntfs. I have not noticed any problems with permissions, but I will be checking this out the next couple of days to see if I can replicate your problem on my system.

---

