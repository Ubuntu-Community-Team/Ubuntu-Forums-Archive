---
title: "Is there an &quot;undo trash&quot; option?"
date: 2009-02-08
forum: General Help
---

### Post by J-Rod on 2009-02-08
Here's the rub. I have ~30gb left in my storage drive. I have accidentally sent a folder containing 78GB of data to trash. Now I cannot move it back out of the trash to where it's supposed to be because the OS complains there's not enough space. Is there a magical terminal way to get around this?

---

### Post by drs305 on 2009-02-08
When you delete a file it goes into the Trash bin but still takes up space. 

You should be able to open nautilus and move the files back to their original location since you are moving them from one place to another and thus not taking up any more space (or right click, Restore, which I suppose you have tried):
```

nautilus ~/.local/share/Trash

```

You asked for a command line solution, you could try:
```
mv ~/.local/share/Trash/files/* /path.to.new.location

```

If you added other files to your system since you deleted those files you will have to make space on your system to restore the Trash files.

To make space, you can remove packages from the cache:
```

sudo apt-get autoclean
sudo apt-get clean

```
or you can delete Trash that you *don't* want to save by using SHIFT-DEL. 

You can also inspect your root trash to see if there are files in there taking up space. Root's trash in recent ubuntu versions is located at /root/.local/share/Trash. Open nautilus with admin privileges and use SHIFT-DEL to remove Trash. Note that by using this command you can delete *anything*, including system files. Be careful since files deleted with SHIFT-DEL are not recoverable.
```

gksudo nautilus /root/.local/share/Trash

```

---

### Post by J-Rod on 2009-02-08
Yeah I understand the why of the problem. I was just wondering if there was a way to basically undo the operation without needing to actually move the data. Meaning the data is likely still in the same physical location on the disk, the OS just needs to have the pointer info to change, indexing it back to where it was before the trash operation. I guess I can just move it across in chunks of 20gb at a time, move - delete - move - delete. I was just hoping there was a more elegant way to do it. Of course in Windows it would be right click - undo, but I can't say I have encountered the same issue in that OS, it might be exactly the same problem. :)

---

### Post by drs305 on 2009-02-08
I was editing my reply when you posted again. The "mv" command or the "right click/Restore" should work for you and I've expanded some of the other suggestions.

---

### Post by J-Rod on 2009-02-08
Thanks for your reply, I have already started moving the data in manageable hunks.

I might revisit this later on a test machine. I was thinking in a what-if scenario, you have a contiguous database file, 100gb, and accidentally somehow send it to trash, you'd have a major issue if you couldn't move it back, especially if it's a live server. Yeah not likely to happen, but you never know! :)

---

### Post by mister_pink on 2009-02-08
Moving it should be fine - if its on the same partition then the OS should just automatically update the file system so it appears in the right place rather than physically moving all the data. Only if its on a different partition or physical disk should there be any actual movement.

---

### Post by zazuge on 2009-05-18
i searched too but didn't find anything 
it seems this feature will be (or is) implemented in the 8.10 and bove
so i used this little trick 
assuming that gnome use the new trash directory structure 
it records trashed files info in .local/trash/info in user home and in .Trash-[UID]/info in other partitions

cd .local/trash/files (or .Trash-UID/files )
for x in *.* ;do echo mv "$x"  "$(cat  "../info/$x.trashinfo"|grep Path|cut -f2 -d'=')" ;done
it seems that trash directories in places like /mnt 
cant know their origin so you may have to add /mnt/ before 
beware test before you lunch this script
if you are sure delete the echo before the mv ;)

---

