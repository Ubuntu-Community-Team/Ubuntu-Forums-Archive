---
title: "Add/Remove Applications Not Displaying after sudo apt-get"
date: 2006-06-07
forum: Desktop Environments
---

### Post by kmfdmk on 2006-06-07
Fresh install onto a HP ZE5170 laptop 60GB hdd, 512mb ram, P4.
This is a dual boot with XP Home/NTFS taking the first 52 GB.

Ubuntu installed on 2 GB ext2 partition
1 GB ext3 Home logical extended (unassigned right now not sure how)
1 GB fat32 logical extended (to swap files between OS's)
950 MB Linux Swap partition

Got Dapper Drake (6.06) installed no problem.  
Ran the updates, (got 11 updates) no problem.
Downloaded & unpacked Kismet no problem.
Got a message about 98% of the 2 GB partition was used (had about 95 MB free) clicked ok & continued.

Ran ./configure to I think compile Kismet... got an error.

Check config.log  I got this error:

configure: error: no acceptable C compiler found in $PATH

[Found this and typed it in a console]("http://www.ubuntuforums.org/showpost.php?p=1091052&postcount=2")
```
sudo apt-get install build-essential
```

[B]install build-essential successfully completed no problem.

Re-Ran ./configure got an error about not enough disk space.

Attempted to start up Add/Remove Applications, the loading window comes up, but when the progress gets to 100% the window disappears.[/B]

I wanted to install Qtpart to resize the 2GB partition if it's going to be an issue or uninstall the games & other unneeded sfwe.

Please assist or point in the right direction.

Thanks,

Rusty

---

### Post by caldevil on 2006-06-07
Resizing ext3 extended partition can be a real pain. IMO first thing you do is mount your /home to 1GB patition that is currently unassigned.

---

### Post by kmfdmk on 2006-06-10
*bump*

---

