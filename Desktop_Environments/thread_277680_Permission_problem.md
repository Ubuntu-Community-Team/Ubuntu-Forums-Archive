---
title: "Permission problem"
date: 2006-10-15
forum: Desktop Environments
---

### Post by cactaur on 2006-10-15
Ok, I think I mounted my partition in a very bad way. I followed [this]("http://psychocats.net/ubuntu/mountlinux") method, and I think I screwed up the permissions for my home folder. So, when I log in, I get this message: 

> GDM could not write to your authorization file. THis could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is no possible to log in. Please contact your system administrator.

I know I have planety of extra disk space, so I think there's something wrong with my home directory. The command that was given in the mounting process was:

sudo chown -R ubuntu:ubuntu /(the filesystem)
(This was in the Dapper live CD).
sudo chmod -R 755 /

Now, I logged into recovery mode, and typed the following command:

sudo chown -R gregory /

But this error message still didn't go away. Does anyone know how to undo the sudo chmod -R 755 /? Or if there are any other solution, I'll be glad to hear. Thank you.

---

### Post by pay on 2006-10-15
I had the same problem after installing Gentoo. What I did was login as root and then change the permisions by right clicking the folder click on properties then permisions tab and changing the owner from root to my user. But I don't think that Ubuntu comes with a root account by default so that might not/probably won't work.

---

### Post by TiredBird on 2006-10-15
The permissions business has certainly caused me no end of troubles but I keep reminding myself that permissions add to the security.

I'm not an expert on this but I have learned a few things through trial and error, (mostly error), that might be of help.

