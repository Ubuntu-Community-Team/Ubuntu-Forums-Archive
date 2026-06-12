---
title: "[SOLVED] mounting partition - not privileged?"
date: 2008-12-07
forum: General Help
---

### Post by zami on 2008-12-07
I'm dualbooting Windows Vista and Ubuntu 8.10, and I'd like to get to some files on the NTFS Windows partition, through Ubuntu.

I can SEE that the partition is there through the file browser, but when I click on the drive, I get this error...

> 
Cannot mount volume.
You are not privileged to mount this volume.


if I wait a moment to close that error window down I get
> 
Unable to mount 90.0 GB Media
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


How can I fix this?

fsdisk -l shows the partition is HPPS/NTSF format, at /dev/sda1 . It's a Windows Vista partition.

I have ntfs-config installed and set to "enable write support for internal device".

I've read this can happen if you shut down Windows "improperly" but, this is not my case, it's a working partition and was last shut down properly.

It's my Windows games partition so I'd like to keep it in working order, too.

Thanks for any help!

-zami

---

### Post by crazyness003 on 2008-12-08
you may be able to do a force mount (kinda risky tho). Im not sure how the command goes.
Try this while i get more info: [http://ubuntuforums.org/showthread.php?t=694301](http://ubuntuforums.org/showthread.php?t=694301)

EDIT: Heres a way to automount (i use this method too) [http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/](http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/)

---

### Post by zami on 2008-12-08
Thank you thank you! I'm reading over both those links.

I don't mind manually mounting as it's pretty rare I'll want to dig around in the Windows (aka Games) partion from Ubuntu, but this business of not having "permission" is confusing.

Can you (or anyone) elaborate on how the "force mount" method is "risky" ?  The Windows partition is my games partition and I really don't want to risk it.  (Nevermind reinstalling Windows, it's the thought of days and days of updating games - ugh!)

-zami

---

### Post by eBoxNet on 2008-12-08
Did your windows shutdown properly last time ?
If not boot on windows and shutdown.

---

### Post by zami on 2008-12-08
> **eBoxNet said:**
> Did your windows shutdown properly last time ?
If not boot on windows and shutdown.
Yep!  And I even rebooted into Windows and shut down again, "just in case".
No go.

edit: forgot to say, thanks for the suggestion though.  I'd hate to go tinkering with command lines for overlooking something that much safer.

-zami

---

### Post by zami on 2008-12-08
Well, I went ahead and forced it following the instructions in the post crazyness003 linked to 
[http://ubuntuforums.org/showthread.php?t=694301](http://ubuntuforums.org/showthread.php?t=694301)

Looks good!  I can browse/edit the Windows partition files from Ubuntu, and I've since booted into Windows and don't notice any ill effects... 

Also when I rebooted into Ubuntu I didn't have to re-force mount, it's already mounted.  So no auto-mount hoops to jump through! 

::cheer::

Thanks for the help all!

-zami

---

### Post by crazyness003 on 2008-12-08
like i said, its risky...but most risks are worth the take. Glad to see you're not having problems anymore.

But to answer your question about forcing a mount: this is my take on the issue. 
When you mount in Ubuntu, it uses a different driver for the FS (i think its called ntfs-3g. basically a layer that the FS loads on top of). This enables a sort of API structure, where you drop a command, the API handles it and tries to translate it for the native ntfs, then vice versa. The risk coems with the flags of the drive. I guess there are some sectors of a partition that hold information about said partition. If these get flags tanked, then you basically lose your partition (since it wont recognize itself). And whenever you add more complicated steps to anythign that has to do with computers...you usually get some bad effects in the process. 
So, by forcing the translated instruction, theres a possibility it will affect the wrong sector = death to your partition.
Thats the risk. But im sure the partition would be recoverable, even if you tank the table or mbr. I know [Disk Genius](http://www.diskgenius.com/) can fix an ntfs partition if it fails.
But then again, its all about luck.

Well, i hope this enlightens you a bit. Also dont take everythign I say as 100% true, like i stated, this is how I interpret the process.

Have fun in Ubuntu (and thanks for marking the thread as [SOLVED])

---

