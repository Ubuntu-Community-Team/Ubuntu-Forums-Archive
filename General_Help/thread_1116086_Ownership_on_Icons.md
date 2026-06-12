---
title: "Ownership on Icons"
date: 2009-04-04
forum: General Help
---

### Post by WitchCraft on 2009-04-04
Hi, question:

I updated my operating system.
The icons didn't show right afterwards.
I found the error was the icons being .ico files instead of .png files.
I converted the icons to png files and the probelm was solved - i thought.

Now I logged in as another user - and the icons are gone again.
The problem is the modified icons have improper ownership set.

example of an icon that displays properly right now:
```

-rw-r--r--  1 user 1000 13622 2005-08-08 20:45 user-desktop.png
-rwx------  1 user 1000 34236 2003-08-21 16:22 user-trash-empty.png

```

example of icons that don't display properly:
```

-rw-------  1 root root 17268 2009-03-22 21:20 user-home.png
-rw-------  1 root root 33181 2009-03-22 20:56 user-trash-full.png

```


How do I change ownership/permission on all files and folders in /usr/share/icons/myicons

so that the icons display correct for all users?

---

### Post by albinootje on 2009-04-04
> **WitchCraft said:**
>  How do I change ownership/permission on all files and folders in /usr/share/icons/myicons

so that the icons display correct for all users?
Does that folder have sub directories or not ?
If it doesn't then it's easy to do this in a nice way :
```

sudo chown 0:0 -R /usr/share/icons/myicons (root is owner/group-owner)
sudo chmod 755 /usr/share/icons/myicons (for the directory)
sudo chmod 644 /usr/share/icons/myicons/* (for the files in it)

```

---

### Post by albinootje on 2009-04-04
If your icons directory does have sub directories, then this is the 
preferred way (I just had to look this up from a crontab on a server, hence the delay)
```

sudo find /usr/share/icons/myicons -type f -exec chmod 644 {} \;
sudo find /usr/share/icons/myicons -type d -exec chmod 755 {} \;

```
The first line does the chmod on files, the second line on all sub-directories and the main directory.

---

### Post by WitchCraft on 2009-04-04
> **albinootje said:**
> Does that folder have sub directories or not ?
If it doesn't then it's easy to do this in a nice way :
```

sudo chown 0:0 /usr/share/icons/myicons (root is owner/group-owner)
sudo chmod 755 /usr/share/icons/myicons (for the directory)
sudo chmod 644 /usr/share/icons/myicons/* (for the files in it)

```

I added -R for all files in folder.
Now I cannot access the folder anymore...

---

### Post by WitchCraft on 2009-04-04
> **albinootje said:**
> If your icons directory does have sub directories, then this is the 
preferred way (I just had to look this up from a crontab on a server, hence the delay)
```

sudo find /usr/share/icons/myicons -type f -exec chmod 644 {} \;
sudo find /usr/share/icons/myicons -type d -exec chmod 755 {} \;

```The first line does the chmod on files, the second line on all sub-directories and the main directory.

thanks, that worked, access is back and correct.
Problem solved now.

---

### Post by albinootje on 2009-04-04
> **WitchCraft said:**
> I added -R for all files in folder.

Hmmm. I forgot the -R indeed, but only in the first line. (Edited it) Glad to see that it works now.

---

