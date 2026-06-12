---
title: "No trash with 'gksu nautilus'"
date: 2008-09-22
forum: Desktop Environments
---

### Post by manolomanolo on 2008-09-22
Hi.

If I execute 'gksu nautilus' and "move to trash" some file I'm unable to restore them back or even completele delete them. Actually I just don't know where those file ended up since I see nothing into the trash bin. Namely If I clik on the trash icon on this "root mode" nautilus window I get this error message:

[B]The folder contents could not be displayed.
Sorry, couldn't display all the contents of "trash": Operation not supported[/B]

Then if I write trash:/// on the nautilus "Location" bar and press Enter I get:

[B]Couldn't find "/trash:".
Please check the spelling and try again.[/B]

The problem is not so silly to me. I use to trash large files and I do risk my hard disk to fill up if I'm unable to completely delete them.

Thanks for your attention.
All the best.

---

### Post by Julolidine on 2008-09-22
I guess I just don't get why you would want to remove the files as a super user?  

Trash in linux is merely a folder.  If you go to your home folder as a regular user, and show the hidden files, you will find a folder called .Trash

Anything with a period in front of the folder name is hidden in Linux.  When you click on "Empty Trash" in nautilus, in essence what it does is simply remove the file from the trash.  There is no restoring files in linux for the most part, because of the structure of the file system.  If you want to restore files, make your home directory a separate partition of fat32.  

There are two ways to get around this problem.  Simply open up terminal and type "rm filepath/filename"  and it will be gone for good.  You probably shouldn't be deleting files that you need super user privileges for.  If you absolutely must "sudo rm filepath/filename".  If you do this, note that you will not ever be able to recover the file.  

If you wish to do this with a folder, type "rm -r /path/to/folder".  If you do this be **very careful**.  One typo can delete your entire hard drive.  Your best bet on this is to type "rm -ri /path/to/folder", as this will give you interactive deleting of files (aka it will prompt you if you really want to delete something).

---

### Post by anotherdisciple on 2008-09-22
In my experience, when you delete things in nautilus as a super user... it skips the trash bin... it gets immediately deleted.

---

### Post by Lacasito on 2008-09-23
Well, every user has its own trashbin in /home/user/.Trash, and root (As every user)has it own trash.
It's in /root directory as a hiden folder named .Trash
So you should look for /root/.Trash and you'll find the files you deleted as root.

---

### Post by anotherdisciple on 2008-09-23
> **Lacasito said:**
> Well, every user has its own trashbin in /home/user/.Trash, and root (As every user)has it own trash.
It's in /root directory as a hiden folder named .Trash
So you should look for /root/.Trash and you'll find the files you deleted as root.

Thanks for the clarification... I'll have to check this out when I get home.

Whenever I delete things as root... I always sudo rm the files... so I'm used to them just being removed immediately.

---

### Post by anars on 2008-09-23
> **anotherdisciple said:**
> Thanks for the clarification... I'll have to check this out when I get home.

Whenever I delete things as root... I always sudo rm the files... so I'm used to them just being removed immediately.

If you do it the "sudo rm"-way, then you're right - the files will get deleted immediately.

If your regular user's trashbin isn't empty, then you cannot empty it using Nautilus in super-user mode like you would normally do. Like the guys above me pointed out, every user has a ~/.Trash/ folder.

---

### Post by sigve on 2008-09-25
as of hardy the trash is located at:
~/.local/share/Trash/files/

so for root it would be:
/root/.local/share/Trash/files/

---

### Post by manolomanolo on 2009-04-05
> **sigve said:**
> as of hardy the trash is located at:
~/.local/share/Trash/files/

so for root it would be:
/root/.local/share/Trash/files/

That solved my problem ):P

---

