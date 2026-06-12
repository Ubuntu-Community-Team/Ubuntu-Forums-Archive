---
title: "Disk full of deleted files."
date: 2009-05-18
forum: General Help
---

### Post by Docaltmed on 2009-05-18
Here's my sad story:

This morning, my desktop manager refused to boot, so I booted from the live CD. Looking around, I saw that in the space of a week or so, sbackup had managed to store 167 GB of backup files on my hard drive, which was now at 100% capacity. I'm pretty sure that's the problem.

I opened nautilus using sudo (I didn't use gksudo, was that a mistake?) and moved the backup files to trash. Then I realized that, from the live CD, I had no way of emptying the trash on the hard drive(at least that I knew of).

So I retreated and booted from the hard drive into root. From the command line there, I tried emptying the trash using the following command:

```
rm -rf ~/.Trash/*
```

df shows 100% full.

I tried:

 rm -rf /home/username/.local/share/Trash/*

Still 100% full.

I looked for all .Trash files using:

```
sudo find / -name .Trash\* -print
```

Found something called Trash-0. So I emptied that. Guess what:

df shows 100% full.

I'm not too deep with things yet, so this pretty much depleted anything I had the knowledge to find and understand. Can anybody offer any suggestions?

---

### Post by Docaltmed on 2009-05-19
Fixed the problem, posting here for others.

I found that there were two directories in /.Trash-0. They were called "files" and "info" 

the "files" directory contained all of the backup files which I had moved to trash, and which were not deleted by my previous rm command, presumably because it didn't specify subdirectories.

Note: the backups themselves are directories, and thus have to be removed using the rm -r command.

The "info" directory had files of type .trashinfo which presumably related to the files in the "files" directory.

I removed those as well. 

This freed up the missing disk space. 

I subsequently ran fsck, assuming that in all the messing around, things had probably gotten a little misplaced.

Now I'm up and running again, except I can't run my gnome desktop, and had to boot into kde. But that's a different issue.

EDIT: Oh, yeah. I also purged sbackup unti I figured out what the heck went wrong there. No point in repeating this little exercise.

---

### Post by mjitkop on 2009-05-19
I'm glad it worked out for you in the end.

Thank you for sharing your experience. Who knows, somebody else may be in the same situation someday and will find a way to fix it by reading this thread. :)

---

