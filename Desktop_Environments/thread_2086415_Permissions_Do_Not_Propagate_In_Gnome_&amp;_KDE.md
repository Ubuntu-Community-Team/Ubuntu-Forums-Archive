---
title: "Permissions Do Not Propagate In Gnome &amp; KDE"
date: 2012-11-20
forum: Desktop Environments
---

### Post by cat2005 on 2012-11-20
I did a fresh 64bit 12.04 install.  I put both Gnome & KDE on it.

I copied files from my NTFS hdd to the newly created /home directory.  The folders & files copied fine.  Unfortunately, the permissions & ownership did not.  

I assumed NTFS doesn't store / read / recognize Linux permissions & ownership.  To fix this, I entered my account's /home directory and reset the permissions & ownership.  Very strangely, the permissions & ownership did not fully propagate.  

In both Gnome & KDE, I could not make the top directory's permissions & ownership fully propagate downward to include all existing folders and files.  Specifically, I could get folder permissions and ownership to change but not file permissions and ownerships.

I ran into this problem before and had to use both chmod and chown.  

[http://ubuntuforums.org/showthread.php?t=1252970&highlight=cat2005+chmod](http://ubuntuforums.org/showthread.php?t=1252970&highlight=cat2005+chmod)

I HATE using those because it is so easy to hose your entire system.  It is enough to make me return to Windows.

**Is my only hope using chmod or chown?**

---

### Post by Mr_JMM on 2012-11-20
I've always used
```
sudo chown -R group:user /path/to/directory
```
Always seems to work for me.

No, not your only choice. Another would be to use nautilus with root permissions and go through every folder and file one at a time. There may be others. I find terminal commands easier though.

---

### Post by JKyleOKC on 2012-11-20
> **cat2005 said:**
> I copied files from my NTFS hdd to the newly created /home directory.The "/home" directory is **not** your home directory, and normally requires root permission in order to write anything to it. It's the system-wide container for **all users'** home directories; if your user name on your system is cat2005, your home directory would be /home/cat2005.

Normally when you copy anything into your own home directory, both its owner and its group membership will automatically be set to those of your account. The owner's permissions will be read-write, plus execute for directories only, and both group and other permissions will be read-only. All of this is automatic and has nothing at all to do with inheritance from any higher directory. As a general rule, inheritance seldom if ever happens in Linux.

In addition to all this, Linux has no knowledge at all of NTFS permissions; the Linux permissions for files on NTFS filesystems are established when the filesystem is mounted, and in recent distributions often default to read-only across the board. However, the "mount" command can be used to specify ownership and permissions, and to change them (for the entire filesystem, not for individual bits and pieces that it contains). It's used from the command line and usually requires root permission to execute. You shouldn't have much need for it, though, since copying from such a system won't inherit the original permissions. Instead, the automatic assignment will take place.

I hope this helps a bit. Permissions happen to be one of the (thankfully, few) areas in which almost nothing you know about Windows is of much use in Linux, and serves only to confuse the issues.

---

### Post by cat2005 on 2012-11-21
Sorry, I should clarify. It is both ownership and permissions with which I am having trouble, but more ownership than permissions.
 
I copied the folders & files from an NTFS drive and placed them into an ext3 drive used for /home. The folders & files went directly into my account-specific home directory. For example, assume cat2005 is the user. I copied the folders & files into /home/cat2005
 
After doing so, linux showed root as the default owner of all folders & files. To fix this, I logged in as root (in both Gnome & KDE) and changed the ownership and permission assignments. I applied the changes to all subfolders and files.
 
The folders changed ownership and permission as desired. The files did not change ownership but did change permission. 
 
**Thus, I must somehow change file ownership.** 
 
Any thoughts?

---

### Post by cat2005 on 2012-11-21
> **Mr_JMM said:**
> I've always used
```
sudo chown -R group:user /path/to/directory
```
Always seems to work for me.
 
No, not your only choice. Another would be to use nautilus with root permissions and go through every folder and file one at a time. There may be others. I find terminal commands easier though.
 
Yes, I thought about using nautilus but I have hundreds of folders & files.  If I use sudo chown, then will that change the ownership for both the folders and files?  Sorry, it has been so long since I last performed this task that I can't remember.

---

### Post by JKyleOKC on 2012-11-21
Specifically, what command did you use to apply the changes to all subfolders and files? The command "sudo chown -R user:group ./*" should have done it for changing ownership and group membership, while "chmod -R perm ./*" where perm=the desired permission should have done it for the permissions if you had already changed ownership to your own user name. Doing such recursive modifications with a wildcard file name is extremely dangerous if done outside your own home directory (and usually makes a system unusable), but within the home directory all data is supposed to be owned by you so it should be safe enough.

Note that the sequence is "user:group" rather than the reverse as given in another post. SInce they are the same, usually, it's an easy mistake to make.

Note also that I left the "sudo" out of the second command; that's added insurance to make sure that any file you do not own (even though there ought not be any such) doesn't get its permissions modified.

Once you get the existing files straightened out to your satisfaction, you can set up an entry in /etc/fstab to mount the NTFS drive with your desired owner:group values and permissions, so you don't have to go through this again. If you'd like to do so we can tell you how...

---

### Post by cat2005 on 2012-11-22
Jim,

I haven't yet run the -R command line instruction.  

Instead, using Gnome & KDE, I just clicked "properties" and tried to apply the ownership and permission changes that way.  It worked on folders but not on files.

My hope is to find some non-command line method to apply the changes to all folders, subfolders, files, etc at once, assuming there is an option.  I am a command line clutz and am wary of using it unless I have no choice.

_Question_

     1)  If I did the -R command, then is this the correct syntax (words, spacing, etc):

               sudo chown -R user:group /path/to/directory

               where user = my account's user ID
               where group = whatever group I want to be the default group

