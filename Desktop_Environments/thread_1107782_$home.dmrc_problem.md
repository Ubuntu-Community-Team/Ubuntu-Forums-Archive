---
title: "$home/.dmrc problem"
date: 2009-03-27
forum: Desktop Environments
---

### Post by Dai777 on 2009-03-27
I've just gone to sign in and I get teh error dialog saying:
user $HOME/.dmrc is is being ignored. File file should be owned by user and have 644 permissions. users $home must be owned by user and not writable by others.

I don't know why this is happening as I have not been playing with the system. How can I fix it. 

Any help would be appreciated.

---

### Post by stderr on 2009-03-27
Try running:

```
chmod 644 ~/.dmrc
```

and then post the output of 

```
ls -l ~/.dmrc
```

It could also be a wider permissions issue with your home directory, so let us know how that goes, and if needed we can either change ownership of dmrc back to you, or change your home directory's permissions back to the way they should be :)

---

### Post by Dai777 on 2009-03-27
> **stderr said:**
> Try running:

```
chmod 644 ~/.dmrc
```

and then post the output of 

```
ls -l ~/.dmrc
```

It could also be a wider permissions issue with your home directory, so let us know how that goes, and if needed we can either change ownership of dmrc back to you, or change your home directory's permissions back to the way they should be :)

here is what I have so far:

dai@dai-desktop:~$ chmod 644 ~/.dmrc
dai@dai-desktop:~$ ls -l ~/.dmrc
-rw-r--r-- 1 dai dai 28 2009-03-26 11:19 /home/dai/.dmrc
dai@dai-desktop:~$ 

dai@dai-desktop:~$ ls -l /home
total 4
drwxr-xr-x 100 dai dai 4096 2009-03-27 14:29 dai
dai@dai-desktop:~$

---

### Post by Dai777 on 2009-03-27
> **Dai777 said:**
> here is what I have so far:

dai@dai-desktop:~$ chmod 644 ~/.dmrc
dai@dai-desktop:~$ ls -l ~/.dmrc
-rw-r--r-- 1 dai dai 28 2009-03-26 11:19 /home/dai/.dmrc
dai@dai-desktop:~$ 

dai@dai-desktop:~$ ls -l /home
total 4
drwxr-xr-x 100 dai dai 4096 2009-03-27 14:29 dai
dai@dai-desktop:~$

seems to have sorted the sign in issue.

Thanks

---

### Post by stderr on 2009-03-27
Yep, those permissions and ownerships given by ls -l look fine now :) 
No problem.

Just for anyone else who finds this thread and who hasn't found a solution yet, the other steps you could have tried had the above not worked would have been along the lines of:
 
**Correct ownership of ~/.dmrc** (replace your_username with... your username, e.g. dai)
```
  $ sudo chown your_username:your_username /home/your_username/.dmrc
```

**Correct home permissions**
(all users can read your home files, only you can write them)
```
  $ chmod -R 755 ~
```
... or, you could choose to use different permissions, such as 
(only your user can read your home files)
```
  $ chmod -R 700 ~
```

---

