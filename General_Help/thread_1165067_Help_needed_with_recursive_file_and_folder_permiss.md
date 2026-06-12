---
title: "Help needed with recursive file and folder permission change"
date: 2009-05-20
forum: General Help
---

### Post by DExcode on 2009-05-20
Hi all, I am posting here because I need some quick help and hoping that someone here can supply the answer.

The problem: When I upload an installation of Magento onto a server I need to change the folder and file permissions to suit the server. This normally means changing 775 to 755 and 664 to 644. This is not difficult in itself, the hassle is that there are 10,000 files and folders. Not all files are 664, some of them are 775.

The solution: I wish to run a script that recursively changes the file and folder permissions. What I need to do is just change all 775 files AND folders to 755 and also change all files from 664 to 644.

Is there a way I can check the folder/file permissions and if it is 775 change it to 755 and if it is 664, then change it to 644.

I know that the following sort of does what I want, but I need a bit finer control and change according to current permissions and not whether it is just a file or folder.

 [FONT=Calibri][COLOR=#0000bb]find [/COLOR][COLOR=#007700]. -[/COLOR][COLOR=#0000bb]type d [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]exec chmod 755 {} \[/COLOR][COLOR=#007700];[/COLOR][/FONT]
  [FONT=Calibri][COLOR=#0000bb]find [/COLOR][COLOR=#007700]. -[/COLOR][COLOR=#0000bb]type f [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]exec chmod 644 {} \[/COLOR][COLOR=#007700];[/COLOR][/FONT]
[FONT=Calibri][SIZE=2]
[/SIZE][/FONT]
[FONT=Calibri][FONT=Verdana][SIZE=2]Any help in this would be greatly appreciated.[/SIZE][/FONT][/FONT]

---

### Post by StuartN on 2009-05-20
> **DExcode said:**
> I need a bit finer control and change according to current permissions and not whether it is just a file or folder.

Just add the -perm option:

```
find . -type d -perm 775 -exec chmod 755 {} \;
```

---

### Post by DExcode on 2009-05-20
Thank you for the reply, this really helps.

To improve my ignorance can you please explain what the option -perm means.

Regards

---

### Post by geirha on 2009-05-20
-perm 775 will limit the match to files/directories having 775 permissions.

It sounds to me like you want to remove write access for the group on all files and directories. You can locate all those files and directories with
```
find . -perm -g=w -ls
```
If that looks like the files you want to change, then change the "-ls" to "-exec chmod g-w {} \;", or use xargs
```
find . -perm -g=w -print0 | xargs -0 chmod g-w --
```

See the man-page of find for more information
```
man find
```

---

### Post by DExcode on 2009-05-20
Thank you for the excellent reply. Indeed you got what I want to do exactly. Thanks for the reference to more information as well.

Regards

---

### Post by sisco311 on 2009-05-20
You can use the -R flag to remove the write access for group recursively:

```
chmod -R g-w /path/to/dir
``` 

;)

---

### Post by geirha on 2009-05-20
> **sisco311 said:**
> You can use the -R flag to remove the write access for group recursively:

```
chmod -R g-w /path/to/dir
``` 

;)

Yes, but I generally try to avoid using chmod's -R option. It's safe in Ubuntu, which has GNU chmod, but other Unix variants may have a different implementation of chmod. Some implementations follow symbolic links when the -R option is used, and if a symbolic link happens to point to / ... guess what happens? :) Using find with -exec or xargs is safer in that regard.

---

### Post by sisco311 on 2009-05-20
> **geirha said:**
> Yes, but I generally try to avoid using chmod's -R option. It's safe in Ubuntu, which has GNU chmod, but other Unix variants may have a different implementation of chmod. Some implementations follow symbolic links when the -R option is used, and if a symbolic link happens to point to / ... guess what happens? :) Using find with -exec or xargs is safer in that regard.

Good point. I didn't know that.

---

### Post by sisco311 on 2009-05-20
> **geirha said:**
> Yes, but I generally try to avoid using chmod's -R option. It's safe in Ubuntu, which has GNU chmod, but other Unix variants may have a different implementation of chmod. Some implementations follow symbolic links when the -R option is used, and if a symbolic link happens to point to / ... guess what happens? :) Using find with -exec or xargs is safer in that regard.

On the other hand chmod without the -R option changes the permissions of the pointed-to file.

To avoid this behavior, one could use something like:
```
find . -not type l -perm -g=w
``` 

I'm still wondering which is faster:
[list]
[*]find all file and remove the write access for group
```
find . -print0 | xarg -0 chmod g-w --
``` or
[*]find files with write access for group and remove the permission
```
find . -perm -g=w -print0 | xargs -0 chmod g-w --
```
[/list]

---

### Post by geirha on 2009-05-20
> **sisco311 said:**
> On the other hand chmod without the -R option changes the permissions of the pointed-to file.

To avoid this behavior, one could use something like:
```
find . -not type l -perm -g=w
``` 


Yes, indeed. Forgot about that. I usually specify either -type f or -type d.

> **sisco311 said:**
> 
I'm still wondering which is faster:
[list]
[*]find all file and remove the write access for group
```
find . -print0 | xarg -0 chmod g-w --
``` or
[*]find files with write access for group and remove the permission
```
find . -perm -g=w -print0 | xargs -0 chmod g-w --
```
[/list]

I would guess the latter, but the best way to know for sure is to make a test case.

---

