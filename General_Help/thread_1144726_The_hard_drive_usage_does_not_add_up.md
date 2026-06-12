---
title: "The hard drive usage does not add up"
date: 2009-05-01
forum: General Help
---

### Post by rasungod_7 on 2009-05-01
Hi,

So I have the same problem as user 982000971 where the Hard Disk Usage Analyzer does not add up. Here is his post.

[http://ubuntuforums.org/showthread.php?t=679946]("http://ubuntuforums.org/showthread.php?t=679946")

I followed what was done in that post and I found that I have a 46GB file in /root. I don't remember ever using root for anything other than sudo apt-get... etc. I am new to linux so it is very possible that I am doing something wrong.

I used the ```
du -h --max-depth=1
``` code to find that all 46GB are in "./. local" 

This is the output when I try and list the files that are in root...
```
:/root$ ls
Desktop
```

Here is the output from the ```
sudo du -h --max-depth=1
``` command
:/root$ sudo du -h --max-depth=1
12K	./.config
4.0K	./.pulse
8.0K	./.hplip
40K	./.gnome2
4.0K	./Desktop
4.0K	./.icedteaplugin
4.0K	./.wapi
46G	./.local
4.0K	./.debtags
436K	./.gstreamer-0.10
528K	./.synaptic
8.0K	./.nautilus
4.0K	./.aptitude
4.0K	./.gnome2_private
128K	./.gconf
12K	./.dbus
12K	./.gconfd
3.7M	./.mozilla
46G	.

Why don't I see all these things when is us "ls"?
How do i remove that huge 46GB file?
How did this happen? What steps can I take in the future so that this kind of thing doesn't happen to me again.
What exactly does the "/." mean?

Thanks,

Rasungod_7

---

### Post by mc4man on 2009-05-01
.local isn't a file, it's a hidden directory in your home folder ( all . <name> are hidden files or directories.

Go to  your home folder, open up .local and see what's in there 

(if you don't see it go Ctrl+h when in home folder or view -> show hidden files

Mainly some config folders, files and .desktops are in .local and your trash folder which is a likely suspect.

(check the properties of folders to see size

---

### Post by cariboo on 2009-05-01
Open Nuatilus as root, press Alt-F2 and type:

```
gksu nautilus
```

This will open nautilus as root, next press Ctrl-h to reveal the hidden files and directories, navigate to .local, which is where root's trash directory is located and remove the trash.

---

### Post by rasungod_7 on 2009-05-01
When I do the control + h and open the .local folder, there is a share folder.

The .local folder contains 81 items, totaling 428.6KB

The trash in the .local folder contains 15 items, totaling 88.0KB

---

### Post by rasungod_7 on 2009-05-01
> **cariboo907 said:**
> Open Nuatilus as root, press Alt-F2 and type:

```
gksu nautilus
```

This will open nautilus as root, next press Ctrl-h to reveal the hidden files and directories, navigate to .local, which is where root's trash directory is located and remove the trash.

I found the file. You were right, it was in the root trash. It is a back up file that was left over from when I was using the back up program Simple Back Up.

I tried to delete it but it would let me. Highlight the folders and press delete. The files would disappear for a moment then pop back.

---

### Post by rasungod_7 on 2009-05-01
I was able to delete the files. Just highlighting them and pressing delete didn't work.

I had to use ```
sudo rm
```

for all the files in the back up folder 

then I used ```
sudo rmdir
```

to remove the folder.

Because of all this I am tried to remove simplebackup using synaptic but it says that is not installed. I couldn't find a file for it in the /var/lib folder or the /bin folder. Yet it is sitting there in System-> Administration

This didn't work either...
```
sudo dpkg --remove --force-remove-simplebackup
```



How do I get rid of the program simplebackup?

As a side question, should I make this a new thread?

Thanks,

Rasungod_7

---

### Post by CatKiller on 2009-05-01
> **rasungod_7 said:**
> I was able to delete the files. Just highlighting them and pressing delete didn't work.

You were running the file browser as root. Looking at root's Trash. Pressing Delete on a file moves it to the Trash... you can probably guess what happens next.

For reference, Shift-Delete in Nautilus deletes a file without just moving it to Trash. Or you can empty the Trash in Nautilus. There is the option of including a Delete command that doesn't move things to the Trash in the context menu (right-click) but I think you have to specifically enable it in Nautilus' preferences.

EDIT: You should probably start a new thread about removing simplebackup to get new eyes, but your dpkg command has an erroneous - between force-remove and simplebackup. Although it's possible that simplebackup just didn't take its menu entry with it when you uninstalled it.

---

### Post by drs305 on 2009-05-01
SimpleBackup is listed as sbackup in synaptic/apt.

For lots of details on disk file sizes, finding lost disk space and finding/deleting trash, refer to the two links in my signature line. (It even covers why root trash doesn't delete if you just press the delete key ;-) ).

---

### Post by rasungod_7 on 2009-05-01
> **CatKiller said:**
> You were running the file browser as root. Looking at root's Trash. Pressing Delete on a file moves it to the Trash... you can probably guess what happens next.

For reference, Shift-Delete in Nautilus deletes a file without just moving it to Trash. Or you can empty the Trash in Nautilus. There is the option of including a Delete command that doesn't move things to the Trash in the context menu (right-click) but I think you have to specifically enable it in Nautilus' preferences.

Ha! Yeah that makes sense, I would try and delete files in the Trash folder only to send them to the Trash folder. 

Thanks for the help, I removed the offending files and was able to remove simple backup program as well.

Thanks again

Rasungod_7

---

