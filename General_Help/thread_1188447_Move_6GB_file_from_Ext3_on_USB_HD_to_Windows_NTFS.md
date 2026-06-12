---
title: "Move 6GB file from Ext3 on USB HD to Windows NTFS"
date: 2009-06-15
forum: General Help
---

### Post by ajhanso on 2009-06-15
I had a system crash on Windows and the only way I could save my data was to use Ubuntu to recover the data onto another harddrive which had the ext3 file system.
 
One of my pst files is 6GB in size and no matter what I do, I cannot copy it back over to my windows  NTFS system so that I can read the pst with Outlook.
 
It seems no matter what I try, I am struggling to move the file from the ext3 file system over to the windows file system.  I have tried it from windows and ubuntu but no luck
 
I think I have tried everything but I am new to Ubuntu so I am hoping that someone will have a simple to understand method of moving this large file over to windows so I can read it again.
 
I am using ubuntu as a live USB at the moment.  Is this the problem or do I need to upgrade to ext4
 
Hope someone can help as I am desperate to get some data held on the pst file.:(

---

### Post by synapsys on 2009-06-15
How are you trying to copy the file?
Are you the superuser (admin) when doing it?

---

### Post by ajhanso on 2009-06-15
See you have gone and thrown me already.  How do I become a superuser?  Your going to have to be gentle with me becuase I have only been doing this for the last 48 hours

---

### Post by synapsys on 2009-06-15
Since you're new, and a windows user, I'll assume you're trying to do this graphically and not using a command line. You will need to figure out where the file is that you're trying to copy. If there is an icon on the desktop for the Ext3 partition then right click that and view properties. It should tell you where it is mounted e.g. (/mnt/sd**) 

Open up a terminal by going to Applications >> Accessories >> Terminal

And type:

```
sudo nautilus /mnt/sd**
```

sd** (being what you found in properties)

That should open it as a superuser and you should be able to copy files over from there.

---

### Post by ajhanso on 2009-06-15
OK, will do.
 
If this works I will kiss your little penguin feet

---

### Post by ajhanso on 2009-06-16
It seems that the superuser login was not the issue. It was becuase I realised that I was trying to copy over the PST file to a FAT32 drive and not NTFS. I thought the limitation was coming from the ext3 drive, but it was the recieving drive that was the problem.
 
I solved this by simply formating the recieving drive to NTFS. Then simply copied and pasted and it worked fine this time.
 
Learning all the time
 
Thanks

---

