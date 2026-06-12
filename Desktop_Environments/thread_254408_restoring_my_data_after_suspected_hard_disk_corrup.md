---
title: "restoring my data after suspected hard disk corruption"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Poirot on 2006-09-09
Hello forum,

I recently experienced a nasty thing. Out of the blue my ubuntu install went a bit crazy, the menus and shutdown button failed to respond. I was forced to do a hard shutdown using the button on my machine.

On rebooting, it checked the filesystem as it was not cleanly unmounted. It went into a console and asked me to run some command that went on to check the disk for errors, it found loads of inode errors and I obediently agreed that it should fix the errors one by one. Ultimately it dumped some stuff in lost+found and rebooted.

I was concerned, this sort of thing isn't supposed to happen in linux. I have been assuming it was a freak hardware problem but really, I haven't a clue.

Now I can't get anywhere because when I get into the gdm it cannot find the theme files, not even the default theme can be loaded. It says it is 'attempting to load the standard greeter' and freezes. I just end up with a mouse pointer and a brown background.

I realise my description of the process is pretty poor but it was late and I was tired. Now I can't replicate it, 

Anyway, I think it's about time I did a fresh install anyway as I have updated from hoary to breezy to dapper and have collected problems along the way (e.g. my Ruby files have the wrong icons and won't open in gedit and many other small things like that). A clean dapper install is clearly better from looking at the liveCD.

So I would like to get my data from the potentially dodgy hard disk using the liveCD. 

I have mounted the disk in the liveCD like this
```
sudo mount -t ext2 /dev/sda3 ~/ -r
```
The only problem is that half of my files seem to be read protected (-rw-------) whilst the rest are available to me (-rw-r--r--).

I want to copy them all to a backup USB pen drive when I am using the liveCD.

Here's my question...

How do I let ubuntu (through the liveCD) know that I am the owner of the files that exist on my old system?

OR

How do I make the files readable from the liveCD?

Also...

What is it that happened to my system? Is there any way I can get some clues? I don't know where to start, especially since I can't get into the gdm properly.

I am totally confused but as long as I get my data back then I am happy to be forced to do the fresh install, I was putting it off anyway.

Thanks a lot, I would appreciate any advice I can get.

Poirot

---

### Post by mssever on 2006-09-09
It really doesn't matter much who the live CD believes the files' owner is.

Given that you're just doing a backup, I would do a ```
sudo cp -a foo bar
```. This will preserve the permissions on the files exactly as they are. Unless you're doing a website or something, there shouldn't be any problem with any files having 600 permissions as opposed to 644. And if the owner is messed up, you merely need to do ```
sudo chown -R youruser files
``` 
Of course, to preserve permissions, you either need to format your pen drive with a Linux format (as opposed to FAT or NTFS), or create a tarball.

Remember, as long as you're dealing with user files--as opposed to system files--the permissions aren't particularly important. As long a you can read and write them--and execute executables and directories, you should be good to go. And those parmissions are pretty easy to fix if you hose them.

To look for problems with GDM, you can boot into recovery mode and look for errors in ~/.xsession-errors and the various logs in /var/log

---

### Post by mssever on 2006-09-09
oops...duplicate post

---