(1) The type of file system is important. Because I have both XP and Linux accessing many of the same things I have several FAT partitions. FAT has no security built into it, only whether it is RW or RO, so how it is mounted, (usually the fstab entry, controls who owns it and what permissions it has.

(2) Permissions that are too restrictive prevent some processes from writing to the files, as you are encountering. I would guess that gdm is running as some owner other than 'root' and not 'ubuntu'. Your 755 makes those files only writable by 'root' or 'ubuntu'. 

(3) Permissions can also be too loose. I got tired of the error messages caused by my write restrictions so I put a 777 on a bunch of files. New problem - some programs refused to run because the data they were about to write was world readable. They wanted restrictions. Anyway, it takes a balance.

(4) Changing the permissions on files that are part of a mounted file system is tricky. I found that I had to unmount the file system, change the permissions on the mount point itself when nothing was mounted, then remount to get the lower level permisssions.

I haven't found any simple answers. It has taken me some experimentation and I'm still not sure I got it right. Good Luck!

---

### Post by TiredBird on 2006-10-15
One more thing. I'm sure you already figured this out yourself but in case you haven't, you have to put 'sudo' in front of any commands that will affect files you don't own. And any files you create as the consequence of a 'sudo'd command will be owned by 'root'. If you want to own it, you'll have to issue another command to change the ownership.

---

### Post by cactaur on 2006-10-15
Pay:

Well, when I used recovery mode, I was automatically root, so, apparently, that still didn't work.

TiredBird:

1. My file system is ext3.

2. Ok, I see, so I decided to change the owner of my home directory to my user account. GRrr, still doesn't work.

3. Well, I never used a number other than 755. Do you know what the number means?

```
sudo chown gregory /home
```

4. Ohhhhhh, sounds messy.

---

### Post by TiredBird on 2006-10-15
755 and 777 are octal permission codes. The first number represents the owner's permission; second number is group permission; and the third number is the permission for all others. Read is a 4, write is a 2 and execute is a 1. You add them together. Seven (7) is read, write and execute, five (5) is read and execute, etc. Therefore your 755 assigns read, write and execute to the owner, read and execute to the group and read and execute to all others. A 777, which should only be used under special circumstances, gives all permissions to everyone and is not secure at all.

These octal numbers are used in the 'chmod' command and other commands that set user permissions. (There are other codes that can be used in those commands that use 'r', 'w' and 'x' but I always use the numbers.) So a command of 'chmod 0755 testfile' assigns to the file 'testfile', read, write and execute for the owner and read and execute for all others. (The zero in the front of '0755' blanks out some other rarely used permission bits.)

'chmod' is for permissions. 'chown' is for ownership. If you use 'chown gregory:gregory testfile', you are setting the ownership of the file 'testfile' to 'gregory' and also assiging 'gregory' as the group name associated with it. I'm not really sure what happens when the group name is left out of the command as you have been doing. It could use the one name for both or it might leave the group as it was. I'm not sure. I always enter both.

Both of these commands take an important option '-R'. (That's a capital R preceded by a minus sign.) It makes the command recursive, it will apply to all directories and files below the one named in the command. However, I have run into some problems changing the permissions on files that are below the current file but on another device - files that were mounted below what I am changing. Now that I think about it, it probably has to do with the 'fat' file systems I use and the fact that I assign ownership and permissions in '/etc/fstab' and it won't let me make changes that contradict what is in fstab. At least that makes sense and if that is the case you won't be affected because you are using only ext3 and you won't have any ownership or permission assignments in fstab.

However, there are some things you need to take a look at. Each program that runs does so as a user. If you start the program explicitly, it will probably run under your user name. However, if you run it with the 'sudo' command it will run as 'root'. If the program was spawned by the system, (and there are many that run all the time to support any user's activity, it may run as 'root' if it needs 'root' capability but with the security problems lately most have thier own name which you might have come across in a list of system users. 

A program running as 'root' can create and/or write to any file. However, a program running under another name has to observe the permissions granted to that user. Your '755' means that only the owner or root can write to it. Look at the ownership and permissions for the files a program has to write to. Make sure it can do what it needs to. I think you'll find that 'gdm' is run under your name so it won't be able to write to anything that is owned by root. 

And how does root get to own so much stuff. Well if you run a program with 'sudo' it will run as root and any files it creates will be owned by root, even if the file is in your directory. Don't use sudo unless you have to and even then be aware of the effect it has on file ownership.

One of the things that might be forcing you into using 'sudo' when you shouldn't have to is the ownership and permissions of the directories. The read, write and execute bits have a different meaning when assigned to directories. Think of a directory as a program. If you want to browse the contents of that directory, get a listing of it or whatever, you have to be able to execute it and you have to have write permission for the directory if you are going to create, delete or modify files within it.

My suspicion is that 'gdm' is not running as root, it is running as 'gregory' or whatever you used as login name, and it is trying to create or modify a file that is either owned by root or is in a directory owned by root and the file and the directory and/or file has a 755 permission set on it.

For further information look at the 'man' pages for 'chmod' and 'chown'. I know they are complicated, I've looked at them both many times and I'm still not sure about all aspects of them. But I can tell you that the concept of ownership and permissions is one of the most important parts of the Linux (Unix) operating system and failure to understand it can cause a lot of problems.

Good luck!

---

### Post by cactaur on 2006-10-16
Ok, I see, well, if only I knew what the authorization file was. Grrrr..... now I see why businesses would want commercial customer support. I wish I knew what to do.

---

### Post by TiredBird on 2006-10-16
If I'm not mistaken, GDM is the Gnome Desktop Manager or something like that. The authorization file it is referring to is probably something hidden in your home directory, (a file that starts with a period is hidden automatically and you have to tell the file manager to explicity display them.) It is probably in a folder that begins with .gnome but I'm not sure. Execute the following commands in a terminal window and you'll probably find it. 
```
cd
ls -al
```
This should list all the files in your home directory, even the hidden ones. The extreme left column shows the permissions (first character is for the type of file, next three are read, write and execute for the owner, next three are the permissions for the group and the last three are permissions for the others. It also shows the owner and group. 

Assuming you find something that starts with .gnome, drill down and do the same thing at successive levels:
```
cd .gnome
ls -al
```
Hunt around. You'll find it. And I suspect that when you do you'll find it owned by 'root' and with no write permission for anyone but the owner.

Assuming the folder name is .gnome, fix it as follows:
```
cd
sudo chown -R gregory:gregory .gnome
```
That should take care of it. GDM probably runs as gregory so a 755 which grants gregory write permission should do it. If it doesn't, 
chmod -R 0777 .gnome
and anyone can read any file in the folder. (I wouldn't recommend this. It's a last ditch effort.)

---

### Post by cactaur on 2006-10-16
hmmm..... I checked, and everything in my home is owned by me. I did

```
ls -l .gnome
```

And everything was owned by me. Very weird.

---

### Post by TiredBird on 2006-10-16
I looked at a Ubuntu Gnome install, done by the live installer, it has three other hidden directories you should look at: .gnome2; .gnome_private; and .gnome2_private. Based on what I just looked at, the ownership on all of those should be your user login and the group for all of them should be the same. For the owner, all of the files and directories in all four of those directories was 'wrx'. Some group and some others had no permissions at all but most had 'w-x'. I didn't find any that had the 'r' set for group or others.

Look through those four folders, drilling down into the lower levels, and see if you find something that looks strange. Hopefully, you will find it.

If you don't find it and you don't get some help from someone more knowledgeable than me, (I'm pretty much a noob), then my only suggestion would be to reinstall. Hopefully you can isolate the data you've put into the system so you don't have to recreate that too.

Good luck. Sorry I wasn't more help.

---

### Post by cactaur on 2006-10-16
All right, I decided to submit it as a bug, and hopefully I'll get a response. And Tiredbird, you've been a great help, you know more about this than me, and I thought I was pretty experienced with Ubuntu.

---

### Post by TiredBird on 2006-10-17
I have to admit this has become a challenge. I like to find solutions for problems and this has certainly been a problem. Unfortunately, no solution yet.

I normally use Xubuntu which is XFCE desktop based but I also have a seldom used Ubuntu (6.06 Dapper) with Gnome desktop. I've been looking at that trying to understand what might be wrong. I have come across a couple of things that might be worth looking into.

I have found two files in the root of my home directory, '.ICEauthority' and '.Xauthority'. The ICE one is owned by me and the X one is owned by root. But both have 'rw' for the owner only - no other permissions. You might take a look at yours and see how they are set up.

The other thing I looked into was whether or not gdm had its own name. I found 'gdm' in my list of users. I don't know what name gdm was operating under at the time you got the error message but at least we know it could have been 'gdm'.

Because of situations such as this that can occur with using unfamiliar and relatively new software, I keep all of my data on partitions that are separate from the operating system. Each of the operating systems mounts and manipulates the same data. If one system breaks or locks me out I just switch to another. 

If you disregard the user data, the operating systems themselves take up only small amounts of space (in today's storage terms anyway). In my laptop I have a 80 GB harddrive but right now I have Windows XP, Ubuntu Gnome and three different versions of Xubuntu on the same drive, all able to access the same data.

I have about 65 GB reserved for data storage. Only 15 GB is used for the five operating systems and a lot of that is wasted. (I also have an extra 160 GB external data only drive that plugs into a USB port and can be accessed from any of the five systems. 

If I have to reinstall a system, (and I've done it many times), all I have to recreate are the settings. I have scripts, copies of which I keep with my data, that create all the mount points and the symlinks to the external data. I also keep copies of my 'fstab' file and other important configuration files with my data.

---

### Post by TiredBird on 2006-10-21
I saw something today that says using 'sudo' instead of 'gksudo' or 'gksu' with a gui type program can cause problems with the ICE authority file. I don't understand all of that but it might have something to do with the problem you experienced.

---

