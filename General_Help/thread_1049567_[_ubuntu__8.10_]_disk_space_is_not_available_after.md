---
title: "[ ubuntu | 8.10 ] disk space is not available after deleting backup file from /  dir."
date: 2009-01-24
forum: General Help
---

### Post by oponto on 2009-01-24
[COLOR="#ffff00"]**________________________________________________________________________________________________**[/COLOR]




[SIZE="7"]**[COLOR="Lime"]SOLVED.SOLVED.SOLVED.[/COLOR]**[/SIZE]



**[COLOR="Yellow"]_________________________________________________________________________________________________[/COLOR]**



Hello,

I created an backup with following commands:

```
sudo su
```

```
cd /
```

```
tar cvpzf backup.tgz --exclude=/backup.tgz /
```

Did not exclude some more files, because I could not find out how
        to recreate them after restoring my system with the backup file.
Did not create it directly on external hdd, because newbie (..) .

After copying the backup file to my external hdd, I deleted it:

```
gksudo nautilus
```
 => moved it to trash,
 => emptied trash

Did that all at least three times.
Those backup files (I deleted after copying) were about 75 GB (3*25 GB).

Now I checked my disk storage, and my disk usage analyzer shows weird things:
 
     partition size: 122,6 GB
     used:           103,7 GB
     /   directory:   24,4 GB

Wtf, stop that.

[SIZE="1"]Looks like I should have informed me better about backing up properly ?
Well, that's another issue.[/SIZE]

Thanks ! :)

---

### Post by oponto on 2009-01-26
**[SIZE="7"]push^^[/SIZE]**


**[SIZE="7"][-X[/SIZE]**

---

### Post by oponto on 2009-01-29
[B][SIZE="7"][COLOR="Red"]PUSHED.
[/COLOR][/SIZE][/B]
Dear community and friends,
I need your help.



Thank you very much !

---

### Post by oponto on 2009-01-29
[SIZE="7"][COLOR="Lime"]**SOLVED.**[/COLOR][/SIZE]

How To _solve the issue_:

Files have been moved ([COLOR="#00ff00"]**[COLOR="Red"]WHY THE ****?[/COLOR]**[/COLOR]) to
```
/root/.local/share/Trash
```

So I found the file, => [COLOR="Lime"]**SOLVED.**[/COLOR]

Now I will try to remove it, what might lead to another thread.


Got tip from the following thread:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Well, the art of ubuntuforums search, though, was hard to find,
there are a lot of words for hard disk..


EDIT1: Removed file successfully, though, had to remove whole trash folder to avoid recreation of file itself. Hm, WTF?! Though, SOLVED.

---

### Post by oponto on 2009-01-30
**[COLOR="Cyan"]The last thing is to explain you how to delete the file after you found it in this weird trash folder:[/COLOR]**


If you delete big files from the root, they are moved to the root trash folder:

```
/root/.local/share/Trash/files
```

Files in this folder are **[COLOR="Red"]NOT shown in the disk usage analyzer[/COLOR]** !

Do only remove them by [COLOR="Orange"]**deleting the "files" folder with Shift+Remove**[/COLOR],
if you try to remove them by moving to trash, they recreate themselves exactly there again (you'd delete them from this place to this place) .

Then recreate the "files" folder.

---

