---
title: "Backup/synchronization suggestions needed"
date: 2009-01-20
forum: General Help
---

### Post by zachthejones on 2009-01-20
I have a USB external drive which I want to backup onto. I've tried sbackup, but it's not exactly what I want. I want something which will more synchronize the specific locations/folders I desire with specific locations/folders on the external drive. I guess what I really need is some sort of synchronization program which can create an up-to-date copy of what I want it to when I want it to.

I think rsync might be able to do it, but I can't find the right documentation/instructions to do what I want. I'd like to be able to set it up and either hit a button or run a script and make it run the sync whenever I need it to.

so, suggestions? directions?

---

### Post by compman25 on 2009-01-20
That's 2 different thing. Did you want it to backup to the external drive or mirror your drive to the external drive?

---

### Post by CrusaderAD on 2009-01-20
Check out my instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=902366](http://ubuntuforums.org/showthread.php?t=902366)

Keep is the best backup program I've found and it works great!

---

### Post by zachthejones on 2009-01-21
Compman25...

Basically I want up-to-date copies of specific folders (documents, pictures, music, video, etc.) on the USB drive. I want to be able to access the "backup" as if it were a regular set of folders and files - most backup programs utilize some sort of compression for the backup, rendering the backup useless for anything except restoration.

One of the reasons for this is my laptop doesn't have room to hold all my music and pictures and video, so I keep certain portions of those folders on my laptop and the rest on the external drive.

And thanks for the heads-up raptormanad, I'll check out Keep. I think sbackup screwed up the backup location and did it to my laptop because all of a sudden I had no space left (which screwed up my browsers till I deleted some stuff for some reason).

Anyone know how to delete the /var/backup folder? I think that may be my problem with this backup mishap...

---

### Post by CrusaderAD on 2009-01-23
To remove a directory, use this but be careful!

sudo rm -r directory

I'm pretty sure that's the syntax. Keep will let you backup to whatever you want, even networked and external hard drives. Externals are in the Media folder.

---

### Post by hyper_ch on 2009-01-23
rsync is the way to go, set a base folder from which it shall start syncing and exclude directories you don't want to have synced...

it's a very simple script plus a list of directories you don't want to sync and then you just make an action/launcher or whatever it's called to run that script.

---

### Post by sedawk on 2009-01-23
I use rsync to do stuff like that (partial and full "mirrors).

E.g. if you want to backup /home and everything below to the
external disk (let's assume /media/disk), run

```

# Only testing, no action
sudo rsync -avn /home /media/disk/

# The real thing
sudo rsync -av /home /media/disk/

```

This will the first time copy home and all subdirectories to 
/media/disk/home.
When you run it again later it will only copy new and changed files.
It will overwrite changed files but not delete files you removed
in /home !
(to delete there is another option available I do not recommend
 to use by default!).

When "mirroring" only big files think about using the "--size-only"
option. Be aware that rsync makes a difference between "/home" 
and "/home/" as an argument. With a trailing slash the direcotory
home will not be copied itself. This can cause trouble when you
normally use "/home/" (not copying home itself) and later on
you forget it and use "/home".

---

### Post by zachthejones on 2009-01-24
Thanks sedawk! Those were the commands I was looking for. It seems to have done what I wanted... But I guess now what I need to learn is how to use scripts....how do I create one? How do I execute one? Are there any good resources where I can start learning how?

I checked out Keep, but it seems to be more of the same as far as backup programs go, though the GUI seems to offer more options than sbackup's.

---

### Post by CrusaderAD on 2009-01-25
I know that once keep does a backup, on its next run, it will only grab the files that changed. This is kinda nice cause the backup won't take as long.

---

### Post by rhodry on 2009-01-25
Try installing and running Grsync. It is a gui frontend to the rsync command. Works nicely and you can run it whenever you want from the menus. For example, you should exclude directories like your /home/user/.thumbnails from backups.

For the other stuff, do a Google search for "linux bash scripting guide" and " rsync example scripts". You will find heaps of introductory stuff to get you started and you can return here for specific follow-up questions.

Rhodry.

---

### Post by zachthejones on 2009-02-26
Thanks rhodry! grsync seems to be doing exactly what I need done at the moment. I think might start using Keep to do more full backups as well.

---

