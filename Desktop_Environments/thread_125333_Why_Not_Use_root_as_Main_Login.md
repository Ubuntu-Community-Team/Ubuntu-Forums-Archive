---
title: "Why Not Use root as Main Login?"
date: 2006-02-03
forum: Desktop Environments
---

### Post by TomAnthony on 2006-02-03
I can only access my ntfs disk from my root user, and I was wondering why using the root as your primary login is not recommended, or is it safe to do this?

---

### Post by ipp3l1 on 2006-02-03
To mount Windows partition and allow users to read only
```

sudo mkdir /media/windows 
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222

```

Assuming that /dev/hda1 is the location of the Windows partition (NTFS) and the local mount folder is: /media/windows 

That's how to mount ntfs disk right so that you can read it even if you're not super user...

And you propably know this, but ubuntu's kernel (orsomething like that) doesn't support writing on ntfs.

---

### Post by aysiu on 2006-02-03
See the third and fourth links of my signature.

---

### Post by ipp3l1 on 2006-02-03
oh, and then the answer to the question in topic...

There are meny benefits of not being logged in continuously in root account. I wont list them all here, but I can tell that it's waaaay more secure. Think if someone happens to "h4X" your computer (highly unlikely using linux but anyway), how lesser chances they have to damage your system, as not being a super user?

---

### Post by TomAnthony on 2006-02-03
[QUOTE=ipp3l1]To mount Windows partition and allow users to read only
```

sudo mkdir /media/windows 
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222

```

Assuming that /dev/hda1 is the location of the Windows partition (NTFS) and the local mount folder is: /media/windows 

That's how to mount ntfs disk right so that you can read it even if you're not super user...

And you propably know this, but ubuntu's kernel (orsomething like that) doesn't support writing on ntfs.[/QUOTE]

The partition does mount at boot, but without permissions. i will try your fix though.

---

### Post by aysiu on 2006-02-03
Please try my suggestion (the fourth link of my signature).
The other way will not mount it at boot.

---

### Post by TomAnthony on 2006-02-03
[QUOTE=aysiu]Please try my suggestion (the fourth link of my signature).
The other way will not mount it at boot.[/QUOTE]

Excellent, and thank you. I'm at work now, but will try that when I get home. This will really save me time. Thanks to evreyone else for the ideas.

---

