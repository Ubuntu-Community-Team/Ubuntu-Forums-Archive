---
title: "[SOLVED] Problem Automatically Mounting Windows SMB Shares in Ubuntu"
date: 2008-02-28
forum: Desktop Environments
---

### Post by MountainX on 2008-02-28
I found a nice tutorial on mounting Windows shares here:

[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

Part of this includes adding credentials to /root/.cifscredentials
and adding this to fstab:
//192.168.0.10/SHARENAME /media/Storage cifs auto,iocharset=utf8,uid=USER,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 

However, after doing this, when I edit a text document, after the first time I save it to the share, I cannot write to it again. If the file is open in gedit, I have to Save As and give it a new file name.

Any idea what to check for? Thanks

**UPDATE:**

The issue is a bug : [https://bugs.launchpad.net/gedit/+bug/34813](https://bugs.launchpad.net/gedit/+bug/34813)

The diagnosis is described in these two comments here:
[https://bugs.launchpad.net/ubuntu/+s...13/comments/20](https://bugs.launchpad.net/ubuntu/+s...13/comments/20)
[https://bugs.launchpad.net/ubuntu/+s...13/comments/40](https://bugs.launchpad.net/ubuntu/+s...13/comments/40)

Based on my experience (and the diagnosis above), it is clearly a **problem with gedit.**

The workaround I had in Gutsy (mounting with smbfs instread of cifs) no longer works in Hardy. Now I guess I'll be forced to switch to another text editor full time. I'll miss gedit, but Cream is a great editor and it doesn't suffer this problem.

---

### Post by MountainX on 2008-02-28
As a follow up to the above post, I see two different recommendations for fstab. I do not know which is the correct one: smbfs or cifs. See below

//192.168.111.103/MyShares /media/MyShares cifs auto,iocharset=utf8,uid=USER,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0

//192.168.111.103/MyShares /media/MyShares smbfs credentials=/root/.smbcredentials,uid=USER,gid=users 0 0

---

### Post by chocolatetoothpaste on 2008-02-28
I have my samba shares mount on login also, but my fstab looks like this:
```

//192.160.0.70/share1  /mnt/share1  smbfs  dmask=777  0  0

```However, i do get an obnoxious request for a password, so I will try adding the part about credentials later this evening.  You might try setting file_mode=777 or dir_mode=777.  I'm not sure if it will help, I don't remember the order of the bits for permissions.

---

### Post by rapiscan on 2008-02-28
cifs is the "Common Internet File System" while smbfs is the samba file system.  You are accessing a windows share so you're using samba.  Samba supports cifs, so you can technically mount it either way.  It seems to me that you might as well mount as the samba file system though.

In this part of the fstab line:
```
uid=USER,gid=users
```
Are you replacing 'USER' with your username and 'users' with your group? Unless you want to choose a different group, 'users' would also be replaced with your username.  This will make you the owner of the files and set the group for the files.

---

### Post by MountainX on 2008-02-28
First, I learned that cifs is meant to replace smbfs.

I also found that files I create on the share are created with read only permissions. When I try to change permissions it says I can't because I'm not the owner. If I change the file permissions as root, then I am able to edit and save them as expected.

So the question is, why would all the files I create on the share be created as read only?

I found someone with the same problem here:
[https://lists.ubuntu.com/archives/ubuntu-uk/2007-August/006465.html](https://lists.ubuntu.com/archives/ubuntu-uk/2007-August/006465.html)

However, I can't use the noperm solution. I need a real and secure solution. Any ideas? Thanks.

[B][SIZE="4"]
The best HowTo is this one:[/SIZE][/B]
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)            :guitar:

---

### Post by MountainX on 2008-02-28
> **rapiscan said:**
>  Unless you want to choose a different group, 'users' would also be replaced with your username.  This will make you the owner of the files and set the group for the files.

Would I be able to replace 'users' with the WIndows user group name (such as Administrators)?

I think your suggestion will solve my problem... I'm getting ready to try it. Thanks.

---

### Post by MountainX on 2008-02-28
Not solved. Here's the line from fstab

//192.168.123.321/MyShares /media/MyShares cifs uid=MyUser,gid=MyUser,credentials=/root/.MyCredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Still, when I create a file on the share, it is read only and it is owned by root. Any ideas?

---

### Post by rapiscan on 2008-02-28
The gid option in the fstab line refers to the group on your linux box that will have access to the files.  So this doesn't relate to users or groups on the samba share. Files on linux are owned by a user and belong to a group and the user/group have certain permissions to access those files.  The uid/gid options allow you to set the user/group for the share that you are mounting.

Edit: I wrote this before I saw your last message.

---

### Post by rapiscan on 2008-02-28
Try it without the file_mode and dir_mode options, so that those are default.

---

### Post by MountainX on 2008-02-28
This is the line I had in fstab and it was creating files that were read only for me and owned by root.

#//192.168.123.321/MyShares /media/MyShares cifs uid=myuser,gid=users,credentials=/root/.MyCredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

I changed it to this as a test and it is working. However this seems to lack security.

//192.168.123.321/MyShares /media/MyShares cifs credentials=/root/.MyCredentials,uid=1000,iocharset=utf8,noperm 0 0

Does this help give a clue about what I'm doing wrong? Thanks

---

### Post by MountainX on 2008-02-28
...also, what is the fastest way to test changes to fstab? It seems like I have to reboot for the changes to take effect and I know there must be a better way in Linux. There is always a better way than the Windows way ;)

P.S. running "sudo mount -a" doesn't seem to be enough (or maybe my changes just aren't changing anything).

---

### Post by rapiscan on 2008-02-29
I believe you need to use both uid and gid options together.  In your example, you only specify the uid.  Also, I think noperm overrides these values, so try setting both uid and gid.  You don't have to use the integer value for your id, you can simply specify your username.   So the fstab line would like something like this:

```
//192.168.123.321/MyShares /media/MyShares cifs credentials=/root/.MyCredentials,uid=username,gid=username,iocharset=utf8 0 0
```

If you still don't have r/w permissions, please find out what permisisons it is being mounted with by typing ```
 ls -l 
``` while you're inside of the mount directory.   Just paste here the permissions and owner/group of a file or folder.

---

### Post by MountainX on 2008-02-29
Thank you for your tips.  I have it working with the following line, but I have a few questions.

```
//192.168.123.321/MyShares /media/MyShares cifs uid=username,gid=users,credentials=/root/.MyCredentials
```

This is a standard Ubuntu Gutsy desktop install. I have not set up any special user groups. Is "gid=users" the best group designation to use here? How do I list all my groups?

Also, I left off the following:
,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Do I lose any security as a result of leaving those parameters off?

 I know rapiscan told me to leave off the other two, and maybe that is exactly why it is working now. Where can I find an explanation of those parameters?

(I don't think I have any character set issues to worry about.)

---

### Post by rapiscan on 2008-02-29
Below is a link that explains file permissions. Please read through the first few sections a couple of times, although it may be a little boring at first.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

The iocharset option defines the character set used to understand the path names of the system that you are mounting.  Some users may want to set this to utf8, if they have utf8 characters in their directory names.  You probably don't have to worry about it though.

You can find out about the groups that you are in by simply typing 'groups' in your terminal (without quotes).  When you create a user, a group with the same name is created.  So if I create a user john, then there also exists a group john.  Generally speaking, there is only on user in the group john, and it is the user john.  That's why I suggest you set your uid to your username as well as your gid to your username.  If you decide you want to share those files with other users on your ubuntu machine, then you can consider setting it to a different group.

file_mode and dir_mode set the permissions for the mounted files and directories.  When you read more about file permissions, you will learn that you can set these to 770 to make sure that only you and your group have access to the files.

---

### Post by MountainX on 2008-02-29
I think I understand things better now. However, something is acting really wierd. 

```
//192.168.123.321/MyShares /media/MyShares cifs uid=username,gid=users,credentials=/root/.MyCredentials
```

if I simply add, ",file_mode=770,dir_mode=770,rw" everything stops working. My computer takes forever to boot up and my share is inaccessible.

Obviously, I could just leave that off, but I would really like to understand this.this

---

### Post by MountainX on 2008-02-29
The other thing I'm having trouble with is that I have to reboot in order for changes to take effect. Using "sudo mount -a" will add the share, but it will not activate substantial permission changes. To make all the changes I'm making for testing, I am having to reboot every time. What is the better way?

---

### Post by rapiscan on 2008-02-29
You can use all of the same cifs options with mount as you can in the fstab file. Here is the man page, which shows you all of the options you have available to you:
[http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)

So an example command would look something like this:
```
mount -t cifs -o uid=username,gid=users,credentials=/root/.MyCredentials //192.168.123.321/MyShares /media/MyShares
```

My first guess with the permissions issue is that it doesn't have the leading zero.  Your first example shows the permissions to be 0777.  The leading zero identifies the number as being in an octal base (permissions are almost always show in an octal form).  In my example, I left it off and just showed 770.  Since permissions are almost always represented in octal, it didn't occur to me that the leading zero was necessary.  Try it with the leading zero, 0770, and see if that fixes your problem.

---

### Post by MountainX on 2008-03-01
I may have encountered a bug or a situation that requires another step we haven't discussed yet. After reading the documentation suggested in this thread, I am fairly comfortable that I'm doing things correctly, yet I am still getting an error.

The common factor in my testing has been that I use Nautilus to create an empty file in the smb share, then I use gedit to attempt to write text into that empty file and save it. This has been failing. At first I thought it was related to write permissions. It is not. 

Below are the latest details of my testing:

Step 1: test read only

sudo mount -t cifs -o credential=/root/.MyCredentials,uid=myuser,gid=myuser,dir_mode=0400,file_mode=0400,ro //192.168.99.5/Shared /media/test

echo "The command is: mount -t cifs -o credential=/root/.MyCredentials,uid=myuser,gid=myuser,dir_mode=0400,file_mode=0400,ro //192.168.99.5/Shared /media/test" > /media/test/deleteme1.out

#bash: /media/test/deleteme1.out: Permission denied
#this is as expected

sudo umount /media/test

Step 2: test with write permissions

sudo mount -t cifs -o credential=/root/.MyCredentials,uid=myuser,gid=myuser,dir_mode=0770,file_mode=0770,rw //192.168.99.5/Shared /media/test

echo "The command is: mount -t cifs -o credential=/root/.MyCredentials,uid=myuser,gid=myuser,dir_mode=0770,file_mode=0770,rw //192.168.99.5/Shared /media/test" > /media/test/deleteme2.out

#ls /media/test
#deleteme2.out (it is listed and it has the correct content)

Step 3: test as I have been doing previously:

Open Nautilus
open test folder (share)
File > Create Document > Empty File "deleteme3.txt"
double click "deleteme3.txt" to open in gedit
enter some text and click save:
**[SIZE="4"]Error: Could not save the file /media/test/deleteme3.txt.[/SIZE]**

I have tested this various ways, but I always get an error with the above steps.

Maybe I should move this to a new thread because the issue is different from what I initially thought it was.

---

### Post by MountainX on 2008-03-01
Assuming this is a different issue than I previously thought it was, I created a new post here:
[http://ubuntuforums.org/showthread.php?p=4434806#post4434806](http://ubuntuforums.org/showthread.php?p=4434806#post4434806)

---

### Post by MountainX on 2008-03-01
This works:

```
sudo mount -t smbfs -o credentials=/root/.MyCredentials,uid=me,gid=me,file_mode=0770,dir_mode=0770 //192.168.9.9/Shared /media/test

```

This doesn't work:
```
sudo mount -t cifs -o credentials=/root/.MyCredentials,uid=me,gid=me,file_mode=0770,dir_mode=0770 //192.168.9.9/Shared /media/test

```

The cifs version fails under this scenario:

Open Nautilus
open test folder (share)
File > Create Document > Empty File "deleteme3.txt"
double click "deleteme3.txt" to open in gedit
enter some text and click save:
Error: Could not save the file /media/test/deleteme3.txt.

---

### Post by rapiscan on 2008-03-01
This is a known bug, which was originally reported for samba cifs.  See this bug report:

[https://bugs.launchpad.net/gedit/+bug/34813](https://bugs.launchpad.net/gedit/+bug/34813)

The developers seem to blame cifs, while some of the users try to blame gedit itself. I would trust that the developers know what they're talking about, and it's a bug with cifs.  This is even more likely since it works fine when it's mounted as smbfs.

I would recomend just using smbfs for now.  Don't forget to mark the thread SOLVED.

---

### Post by MountainX on 2008-03-27
Thanks. It is indeed a known bug and thanks for the link.

The diagnosis is described in these two comments here:
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/20](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/20)
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/40](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/34813/comments/40)

Based on my experience, it is clearly a problem with gedit.

The workaround I had in Gutsy (mounting with smbfs instread of cifs) no longer works in Hardy. Now I guess I'll be forced to switch to another text editor full time. Switching to Cream is a good thing anyway :)

---

