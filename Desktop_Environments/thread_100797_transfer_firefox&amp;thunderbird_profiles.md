---
title: "transfer firefox&amp;thunderbird profiles"
date: 2005-12-08
forum: Desktop Environments
---

### Post by Sander50 on 2005-12-08
Hey all,

i use ubuntu now for some time, and i really like it. So i want to quit windows, and use just only ubuntu.

But I need my old thunderbird and firefox settings/data. I know it is possible to transfer mozilla profiles in windows, i did that before. 

I tried to transfer the thunderbird-profile from windows (xp) to ubuntu the same way i did before (in windows), but that doesn't work! How can I do this?

Sander

---

### Post by timetunnel on 2005-12-08
The problem is that they store absolute paths in their preferences, so you have to change them. If I remember right, they are all in "prefs.js" and maybe in "user.js" in your profile folder. Just replace all paths to the appropriate new path and it should work.

That works only if you copy the **whole profile** from Windows to Linux into an empty profile folder. Don't copy only parts of your windows profile into an existing profile on Linux.

HTH
Jens

---

### Post by Sander50 on 2005-12-08
thanx man! got my email working now... now firefox to go... ;)

---

### Post by Sander50 on 2005-12-09
Yeah got firefox working too!
thnx!

---

### Post by rasmusbp on 2005-12-14
hi,

i'm completely new to linux, recently installed ubuntu in a dualboot system with xp, and so far i'm thrilled about ubuntu 5.10! 

however, i'd like to transfer my profile (including all emails, contacts, account info etc.) from my xp-thunderbird to ubuntu. but i'm having problems understanding the advice in this thread: 

"Just replace all paths to the appropriate new path and it should work."

Please forgive my linux-ignorance, but I don't get it. 
Also, I tried to solve the problem in the auld xp-way simply by overwriting the ubuntu profile folder with the xp profile folder. but i get a system error saying "you do not have permission for this operation" (or something like that). 

can someone please guide me through this? I'm sure there are plenty of other linux virgins like me with the same problem...

Thnx
Rasmus
Copenhagen, Denmark

---

### Post by timetunnel on 2005-12-14
I'll try a brief howto that worked for me. Please read and understand completely before proceeding.
[LIST=1]
[*] exit Thunderbird and Firefox
[*]On Linux make sure there are no data in your firefox / thunderbird profile that you still need (email, bookmarks whatever). Then completely delete these profiles. They should be in "/home/username/.mozilla/firefox" and "/home/username/.mozilla-thunderbird" (replace "username" with you linux login name in the paths). These folders should be completely empty afterwards 
[*]Now copy the **complete ** profile from Windows to the appropriate path. For example from "C:\Documents and Settings\Application Data\Thunderbird" to "/home/username/.mozilla-thunderbird"
[*]Open "/home/username/.mozilla-thunderbird/Profiles/something/prefs.js" in a text editor like "gedit" (replace "something" in the path with what you see on your machine, the folder name in that location looks different on each computer and contains random numbers and letters)
[/LIST]
Having that file open, continue this way:
You have to manually look into each line of that file now and decide if it's a directory path. The paths are not stored in a relative way, so you'll see this for example:
```
"C:\\Documents and Settings\\username\\Application Data\\Thunderbird\\Profiles\\default.bla\\News
```
Having that in a Linux profile can't work because path names are not accessed that way there. See the double backslahes? That's the way Windows paths are stored there. You now have to change this path to the appropriate path on you Linux box, in the case of the example above to:
```
/home/username/.mozilla-thunderbird/default.bla/news

```

That's what I meant with
> Just replace all paths to the appropriate new path and it should work.

You must be careful that you only change pathnames, nothing else. And watch the case-sensitivity of path names. "News" and "news" are different folders on Linux.
I hope you get the idea.
Do the same for the firefox "prefs.js" file, of course.

As for you error:
> i get a system error saying "you do not have permission for this operation" (or something like that)
Please, always give the exact error message, not "something like that". If you copy files around in your mozilla profiles you shouldn't get a permission error. Are you sure you didn't try to copy to the home folder of another user or a system folder like "/usr"?

Jens

---

### Post by rasmusbp on 2005-12-14
that worked perfectly, thanks! :KS

---

### Post by timetunnel on 2005-12-14
You're welcome. :D

---

### Post by rasmusbp on 2005-12-14
oh yeah, i still have the the problem with permissions. 

e.g. when I try to delete a file on my windows FAT32 partition (hda6) for shared files, I get this message: "....cannot be deleted because you do not have permissions to modify its parent folder". 

it's a bit of a problem since I'm planning to use that partition as a shared read/write drive btw xp and ubuntu. 

thanks again!

---

### Post by timetunnel on 2005-12-14
How does your /etc/fstab file look like for that partition?

---

### Post by rasmusbp on 2005-12-14
This is it:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc          proc         defaults                    0  0  
/dev/hda2  /              ext3         defaults,errors=remount-ro  0  1  
/dev/hda1  /media/hda1    vfat         defaults                    0  0  
/dev/hda6  /media/hda6    vfat         rw                          0  0  
/dev/hda5  none           swap         sw                          0  0  
/dev/hdc   /media/cdrom0  udf,iso9660  user,noauto                 0  0  

