---
title: "can't elliminate folder with files in recyclage bin"
date: 2009-02-05
forum: General Help
---

### Post by bertolo on 2009-02-05
Hi!
 i can't eliminate a folder from bin, i can't restore i can't do nothing with it. the folder is full of files.
any solution ?

---

### Post by fooman on 2009-02-05
the trash is located at "~/.local/share/Trash/files/"....so you could try emptying it from a terminal with this command:

```
rm -rf ~/.local/share/Trash/files/*
```if that doesn't do it, or you see an error about not having permission...  try putting a sudo in front:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

hope that helps.

---

### Post by drs305 on 2009-02-05
If you open your file browser with admin privileges and you can browse and delete *any* folder. Note: *Any* folder includes system files, so know what you are deleting before you do it. Since the deleted files may belong to 'root', use SHFT-DELETE to bypass the Trash bin (but again, be careful - once they are deleted in this manner you cannot get them back).

```
gksudo nautilus
```

---

### Post by bertolo on 2009-02-05
don't work. don't say nothing and the folder still there.
i don't know where is ~/local/share :/

---

### Post by whitegourd on 2009-02-05
> **bertolo said:**
> don't work. don't say nothing and the folder still there.
i don't know where is ~/local/share :/

It's in a hidden directory ...  ~/.local/share
don't forget the dot (.)

---

### Post by fragos on 2009-02-05
If you move to trash a folder that contains files owned by root you can't empty the trash bin without changing ownership to yourself.

---

### Post by drs305 on 2009-02-05
> **bertolo said:**
> don't work. don't say nothing and the folder still there.
i don't know where is ~/local/share :/

If you are trying to browse to it, open nautilus as I advised, click on your username in the Places pane (left side), then CTRL-H if you can't see ".local" in the right pane. CTRL-H will allow you to see hidden folders/files. Click on ".local", then "share" and one of the folders you should see is "Trash", which contains "files" and "info" folders.

For root trash, click on "File System" in the left, the on the right side "root", then ".local", "share", then "Trash".

---

### Post by thelugnut on 2009-02-05
I believe the corrcect code is:

 > rm -r -i <folder name>

You might need a "sudo", If the folder is protected.

---

### Post by bertolo on 2009-02-05
ok i found the ~/.local/share/files but files only have 1 file that is xorg.conf.backup
:/

---

### Post by drs305 on 2009-02-05
Perhaps it's just time to refer you to a tutorial on how to delete Trash:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")
You can probably start with Section 6.

---

