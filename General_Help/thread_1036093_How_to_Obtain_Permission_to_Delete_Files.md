---
title: "How to Obtain Permission to Delete Files"
date: 2009-01-10
forum: General Help
---

### Post by Indyviews on 2009-01-10
Hi I am new to Linux, have figured a few things out but am very weary of simply trying to delete files. When I right click there is no delete or empty wastecan. After highlighting and attemped deletion, I cannot move to trash and am asked if I wish to delete immediately, in which I am told there is an error and I do not have permission.

I have read many posts on this subject and tried various ways to do so. I tried gksudo nautilus and got to root and after managing to find the folder I wished to delete (couldn't find where I could get permission) I  found that I could move it to the trash can. So I clicked that and yes the folder is gone, but not into the trash can and I have no idea where it went.

Here is what is on my terminal:

steve@steve-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
Initializing nautilus-clamscan extension

** (nautilus:7640): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///home/steve/Videos/My%20Sony%20Photographs
--> file:///home/steve/Videos
--> file:///root
--> file:///home/steve
--> file:///
--> file:///home

(nautilus:7640): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 6 elements at quit time (keys above)

(nautilus:7640): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 6 elements at quit time
seahorse nautilus module shutdown
steve@steve-desktop:~$ 

By changing user authorizations to yes, I have managed to be able to delete files from Desktop (that I had downloaded). At this time...I would like to know  how to get permission to delete files so it will be a simple thing to do.

I am using Ubuntu 8.10 32 bit and don't know much about all the jargon but will try if put as simple as possible. Thanks for any help.

By the way I really like Linux so far, have figured out much on my own but still have a few things to work on.

Update: After writing the above and making said Authorizations above...The terminal now says:

steve@steve-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
Initializing nautilus-clamscan extension

** (nautilus:5999): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I guess I need to know how to enable user sharing.

---

### Post by GMachine_24 on 2009-01-10
When I want to remove files, I use the command line.

```


sudo rm -r /mountpoint/foldername


```

You must be careful as this command will remove everything in "foldername".

You must have permission to make this change. If you need to change permissions for a folder, you can:

```


[sudo chmod 777 /mountpoint/foldername]


```

This will essentially enable anyone on your computer to read/write to the /mountpoint/foldername location. If you want to be more restrictive than that, read up on changing permissions:

```


man chmod | more


```

or find one of the many howtos on the Ubuntu or other Linux site. Good luck.

---

### Post by mc4man on 2009-01-10
> tried gksudo nautilus and got to root and after managing to find the folder I wished to delete (couldn't find where I could get permission) I found that I could move it to the trash can. So I clicked that and yes the folder is gone, but not into the trash can and I have no idea where it went.

When you delete a file or folder as root (gksudo nautilus) it goes into the root trash. 
When deleting as root you can do 2 things

Use shift+delete

Or open gksudo nautilus
Go edit -> preferences and in the behavior tab then make  changes you want

**Don't make too many other changes in the 'root' preferences** (confine yourself to trash behavior

For user preferences go to home folder -> edit -> preferences and feel free to change what you want


Edit: as long as you get a 'root file browser' when running gksudo nautilus you can ignore the warning stuff, everyone gets it to some degree

---

### Post by Indyviews on 2009-01-10
Thanks for taking the time to reply **GMachine_24**...it didn't seem to help but I will keep working at getting permission.

---

### Post by Indyviews on 2009-01-10
Your shift & delete did the trick **mc4man** and I thank you for your help. I had already changed the preferences in the Home Folder and it didn't help but at least I can delete files not.

---

### Post by GMachine_24 on 2009-01-10
If you want to change "ownership" of a particular folder or what have you, use the 

chown

command.

You can change the ownership to your username and then have at it from there.

Again, check the man pages for specifics on chown or this page has very simple instructions and is an OK place to start on information for chown and chmod

[http://www.linuxheadquarters.com/howto/basic/chown.shtml](http://www.linuxheadquarters.com/howto/basic/chown.shtml)

---

