---
title: "Retrieve emails in evolution from Live CD"
date: 2010-07-08
forum: Desktop Environments
---

### Post by Man with Hat on 2010-07-08
I don't know if the title of this thread is going to make what I am asking as confusing or if I can just manage that now :)

My ubuntu bootup + login + well everything is kinda in trouble at the moment. I am only able to access my computer through the live CD currently. Before I wipe the whole hard drive, is there a way to retrieve all of my emails in evolution? I have access to the partition that everything is stored on, but I have no idea where my emails are kept etc  
[-o<

---

### Post by dondiego2 on 2010-07-08
Found this on Google

The evolution data is stored at ~/.evolution (same as /home/<username>/.evolution)

---

### Post by Man with Hat on 2010-07-08
Cheers for that! 

Any idea how I can access it though as there are little padlocks on the files. I know my sudo password still from the old install. Also I don't really know what to look for when I get in there (unless all my emails look like separate files or something)

I might try this once I know how to get at my files :)

[http://embraceubuntu.com/2005/12/03/how-to-backup-evolution/](http://embraceubuntu.com/2005/12/03/how-to-backup-evolution/)

---

### Post by nothingspecial on 2010-07-08
Open up a terminal and type gksudo nautius, you should then be able to copy them

---

### Post by dondiego2 on 2010-07-08
I'm not sure but I would try and copy that whole ~/.evolution folder to a usb drive.  The lock on the folders means you don't have permission but your root password should give you permission.  Can you copy the folder even though it is locked?  Can you log in with your root password?  My folders are not locked.

---

### Post by Man with Hat on 2010-07-08
> **nothingspecial said:**
> Open up a terminal and type gksudo nautius, you should then be able to copy them

I did that, there was no output, but I'll assume that something happened as it didn't complain ;) I still can't open any folder that has a big white cross on it as I don't have permission, but this doesn't seem to matter as I do have access to the evolution folder now. I could probably do what *dondiego2* suggested and copy the whole folder across, but I have no idea how to restore it to evolution if I do end up formatting the drive. It may be as simple as copying it back into the same location, I don't know. I am also reading and trying to follow the instructions in the link that I posted earlier (can't hurt to cover a couple of different ways) but I don't know how to change to the drive that has my evolution folder on it. I am googling the answer as well as replying to these, so if there is no reply soon, I am sure that the answer to this one should be easier to find :)

---

### Post by Man with Hat on 2010-07-08
> **dondiego2 said:**
> I'm not sure but I would try and copy that whole ~/.evolution folder to a usb drive.  The lock on the folders means you don't have permission but your root password should give you permission.  Can you copy the folder even though it is locked?  Can you log in with your root password?  My folders are not locked.

Read above :)

---

### Post by Man with Hat on 2010-07-08
found it, I have to type

cd /media
ls

then cd c37db846-1f03-49c2-8f7

{the ridiculous long name that my drive has here. Whatever happened to sda1? It is now c37db846-1f03-49c2-8f7}

---

### Post by nothingspecial on 2010-07-08
> **Man with Hat said:**
> found it, I have to type

cd /media
ls

then cd c37db846-1f03-49c2-8f7

{the ridiculous long name that my drive has here. Whatever happened to sda1? It is now c37db846-1f03-49c2-8f7}

Is that your external drive or your ubuntu partition on the computer?

gksudo nautilus doesn`t change any permissions or anything, it should open up your file browser as root. Then you should be able to navigate to your ubuntu partition an find .evolution , right click copy and then navigate to your external and right click paste.

If only you`d never bought that fancy soundcard hey, none of this would have happened.

---

### Post by Man with Hat on 2010-07-08
GARGH!

Now I am getting permission denied trying to do the .tar.gz file in  terminal. I tried gksudo nautius again, but nothing. This is what it says when I try:

```
ubuntu@ubuntu:/media/c37db846-1f03-49c2-8f74-2b0052660a81/home/cam$ tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution
.evolution/
.evolution/calendar/
tar: .evolution/calendar/local: Cannot open: Permission denied
.evolution/calendar/views/
.evolution/calendar/config/
tar: .evolution/calendar/config/TaskPad: Cannot open: Permission denied
tar: .evolution/calendar/searches.xml: Cannot open: Permission denied
.evolution/tasks/
tar: .evolution/tasks/local: Cannot open: Permission denied
.evolution/tasks/config/
.evolution/categories.xml
.evolution/addressbook/
.evolution/addressbook/local/
.evolution/addressbook/local/system/
.evolution/addressbook/local/system/addressbook.db
tar: evolution-backup.tar.gz: Cannot open: Permission denied
tar: Error is not recoverable: exiting now

```

---

### Post by nothingspecial on 2010-07-08
Why are you trying to tarball it, just copy it to your external drive

```
 sudo cp -rv /media/c37db846-1f03-49c2-8f74-2b0052660a81/home/cam/.evolution /path/to/your/external/drive
```

---

