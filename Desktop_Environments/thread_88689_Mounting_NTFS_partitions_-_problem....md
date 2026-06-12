---
title: "Mounting NTFS partitions - problem..."
date: 2005-11-10
forum: Desktop Environments
---

### Post by //RF on 2005-11-10
Hello to everyone, my 1st post :)

Anyway, installed Kubuntu linux yesterday as i am trying to get finally rid of Windows completely. I have lots of data saved to my hard-disks which are partitioned in windows and are in NTFS format. I can mount them easily but the problem is very strange...

I have folders with names like {PICTURES} etc etc. but i cant see/access to those at all. Other folders i see perfectly and can access them without any problems.

Is there something what i can do to access to those folders also?

Has it something to do with those starting letters of the folder name?


//RF

---

### Post by steve0921 on 2005-11-10
I'm no guru, but I'd be willing to be that the curly braces are giving you the problem. I just ran 'mkdir {PICTURES}' as a test and it didn't give me an error, but it dropped the braces from the name of the created folder.

If there aren't too many such folders, and you're not too attached to the names as is, I would try renaming them.

I'm not sure what the braces actually mean, but I think this would solve the problem.

---

### Post by Kapre on 2005-11-10
[QUOTE=//RF]Hello to everyone, my 1st post :)

Anyway, installed Kubuntu linux yesterday as i am trying to get finally rid of Windows completely. I have lots of data saved to my hard-disks which are partitioned in windows and are in NTFS format. I can mount them easily but the problem is very strange...

I have folders with names like {PICTURES} etc etc. but i cant see/access to those at all. Other folders i see perfectly and can access them without any problems.

Is there something what i can do to access to those folders also?

Has it something to do with those starting letters of the folder name?

//RF[/QUOTE]

since it's an NTFS format - maybe the braces means that the folder is password protected that is why it is in braces (and you can see/access the other ones)

K

---

### Post by //RF on 2005-11-10
1st of all, thanks for VERY fast answers.

2nd, The folders are not protected at all.

So, is there only one solution:

Installing Windows again for renaming the folders and then installing linux back and mount them :D. Sounds too difficult to be the only solution.

//RF

---

### Post by //RF on 2005-11-10
Why do i always ask before i read things carefully, so i mounted the hard disk with command:
```
sudo mount -t ntfs -o umask=0222,nls=utf8 /dev/sdb1 /mnt/test
```

and booom, it worked flawlessly.

Anyway, thanks for quick answers and support, great forum this is.

---

### Post by Kapre on 2005-11-10
[QUOTE=//RF]1st of all, thanks for VERY fast answers.

2nd, The folders are not protected at all.

So, is there only one solution:

Installing Windows again for renaming the folders and then installing linux back and mount them :D. Sounds too difficult to be the only solution.

//RF[/QUOTE]

Can you try and use a liveCD, just boot with it and make a new folder and copy all the files on this {PICTURES} folder to a new folder so you can access them.

K

---