Thank you again.

---

### Post by JKyleOKC on 2012-11-22
> **cat2005 said:**
> _Question_

     1)  If I did the -R command, then is this the correct syntax (words, spacing, etc):

               sudo chown -R user:group /path/to/directory

               where user = my account's user ID
               where group = whatever group I want to be the default groupYes, that's correct.

The command line is usually the simplest way to handle such repetitive tasks, but you're quite correct to view it with suspicion. Any time someone gives you a command to run, be sure to ask for an explanation of what it does. This will give you more confidence in its use as you learn more of the details. 

Here, specifically, is what that command does: "sudo" switches to the super user's powers for the duration of the command that follows, and leaves them available for 15 minutes afterward (although you can change the timeout period if that makes you uncomfortable). "chown" is the command to change ownership and group membership of files and directories. "-R" is one of many options to the command, and makes it run recursively on not only the named file/directory but on all others below the named one in the tree. Finally comes the path to the topmost directory you want the command to act upon.

What makes the "-R" option dangerous is that it acts blindly, with no regard for existing ownership or permissions. When the specified area is limited and you are confident there will be no conflicts, it's perfectly safe. However it should never be used on system directories or, even worse, the entire file system. Many critical capabilities, including "sudo" itself, require specific combinations of ownership and permissions, and quit working entirely if those are changed.

---

### Post by cat2005 on 2012-11-24
Jim,

I did the -R command and it worked.  However, I got a strange message.  Below is my terminal text.  

