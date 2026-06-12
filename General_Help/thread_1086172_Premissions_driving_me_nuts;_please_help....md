---
title: "Premissions driving me nuts; please help..."
date: 2009-03-03
forum: General Help
---

### Post by ddigler on 2009-03-03
Is there a way to do away with ALL permission restrictions for a specific account (ie. allow my account to access and delete anything at will). This has BY FAR been the roughest part of my transition from windows.

Currently, I cannot empty trash on my desktop because there are 3 folders in there that contain folders that are locked. When I try to access through sudo nautilus it returns 'Sorry, could not display all the contents of "trash": Operation not supported' I don't want to use terminal to empty trash, shouldn't have to be that way...

Additionally, whenever i connect my 8GB pen drive it locks all of the files half the time even though I am the one that added them on this very machine and I cannot access the .Trash to empty it with sudo nautlius (ie, while in Nautilus as root I cannot view my hidden files) even though they show when not logged as root??

Bottom line, tired of the locks, can't make any sense of it. Is there a way to do away with that BS? How do you guys handle this? Thanks.

---

### Post by Iowan on 2009-03-03
> **ddigler said:**
>  How do you guys handle this?  I've learned that if **sudo** won't work, there's usually another reason/problem.  I have a server with root account active, but no longer use it - the root account (and forum policy prevents sharing how to do it). My trash usually deletes just fine, but if something "undelete-able" ends up there, I resort to terminal and sudo.

---

### Post by ddigler on 2009-03-03
Thanks for the input. So firstly, can you give me a command to clear trash with terminal?

Also, the majority of the probs I have right now are with removable USB drives. Half the time I can't write any files to them "Device is read only file system." and the other half of the time they work. 

What can I do to get my USB drives (mp3 player and flash drives) working?

---

### Post by oldos2er on 2009-03-03
For your pen drive, try: With the drive plugged in, press Alt+F2. Type **gksu nautilus** and then type your password. Once open, go to /media. Right-click on usbdisk, and select Properties. Go over to the Permissions tab, and enable writing for all users.

 You shouldn't need to log in as root to empty your trash. I agree with the assessment that if you do, something's wrong. You might want to read [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)

 To empty your trash in terminal, run 
```
cd /home/user/.local/share/Trash

rm -r *
``` where 'user' is your username.

---

### Post by ddigler on 2009-03-03
Thanks Ann. Tried the trash code. Here is what I keep getting:

```
zac@Home-Office-PC:~$ cd ~/.local/share/Trash
zac@Home-Office-PC:~/.local/share/Trash$ rm -r *
rm: descend into write-protected directory `files/ushare-1.1a-NeToU/src/usr'? y
rm: descend into write-protected directory `files/ushare-1.1a-NeToU/src/usr/bin'? y
rm: remove write-protected regular file `files/ushare-1.1a-NeToU/src/usr/bin/ushare'? y
rm: cannot remove `files/ushare-1.1a-NeToU/src/usr/bin/ushare': Permission denied
rm: descend into write-protected directory `files/Templates/CMakeFiles'? y
rm: remove write-protected regular file `files/Templates/CMakeFiles/CMakeDirectoryInformation.cmake'? y
rm: cannot remove `files/Templates/CMakeFiles/CMakeDirectoryInformation.cmake': Permission denied
rm: remove write-protected regular file `files/Templates/CMakeFiles/progress.make'? 
```

There are 3 folders in there that I simply cannot delete. Any other ideas?

Also, is it normal that I cannot access trash from 'sudo nautilus'?

---

### Post by adult swim on 2009-03-03
have you tried ```
sudo rm -rf ~/.local/share/Trash/*
```

---

### Post by ddigler on 2009-03-03
Swim like your avatar, going to see them this summer!! :D

Your code worked, my desktop trash is clear thanks!!

My prob now is I cannot clear the .Trash folder from my 8GB pen drive. Keeps giving me read only file system. Does this indicate corrupt file system? What should I do?

---

### Post by ddigler on 2009-03-03
> For your pen drive, try: With the drive plugged in, press Alt+F2. Type gksu nautilus and then type your password. Once open, go to /media. Right-click on usbdisk, and select Properties. Go over to the Permissions tab, and enable writing for all users.

You shouldn't need to log in as root to empty your trash. I agree with the assessment that if you do, something's wrong. You might want to read [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)

Upon messing with this further, I realize the following. when i mount the drive I have full read/write/delete permissions. When I enable hidden files and try to delete .Trash i get the read only file system error. 

After that EVERYTHING on the drive (including everything that was working before) has a lock on it. Then I tried sudo nautilus and got the same exact thing.

Insight?

---

### Post by adult swim on 2009-03-03
hey ddigler, sorry for the delay
go to a terminal and issue this command
```
ls -l /media
``` paste what it returns

---

### Post by 3rdalbum on 2009-03-04
It looks like your "permission denied" errors come from trying to trash a directory full of source code that you have installed. When you run the "sudo make install" command, it creates several files, and because you have run the command as root those files will be owned by root as well. When your normal user account tries to delete them, it can't because they are root-owned.

If you run a root file browser and enable the "Delete" function in it, then that is the best way to delete root-owned files.

I for one wouldn't tell you how to give your user account the same permissions as root; it causes too many problems including security problems and certain programs not working properly, and of course the fact that all operating systems are moving to this "seperation of root and user" model; it's something you'll have to get used to.

I hope this post has increased your understanding of Linux.

---

### Post by ddigler on 2009-03-04
> **adult swim said:**
> hey ddigler, sorry for the delay
go to a terminal and issue this command
```
ls -l /media
``` paste what it returns

Will do this tonight when I get home. Thx.

---

### Post by ddigler on 2009-03-04
> **3rdalbum said:**
> It looks like your "permission denied" errors come from trying to trash a directory full of source code that you have installed. When you run the "sudo make install" command, it creates several files, and because you have run the command as root those files will be owned by root as well. When your normal user account tries to delete them, it can't because they are root-owned.

If you run a root file browser and enable the "Delete" function in it, then that is the best way to delete root-owned files.

I for one wouldn't tell you how to give your user account the same permissions as root; it causes too many problems including security problems and certain programs not working properly, and of course the fact that all operating systems are moving to this "seperation of root and user" model; it's something you'll have to get used to.

I hope this post has increased your understanding of Linux.

This has helped. I am still learning the very basics. What happened was I installed a few programs using terminal (not available through repositories).

After trying the software and not getting it to work properly went to uninstall. Not knowing how to do that I just decided to delete the ap folders which is when I got the error when trying to clear from trash. 

Now I know how to fix it though and why it occurred. Thanks.

---

### Post by shateredsoul on 2009-03-04
I've had the same issue.. but with mp3 players.  

The trash thing command worked! Thanks!

One question though.. I recently reinstalled ubuntu and the first thing I did was copy over a folder I made (titled my documents) to the desktop.

Everything in that folder was locked.  

It couldn't be a problem I caused since it was a fresh install. Any insight on how to change this option?

How can I make the folder readable and writeable by me? Instead of root...

I agree, this is the most frustrating part of the change.

---

### Post by oldos2er on 2009-03-04
If you installed a program compiled from source code with "sudo make install," to uninstall it you would go back into the source code folder and run "sudo make uninstall."

---

