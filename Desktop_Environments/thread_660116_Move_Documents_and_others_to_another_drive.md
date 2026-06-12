---
title: "Move Documents and others to another drive"
date: 2008-01-06
forum: Desktop Environments
---

### Post by Aqualung on 2008-01-06
How can I move the Documents, Desktop, Music etc. folders (i.e. most of the folders in my Ubuntu home folder) to a different drive, specifically on the NTFS-formatted drive that contains all my Windows goodies (documents, pictures etc.)? I need the Ubuntu Documents folder to be the same as my Windows Documents folder, my Ubuntu Music folder to be the same as my Windows Music folder and so on and so forth... It should, ultimately, be an issue of getting the Ubuntu icons in question to point to my Windows folders.

Better yet, how can I move the whole home folder onto the drive that contains my Windows profile?

I've been doing some searches, and I have found only situations where the new drive that is to host the folders in question is barren. Note, then, that I need to conflate my Windows and Ubuntu profiles, so that, until my switch to Ubuntu is complete, I get to share the profiles (or, at least, the essential media and document folders) between the two OSs *without* having to synchronize folders etc.

---

### Post by PeterJS on 2008-01-06
> **Aqualung said:**
> 
Better yet, how can I move the whole home folder onto the drive that contains my Windows profile?

You don't want to do that, NTFS doesn't support all the filesystem and security features necessary to make a home directory work the way it should. And the settings are stored in such vastly different way there's no real benefit to having them all together.

> 
How can I move the Documents, Desktop, Music etc. folders (i.e. most of the folders in my Ubuntu home folder) to a different drive, specifically on the NTFS-formatted drive that contains all my Windows goodies (documents, pictures etc.)? I need the Ubuntu Documents folder to be the same as my Windows Documents folder, my Ubuntu Music folder to be the same as my Windows Music folder and so on and so forth... It should, ultimately, be an issue of getting the Ubuntu icons in question to point to my Windows folders.


The easiest way to do this is to mount the NTFS drive automatically at boot and move everything out of your ~/Documents folder in to windows my documents, the same for ~/Music, etc. And then use symlinks to have the windows directories show up in your home folder.
Example:
```

ln -s /media/windows/Documents\ and\ Settings/User/My\ Documents ~/Documents

```
Note that the ~/Documents folder has to be emptied and delete before this will work.

---

### Post by Aqualung on 2008-01-06
> **PeterJS said:**
> The easiest way to do this is to mount the NTFS drive automatically at bootThanks. How do i do that?> and move everything out of your ~/Documents folder in to windows my documents, the same for ~/Music, etc. And then use symlinks to have the windows directories show up in your home folder.
Example:
```

ln -s /media/windows/Documents\ and\ Settings/User/My\ Documents ~/Documents

```
Note that the ~/Documents folder has to be emptied and delete before this will work.Okay. Will that work for the Desktop folder as well? Also, I assume I have to replace User w/my username etc. Better yet, it looks to me that I have to give this symlinks command a closer look to figure out the syntax...

---

### Post by PeterJS on 2008-01-06
> **Aqualung said:**
> Thanks. How do i do that?

The ntfs-config tool should set this up for you.

> 
Okay. Will that work for the Desktop folder as well?
I've never tried that particular set up, can't think of a technical reason it wouldn't work. It'd be kinda weird, you'd end up with linux short cuts on your window's desktop and vice versa. It'd be funny looking but not harmful.

> 
Also, I assume I have to replace User w/my username etc. Better yet, it looks to me that I have to give this symlinks command a closer look to figure out the syntax...For all the dry details:
```

man ln

```The cliff notes go something like this:
ln is the (filesystem) linker (not to be confused with the program linker (ld)). 

The is -s flag less it to make a soft link (also called a symlink), the other option is a hardlink. A symlink functions a lot like a window's shortcut, but can be used completely interchangeably with the original file. A hard link pretty much amounts to giving a second file name to an existing file.

The format of the locations is the thing you want to link to first, and where you want the link to appear second.

---

