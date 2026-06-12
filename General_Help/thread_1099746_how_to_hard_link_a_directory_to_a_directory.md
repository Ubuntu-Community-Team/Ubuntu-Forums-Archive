---
title: "how to hard link a directory to a directory?"
date: 2009-03-18
forum: General Help
---

### Post by MountainX on 2009-03-18
I have a directory (common) that contains many subdirectories and files. I want to put a link to "common" in each user's home directory.

I thought a hard link would be best. How do I hardlink to a directory?

man ln is confusing. It says, 
> 
 ln [OPTION]... TARGET... DIRECTORY     (3rd form)

       -d, -F, --directory
              allow the superuser to attempt to hard link  directories  (note:
              **will  probably  fail**  due  to  system restrictions, even for the
              superuser)
I don't get it...

trying several things results in errors like this:
```

$ ln common/ ./personal/
ln: `common/': hard link not allowed for directory

```

I want a link that looks and acts like a directory and allows the user to seemlessly access the contents of the original (linked) directory. What is recommended?

---

### Post by mcduck on 2009-03-18
You should use soft link instead. It does exactly what you are asking for, apart from having a small link mark at the corner of the icon to tell that it's a link.

---

### Post by MountainX on 2009-03-18
OK. Thanks.

---

### Post by Dilligaf on 2009-03-18
Personally I would use a soft link. With a hard link if you deleted a user the /common/ directory would be deleted, try: ln -s /common/ /home/username/directory   assuming /common is in your root directory. Also check permissions on /common or try running as sudo.

Mike

---

### Post by stchman on 2009-03-18
> **MountainX said:**
> I have a directory (common) that contains many subdirectories and files. I want to put a link to "common" in each user's home directory.

I thought a hard link would be best. How do I hardlink to a directory?

man ln is confusing. It says, 
I don't get it...

trying several things results in errors like this:
```

$ ln common/ ./personal/
ln: `common/': hard link not allowed for directory

```

I want a link that looks and acts like a directory and allows the user to seemlessly access the contents of the original (linked) directory. What is recommended?

Yes, soft links are the way to go.

You can also create a soft link by middle mouse clicking and dragging the folder to wherever you need it.

---

### Post by MountainX on 2009-03-18
How do I create a symbolic (soft) link to a directory that resides on a file server (over NFS)?

```
The Link "Link to TargetFolder" is Broken. Move it to Trash?

This link can't be used, because its target "/home/myuser/.gvfs/sftp on myserver/home/common/TargetFolder" doesn't exist.
```

---

### Post by geirha on 2009-03-18
It's also possible to mount a directory on another directory:
```
sudo mount -o bind /media/common /home/*username*/common
```
The corresponding fstab entry (which would make the mount happen automatically at boot) would be:
```
/media/common /home/*username*/common none bind 0 0
```

---

### Post by Dilligaf on 2009-03-18
Using the command line works for me linking directories on a cifs mount that's mounted in fstab. Looking at your error message makes me wonder what you used, is there really a directory called "TargetFolder" on your share? Is your share mounted automatically on boot? I haven't been able to link to a directory on a mount using the GUI method.

Mike

---

### Post by MountainX on 2009-03-21
> **geirha said:**
> It's also possible to mount a directory on another directory:
```
sudo mount -o bind /media/common /home/*username*/common
```The corresponding fstab entry (which would make the mount happen automatically at boot) would be:
```
/media/common /home/*username*/common none bind 0 0
```

Thank you -- very cool!

---

### Post by MountainX on 2009-03-21
> **Dilligaf said:**
>  Looking at your error message makes me wonder what you used, is there really a directory called "TargetFolder" on your share? 
Mike

Part of my problem is that I was using sshfs. Yes, there is a directory called "TargetFolder" on my share. When I connected via NFS rather than sshfs, it worked.

---

### Post by megabuffen on 2010-10-22
To my surprise I was actually able to crate a hard link on my iPhone. Not quite what I expected from an Apple device. It solved the problem of every application having it's own little sandbox, so that I can now open downloaded files with QuickOffice.

---

### Post by JustinR on 2010-10-22
> **megabuffen said:**
> To my surprise I was actually able to crate a hard link on my iPhone. Not quite what I expected from an Apple device. It solved the problem of every application having it's own little sandbox, so that I can now open downloaded files with QuickOffice.

With the 'ln' command (thats an L not an I).

---

### Post by dcstar on 2010-10-22
> **MountainX said:**
> I have a directory (common) that contains many subdirectories and files. I want to put a link to "common" in each user's home directory.

I thought a hard link would be best. How do I hardlink to a directory?
.........

A "hardlink" is basically an alias filename for a file that exists on a single filesystem and is limited by that concept.

You can have a file with multiple hardlinks and if you delete those hardlinks the file still exists until you delete the final link that is associated to that file.

Softlinks are much more flexible (they work across filesystems), but if you delete the target of the softlink then the links will still remain, but no longer link to anything.

---

