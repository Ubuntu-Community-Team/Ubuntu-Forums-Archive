---
title: "Cannot change the permissions of all files in a folder."
date: 2008-04-25
forum: Desktop Environments
---

### Post by Bubtottle on 2008-04-25
Hello

I have a computer with Hardy Heron Ubuntu (Gnome) installed on it. 

I had some files on a Windows computer (mainly music files with some pictures and very few documents) and I have copied them across to my linux computer. However, when on my linux computer, I found that the files and folders all are owned by 'nobody' and thus I have no permissions to access them. I would like to change all the permissions so that my user is the owner of all the files. Following is a list of ways I have attempted to achieve this, all of which have failed.

-'sudo nautilus', changing the permissions of the directory all the files are in and then clicking 'Apply Permissions to Enclosed Files'. This had no effect on the enclosed files.
-'gksudo nautilus', same method and result as 'sudo nautilus'
-'sudo chown -R username:username /path' (replacing 'username' and 'path'), terminal just goes to a new line with nothing on it but the '>' symbol and nothing more happens.
-'chown -R user_name ~/folder_name', same as above
-'chmod -R 755 /folder/name', comes up with another prompt, nothing has happened.

Any help in changing all files, folders and subfolders would be greatly appreciated.

---

### Post by bingoUV on 2008-04-25
Can you post the output of the following command ?
```

sudo mount

```

---

### Post by Bubtottle on 2008-04-25
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/username/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=username)

I have replaced my account name with 'username'

---

### Post by Bubtottle on 2008-04-25
After playing around a bit more, I have found that if I copy all the files to a different directory (when I'm not root), the copied files are owned by my user. 
This solves my problem but I still do not know how to change the permissions of multiple files at once should I ever need to.

---

### Post by bingoUV on 2008-04-26
The filesystem that you are presumably using is writable, no problems there.   ```
 sudo chown -R username:username /path 
```  The above command is the one that should have worked. The reason why it gave a prompt with > sign is that you used some unterminated quotation mark in your command. Try it again and if it does not work, post here the exact command you used, without removing quotation marks from it.

---

### Post by NE Key on 2008-04-27
> **bingoUV said:**
>    ```
 sudo chown -R username:username /path 
```  .

Is that ;
sudo chown -R oldname:newname /path
OR
sudo chown -R newname: oldname /path

?????????????????

---

### Post by bingoUV on 2008-04-27
> **NE Key said:**
> Is that ;
sudo chown -R oldname:newname /path
OR
sudo chown -R newname: oldname /path

?????????????????

 Well, actually it is  ```
 sudo chown -R new_username:new_groupname /path 
```  It was written username:username becuase by default Ubuntu creates a group named identically as your username and adds the user to the group as a member. So the second username actually referred to this group identically named as the user.

---

### Post by hartdg on 2008-05-01
I have a similar problem. While I can revert to command line mode to change the ownership & permissions I'd far rather work in gui mode.

Any ideas on why the 'Apply Permissions to Enclosed Files' button in Nautilus does not work properly? I've tried using it before and found the results to be variable and frustrating. Is this a known bug?

---

### Post by bingoUV on 2008-05-01
> **hartdg said:**
> I have a similar problem. While I can revert to command line mode to change the ownership & permissions I'd far rather work in gui mode.

Any ideas on why the 'Apply Permissions to Enclosed Files' button in Nautilus does not work properly? I've tried using it before and found the results to be variable and frustrating. Is this a known bug?

 In my experience, it does work but it is a bit confusing. There are two sorts of permissions listed in the gui for a directory. File access and folder access. Since the current object is a folder, making any changes in file access part of it does not make any difference in its own permissions. But now if you click on 'Apply Permissions to Enclosed Files', these file permissions are applied to files within the directory. Also, these changes do not persist for the directory itself. Next time when you open the gui for directory permissions, file access part will be empty again.  
 
Does it not behave like this for you?

---

### Post by hartdg on 2008-05-01
Thanks. I'd not registered the distinction of folder vs. file permissions & I don't yet understand their interaction. Some reading to be done by me...

---

### Post by tautech on 2008-08-05
I also have the same problem..

Seems the only way to go at this stage is with command terminal.

chown changes the ownership of folders and files.
chmod changes writes to files.

The nice thing is it works and its fast at it.
Here are the commands in full.

"chown -hR root:users /home/folder"
the -hR alows changes to be made to all files and subfolders
the root:users > owner:group
the /home/folder refers to the folder you choose from the root and has to be enterd starting from the root and choosing the folder you want.

Now that your ownership and group rights have been done. You will have to do the read, write and executable options.

"chmod -R a +rwx /home/folder"
the -R changes all files and subfolders
a is for all the 3 security groups.. you can change this to
g for group, u for owner and o for other.. when you look at the file perrmisions in nautilus advanced file permisions you will get the idea behind this. the owner may be able to read write and execute but the group may only be able to write and the others will only be able to read the file.
+ can be changed to - (to take away a right)r=read w=write x=exe
/ anf the folder you want to change with ist contents

Hopes this helps others
I beleive it is better to learn the commands anyway because they work faster and can be used on most linux systems regardless of gui installed or not.

best of luck

---