---

### Post by timetunnel on 2005-12-14
Hmmm. Ok. I'm not an expert in "mount" and "fstab" stuff, so just an idea:

Open a terminal. Check the file permissions with
```
ls -l /media
```
What's the line for "hda6" look like? Do the same for
```
ls -l /media/hda6
```
and post one line here.
They will look similar to this:
```
drwxr-xr-x  2 root  root   4096 2005-11-02 22:39 hda6
```
These are  permissions, owner and group  for the folders specified. I guess there's something wrong with them on your computer.

Jens

---

### Post by rasmusbp on 2005-12-15
hi jens,

you're probably right. everything else just seems to work perfect, though. 

here what I got from the terminal:
> 
rasmus@ubuntu:~$ ls -l /media
total 36
lrwxrwxrwx   1 root root     6 2005-12-13 18:31 cdrom -> cdrom0
drwxr-xr-x   2 root root  4096 2005-12-13 18:31 cdrom0
drwxr-xr-x  10 root root 16384 1970-01-01 01:00 hda1
drwxr-xr-x   6 root root 16384 1970-01-01 01:00 hda6


What does that tell you?

Thanks,
Rasmus

---

### Post by timetunnel on 2005-12-15
> What does that tell you?
I guess that means you don't know how to read it. Ok. Here we go:

```
drwxr-xr-x 6 root root 16384 1970-01-01 01:00 hda6
```

This line tells you that "/media/hda6" is a directory (the "d" on the very left), the "owner" for that folder is "root" (first appearance of "root") and the "group" is "root" as well (second appearance of "root"). Permissions for files and folders can be set for owners and users (and "others", please refer to the man pages or other docs for more details about that). The letter on the left tell you what permission owner, group and other have. From left to right:

d = is a directory
r = read access allowed for owner "root"
w = write access allowed for owner "root"
x = execution of binaries allowed for owner "root"
r = read access allowed for group "root"
- = write access NOT allowed for group  "root"
x = execution of binaries allowed for group "root"
(the other three letters are similar permission for "others")

Don't get confused about the write permissions here. Since "root" has write access as owner, it doesn't matter that it doesn't as group. So "root" is allowed to do anything in that folder.

That's our today's "lesson"  ;) 

Now back to your problem:  On my computer, I changed the permissions of the folder of my FAT32 partition to allow write access to my "user" and mounted it with options that allows especially me to write there, but I think the "righter" solution is to leave the permission of "/media/hda6" as they are and do all in the "/etc/fstab" file. I just googled that solution so this approach is new and theory to me as well:

Like in the post before, change the line of your FAT32 partition hda6:
```
sudo gedit /etc/fstab
```
```
/dev/hda6 /media/hda6 vfat defaults,iocharset=utf8,umask=000 0 0
```
This allows everyone to write to that partition (see the docs about "umask" in  "man mount") 

I found that solution here:
[http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)
(they do the mounting only temporarily there, but with thei fstab solution it's permanent and you don't have to do that again and again)

Let me know if it works
Jens

---

### Post by rasmusbp on 2005-12-15
jens, 

thanks for the lesson! i'm not very technically minded, though, just want the damn things to work! 

ok, i did what you suggested, but i still get the same problem when trying e.g. to delete a file on hda6. i also tried to access a file, to change the permissions there, but the options are "grey", not accessible, and it says "You are not the owner, so you can't change these permissions". 

here's what the fstab reads:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc          proc         defaults                           0  0  
/dev/hda2  /              ext3         defaults,errors=remount-ro         0  1  
/dev/hda1  /media/hda1    vfat         defaults                           0  0  
/dev/hda6  /media/hda6    vfat         defaults,iocharset=utf8,umask=000  0  0  
/dev/hda5  none           swap         sw                                 0  0  
/dev/hdc   /media/cdrom0  udf,iso9660  user,noauto                        0  0 

damn it...

---

### Post by timetunnel on 2005-12-15
That's strange. I just checked with the same line in fstab on my computer and it worked. Did you reboot or unmount/mount the partition after the change (changes in fstab only take effect after reboot or remount of the partition)?

Sorry, I'm lost here. I suggest you start a new thread for that problem, so some other guys might be able to help you.

Jens

---

### Post by rasmusbp on 2005-12-16
jens, you're the man! it is in fact today, after a reboot and a good nights sleep... i had the idea that rebooting was a windows thing, I guess...

thanks a lot again. my ubuntu is pretty much working the way I want now. 

cheers,
rasmus.

---

### Post by timetunnel on 2005-12-16
Good to hear that. 
Rebooting **is** a Windows thing actually. Usually it isn't neccessary in Linux. Often only restarting a service is needed.  In case of a change in fstab you only have to unmount and the mount the partition again. Mostly one can do that while the system is running. However, if you have no idea how to do that, a reboot is a good choice. But then you do it just because you don't know how to do it without rebooting - and not because it's really neccessary. So here's a huge difference between Windows and Linux.

Anyway, have fun. :) 

Jens

---

