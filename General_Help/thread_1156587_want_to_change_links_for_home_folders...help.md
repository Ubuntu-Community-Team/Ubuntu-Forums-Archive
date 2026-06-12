---
title: "want to change links for home folders...help"
date: 2009-05-11
forum: General Help
---

### Post by zero7404 on 2009-05-11
i have a laptop with 2 hard drives, the first has vista and ubuntu on it, the second i have formatted in ntfs and have all my personal stuff on it.

in vista i have my documents folders from the OS looking at the corresponding folders on the second drive, for example: when in Vista, the Document object is linked to a folder with the same name on the second disk, so all my documents are on the second disk (non-OS). etc...for music, pictures, so on....

i'd like to do something similar with my ubuntu installation. i'd like some of the folders in home to look at the locations i specify on the second disk.

so i'd like both ubuntu and vista to work with the same directories with respect to the following:

Documents
Music
Pictures
Videos
Downloads

is it possible to use links to achieve this ?

---

### Post by taurus on 2009-05-11
Yes, you can create links from your $HOME to those directories on the second harddrive.

Assuming your second harddrive is mounted to /media/sdb1, you would do something like

```
ln -s /media/sdb1/Downloads ~/Downloads
ls -la ~
```

---

### Post by zero7404 on 2009-05-11
> **taurus said:**
> Yes, you can create links from your $HOME to those directories on the second harddrive.

Assuming your second harddrive is mounted to /media/sdb1, you would do something like

```
ln -s /media/sdb1/Downloads ~/Downloads
ls -la ~
```

taurus, hey....

thanks for the prompt response
so, if i issue this for all the folders i want, they will be linked until i unlink them, regardless of restarts, etc..?
i have the second drive set to automount when the OS starts. if i need to unmount it then remount it, am i still ok ?

can i ask what the ~ means in the first command ?

skimming thru the ubuntu pocket guide pdf, i spotted the ~ in the ls command, but i don't know what it means there either.

---

### Post by Bios Element on 2009-05-11
~ Stands for your /home/<user> directory.

---

### Post by zero7404 on 2009-05-11
so i'm creating a symbolic link to the corresponding directory on the second disk. 

is the path the mountpoint that is also displayed in gparted ? or must it reference the physical disk /dev/sdb1 ? my mountpoint is shown as /media/Storage

---