### Post by Man with Hat on 2010-07-08
> **nothingspecial said:**
> Is that your external drive or your ubuntu partition on the computer?

gksudo nautilus doesn`t change any permissions or anything, it should open up your file browser as root. Then you should be able to navigate to your ubuntu partition an find .evolution , right click copy and then navigate to your external and right click paste.

If only you`d never bought that fancy soundcard hey, none of this would have happened.

It is my partition with ubuntu on it, my other drive comes up as "storage" :)

I can't even seem to be able to copy across to it, I have tried *gksudo nautius* a few times now and still no joy [-(

My problems really started because I owned a bad copy of windows, I threw it in the bin (along with every burnt music cd etc) and decided to try linux as I couldn't afford the insane cost from Microsoft. Since then I have learned to love linux a lot, but it does frustrate me like nothing I know! This part of my problems did in fact start with my fancy sound card, but that is why I have decided to duel boot (I now have old windows cd from a friend who upgraded). Now I can have the best of both worlds (as well as the worst ;))

---

### Post by nothingspecial on 2010-07-08
> **Man with Hat said:**
> It is my partition with ubuntu on it, my other drive comes up as "storage" :)




In that case 
 ```
sudo cp -rv /media/c37db846-1f03-49c2-8f74-2b0052660a81/home/cam/.evolution /media/storage
```

---

### Post by Man with Hat on 2010-07-08
> **nothingspecial said:**
> Why are you trying to tarball it, just copy it to your external drive

```
 sudo cp -rv /media/c37db846-1f03-49c2-8f74-2b0052660a81/home/cam/.evolution /path/to/your/external/drive
```

WHOOHOO That worked! :D

I was just following the guide as it said it was a good way to backup evolution. If you read it, it wants 

[LIST=1]
[*]~/.evolution/
[*]~/.gconf/apps/evolution/
[*]~/.gnome2_private/Evolution
[/LIST]
I might just try to copy the other two as well, maybe I just need to copy them back after the format?

---

### Post by nothingspecial on 2010-07-08
I`ll just warn you now that I don`t know for a fact if that will work because I don`t use evolution.

But google seems to thinks so, so I wouldn`t worry too much.

Hopefully you should just be able to over write the empty one in your new installation.

---

### Post by Man with Hat on 2010-07-08
> **nothingspecial said:**
> I`ll just warn you now that I don`t know for a fact if that will work because I don`t use evolution.

But google seems to thinks so, so I wouldn`t worry too much.

Hopefully you should just be able to over write the empty one in your new installation.

That's what I am hoping. Apparently the file in gnome2 doesn't exist, I tried to see if it existed by clicking through it in the GUI, but .gnome2 has a white X on it and won't let me see inside. 

```
cd /media/c37db846-1f03-49c2-8f74-2b0052660a81/home/cam
ls -a

```And I can see the .gnome2 file, but can't access it in here. All I know about permissions here is sudo, but I don't know how to apply it further...

---

### Post by dondiego2 on 2010-07-08
> **Man with Hat said:**
> It is my partition with ubuntu on it, my other drive comes up as "storage" :)

I can't even seem to be able to copy across to it, I have tried *gksudo nautius* a few times now and still no joy [-(
  


You keep typing "nautius"  instead of "nautilus".  It was a typo in the original post.  Just wanted to make sure you are typing it correctly.

---

### Post by Man with Hat on 2010-07-08
> **dondiego2 said:**
> You keep typing "nautius"  instead of "nautilus".  It was a typo in the original post.  Just wanted to make sure you are typing it correctly.
#-o THANK YOU!

Now I really can access these parts. Grr stupid typos! I now know that the inside of this folder is empty so I do not need to worry about copying it across. That's all I wanted to see :)

Cool, well I'm off to bed and I will check my thread about [_boot up_]("http://ubuntuforums.org/showthread.php?t=1525153") in the morning. If no further help on that one, I shall format my drives and start again! Cheers mate

---

### Post by nothingspecial on 2010-07-08
Who ever said I could type :-\"

Credit to you for copying it verbatim though.

---

### Post by Man with Hat on 2010-07-09
No problem, its all part of the learning process for me :) I now have a much better understanding of what nautilus does (well I didn't know about its existence before so I can only improve on that!)

Just thought that I would add that I have managed to copy those files (selecting to overwrite) into the new install, and when I loaded up evolution again. Whoo there are my emails, contacts and everything else!

!!!THANKS HEAPS FOR THE HELP!!!

---

### Post by nothingspecial on 2010-07-09
How did the dual boot installation go.

Is everything as it should be?

---

### Post by Man with Hat on 2010-07-09
Well.... I haven't actually undergone that yet. Probably best to read the thread [_Here_]("http://ubuntuforums.org/showthread.php?p=9567675#post9567675") as I have updated it a fair bit! I do have access to both Ubuntu and Win XP at the moment though... Next task is to become the superuser again in Ubuntu. I seem to have lost the privilege LOL

---

