---
title: "Is this a good way to backup?"
date: 2009-06-02
forum: General Help
---

### Post by cmwslw on 2009-06-02
I'm about to start backing up my drive, but I'm wondering if this is a good way to do it:

```
sudo rsync -a --stats --exclude-from /.bak-exclude / /media/disk
```

/.bak-exclude:
```
/proc/*
/lost+found/*
/mnt/*
/media/*
/sys/*
```

The command makes a nice recreation in my external hard drive, but I am still wondering if this will help me when I really need it. How would I ever restore something like this? Is this a good way to back up?

Thanks -Cory

---

### Post by colau on 2009-06-02
> **cmwslw said:**
> I'm about to start backing up my drive, but I'm wondering if this is a good way to do it:

```
sudo rsync -a --stats --exclude-from /.bak-exclude / /media/disk
```

/.bak-exclude:
```
/proc/*
/lost+found/*
/mnt/*
/media/*
/sys/*
```

The command makes a nice recreation in my external hard drive, but I am still wondering if this will help me when I really need it. How would I ever restore something like this? Is this a good way to back up?

Thanks -Cory
```

aptitude install grsync

```

---

### Post by cmwslw on 2009-06-03
> **colau said:**
> ```

aptitude install grsync

```

Thanks! I just installed that. I like how it gives you a progress bar. Anyways, to restore this backup I would just copy over files, install GRUB and I'm good to go? I have directories like /sys and /dev backed up, but nothing in them is backed up. Do I need to make some files in those before my system can run?

---

### Post by albinootje on 2009-06-03
> **cmwslw said:**
>  I have directories like /sys and /dev backed up, but nothing in them is backed up. Do I need to make some files in those before my system can run?

Be careful if you intend to do a full system backup. Directories like /dev, /proc, and /sys are "special".

In the past, (for quick backup/restore) I've left /proc and /sys for what they were (you can create them manually with mkdir in the restore steps), and used tar for backing up /dev

---

### Post by cmwslw on 2009-06-03
> **albinootje said:**
> Be careful if you intend to do a full system backup. Directories like /dev, /proc, and /sys are "special".

In the past, (for quick backup/restore) I've left /proc and /sys for what they were (you can create them manually with mkdir in the restore steps), and used tar for backing up /dev

So /dev does need to be backed up? And if I just create the directories like /proc and /sys and reinstall GRUB, my system will boot up fine?

---

### Post by billbear on 2009-06-03
click my signature

---

### Post by cmwslw on 2009-06-03
> **billbear said:**
> click my signature

That would work fine if I was doing a one-time backup, but I need to do multiple backups using rsync. I got the backup down right now, I just need to know how I can restore

---

### Post by hessiess on 2009-06-03
> 
I just need to know how I can restore 

You should be able to just rsync from the back up over the top of the original files to restore it.

From reading the thread it sounds like you want to keep a history of changes, you may want to consider using a version control system such as bzr or svn to manage your files. You wouldn't want to use something that always stores complete local repository's if you have a large quantity of data(git etc), even SVN storing two copies of everything can be problematic unless you have a lot of spare disk space.

---