[B]catprime@lincpu:~$ sudo chown -R catprime:catprime /home/catprime
[sudo] password for catprime: 
chown: cannot access `/home/catprime/.gvfs': Permission denied
catprime@lincpu:~$ [/B]


I couldn't find a ".gvfs" file even when I made all files visible.  Now if I try to change any ownership or permission settings the normal way (i.e., not via -R) and apply to all folders, subfolders and files, I get this strange message:

**Setting ACL for /home/catprime/.gvfs**

Any thoughts?

---

### Post by JKyleOKC on 2012-11-24
It's a known bug, but launchpad doesn't show it as having much priority. The ".gvfs" subdirectory in your home directory provides mount points for devices you mount by the "gigolo" program and possibly "samba" also, and is supposed to have permission for only its owner -- which should be you. The bug is that the super user is not allowed access to it, which should never happen. This probably is what causes the message when you try to change permissions from the GUI recursively, since the GUI must use root permissions behind the scenes to do so.

Since it's not something that you use explicitly, and which the system uses only under certain conditions, best just ignore the error. You should be able to see the directory using the command "ls -la $HOME |grep gvfs" which tells the list (ls) command to list all directories within your home directory in long format then filter out all except .gvfs; don't use "sudo" with the command and it should give you the ".gvfs" entry with permissions of "drwx------" with owner and group both yours.

---

### Post by cat2005 on 2012-11-25
Jim,

If I correctly understand you, then I may ignore that message and continue using my computer as normal.  

Correct?

---

### Post by cat2005 on 2012-11-25
Jim,

My desktop has 3 internal hdds.  

1st  -  Ubuntu
2nd  -  Win7
3rd  -  Split in half.  Half is NTFS and half is ext3.

I made a backup of my linux data on a 3rd hdd in the ext3 partition.

I want to do the -R command to make my main Ubuntu account own all the files on the 3rd hdd ext3 partition.  Could you kindly tell me if my command line syntax is correct?

sudo chown -R user:group /media/sdc2/lincpu

where "user" = the user account I want to be owner
where "group" = the group I want to be the default group
where "media" = what it shows under when I mount it
where "sdc2" = the ext3 partition's label
where "lincpu" = the single folder containing everything

---

### Post by JKyleOKC on 2012-11-25
That ought to do it. 

And in reply to your earlier message, I don't think you will have any problem just ignoring the messages about .gvfs. If you run the command I suggested you can tell whether things are as they should be for that directory.

---

### Post by cat2005 on 2012-11-25
> **JKyleOKC said:**
> It's a known bug, but launchpad doesn't show it as having much priority. The ".gvfs" subdirectory in your home directory provides mount points for devices you mount by the "gigolo" program and possibly "samba" also, and is supposed to have permission for only its owner -- which should be you. The bug is that the super user is not allowed access to it, which should never happen. This probably is what causes the message when you try to change permissions from the GUI recursively, since the GUI must use root permissions behind the scenes to do so.

Since it's not something that you use explicitly, and which the system uses only under certain conditions, best just ignore the error. You should be able to see the directory using the command "ls -la $HOME |grep gvfs" which tells the list (ls) command to list all directories within your home directory in long format then filter out all except .gvfs; don't use "sudo" with the command and it should give you the ".gvfs" entry with permissions of "drwx------" with owner and group both yours.


Jim,

I did this in terminal:

**ls -la $HOME |grep gvfs**

and got that:

[B]catprime@lincpu:~$ ls -la $HOME |grep gvfs
dr-x------  2 catprime catprime     0 Nov 25 16:09 .[COLOR=DarkRed]gvfs[/COLOR]
catprime@lincpu:~$ [/B]

What does that message tell you?  The "gvfs" was in red text.

---

### Post by JKyleOKC on 2012-11-25
That says that you DO own the directory but do not have write permission to it, which would mean that you probably cannot mount devices via gigolo or samba -- which in turn may not matter at all to you.

Try "chmod 700 $HOME/.gvfs" and then repeat the listing/grep test to see if it makes any difference. The "gvfs" being in red is grep's way of identifying the string that it was searching for. Again, don't use sudo with this chmod command, since the known bug would definitely give you a "permission denied" report. Since you're the owner, chmod should work properly without it.

EDIT: It also shows that the directory isn't using any space, which is a bit strange; in my system, the listing shows 4096 bytes in use.

---

### Post by cat2005 on 2012-11-25
> **JKyleOKC said:**
> That says that you DO own the directory but do not have write permission to it, which would mean that you probably cannot mount devices via gigolo or samba -- which in turn may not matter at all to you.

Try "chmod 700 $HOME/.gvfs" and then repeat the listing/grep test to see if it makes any difference. The "gvfs" being in red is grep's way of identifying the string that it was searching for. Again, don't use sudo with this chmod command, since the known bug would definitely give you a "permission denied" report. Since you're the owner, chmod should work properly without it.

EDIT: It also shows that the directory isn't using any space, which is a bit strange; in my system, the listing shows 4096 bytes in use.


Jim,

I did the chmod command followed by the ls command and received the same result.  I didn't use sudo for either.  

I did the -R in my 3rd hdd ext3 partition and (so far) it appeared to work. 

Interestingly, I receive the .gvfs message while in KDE.  I don't receive it while in Gnome.  

I will do a clean install and see if that helps.  I will post my findings.

Thanks again, I appreciate it.

---

### Post by JKyleOKC on 2012-11-25
> **cat2005 said:**
> Interestingly, I receive the .gvfs message while in KDE.  I don't receive it while in Gnome.As best I can tell from the man pages and searching via Google, .gvfs is a Gnome utility so it might be that KDE has to do something to deal with it...

---

### Post by cat2005 on 2012-11-26
> **JKyleOKC said:**
> As best I can tell from the man pages and searching via Google, .gvfs is a Gnome utility so it might be that KDE has to do something to deal with it...


Jim,

While in the highest directory of my /home (i.e.,  /home/catprime) the ownership and permissions won't carry down.  However, if I go 1 directory down, and apply them there, then it appears to work.  It appears to avoid the .gvfs message.  That is good enough for me.

**Thank you so much for your help!**

---

### Post by cat2005 on 2012-11-29
I encountered this problem with KDE.  It is so frustrating.  I would really appreciate some insight as to why this happens and how to stop it.

I am using Ubuntu 12.04 64 bit.  I added KDE 4.8.5 and use it.  I have 2 accounts.  One is called prime.  The other is called regular.  Neither can view inside the other's /home directory.  Each folder is "sticky" so that only the folder's owner and root can change ownership and permission.

I cut and paste a file from my prime home to my regular home.  Once in my regular home, the file still showed prime as the owner.  It should have shown regular as the owner.

First, I logged in as regular.  I went to the folder containing the file and changed the ownership to  regular.   I selected "apply to subfolders and files".  This should have  carried the ownership change to the subfolders and files.  It did not.   Nothing changed.

Second, I did kdesudo dolphin and became root.  I tried doing the same thing as root but again, nothing changed.  

How can something that should be so simple not work?  Frustrating problems like this make no sense.  I hate Microsoft but will  give it credit:  file permissions transfer as they should.

I would really appreciate any insight:

**1)  Why doesn't this work?**

**2)  How can I permanently fix this?**

---

### Post by cat2005 on 2012-11-30
Anyone?  Bueller?

---

### Post by Isamu715 on 2012-11-30
Permissions won't change automatically when copying to another user's home direcotory. Since the file was owned by prime and copied by prime the permissons remain. Try executing the following command as root or the owner:
```
chown username filename
```
wher you'd probably replace *username* with *regular *and *filename *with the path to the file, permissions of which you want to change. Path is not required when you execute the command directly from the folder containing said file, the filename would suffice then. When using this command to change ownership of directories use the *-R* option.

---

### Post by cat2005 on 2012-11-30
Isamu715,
 
I am familar with the -R option but it is so easy to hose your system.  Do you know of any other way, either via command line or gui?
 
Or is -R my only choice to change ownership for the dozens of subfolders and files within them?
 
Thank you.

---

### Post by cariboo on 2012-11-30
Please don't create multiple threads on the same subject. I have merged your two threads.

---

