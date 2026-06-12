---
title: "/home partition?"
date: 2009-03-04
forum: General Help
---

### Post by nothingspecial on 2009-03-04
I`m about to upgrade my wifes netbook to 8.10.

She would like to keep everything as it was.

I`ve read about a seperate /home partition but as I make a regular backup of her home directory, would removing the new home directory and replacing it with the latest backed up one have the same effect?

If so are there any pitfalls to watch for?

Thanks

**Edit, when I say upgrade, I mean a clean install **

---

### Post by albandy on 2009-03-04
yes, but only will work well if you install the same packages and users, and userid are the same.

So create the users in the same order you created before or change the owner of the files after restoring the backup

the best way to backup /home is with tar
sudo tar zcvfp /backupfolder/home.tgz /home
then restore it this way:
cd /
sudo tar zxvf /backupfolder/home.tgz

---

### Post by nothingspecial on 2009-03-04
Thanks

---

### Post by pmlxuser on 2009-03-04
sometimes you have an file ownership issue , but usually thats what i do when thing are really messed up with my system and it usually works OK

just make sure that when u back up u are not sudo; but just nomal user coz if the file ownership arise you can just do

```
 $sudo chown user:user /folder 
```

---

