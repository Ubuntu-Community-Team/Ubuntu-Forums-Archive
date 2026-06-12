---
title: "How to move directories from command prompt"
date: 2009-05-27
forum: General Help
---

### Post by quickk on 2009-05-27
Hi everyone, 

   I want to move non-empty directories from the command prompt.  I thought that this would work:

```
move dir1 /path/dir2
```

but, if dir2 has some files in it, I get an error message: ```
Directory not empty
```.

How do I get around this?  Is there a way to tell it to merge both directories like Nautilus does?

Thanks!

---

### Post by nebileix on 2009-05-27
Try using the -v switch with mv command to find out which directory u cant move.

Possible cause will be with permission.

Or try with the -f(force) switch.

---

### Post by quickk on 2009-05-27
I tried with the --force switch and get the same error.  I also tried -v but I don't get any more info.  

It seems that the mv command fails whenever the target directory has stuff in it.  I find this really strange and can't seem to find a solution on google...

---

### Post by StuartN on 2009-05-27
mv (not move) will normally move a directory and all contents to a new path, without any switches, e.g. mv temp ~/Documents

---

### Post by nebileix on 2009-05-27
wat dir are u trying to move? there might be some files lock by certain process, therefore u cant move it i guess. Make sure u have the permission and access right for that dir.

---

### Post by CatKiller on 2009-05-27
I think, although I haven't tested it, that cp with the -u option will merge the directories. Then, if it works, you can delete the original.

---

### Post by ActiveFrost on 2009-05-27
Check [THIS]("http://linux.about.com/library/cmd/blcmdl1_mv.htm") ;)

---

### Post by CatKiller on 2009-05-27
> **ActiveFrost said:**
> Check [THIS]("http://linux.about.com/library/cmd/blcmdl1_mv.htm") ;)

...except the man page doesn't help because mv doesn't have a merge option...

I understand some people were writing it in sometime last year, but it hasn't happened yet, AFAIK.

---

### Post by boof1988 on 2009-05-27
> **quickk said:**
> Hi everyone, 

   I want to move non-empty directories from the command prompt.  I thought that this would work:

```
move dir1 /path/dir2
```

but, if dir2 has some files in it, I get an error message: ```
Directory not empty
```.

How do I get around this?  Is there a way to tell it to merge both directories like Nautilus does?

Thanks!

If you do not need to keep the name (dir1)... You could use the following...

```
mv /OtherPathAsNeeded/dir1/* /path/dir2/
```

The command will move all of the contents of dir1 to dir2.

Is this what you are looking for?

---

### Post by quickk on 2009-05-27
What I was trying to do is move over files from a previous home directory to a new one.  Maybe I'm wrong about this, but I thought that it was not a good idea to use the same home directory when installing a new version of Ubuntu.  So after an installation, I need to move some files over from the oldhome to the newhome.  For example:

```
mv \home\oldhome\Documents \home\newhome\Documents
```
```
mv \home\oldhome\Pictures \home\newhome\Pictures
```

I'm getting tired of always doing this manually with Nautilus and I am trying to write a script to automate the process.  Copying the files over isn't really an option because this would take far too long since I'm dealing with roughly 500GBs of data.  

From what I've learned, the mv command will fail if the target directory exists and has stuff in in.  I guess that I could delete the new directories that were created during the installation before moving the old one, but I'm afraid that I'd accidentally lose all my data (for example, if I accidentally run the script twice).  

Any suggestions?

---

### Post by quickk on 2009-05-27
> Check THIS
I have, and there is no merge option (maybe you should check it ;) )

> **boof1988 said:**
> If you do not need to keep the name (dir1)... You could use the following...

```
mv /OtherPathAsNeeded/dir1/* /path/dir2/
```

The command will move all of the contents of dir1 to dir2.

Is this what you are looking for?

This might work. It's still not ideal but a lot safer than my solution using rm!  Thanks :D

---

### Post by ActiveFrost on 2009-05-27
Let's say you've 2 directories :
```
/home/old/Documents
/home/new/Documents
```
You want to move your old files from the old dir to a new one :
```
mv /home/old/Documents/* /home/new/Documents/
```

Now, all your /home/old/Documents directory have been moved to /home/new/Documents !
Am I wrong ?

---

### Post by quickk on 2009-05-27
> **ActiveFrost said:**
> Let's say you've 2 directories :
```
/home/old/Documents
/home/new/Documents
```
You want to move your old files from the old dir to a new one :
```
mv /home/old/Documents/* /home/new/Documents/
```

Now, all your /home/old/Documents directory have been moved to /home/new/Documents !
Am I wrong ?

This works perfectly!  Thanks!

---

### Post by CatKiller on 2009-05-27
> **quickk said:**
> Maybe I'm wrong about this, but I thought that it was not a good idea to use the same home directory when installing a new version of Ubuntu.

There's nothing wrong with it. A lot of people have a partition for /home just for this purpose. And if there were something wrong with it, copying all the files from the old install into the new one like that would be just as bad.

It's easiest if you re-create the new users in the same order and give them the same names so that you don't have permissions problems, but it's certainly doable.

---

### Post by quickk on 2009-05-27
> 
It's easiest if you re-create the new users in the same order and give them the same names so that you don't have permissions problems

I always wondered about this.  I guess that I was afraid that somehow the new installation would mess up my old files.  Also, I am just moving over my files, firefox, thunderbird and a few other folders.  I thought that if I kept all of the hidden folders, I might carry over problems that developed in the old installation to the new one.

---

### Post by CatKiller on 2009-05-27
> **quickk said:**
> I always wondered about this.  I guess that I was afraid that somehow the new installation would mess up my old files.  Also, I am just moving over my files, firefox, thunderbird and a few other folders.  I thought that if I kept all of the hidden folders, I might carry over problems that developed in the old installation to the new one.

The only wrinkle is of ownership; each user should own their own Home folder. Permissions are handled internally using the UID of each user or group rather than the user name. By default, the user's Home folder is defined by the user's name. That's why it's just easier to add the users back in the same order, and to give them the same names that they had before. But it's still possible to specify the new user's UID and Home folder as you create them if you wanted instead.

It's important to backup the Home folders before you re-install, but it's important to back up your important data in any case. Spontaneous catastrophic hard drive failure does happen.

There is the potential that the old configuration files might cause problems with the newer version of a particular piece of software, but it's uncommon. And if a particular application is a problem, generally just renaming the old configuration file will cause a new one to be generated from the defaults. System-wide configuration files are kept elsewhere in the filesystem (usually in /etc) and so would be re-created on a new install anyway.

---

### Post by nebileix on 2009-05-27
oh i c. no wonder u cant move certain files.

The folder .gvfs in home directory is stopping u from doing it.

Instead do the moving operation in recovery mode and remember to chown back to your user name and u all done. All setting and preference will be back as it is.

---

