---
title: "I can not see the contents of the trash folder"
date: 2010-07-05
forum: Desktop Environments
---

### Post by LorDVipeR on 2010-07-05
Hi when try recover a file from thash folder, i cant see the contents, but, when make properties to the folder, show 47 files on the trash folder, and the docklets of docky, also show files (41 files).

Please help me with this problem

Sorry for my english....

Ubuntu Lucid 10.04

[U][[IMG]http://img822.imageshack.us/img822/3903/pantallazozex5zc.th.png[/IMG]]("http://img822.imageshack.us/i/pantallazozex5zc.png/")


[/U]

---

### Post by bigsmitty64 on 2010-07-05
Try open your trash folder and while in there hit Ctrl+H to show hidden files. Mine was like that by default and I don't know why.
There is probably another answer to this but that worked for me. By the way, I LOVE your desktop. Nice work!

---

### Post by LorDVipeR on 2010-07-05
> **bigsmitty64 said:**
> Try open your trash folder and while in there hit Ctrl+H to show hidden files. Mine was like that by default and I don't know why.
There is probably another answer to this but that worked for me. By the way, I LOVE your desktop. Nice work!




I already did, but does  not work... :-|

---

### Post by someone235 on 2010-07-07
I've found a solution:
go to ~/.local/share/Trash and change the directory 'files' to another name (e.g '.files'). Then enter the renamed directory (e.g ~/.local/share/Trash/.files), select all the files, and delete them.
it does some mess in the trash, but it still works well...

---

### Post by paparozoumis on 2010-07-07
Take also a look in this thread.. 
I had the same problem twice.. 
Now it works fine... 
[http://ubuntuforums.org/showthread.php?t=1505145](http://ubuntuforums.org/showthread.php?t=1505145)

---

