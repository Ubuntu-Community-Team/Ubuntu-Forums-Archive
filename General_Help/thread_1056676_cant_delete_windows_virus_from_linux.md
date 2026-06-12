---
title: "cant delete windows virus from linux"
date: 2009-02-01
forum: General Help
---

### Post by change.chases.me on 2009-02-01
i got 2 files, '8.bat' and 'autorun.inf'(which is actually a gif image) in my C: ntfs partition.
i can see them very clearly from linux, can open them too, and have changed their permissions to 777 . but still i cant delete them, even as root...not even rm -f works.
i get an error saying...no such file found !! 
when i issue the command 'touch 8.bat' it doesnt produce a new file, just change the timestamp of 8.bat..which means that linux is detecting the original 8.bat file.
can anyone please help me....its very urgent, as i have configured my project on windows and i cant afford to reinstall windows.
thanks a lot.

---

### Post by Boomhauer on 2009-02-01
if youve got the drive mounted already, unmount it.
then run ```
mount -t ntfs-3g /dev/sdaX /mnt
``` changing sdaX to whatever your ntfs drive is
then ```
cd /mnt

sudo rm -f /path/to/8.bat

sudo rm -f /path/to/autorun.inf
```

---

### Post by change.chases.me on 2009-02-01
i had already mounted it with ntfs-3g. i can write to all other files.

---

### Post by HermanAB on 2009-02-01
Use BartPE to repair broken windows.

Cheers,

Herman

---

### Post by change.chases.me on 2009-02-01
thanks herman, but repairing windows might cause trouble in using the licenced  software i am using. besides that, i am not sure if this software is good enough, i have never read about it before.
can you just help me delete that file....or give me the reason why am i unable to delete the file ?

---

### Post by Oblivion.Wielder on 2009-02-01
this happened to me once, the only way i could fix it was removing the files from the "command prompt" in windows before actually starting it (you know the black screen before the windows logo appearing.
Good luck

---

### Post by jocko on 2009-02-01
As you can touch the files, I think you should be able to overwrite them with new files with the same name
Try this:
```
sudo -i
echo test > /path/to/8.bat
echo test > /path/to/autorun.inf
```
That should overwrite the files with simple text files (containing the word "test").
After that they should be harmless (unless the virus exists somewhere else and replaces the files again), and hopefully you should be able to delete them.

---

### Post by HermanAB on 2009-02-01
The problem is that the Linux ntfs driver doesn't support all the crazy features of ntfs.  That is why the best way to fix windows is with BartPE, a CDROM bootable version of WinXP which you make yourself from your own copy of WinXP.  You can then install and run all the normal Windows repair programs like Hijackthis, Spybot Search and Destroy and so on.

The overwrite trick suggested above may work - worth a try.

Cheers,

Herman

---

### Post by hyperdude111 on 2009-02-01
Login as root and then try because root can do what it wants.

---

### Post by jocko on 2009-02-01
> **hyperdude111 said:**
> Login as root and then try because root can do what it wants.
If it doesn't work with sudo, it will not work when logged in as root either... And as you see in the first post, he can write to other files on the same partition, just not these two virus files, so it's not a permission problem. More likely it's some oddity in the ntfs file system that protects those specific files from being deleted.

---

